---
title: Algoritmo Minimax y Ajedrez
layout: post
---

Alguna vez te has preguntado, ¿Cómo piensan los módulos de ajedrez? ¿Cómo hacen para obtener las mejores jugadas? ¿Qué hace un módulo mejor que otro?

Los módulos de ajedrez son programas desarrollados por humanos, inteligencias artificiales. Ellas no piensan realmente, lo que hacen es seguir una serie de pasos para determinar las siguientes jugadas.

Las forma de calcular no es muy diferente a la que hacemos nosotros en una partida, la diferencia es que el módulo revisa cada una de las posiciones posibles y no tiene sesgos como nosotros, la máquina no tiene sentimientos y no se guía por el instinto.

Minimax es el algoritmo que se utiliza como base para la búsqueda de las mejores jugadas. Tiene muchos inconvenientes y con el tiempo se ha ido optimizando, posteriormente se desarrollaron algoritmos como la Poda Alpha beta y el Depth First Search sin embargo la base sigue siendo la misma.

Minimax realiza una búsqueda en árbol, es decir, va revisando jugada a jugada cada una de las posiciones posibles de la posición actual, a cada posición se le llama Nodo.

Depth (Profundidad) se refiere a la cantidad de Nodos que va a revisar para determinar la mejor jugada, es decir, si indicamos un Depth de 16, el módulo calculará hasta 16 jugadas por delante.

Minimax es un algoritmo de búsqueda por fuerza bruta, por si solo no puede decidir qué jugadas descartar a como lo hace un humano, por ejemplo, no valoramos jugar h3 o a3 al inicio de una partida.

Se dice que el jugador en turno es Max y el jugador rival es Min, Max se refiere a maximizar las posibilidades de ganar y Min se refiere a minimizar las posibilidades de ganar del rival.

Esto parece un poco complejo, pero es realmente simple y aplicable a cualquier juego de dos jugadores, la idea es que si yo estoy en turno voy a buscar la jugada que me de mas oportunidades de ganar y calcular la jugada del rival que reduce mis oportunidades de ganar.

## Minimax es débil en apertura

Para el primer turno de cada bando hay un total de 400 posiciones posibles, nada para una máquina, sin embargo, para el tercer turno se calculan mas de 9 millones de variantes posibles, el número de variantes en la apertura aumenta exponencialmente, por lo que podemos intuir que un módulo tardaría demasiado en calcular con una profundidad de 16 nodos.

Por tanto, por si solo el módulo debe ayudarse con una base de datos de aperturas precalculadas. En los primeros de módulos de ajedrez las bases de datos de aperturas tenían solo las variantes mas comunes y por eso para ganarle a un módulo antiguo era suficiente "sacarlo de libro", ya que no alcanzaría su potencia para calcular la mejor jugada.

## Pero ¿Cómo hace para elegir?

Aquí es donde entra el problema, la mayoría de módulos utilizan practicamente el mismo método, pero el cómo eligen las jugadas es donde está la diferencia entre uno y otro.

El módulo debe evaluar la posición final, a esto se llama Función de Evaluación.

Los primeros módulos de ajedrez valoraban las posiciones de manera material, es decir, entre mas material mejor.