---
layout: post
title: Jaque mates y finales básicos en ajedrez
---

{% include canvaschess.html %}

El último día me pusieron a practicar jaque mates básicos y finales con peones, nos saltamos los mates de torre y rey, dama y rey, etc porque ya los manejo, pero igualmente me puse a practicarlos contra la pc buscando la manera mas rápida y tratando de no cometer errores que alarguen el final.

# Rey y torre contra Rey

El mas básico de todos, el objetivo es acorralar al rey en una fila o columna usando la torre como delimitador, luego hacer que el rey se coloque enfrente a nuestro rey quitando las casillas de escape para dar mate con la torre. Según capablanca en cualquier posición se debería dar mate en menos de 20 jugadas.

Ejercicio 1:

<script>
    var viewer = new CHESS.PgnViewer({
        pgn_text: "%5BEvent%20%22vs%20Computer%22%5D%0A%5BSite%20%22Chess.com%22%5D%0A%5BDate%20%222021.03.24%22%5D%0A%5BRound%20%22%3F%22%5D%0A%5BWhite%20%22Deybis%20Melendez%22%5D%0A%5BBlack%20%22Maximum%22%5D%0A%5BResult%20%221-0%22%5D%0A%5BSetUp%20%221%22%5D%0A%5BFEN%20%227k%2F8%2F8%2F8%2F8%2F8%2F8%2FR6K%20w%20-%20-%200%201%22%5D%0A%5BTimeControl%20%22-%22%5D%0A%0A1.%20Ra7%20Kg8%202.%20Kg2%20Kf8%203.%20Kf3%20Ke8%204.%20Ke4%20Kd8%205.%20Kd5%20Kc8%206.%20Kd6%20(6.%20Kc6%20Kd8%20%7Balargando%20el%20mate%7D)%206...%20Kb8%207.%20Rh7%20Kc8%208.%0ARg7%20%7BPierdo%20un%20tiempo%20para%20obligar%20al%20rey%20ir%20a%20la%20esquina%7D%208...%20Kb8%20(8...%20Kd8%209.%20Rg8%23)%209.%20Kc6%20Ka8%2010.%20Kb6%20Kb8%2011.%20Rg8%23%201-0",
        piece_set: 'https://s3.amazonaws.com/canvas-chess/pieces/merida',
    });
</script>

Ejercicio 2:

Con el rey en el centro, solo hay que conseguir que el rey contrario se coloque en frente de nuestro rey, para hacer que retroceda con la torre.

<script>
    var viewer = new CHESS.PgnViewer({
        pgn_text: "%5BEvent%20%22vs%20Computer%22%5D%0A%5BSite%20%22Chess.com%22%5D%0A%5BDate%20%222021.03.24%22%5D%0A%5BRound%20%22%3F%22%5D%0A%5BWhite%20%22Deybis%20Melendez%22%5D%0A%5BBlack%20%22Maximum%22%5D%0A%5BResult%20%221-0%22%5D%0A%5BSetUp%20%221%22%5D%0A%5BFEN%20%228%2F8%2F8%2F4k3%2F8%2F8%2F8%2F4K2R%20w%20-%20-%200%201%22%5D%0A%5BTimeControl%20%22-%22%5D%0A%0A1.%20Ke2%20Ke4%202.%20Rh4%2B%20Kd5%203.%20Ke3%20Ke5%204.%20Rh5%2B%20Kd6%205.%20Ke4%20Kc6%206.%20Kd4%20Kd6%207.%20Rh6%2B%20Kd7%0A8.%20Ke5%20Kc7%209.%20Kd5%20Kb7%2010.%20Kc5%20Kc7%2011.%20Rh7%2B%20Kd8%2012.%20Kd6%20Ke8%2013.%20Ra7%20Kf8%2014.%20Ke6%0AKg8%2015.%20Kf6%20Kh8%2016.%20Kg6%20Kg8%2017.%20Ra8%23%201-0",
        piece_set: 'https://s3.amazonaws.com/canvas-chess/pieces/merida',
    });
</script>

Ejercicio 3:

<script>
    var viewer = new CHESS.PgnViewer({
        pgn_text: "%5BEvent%20%22vs%20Computer%22%5D%0A%5BSite%20%22Chess.com%22%5D%0A%5BDate%20%222021.03.24%22%5D%0A%5BRound%20%22%3F%22%5D%0A%5BWhite%20%22Deybis%20Melendez%22%5D%0A%5BBlack%20%22Maximum%22%5D%0A%5BResult%20%221-0%22%5D%0A%5BSetUp%20%221%22%5D%0A%5BFEN%20%227R%2F8%2F8%2F3k4%2F8%2F8%2F8%2FK7%20w%20-%20-%200%201%22%5D%0A%5BTimeControl%20%22-%22%5D%0A%0A1.%20Kb2%20Kd4%202.%20Kc2%20Ke4%203.%20Kd2%20Kd4%204.%20Rh4%2B%20Kd5%205.%20Ke3%20Kc5%206.%20Kd3%20Kd5%207.%20Rh5%2B%20Kd6%0A8.%20Ke4%20Kc6%209.%20Kd4%20Kd6%2010.%20Rh6%2B%20Kd7%2011.%20Ke5%20Kc7%2012.%20Kd5%20Kb7%2013.%20Kc5%20Kc7%2014.%20Rh7%2B%0AKd8%2015.%20Kd6%20Ke8%2016.%20Ra7%20Kf8%2017.%20Ke6%20Kg8%2018.%20Kf6%20Kh8%2019.%20Kg6%20Kg8%2020.%20Ra8%23%201-0",
        piece_set: 'https://s3.amazonaws.com/canvas-chess/pieces/merida',
    });
</script>

Probé varias posiciones y como no soy Capablanca en muchas tardé poco mas de 20 jugadas.

# Rey y Dama contra Rey

Aquí se aplica lo mismo que con la torre con la adición de que la Dama se mueve en diagonal haciendo que sea mas fácil quitarle espacio al rey contrario.

Ejercicio:

<script>
    var viewer = new CHESS.PgnViewer({
        pgn_text: "%5BEvent%20%22vs%20Computer%22%5D%0A%5BSite%20%22Chess.com%22%5D%0A%5BDate%20%222021.03.24%22%5D%0A%5BRound%20%22%3F%22%5D%0A%5BWhite%20%22Deybis%20Melendez%22%5D%0A%5BBlack%20%22Maximum%22%5D%0A%5BResult%20%221-0%22%5D%0A%5BSetUp%20%221%22%5D%0A%5BFEN%20%228%2F8%2F8%2F4k3%2F8%2F8%2F8%2F4K2Q%20w%20-%20-%200%201%22%5D%0A%5BTimeControl%20%22-%22%5D%0A%0A1.%20Qc6%20Kf5%202.%20Qd6%20Kg4%203.%20Qe5%20Kh4%204.%20Qf5%20Kg3%205.%20Ke2%20Kg2%206.%20Qf3%2B%20Kh2%207.%20Qg4%20Kh1%208.%0AKf2%20Kh2%209.%20Qg2%23%201-0",
        piece_set: 'https://s3.amazonaws.com/canvas-chess/pieces/merida',
    });
</script>

# Rey y dos alfiles contra Rey

Para dar mate con dos alfiles se debe acorralar al rey en una esquina y dar mate con el alfil del color de la esquina, el orden aquí es muy importante, por lo que en ocasiones hay que perder un tiempo para lograr el orden correcto. Se utiliza la pareja de alfiles para delimitar el espacio del rey, cuando están juntos consiguen que el rey no pueda tocarlos.

Ejercicio:

<script>
    var viewer = new CHESS.PgnViewer({
        pgn_text: "%5BEvent%20%22vs%20Computer%22%5D%0A%5BSite%20%22Chess.com%22%5D%0A%5BDate%20%222021.03.24%22%5D%0A%5BRound%20%22%3F%22%5D%0A%5BWhite%20%22Deybis%20Melendez%22%5D%0A%5BBlack%20%22Maximum%22%5D%0A%5BResult%20%221-0%22%5D%0A%5BSetUp%20%221%22%5D%0A%5BFEN%20%227k%2F8%2F8%2F8%2F8%2F8%2F8%2F2B1KB2%20w%20-%20-%200%201%22%5D%0A%5BTimeControl%20%22-%22%5D%0A%0A1.%20Bd3%20Kg8%202.%20Bg5%20Kf7%203.%20Bf5%20%7BLe%20quito%20todas%20las%20casillas%20posibles%20al%20rey%20y%20ahora%20muevo%20mi%20rey%20para%20acorralar%20mas%7D%20Kf8%204.%20Kf2%20Kg7%205.%20Kg3%20Kg8%206.%20Kh4%20Kf7%207.%20Kh5%20Kf8%208.%0AKg6%20Ke8%209.%20Bf6%20%7BPierdo%20un%20tiempo%20para%20que%20el%20rey%20se%20coloque%20en%20una%20posici%C3%B3n%20donde%20puedo%20enviarlo%20a%20la%20esquina%20y%20dar%20mate%7D%20Kf8%2010.%20Bd7%20Kg8%2011.%20Be7%20Kh8%2012.%20Kh6%20%7Bdebo%20perder%20un%20tiempo%20para%20evitar%20tablas%20por%20ahogado%7D%20(12.%20Be6%201%2F2-1%2F2)%20%201...%20Kg8%2013.%20Be6%2B%20Kh8%2014.%20Bf6%23%201-0",
        piece_set: 'https://s3.amazonaws.com/canvas-chess/pieces/merida',
    });
</script>

# Final de peón y rey contra rey

Si el rey contrario se encuentra en frente del peón, la partida será tablas, es importante colocar al rey adelante del peón para crear un pasillo donde pase el peón sin que el rey contrario lo capture o consiga tablas por ahogado.

Ejercicio 1:

<script>
    var viewer = new CHESS.PgnViewer({
        pgn_text: "%5BEvent%20%22vs%20Computer%22%5D%0A%5BSite%20%22Chess.com%22%5D%0A%5BDate%20%222021.03.24%22%5D%0A%5BRound%20%22%3F%22%5D%0A%5BWhite%20%22Deybis%20Melendez%22%5D%0A%5BBlack%20%22Maximum%22%5D%0A%5BResult%20%22*%22%5D%0A%5BSetUp%20%221%22%5D%0A%5BFEN%20%228%2F8%2F5k2%2F8%2F5K2%2F8%2F4P3%2F8%20w%20-%20-%200%201%22%5D%0A%5BTimeControl%20%22-%22%5D%0A%0A1.%20e3%20Ke6%202.%20Ke4%20Kf6%203.%20Kd5%20Ke7%204.%20Ke5%20Kd7%205.%20Kf6%20Ke8%206.%20e4%20Kf8%207.%20e5%20Ke8%208.%20Ke6%0AKd8%209.%20Kf7%20Kc7%2010.%20e6%20Kd6%2011.%20e7%20Ke5%2012.%20e8%3DQ%2B%20Kd4%20*",
        piece_set: 'https://s3.amazonaws.com/canvas-chess/pieces/merida',
    });
</script>

# Oposición

Los reyes no se pueden tocar, a ese espacio que los dividen se le llama oposición, ganar la oposición es cuando el rey contrario cede al rey la batalla por una o varias casillas que le rodean. Me gusta pensar que es como pastorear una oveja. En el ejercicio anterior el blanco ganaba oposición frente al rey contrario para conseguir las casillas necesarias para coronar el peón.

Manejar la oposición es importante para ganar partidas, Capablanca da unos ejemplos de finales donde se aplica esto.

Ejercicio 1:

<script>
    var viewer = new CHESS.PgnViewer({
        pgn_text: "%5BEvent%20%22vs%20Computer%22%5D%0A%5BSite%20%22Chess.com%22%5D%0A%5BDate%20%222021.03.24%22%5D%0A%5BRound%20%22%3F%22%5D%0A%5BWhite%20%22Deybis%20Melendez%22%5D%0A%5BBlack%20%22Maximum%22%5D%0A%5BResult%20%221-0%22%5D%0A%5BSetUp%20%221%22%5D%0A%5BFEN%20%225k2%2F6p1%2F4K1P1%2F5P2%2F8%2F8%2F8%2F8%20w%20-%20-%200%201%22%5D%0A%5BTimeControl%20%22-%22%5D%0A%0A1.%20Kd7%20Kg8%20%7Ble%20quito%20casillas%20al%20rey%20negro%20y%20obligo%20a%20retirarse%20por%20g8%7D%202.%20Ke7%20Kh8%203.%20f6%20(3.%20Kf7%201%2F2-1%2F2)%203...%20gxf6%204.%20Kf7%20%7BEsta%20posici%C3%B3n%20ser%C3%ADa%20tablas%20si%20no%20existiera%20el%20pe%C3%B3n%20f6%7D%20f5%205.%20g7%2B%20Kh7%206.%20g8%3DQ%2B%20Kh6%207.%20Qg6%23%201-0",
        piece_set: 'https://s3.amazonaws.com/canvas-chess/pieces/merida',
    });
</script>

Ejercicio 2:

Esta posición la practiqué bastante, tanto jugar f5 como g5 genera tablas, stockfish en varias me consiguió la tabla pero al final conseguí entender como ganar, me jugó de dos maneras:

<script>
    var viewer = new CHESS.PgnViewer({
        pgn_text: "%5BEvent%20%22vs%20Computer%22%5D%0A%5BSite%20%22Chess.com%22%5D%0A%5BDate%20%222021.03.24%22%5D%0A%5BRound%20%22%3F%22%5D%0A%5BWhite%20%22Deybis%20Melendez%22%5D%0A%5BBlack%20%22Maximum%22%5D%0A%5BResult%20%22*%22%5D%0A%5BSetUp%20%221%22%5D%0A%5BFEN%20%228%2F6p1%2F3k4%2F8%2F3K1PP1%2F8%2F8%2F8%20w%20-%20-%200%201%22%5D%0A%5BTimeControl%20%22-%22%5D%0A%0A1.%20Ke4%20Ke6%202.%20f5%2B%20Kf6%203.%20Kf4%20g6%204.%20g5%2B%20Ke7%205.%20f6%2B%20Ke6%206.%20Ke4%20Kf7%207.%20Ke5%20Kf8%208.%0Af7%20Kxf7%209.%20Kd6%20Kf8%2010.%20Ke6%20Kg7%2011.%20Ke7%20Kg8%2012.%20Kf6%20Kh7%2013.%20Kf7%20Kh8%2014.%20Kxg6%20Kg8%0A15.%20Kh6%20Kf7%2016.%20Kh7%20Ke6%2017.%20g6%20Kd6%2018.%20g7%20Kc5%2019.%20g8%3DQ%20Kb4%20*",
        piece_set: 'https://s3.amazonaws.com/canvas-chess/pieces/merida',
    });
</script>

<script>
    var viewer = new CHESS.PgnViewer({
        pgn_text: "%5BEvent%20%22vs%20Computer%22%5D%0A%5BSite%20%22Chess.com%22%5D%0A%5BDate%20%222021.03.24%22%5D%0A%5BRound%20%22%3F%22%5D%0A%5BWhite%20%22Deybis%20Melendez%22%5D%0A%5BBlack%20%22Maximum%22%5D%0A%5BResult%20%22*%22%5D%0A%5BSetUp%20%221%22%5D%0A%5BFEN%20%228%2F6p1%2F3k4%2F8%2F3K1PP1%2F8%2F8%2F8%20w%20-%20-%200%201%22%5D%0A%5BTimeControl%20%22-%22%5D%0A%0A1.%20Ke4%20g6%202.%20Kd4%20Ke6%203.%20Kc5%20Ke7%204.%20Kd5%20Kd7%205.%20Ke5%20Ke7%206.%20g5%20Kf7%207.%20Kd6%20Kf8%208.%0AKe6%20Kg7%209.%20Ke7%20Kg8%2010.%20Kf6%20Kf8%2011.%20Kxg6%20Ke7%2012.%20Kh7%20Ke6%2013.%20g6%20Kf6%2014.%20g7%20Kf5%0A15.%20g8%3DQ%20Kxf4%20*",
        piece_set: 'https://s3.amazonaws.com/canvas-chess/pieces/merida',
    });
</script>

# Maniobra de Reti

Este ejemplo que vimos en clase permite ver cómo funciona la geometría en el ajedrez, en principio parece que el rey puede viajar mas rapido yendo en línea recta, pero no es así, ya que viajar en diagonal sirve de igual manera, lo que permite que el rey pueda dirigirse a 2 puntos al mismo tiempo sin perder turnos.

Ejercicio 1:

En esta posición pareciera que el Rey blanco corona y lo hace pero realizando la maniobra de reti, es necesario evitar que el rey contrario nos encierre causando ahogado, por eso evitamos su paso de esta manera.

<script>
    var viewer = new CHESS.PgnViewer({
        pgn_text: "%5BEvent%20%22vs%20Computer%22%5D%0A%5BSite%20%22Chess.com%22%5D%0A%5BDate%20%222021.03.24%22%5D%0A%5BRound%20%22%3F%22%5D%0A%5BWhite%20%22Deybis%20Melendez%22%5D%0A%5BBlack%20%22Maximum%22%5D%0A%5BResult%20%22*%22%5D%0A%5BSetUp%20%221%22%5D%0A%5BFEN%20%228%2Fp4K2%2FP7%2F8%2F8%2F8%2F1k6%2F8%20w%20-%20-%200%201%22%5D%0A%5BTimeControl%20%22-%22%5D%0A%0A1.%20Ke6%20Kc3%202.%20Kd5%20Kb4%203.%20Kc6%20Kc4%204.%20Kb7%20Kc5%205.%20Kxa7%20Kc6%206.%20Kb8%20Kd5%207.%20a7%20Kd4%208.%0Aa8%3DQ%20Ke3%20*",
        piece_set: 'https://s3.amazonaws.com/canvas-chess/pieces/merida',
    });
</script>

Para que sea mas claro, jugué la misma posición dirigiendome en línea recta hacia el peón:

<script>
    var viewer = new CHESS.PgnViewer({
        pgn_text: "%5BEvent%20%22vs%20Computer%22%5D%0A%5BSite%20%22Chess.com%22%5D%0A%5BDate%20%222021.03.24%22%5D%0A%5BRound%20%22%3F%22%5D%0A%5BWhite%20%22Guest%22%5D%0A%5BBlack%20%22Maximum%22%5D%0A%5BResult%20%221%2F2-1%2F2%22%5D%0A%5BSetUp%20%221%22%5D%0A%5BFEN%20%228%2Fp4K2%2FP7%2F8%2F8%2F8%2F1k6%2F8%20w%20-%20-%200%201%22%5D%0A%5BTimeControl%20%22-%22%5D%0A%0A1.%20Ke7%20Kc3%202.%20Kd7%20Kd4%203.%20Kc7%20Kd5%204.%20Kb7%20Kd6%205.%20Kxa7%20Kc7%206.%20Ka8%20Kc8%207.%20a7%20Kc7%0A1%2F2-1%2F2",
        piece_set: 'https://s3.amazonaws.com/canvas-chess/pieces/merida',
    });
</script>

Aquí el blanco parece que está perdido pero con la misma maniobra podemos conseguir tablas, el objetivo es que si el Rey negro decide capturar el peón, supone perder un tiempo lo que permite al rey blanco capturar el peón consiguiendo tablas, si no captura el blanco puede coronar igualmente consiguiendo también tablas.

<script>
    var viewer = new CHESS.PgnViewer({
        pgn_text: "%5BEvent%20%22vs%20Computer%22%5D%0A%5BSite%20%22Chess.com%22%5D%0A%5BDate%20%222021.03.24%22%5D%0A%5BRound%20%22%3F%22%5D%0A%5BWhite%20%22Deybis%20Melendez%22%5D%0A%5BBlack%20%22Maximum%22%5D%0A%5BResult%20%22*%22%5D%0A%5BSetUp%20%221%22%5D%0A%5BFEN%20%227K%2F8%2Fk1P5%2F7p%2F8%2F8%2F8%2F8%20w%20-%20-%200%201%22%5D%0A%5BTimeControl%20%22-%22%5D%0A%0A1.%20Kg7%20Kb6%202.%20Kf6%20h4%203.%20Ke5%20h3%204.%20Kd6%20h2%205.%20c7%20h1%3DQ%206.%20c8%3DQ%20Qd1%2B%20*",
        piece_set: 'https://s3.amazonaws.com/canvas-chess/pieces/merida',
    });
</script>