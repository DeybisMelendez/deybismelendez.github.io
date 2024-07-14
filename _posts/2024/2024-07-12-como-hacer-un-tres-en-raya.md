---
title: Como hacer un tres en raya
layout: post
tag: programación
---

Decidí hacer una IA de Tres en Raya sencillo porque me entró curiosidad conocer cuantas posiciones posibles se pueden alcanzar en el juego. Luego de desarrollarlo, llegué a la siguiente conclusión:

| Jugadas (Depth) |  Nodos  | Victoria Primer Jugador  | Victoria Segundo Jugador |
| :-------------: | :-----: | :----------------------: | :----------------------: |
|       1         |   9     |   ---   |    ---    |
|        2        |     72  |  ---    |  ---      |
|        3        | 504     | ---     |  ---      |
|        4        | 3024    | ---     |  ---      |
|       5         |   15120 |   1440  |    ---    |
|       6         |   56160 |   1440  |    5328   |
|       7         |  154944 |  49392  |   5328    |
|       8         |  255168 |  49392  |   77904   |
|       9         |  255168 |  131184 |   77904   |

El juego contiene 255,168 estados posibles, de los cuales el primer jugador gana 131,184, el segundo jugador gana 77,904 y 46,080 son empates.

Me llamó mucho la atención que en el Depth 8 y 9 da la misma cantidad de nodos, pero esto puede ser porque la última jugada solo sirve para definir el resultado final de la partida (empate o victoria para el primer jugador). Si suponemos una posición cualquiera en la séptima jugada, quedarán dos casillas disponibles para rellenar, la última jugada no suma mas a los nodos porque solo queda una jugada por realizar. El contador por tanto a partir de la séptima jugada sumará 2 posiciones posibles por cada estado, y en la octava jugada solo sumaría 1 por cada estado (que son 2), entonces la suma es la misma. En pocas palabras, la octava jugada define a la novena jugada de manera implícita.

![Ejemplo de nodos en séptima jugada](https://i.postimg.cc/YSRrmKDQ/Captura-de-pantalla-2024-07-14-10-09-21.png)

Para resolver este juego se puede utilizar el algoritmo [Minimax](https://en.wikipedia.org/wiki/Minimax), en este caso he utilizado la variante [negamax](https://en.wikipedia.org/wiki/Negamax) que es mas simplificada pero no menos complejo.

Para la representación del juego decidí utilizar [bitboards](https://es.wikipedia.org/wiki/Bitboard) para minimizar los recursos necesarios, aunque hubiera bastado con utilizar arrays, ya que el juego es bastante corto.

El programa lo desarrollé en javascript para luego hacer un minijuego en HTML. Puede encontrar el proyecto completo en [Github](https://github.com/DeybisMelendez/tres-en-raya). O probarlo directamente en este blog [aquí](https://deybismelendez.github.io/tres-en-raya/).

{% highlight js %}
// ticTacToeAI.js
class TicTacToeAI {
    board = [
        0b000000000, // Tablero Primer jugador
        0b000000000, // Tablero Segundo jugador
    ]
    FIRST_PLAYER = 0
    SECOND_PLAYER = 1
    DRAW_PATTERN = 0b111111111
    WIN_PATTERN = [
        0b100100100,
        0b010010010,
        0b001001001,
        0b111000000,
        0b000111000,
        0b000000111,
        0b100010001,
        0b001010100
    ]
    MOVE_PATTERN = [
        0b100000000,
        0b010000000,
        0b001000000,
        0b000100000,
        0b000010000,
        0b000001000,
        0b000000100,
        0b000000010,
        0b000000001,
    ]
}
{% endhighlight %}

## Bitboards

Los [bitboards](https://es.wikipedia.org/wiki/Bitboard) son números binarios donde cada bit representa la ocupación de una casilla en el tablero, en este caso se requieren 9 bits para representar un tablero de Tres en Raya y un tablero separado para cada jugador, en total 18 bits, se podría utilizar un solo bitboard de 18 bits para todo el tablero, pero decidí mantener separado ambos jugadores para no hacer mas complicado el desarrollo. De esta manera, se puede utilizar operadores bit a bit para realizar jugadas, deshacer jugadas, validar victorias, etc.

La representación de [números binarios en Javascript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Numbers_and_dates#binary_numbers) se escribe con "0b" y luego el número binario, esto facilita mucho escribir las posiciones pero en otros lenguajes de programación se puede utilizar directamente números enteros o hexadecimales para la representación de los bitboards.

![Orden de los bits](https://i.postimg.cc/fyFjQ6w4/Captura-de-pantalla-2024-07-12-15-23-56.png)

Es importante conocer el orden en que identificar cada casilla, la representación en binario se daría con el patrón 012345678, por ejemplo:

![Ejemplo de bitboard](https://i.postimg.cc/NjtbGv6Y/Captura-de-pantalla-2024-07-12-15-32-49.png)

Este sería una representación bitboard de un jugador, el número binario se escribiría 111010001.

Es por esto que escribí un array con dos tableros, uno para cada jugador, donde ambos inician con las casillas vacías (0b000000000).

DRAW_PATTERN tiene todos los bits en 1 (0b111111111). Al comparar bit a bit con los dos tableros se podría conocer de manera eficiente si el juego es empate luego de validar las victorias.

WIN_PATTERN es un array que contiene todos los patrones de líneas para ganar (en total 8), que incluye 3 líneas en horizontal, 3 líneas en vertical y 2 líneas en diagonal. El primer item de WIN_PATTERN es 0b100100100, como ejemplo visual:

![Representación del primer patrón de WIN_PATTERN](https://i.postimg.cc/WzXpDvdK/Captura-de-pantalla-2024-07-12-15-41-50.png)

MOVE_PATTERN, debido a que una jugada es ocupar una casilla vacía, es bastante fácil representar las jugadas del juego en bitboard, solo es ocupar un bit en cada una de las 9 casillas. Luego solo se itera a través de la lista y se valida si la casilla está vacía, de esta manera se puede obtener la jugada.

## Generación de jugadas

{% highlight js %}
generateMoves() {
    let moves = []
    let allBoard = this.board[this.FIRST_PLAYER] | this.board[this.SECOND_PLAYER]
    for (let i = 0; i < this.MOVE_PATTERN.length; i++) {
        if ((this.MOVE_PATTERN[i] & allBoard) == 0) {
            moves.push(this.MOVE_PATTERN[i])
        }
    }
    return moves
}
{% endhighlight %}


Para generar y validar las jugadas se necesita aplicar [operadores binarios](https://es.wikipedia.org/wiki/Operador_a_nivel_de_bits), primero se requiere conocer todas las casillas que están ocupadas por ambos jugadores, para validar cuales están vacías. Esto se puede realizar con el operador bit a bit OR. Ejemplo:

![Ejemplo del operador OR en la generación de jugadas](https://i.postimg.cc/50knfP1V/Captura-de-pantalla-2024-07-12-16-37-30.png)

De esta manera todos los bits en cero serían jugadas posibles del juego.

Luego se debe iterar a través de todos los patrones de jugadas, y con el operador bit a bit AND, se puede validar si la casilla de la jugada está vacía y por tanto es posible ocuparla. Ejemplo:

![Ejemplo del operador AND en la generación de jugadas](https://i.postimg.cc/YS5TxscS/Captura-de-pantalla-2024-07-12-15-58-01.png)

En el ejemplo se puede observar que el resultado de la operación da cero, esto significa que la jugada es posible de realizar porque la primer casilla del tablero está vacía.

Conociendo todo esto, se vuelve fácil determinar las victorias y empates:

{% highlight js %}
isDraw() {
    if ((this.board[this.FIRST_PLAYER] | this.board[this.SECOND_PLAYER]) == this.DRAW_PATTERN) {
        return true
    }
    return false
}
isEndGame() {
    for (let i = 0; i < this.WIN_PATTERN.length; i++) {
        if ((this.board[this.FIRST_PLAYER] & this.WIN_PATTERN[i]) == this.WIN_PATTERN[i] ||
            (this.board[this.SECOND_PLAYER] & this.WIN_PATTERN[i]) == this.WIN_PATTERN[i]) {
            return true
        }
    }
    return false
}
{% endhighlight %}

Para validar el empate solo se debe unificar los tableros de cada jugador y validar si todas las casillas están ocupadas, para una validación mas exacta tendría que verificarse que en ese estado no hay victoria de ningún jugador, por eso el orden es importante.

En el caso de la victoria, solo es cuestión de compararlo con los patrones de victoria, similar a la generación de movimientos.

## Hacer y Deshacer jugadas

Es importante hacer y deshacer jugadas para poder iterar a través de todo el árbol de variantes del juego.
{% highlight js %}
makeMove(turn, move) {
    if (turn == 1) {
        this.board[this.FIRST_PLAYER] |= move
     } else {
         this.board[this.SECOND_PLAYER] |= move
    }
}
    
unMakeMove(turn, move) {
    if (turn == 1) {
        this.board[this.FIRST_PLAYER] ^= move
    } else {
        this.board[this.SECOND_PLAYER] ^= move
    }
}
{% endhighlight %}

El turno tendría dos valores, +1 para el primer jugador y -1 para el segundo jugador, esto es para facilitar la evaluación de los estados del juego.

Lo que hacen el make y unmake es simplemente agregar el bit de la jugada en la casilla vacía y eliminarla si se deshace.

## Algoritmo Negamax

{% highlight js %}
negamax(turn) {
    if (this.isEndGame()) {
        return -turn * turn
    } else if (this.isDraw()) {
        return 0
    }
    let moves = this.generateMoves()
    let maxScore = -1000
    for (let i=0; i < moves.length; i++) {
        this.makeMove(turn, moves[i])
        maxScore = Math.max(maxScore, -this.negamax(-turn))
        this.unMakeMove(turn, moves[i])
    }
    return maxScore
}
{% endhighlight %}

El algoritmo [negamax](https://en.wikipedia.org/wiki/Negamax) es una manera simplificada del [Minimax](https://en.wikipedia.org/wiki/Minimax), se basa en el supuesto de que **MIN() == -MAX()** o viceversa **MAX() == -MIN()**. Con esto se puede simplificar la implementación de Minimax en una sola función jugando con la negación de la evaluación, en lo personal me siento mucho mas cómodo con este algoritmo que con el original, aunque es mas complicado de manejar.

El pseudo código sería el siguiente:

{% highlight c %}
int negaMax( int depth, int turn ) {
    if ( depth == 0 || isNodeTerminal() ) return evaluate() * turn;
    int maxScore = -oo;
    for ( all moves)  {
        score = -negaMax( depth - 1, -turn );
        if( score > maxScore )
            maxScore = score;
    }
    return maxScore;
}
{% endhighlight %}

Es importante que la valoración final del negamax se multiplique por el turno que mueve (+1 para el primer jugador, -1 para el segundo jugador), esto es porque la valoración del segundo jugador siempre será negativa.

## Obtener la mejor jugada

Al desarrollador no le interesa tanto la evaluación, si no obtener la mejor jugada, para ello podemos envolver en otra función el Minimax y buscar la jugada con la mejor evaluación:

{% highlight js %}
getBestMove(turn) {
    let moves = this.generateMoves()
    let bestScore = -1000
    let bestMove = 0
    for (let i = 0; i < moves.length; i++) {
        this.makeMove(turn,moves[i])
        let score = -this.negamax(-turn)
        if (score > bestScore) {
            bestScore = score
            bestMove = moves[i]
        }
        this.unMakeMove(turn,moves[i])
    }
    return this.MOVE_PATTERN.indexOf(bestMove)
}
{% endhighlight %}

La razón por la que prefiero devolver el index y no el número binario es para que sea mas fácil ver cual es la jugada que se quiere realizar, ya que esta función sirve de comunicación con el usuario.

Por ejemplo, si la función devuelve 0, significa que la primer jugada es la primer casilla del tablero, la esquina superior izquierda, y si devuelve 8 sería la esquina inferior derecha.

Para realizar un movimiento entonces solo bastaría con algo como:

{% highlight js %}
ticTacToe.makeMove(turn,ticTacToe.MOVE_PATTERN[myBestMove])
{% endhighlight %}

Con todo esto ya puedes hacer jugadas, deshacer jugadas, y obtener las mejores jugadas. Suficiente para implementar un juego contra la IA.

Si desea jugar contra esta IA puede hacerlo dando clic [aquí](https://deybismelendez.github.io/tres-en-raya/).

## Performance Test

He agregado funcionalidad para encontrar estadísticas del juego (mi objetivo original), con ello obtuve la información que mostré al inicio.

El [Perft](https://www.chessprogramming.org/Perft) es una prueba para encontrar bugs, si el resultado no coincide con los valores ya calculados antes, entonces hay un error que corregir. Originalmente se trata de buscar todos los nodos posibles a partir de la posición inicial, yo añadí otras estadísticas como la cantidad de empates y victorias.

La función perft es similar al Negamax pero este no busca evaluación si no solo contar los nodos.

{% highlight js %}
perft(depth, turn) {
    if (this.isFirstPlayerWin()) {
        this.firstPlayerWinCount++
        return 1
    } else if (this.isSecondPlayerWin()) {
        this.secondPlayerWinCount++
        return 1
    } else if (this.isDraw()) {
        this.drawsCount++
        return 1
    }
    if (depth == 0) {
        return 1
    }
    let total = 0
    let moves = this.generateMoves()
    for (let i=0; i < moves.length; i++) {
        this.makeMove(turn, moves[i])
        total += this.perft(depth-1, -turn)
        this.unMakeMove(turn, moves[i])
    }
    return total
}
{% endhighlight %}

El código completo lo puede encontrar [aquí](https://github.com/DeybisMelendez/tres-en-raya).