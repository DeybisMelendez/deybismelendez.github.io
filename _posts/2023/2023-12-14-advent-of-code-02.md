---
title: Solución Advent of Code 2023 día 2
layout: post
---

El problema puede encontrarse aquí: [Advent of Code 2023 día 2](https://adventofcode.com/2023/day/2).

## Parte 1

En la primera parte se debe verificar cuales juegos son posibles y sumar los IDs, esto significa que similar al reto del día 1 hay que iterar a través de cada línea, por tanto obtenemos las entradas y declaramos los cubos máximos en una constante.

{% highlight lua %}
require "utils"
local maxCubeColors<const> = {
    blue = 14,
    green = 13,
    red = 12
}

local function getInput()
    local input = readFile("02input.txt")
    return splitString(input, lineDelimiter)
end
{% endhighlight %}

Ahora la idea sería estructurar cada línea dividiendo en pequeños strings, primero dividir la línea por ":" esto daría dos elementos, la primera contendría el ID y la segunda el Juego. Luego al Juego lo podemos dividir por ";" lo que daría un array de Set o subconjunto, luego a cada Set lo podemos dividir por "," y obtener otro array por cada cubo, por último dividir por "%s" (espacio) y obtener el color del cubo y el número.

Decidí hacer todo eso en la misma iteración mientras resuelvo el ejercicio.

{% highlight lua %}
local function answer1()
    local lines = getInput()
    local game = ""
    local gameID = 0
    local sets = {}
    local cubes = {}
    local cube = {}
    local cubeNumber = 0
    local cubeColor = ""
    local isSetVerified = true
    local result = 0

    for _, line in ipairs(lines) do
        game = splitString(line, colonDelimiter) -- Divide el string por ;
        gameID = tonumber(string.sub(game[1], 5, -1)) -- Extrae el ID del juego
        sets = splitString(game[2], semiColonDelimiter) -- Divide el juego en subconjuntos

        for _, set in ipairs(sets) do -- por cada subconjunto de juego, verificamos que sea correcto
            isSetVerified = true -- en cada iteración restablecemos la condición a true
            cubes = splitString(set, commaDelimiter)
            for _, cubeCount in ipairs(cubes) do
                cube = splitString(cubeCount, spaceDelimiter) -- dividimos el string por "%s" (caracter espacio)
                cubeNumber = tonumber(cube[1])
                cubeColor = cube[2]
                if cubeNumber > maxCubeColors[cubeColor] then
                    isSetVerified = false
                    -- si el número de un cubo es inválido, no se necesita verificar mas
                    break
                end
            end
            if not isSetVerified then
                -- no es necesario iterar mas si un cubo es inválido
                break
            end
        end
        if isSetVerified then
            -- Por último si no hay poda y el isSetVerified se mantiene verdadero, entonces suma el ID
            result = result + gameID
        end
    end
    return result
end
{% endhighlight %}

## Parte 2

En la parte 2 te cambia las condiciones, ahora te pide determinar la mínima cantidad de cubos necesarios para que un juego sea posible, aquí se puede dar lugar a una confusión, en este caso, la mínima cantidad de cubos necesarios es la máxima cantidad de cubos de cada juego, por lo que solo hay que buscar cada cubo inicializando el valor en 0, y solo aplicar una función max(), es decir, quedarse siempre con el máximo valor de cada cubo.

{% highlight lua %}
local function answer2()
    local input = readFile("02input.txt")
    local lines = splitString(input, lineDelimiter)
    local game = ""
    local sets = {}
    local cubes = {}
    local cube = {}
    local cubeNumber = 0
    local cubeColor = ""
    -- declaramos la cuenta de los cubos en cero
    local minCube = { 
        blue = 0,
        red = 0,
        green = 0
    }
    local result = 0

    for _, line in ipairs(lines) do
        game = splitString(line, colonDelimiter)
        sets = splitString(game[2], semiColonDelimiter)
        -- hay que restablecer el mínimo en cada juego
        minCube.blue = 0
        minCube.red = 0
        minCube.green = 0

        for _, set in ipairs(sets) do
            cubes = splitString(set, commaDelimiter)

            for _, cubeCount in ipairs(cubes) do
                cube = splitString(cubeCount, spaceDelimiter)
                cubeNumber = tonumber(cube[1])
                cubeColor = cube[2]
                -- Aquí está el detalle, hay que comparar el número del cubo con el mínimo actual
                -- y quedarnos con el número mayor
                if cubeNumber > minCube[cubeColor] then
                    minCube[cubeColor] = cubeNumber
                end
            end
        end
        -- Vamos sumando en cada iteración el múltiplo de los cubos
        result = result + minCube.blue * minCube.red * minCube.green
    end
    return result
end
{% endhighlight %}

Con esto ya se puede obtener la solución de ambas partes
{% highlight lua %}
print("Parte 1:", answer1())
print("Parte 2:", answer2())
{% endhighlight %}

Puede encontrar mi código completo aquí: [Github](https://github.com/DeybisMelendez/AdventOfCode).