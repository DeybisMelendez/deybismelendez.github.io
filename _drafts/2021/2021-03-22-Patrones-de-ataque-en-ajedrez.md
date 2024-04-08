---
layout: post
title: Patrones de ataque en ajedrez
---
{% include canvaschess.html %}

En los siguientes días en la academia aprendí algunos patrones de ataque y jaque mate.

# El sacrificio de Greco

El maestro Lester me vió jugar con Nelson y casi al finalizar la apertura nos comenzó a enseñar un patrón de ataque, este patrón viene de una partida de Greco en 1620, me pareció una idea de ataque muy buena, tanto que luego la practiqué con éxito en chess.com. La partida original fue esta:

<script>
    var viewer = new CHESS.PgnViewer({
        pgn_text: "%5BEvent%20%22Miscellaneous%20Game%22%5D%0A%5BSite%20%22%3F%22%5D%0A%5BDate%20%221620.%3F%3F.%3F%3F%22%5D%0A%5BEventDate%20%22%3F%22%5D%0A%5BRound%20%2225%22%5D%0A%5BResult%20%221-0%22%5D%0A%5BWhite%20%22Gioachino%20Greco%22%5D%0A%5BBlack%20%22NN%22%5D%0A%5BECO%20%22C01%22%5D%0A%5BWhiteElo%20%22%3F%22%5D%0A%5BBlackElo%20%22%3F%22%5D%0A%5BPlyCount%20%2223%22%5D%0A%0A1.e4%20e6%202.d4%20Nf6%203.Bd3%20Nc6%204.Nf3%20Be7%205.h4%20O-O%206.e5%20Nd5%207.Bxh7%2B%0AKxh7%208.Ng5%2B%20Bxg5%209.hxg5%2B%20Kg8%2010.Qh5%20f5%2011.g6%20Re8%2012.Qh8%23%201-0",
        piece_set: 'https://s3.amazonaws.com/canvas-chess/pieces/merida',
    });
</script>

La partida que jugué donde vi que podía aplicar la misma idea fue esta:

<script>
    var viewer = new CHESS.PgnViewer({
        pgn_text: "%5BEvent%20%22Live%20Chess%22%5D%0A%5BSite%20%22Chess.com%22%5D%0A%5BDate%20%222021.03.18%22%5D%0A%5BRound%20%22%3F%22%5D%0A%5BWhite%20%22deybismelendez%22%5D%0A%5BBlack%20%22akshaykumra%22%5D%0A%5BResult%20%221-0%22%5D%0A%5BECO%20%22B29%22%5D%0A%5BWhiteElo%20%22845%22%5D%0A%5BBlackElo%20%22852%22%5D%0A%5BTimeControl%20%22180%22%5D%0A%5BEndTime%20%227%3A40%3A54%20PDT%22%5D%0A%5BTermination%20%22deybismelendez%20won%20by%20checkmate%22%5D%0A%0A1.%20e4%20c5%202.%20Nf3%20Nf6%203.%20d4%20e6%204.%20Nc3%20Nc6%205.%20e5%20Nd5%206.%20h4%20Be7%207.%20Bd3%20O-O%208.%20Bxh7%2B%0AKxh7%209.%20Ng5%2B%20Bxg5%2010.%20hxg5%2B%20Kg8%2011.%20Qh5%20f6%2012.%20g6%20Nxc3%2013.%20Qh8%23%201-0",
        piece_set: 'https://s3.amazonaws.com/canvas-chess/pieces/merida',
    });
</script>

## Mate de la coz

Este mate se produce cuando un caballo da jaque a un rey que está encerrado, el caballo al tener la propiedad de "saltar casillas" hace posible este tipo de jaque mate.

Ejemplo:

<script>
    var viewer = new CHESS.PgnViewer({
        pgn_text: "%5BEvent%20%22%3F%22%5D%0A%5BSite%20%22%3F%22%5D%0A%5BDate%20%22%3F%3F%3F%3F.%3F%3F.%3F%3F%22%5D%0A%5BRound%20%22%3F%22%5D%0A%5BWhite%20%22%3F%22%5D%0A%5BBlack%20%22%3F%22%5D%0A%5BResult%20%221-0%22%5D%0A%5BSetUp%20%221%22%5D%0A%5BFEN%20%225rk1%2F6pp%2F8%2F6N1%2F8%2F2Q5%2F8%2F4K3%20w%20-%20-%200%201%22%5D%0A%0A1.%20Qc4%2B%20Kh8%20(1...%20Rf7%202.%20Qxf7%2B%20Kh8%203.%20Qf8%23)%202.%20Nf7%2B%20Kg8%20(2...%20Rxf7%203.%20Qc8%2B%20Rf8%0A4.%20Qxf8%23)%203.%20Nh6%2B%20Kh8%204.%20Qg8%2B%20Rxg8%205.%20Nf7%23%201-0",
        piece_set: 'https://s3.amazonaws.com/canvas-chess/pieces/merida',
    });
</script>

Encontré algunas partidas que finalizan con este patrón de mate:

<script>
    var viewer = new CHESS.PgnViewer({
        pgn_text: "%5BEvent%20%22Interpolis%2014th%22%5D%0A%5BSite%20%22Tilburg%20NED%22%5D%0A%5BDate%20%221990.09.24%22%5D%0A%5BEventDate%20%22%3F%22%5D%0A%5BRound%20%2214%22%5D%0A%5BResult%20%221-0%22%5D%0A%5BWhite%20%22Jan%20Timman%22%5D%0A%5BBlack%20%22Nigel%20Short%22%5D%0A%5BECO%20%22A93%22%5D%0A%5BWhiteElo%20%22%3F%22%5D%0A%5BBlackElo%20%22%3F%22%5D%0A%5BPlyCount%20%2259%22%5D%0A%0A1.d4%20e6%202.c4%20f5%203.g3%20Nf6%204.Bg2%20Be7%205.Nf3%20d5%206.O-O%20O-O%207.b3%20Bd7%0A8.Ba3%20Nc6%209.Qc1%20a5%2010.Bxe7%20Qxe7%2011.Nc3%20Be8%2012.Qe3%20dxc4%2013.bxc4%0ARd8%2014.Rfd1%20Ng4%2015.Qf4%20Bf7%2016.Rab1%20e5%2017.dxe5%20Rxd1%2B%2018.Rxd1%0AQc5%2019.Ng5%20Bxc4%2020.Nd5%20Nd8%2021.e6%20Bxd5%2022.Rxd5%20Qa3%2023.Rd7%20Nc6%0A24.Bxc6%20bxc6%2025.e7%20Re8%2026.Qc4%2B%20Kh8%2027.Nf7%2B%20Kg8%2028.Nh6%2B%20Kh8%0A29.Qg8%2B%20Rxg8%2030.Nf7%23%201-0",
        piece_set: 'https://s3.amazonaws.com/canvas-chess/pieces/merida',
    });
</script>

<script>
    var viewer = new CHESS.PgnViewer({
        pgn_text: "%5BEvent%20%22New%20York%22%5D%0A%5BSite%20%22New%20York%2C%20NY%20USA%22%5D%0A%5BDate%20%221946.%3F%3F.%3F%3F%22%5D%0A%5BEventDate%20%22%3F%22%5D%0A%5BRound%20%22%3F%22%5D%0A%5BResult%20%220-1%22%5D%0A%5BWhite%20%22Edward%20Lasker%22%5D%0A%5BBlack%20%22Israel%20Albert%20Horowitz%22%5D%0A%5BECO%20%22D04%22%5D%0A%5BWhiteElo%20%22%3F%22%5D%0A%5BBlackElo%20%22%3F%22%5D%0A%5BPlyCount%20%2228%22%5D%0A%0A1.d4%20Nf6%202.Nf3%20d5%203.e3%20c5%204.c4%20cxd4%205.Nxd4%20e5%206.Nf3%20Nc6%207.Nc3%0Ad4%208.exd4%20exd4%209.Nb5%20Bb4%2B%2010.Bd2%20O-O%2011.Bxb4%20Nxb4%2012.Nbxd4%20Qa5%0A13.Nd2%20Qe5%2B%2014.Ne2%20Nd3%23%200-1",
        piece_set: 'https://s3.amazonaws.com/canvas-chess/pieces/merida',
    });
</script>

<script>
    var viewer = new CHESS.PgnViewer({
        pgn_text: "%5BEvent%20%22Paris%22%5D%0A%5BSite%20%22Paris%20FRA%22%5D%0A%5BDate%20%221859.03.31%22%5D%0A%5BEventDate%20%22%3F%22%5D%0A%5BRound%20%22%3F%22%5D%0A%5BResult%20%221-0%22%5D%0A%5BWhite%20%22Paul%20Morphy%22%5D%0A%5BBlack%20%22Schrufer%22%5D%0A%5BECO%20%22C56%22%5D%0A%5BWhiteElo%20%22%3F%22%5D%0A%5BBlackElo%20%22%3F%22%5D%0A%5BPlyCount%20%2247%22%5D%0A%0A1.e4%20e5%202.Nf3%20Nc6%203.Bc4%20Nf6%204.d4%20exd4%205.O-O%20Nxe4%206.Re1%20d5%0A7.Bxd5%20Qxd5%208.Nc3%20Qh5%209.Nxe4%20Be6%2010.Neg5%20Bb4%2011.Rxe6%2B%20fxe6%0A12.Nxe6%20Qf7%2013.Nfg5%20Qe7%2014.Qe2%20Bd6%2015.Nxg7%2B%20Kd7%2016.Qg4%2B%20Kd8%0A17.Nf7%2B%20Qxf7%2018.Bg5%2B%20Be7%2019.Ne6%2B%20Kc8%2020.Nc5%2B%20Kb8%2021.Nd7%2B%20Kc8%0A22.Nb6%2B%20Kb8%2023.Qc8%2B%20Rxc8%2024.Nd7%23%201-0",
        piece_set: 'https://s3.amazonaws.com/canvas-chess/pieces/merida',
    });
</script>

# Doble sacrificio de alfil

Este es otro patrón de ataque que he visto en la academia, sacrifica los dos alfiles contra el enroque para dejar al rey expuesto.

Este patrón nace en una partida entre Lasker vs Bauer:

<script>
    var viewer = new CHESS.PgnViewer({
        pgn_text: "%5BEvent%20%22Amsterdam%22%5D%0A%5BSite%20%22Amsterdam%20NED%22%5D%0A%5BDate%20%221889.08.26%22%5D%0A%5BEventDate%20%221889.08.26%22%5D%0A%5BRound%20%221%22%5D%0A%5BResult%20%221-0%22%5D%0A%5BWhite%20%22Emanuel%20Lasker%22%5D%0A%5BBlack%20%22Johann%20Hermann%20Bauer%22%5D%0A%5BECO%20%22A03%22%5D%0A%5BWhiteElo%20%22%3F%22%5D%0A%5BBlackElo%20%22%3F%22%5D%0A%5BPlyCount%20%2275%22%5D%0A%0A1.f4%20d5%202.e3%20Nf6%203.b3%20e6%204.Bb2%20Be7%205.Bd3%20b6%206.Nc3%20Bb7%207.Nf3%0ANbd7%208.O-O%20O-O%209.Ne2%20c5%2010.Ng3%20Qc7%2011.Ne5%20Nxe5%2012.Bxe5%20Qc6%0A13.Qe2%20a6%2014.Nh5%20Nxh5%2015.Bxh7%2B%20Kxh7%2016.Qxh5%2B%20Kg8%2017.Bxg7%20Kxg7%0A18.Qg4%2B%20Kh7%2019.Rf3%20e5%2020.Rh3%2B%20Qh6%2021.Rxh6%2B%20Kxh6%2022.Qd7%20Bf6%0A23.Qxb7%20Kg7%2024.Rf1%20Rab8%2025.Qd7%20Rfd8%2026.Qg4%2B%20Kf8%2027.fxe5%20Bg7%0A28.e6%20Rb7%2029.Qg6%20f6%2030.Rxf6%2B%20Bxf6%2031.Qxf6%2B%20Ke8%2032.Qh8%2B%20Ke7%0A33.Qg7%2B%20Kxe6%2034.%20Qxb7%20Rd6%2035.%20Qxa6%20d4%2036.%20exd4%20cxd4%2037.%20h4%20d3%0A38.%20Qxd3%201-0%0A",
        piece_set: 'https://s3.amazonaws.com/canvas-chess/pieces/merida',
    });
</script>

Judit Polgar le aplica este ataque a Karpov en 2003:

<script>
    var viewer = new CHESS.PgnViewer({
        pgn_text: "%5BEvent%20%227th%20Essent%22%5D%0A%5BSite%20%22Hoogeveen%20NED%22%5D%0A%5BDate%20%222003.10.12%22%5D%0A%5BEventDate%20%222003.10.12%22%5D%0A%5BRound%20%221%22%5D%0A%5BResult%20%221-0%22%5D%0A%5BWhite%20%22Judit%20Polgar%22%5D%0A%5BBlack%20%22Anatoly%20Karpov%22%5D%0A%5BECO%20%22C42%22%5D%0A%5BWhiteElo%20%222722%22%5D%0A%5BBlackElo%20%222693%22%5D%0A%5BPlyCount%20%2251%22%5D%0A%0A1.%20e4%20e5%202.%20Nf3%20Nf6%203.%20Nxe5%20d6%204.%20Nf3%20Nxe4%205.%20d4%20d5%206.%20Bd3%20Be7%0A7.%20O-O%20Nc6%208.%20c4%20Nb4%209.%20Be2%20O-O%2010.%20a3%20Nc6%2011.%20cxd5%20Qxd5%0A12.%20Nc3%20Nxc3%2013.%20bxc3%20Qd6%2014.%20Rb1%20b6%2015.%20Re1%20Be6%2016.%20Bd3%20Rae8%0A17.%20Rb5%20Na5%2018.%20Rbe5%20Nc6%2019.%20R5e2%20Bd7%2020.%20d5%20Na5%2021.%20Ne5%20Bf6%0A22.%20Bf4%20Bxe5%2023.%20Bxe5%20Qxa3%2024.%20Re3%20Qc5%2025.%20Bxh7%2B%20Kxh7%2026.%20Qh5%2B%0A1-0%0A",
        piece_set: 'https://s3.amazonaws.com/canvas-chess/pieces/merida',
    });
</script>

Aquí Karpov se retira porque la mayoría de sus piezas están en el flanco de dama, su rey está expuesto, por lo que hay mate en pocas.

Otra partida donde se aplica el ataque:

<script>
    var viewer = new CHESS.PgnViewer({
        pgn_text: "%5BEvent%20%22St.%20Petersburg%22%5D%0A%5BSite%20%22St.%20Petersburg%20%20RUE%22%5D%0A%5BDate%20%221914.04.28%22%5D%0A%5BEventDate%20%221914.04.21%22%5D%0A%5BRound%20%225%22%5D%0A%5BResult%20%220-1%22%5D%0A%5BWhite%20%22Aron%20Nimzowitsch%22%5D%0A%5BBlack%20%22Siegbert%20Tarrasch%22%5D%0A%5BECO%20%22D30%22%5D%0A%5BWhiteElo%20%22%3F%22%5D%0A%5BBlackElo%20%22%3F%22%5D%0A%5BPlyCount%20%2264%22%5D%0A%0A1.%20d4%20%7B%20Notes%20by%20Raymond%20Keene.%20Here%20is%20a%20brilliant%20win%20by%0ATarrasch.%20%7D%20d5%202.%20Nf3%20c5%203.%20c4%20e6%204.%20e3%20Nf6%205.%20Bd3%20Nc6%206.%20O-O%0ABd6%207.%20b3%20O-O%208.%20Bb2%20b6%209.%20Nbd2%20Bb7%2010.%20Rc1%20Qe7%2011.%20cxd5%20%7B11%0AQe2!%3F%20%7D%2011...exd5%2012.%20Nh4%20g6%2013.%20Nhf3%20Rad8%2014.%20dxc5%20bxc5%0A15.%20Bb5%20Ne4%2016.%20Bxc6%20Bxc6%2017.%20Qc2%20Nxd2%2018.%20Nxd2%20%7B'The%20guardian%0Aof%20the%20king's%20field%20leaves%20his%20post%20for%20a%20moment%2C%20assuming%0Awrongly%20that%2019%20Qc3%20is%20a%20major%20threat'%20--%20Tartakower.%20If%2018%0AQxd2%20d4%2019%20exd4%20Bxf3%2020%20gxf3%20Qh4%20%7D%2018...d4%20%7B!%7D%2019.%20exd4%20%7B19%0ARfe1!%20%7D%20Bxh2%2B%2020.%20Kxh2%20Qh4%2B%2021.%20Kg1%20Bxg2%20%7B!%7D%2022.%20f3%20%7B22%20Kxg2%0AQg4%2B%2023%20Kh2%20Rd5-%2B%20%7D%2022...Rfe8%2023.%20Ne4%20Qh1%2B%2024.%20Kf2%20Bxf1%2025.%20d5%0A%7B25%20Rxf1%20Qh2%2B%20or%2025%20Nf6%2B%20Kf8%2026%20Nxe8%20Qg2%2B%20%7D%2025...f5%2026.%20Qc3%0AQg2%2B%2027.%20Ke3%20Rxe4%2B%2028.%20fxe4%20f4%2B%20%7B28...Qg3%2B!%20%7D%2029.%20Kxf4%20Rf8%2B%0A30.%20Ke5%20Qh2%2B%2031.%20Ke6%20Re8%2B%2032.%20Kd7%20Bb5%23%200-1%0A",
        piece_set: 'https://s3.amazonaws.com/canvas-chess/pieces/merida',
    });
</script>

