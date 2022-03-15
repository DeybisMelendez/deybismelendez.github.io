---
layout: post
title: Primer día en la academia de ajedrez
---
{% include canvaschess.html %}

Ayer fue mi primer día en la academia de ajedrez, vimos temas básicos sobre el ajedrez, sobre como se mueven las piezas, el valor de las piezas, principios de apertura y mates básicos. Luego jugamos partidas blitz para practicar.

## El valor de las piezas

| Pieza | Valor |
| --- | --- |
| Peón | 1 |
| Caballo | 3 |
| Alfil | 3 |
| Torre | 5 |
| Dama (reina) | 9 |

Algo que no se mencionó pero ya conocía es el valor del Rey, este tiene un valor infinito ya que es el objetivo principal del oponente.

# El valor es relativo

Estos valores que damos a las piezas son relativos, al inicio de la partida valen eso, sin embargo, el valor de una pieza puede cambiar según su posición, por ejemplo, un peón que está por coronar vale mucho mas que 1 punto y un Alfil encerrado podría no valer nada. Una pieza por dar jaque mate podría tener un valor mayor que la Dama.

# Alfiles vs Caballos

En posiciones cerradas, con estructuras de peones complejas, los caballos valen mas que los alfiles, sin embargo, en posiciones abiertas, con mucho espacio, los alfiles valen mas, sobre todo si se tiene la pareja, debido a la distancia que pueden recorrer.

# Principios básicos de apertura

1. Desarrollar piezas, es importante sacar las piezas a jugar, sin que se estorben y estén defendidas entre ellas mismas.

2. Luchar por el centro, ganar el centro da ventaja contra el oponente, se entiende por centro a las casillas e5,d5,e4,d4 y sus alrededores también son importantes.

3. Asegurar al rey, esto en pocas palabras, enrocar.

# Apertura

Nos dijeron que jugaramos aperturas con e4 para empezar, siguiendo los principios. Por suerte yo ya conozco algunas aperturas, las que mas juego son la Italiana, Petrov, Defensa de los 2 Caballos y Española o Ruy Lopez. Sobretodo la Italiana.

# Partidas jugadas

Como fue en blitz, no anoté ni grabé ninguna partida, pero si recuerdo bien una de ellas, ya que me puse en aprietos muy pronto, sin embargo logré remontar, intenté recordar cómo jugamos, yo jugué con negras:

<script>
    var viewer = new CHESS.PgnViewer({
        pgn_text: '%5BSite%20%22Academia%20Ajedrez%20Alcaldia%20Managua%22%5D%0A%5BDate%20%222021.03.15%22%5D%0A%5BWhite%20%22Oponente%22%5D%0A%5BBlack%20%22Deybis%20Melendez%22%5D%0A%5BResult%20%220-1%22%5D%0A%5BTermination%20%22Oponente%20won%20by%20checkmate%22%5D%0A1.%20e4%20e5%202.%20Nf3%20Nc6%203.%20Bc4%20Nf6%204.%20Ng5%20Nxe4%205.%20Nxf7%20Qf6%206.%20O-O%20Bc5%207.%20Nxh8%20Nxf2%208.%20Qe2%20Ne4%2B%209.%20Kh1%20Ng3%2B%2010.%20hxg3%20Qh6%2B%2011.%20Qh5%2B%20Qxh5%23%200-1',
        piece_set: 'https://s3.amazonaws.com/canvas-chess/pieces/merida'
    });
</script>

Investigando un poco descubrí que la variante que jugamos se llama [Ataque Fegatello](https://es.wikipedia.org/wiki/Defensa_de_los_dos_caballos){:.link-light} o ataque del hígado frito xD.

La partida fue a 5 minutos, por lo que hay errores por montón, pero me pareció bonita la combinación, excepto que después analizando mi partida vi que era mejor 7... Axf2 en lugar de 4...Cxf2 que es mas floja, se realiza la misma combinación sin realizar el jaque a la descubierta. Obviamente el blanco pudo defender mejor sacrificando la torre.

Yo suelo jugar 3...Ac5 entrando en la línea principal de la italiana, pero esta vez quise jugar con la variante de la defensa de los dos caballos con 3...Cf6. No me esperaba la jugada 4. Cg5 (ataque fegatello) amenazando ataque doble, aunque no es la primera vez que me lo aplican. En el momento que jugué Cxe4 pensé que no era la mejor jugada y que yo estaba perdiendo por el ataque doble, luego investigando ví que la jugada principal es jugar d5 directamente, yo pensé que si el blanco decide capturar el caballo, luego jugaría d5 atacando al alfil y caballo recuperando pieza, quise aventarme a jugar mas agresivo pensando en que mi rival podría cometer el error de jugar materialista y así fue porque decidió capturar el peón con el caballo, que según stockfish era mucho mejor capturar con el alfil quitandome el enroque.

La Mildred ha jugado muy bien ese día, hemos estado jugando de vez en cuando en clase de arte y en chess.com y ha estado estudiando conmigo aperturas y algunos motivos tacticos, me sorprendió mucho ver que le ganó a Nelson Córdoba por tiempo y a Rafael Vargas practicamente le capturó todas sus piezas. Sin duda ella me va a superar pronto.

Algunas fotos que tomamos:

![foto 1](https://i.postimg.cc/zLsCyQmm/academia-ajedrez-dia-1-1.jpg)

![foto 2](https://i.postimg.cc/B8L5Q0Vc/academia-ajedrez-dia-1-2.jpg)

![foto 3](https://i.postimg.cc/K1sr2zJ8/academia-ajedrez-dia-1-3.jpg)