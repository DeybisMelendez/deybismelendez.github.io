---
title: Solución Advent of Code 2023 día 1
layout: post
---

El problema puede encontrarse aquí: [Advent of Code 2023 día 1](https://adventofcode.com/2023/day/1).

## Parte 1

Para resolver este ejercicio se necesita iterar a través de cada línea de la entrada del rompecabezas.
En cada iteración hay que buscar 2 números, lo que yo hice fue buscar el primer dígito buscando caracter
por caracter de izquierda a derecha, y luego el segundo dígito buscando caracter por caracter de derecha a izquierda.

Dicho esto, comenzamos declarando una función que obtenga la entrada del rompecabezas y convierta cada línea
en un elemento de un array.

{% highlight lua %}
require "utils"
-- utils: Es una librería que contiene algunos pocas funciones útiles que no trae Lua por defecto

local function getInput()
    local input = readFile("01input.txt") -- Obtenemos el string de la entrada
    return splitString(input, lineDelimiter) -- Dividimos el string por la cantidad de líneas
end
{% endhighlight %}

Ahora solo se realiza la busca de los números de una línea para eso declaro una función foundCalibrationValue()

{% highlight lua %}
local function foundCalibrationValue(line, readWords)
    local firstDigit = "" -- los digitos serían strings cuando los encontramos
    local lastDigit = ""

    -- Buscamos de izquierda a derecha el primer dígito
    for i = 1, #line do
        local char = line:sub(i, i)
        if tonumber(char) ~= nil then
            firstDigit = char
            break
        end
    end

    -- Buscamos de derecha a izquierda el segundo dígito
    for i = #line, 1, -1 do
        local char = line:sub(i, i)
        if tonumber(char) ~= nil then
            lastDigit = char
            break
        end
    end
    -- Devolvemos los dígitos concatenando primero y luego convirtiendolo a número
    return tonumber(firstDigit .. lastDigit)
end
{% endhighlight %}

Ahora solo se itera por cada línea y se suman los números

{% highlight lua %}
local function answer1()
    local lines = getInput()
    local result = 0
    for _, line in ipairs(lines) do
        result = result + foundCalibrationValue(line)
    end
    return result
end
{% endhighlight %}

## Parte 2

En la parte dos nos piden encontrar además de digitos números escritos, a esto solo le agregamos una condición a la función foundCalibrationValue para indicar que busque también esos números.

Para lograr esto, lo que pensé fue simplemente agregar los dígitos en caso de existir un número en palabra, debido a que los números se mezclan entre sí, para evitar inconvenientes se puede duplicar la palabra e insertar el dígito
en medio, por ejemplo, si se encuentra la palabra "one", cambiar esa palabra por "one1one" y se aplicaría luego lo mismo que la primera parte.

{% highlight lua %}
-- Declaramos una lista de las palabras a buscar
local numbers<const> = {"one", "two", "three", "four", "five", "six", "seven", "eight", "nine"}


local function foundCalibrationValue(line, readWords)
    -- se agregaría lo siguiente:
    local x, y = 0, 0 -- index de la primer letra y última letra de la palabra

    if readWords then -- si se permite leer palabras
        for i = 1, #numbers do -- iteramos a través de la lista de números
            x, y = string.find(line, numbers[i]) -- Lua tiene una función que permite encontrar coincidencias
            if x ~= nil and y ~= nil then
                -- si se encuentra una palabra, se sustituye la palabra por "palabra#palabra"
                line = line:gsub(numbers[i], string.sub(numbers[i], 1, 1) .. i .. string.sub(numbers[i], -1))
            end
        end
    end

    -- la búsqueda continúa como en la primera parte

    return tonumber(firstDigit .. lastDigit)
end
{% endhighlight %}

Listo, ya solo adaptamos la solución 1 agregando false a la función y creamos la función para obtener la segunda parte.

{% highlight lua %}
local function answer1()
    local lines = getInput()
    local result = 0
    for _, line in ipairs(lines) do
        result = result + foundCalibrationValue(line, false)
    end
    return result
end

local function answer2()
    local lines = getInput()
    local result = 0
    for _, line in ipairs(lines) do
        result = result + foundCalibrationValue(line, true)
    end
    return result
end

print("Parte 1:", answer1())
print("Parte 2:", answer2())
{% endhighlight %}