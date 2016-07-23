---
layout: problem
title: "Problem C: Cuadrolandia"
date: 2016-07-22 21:12 -0500
categories: cuscontest
color: "#ff294d"
showinmenu: true
---

## Problem description


En el país de Cuadradolandia, las construciones se realizan usando figuras geométricas muy especiales. Los habitantes de esta ciudad se divierten contando el número de cuadrados, cubos, hipercupos u otras figuras geométricas de tamaño regular.

Cierto día Warrencio, el más hábil de la ciudad se pregunta sí hay una forma de calcular el número de cuadrados para una pared de $$N\times N$$ o el número de cubos en un edificio de $$N\times N\times N$$ o el número de hipercubos en un edificio de $$N\times N\times N\times N$$ o inclusive para edificaciones en espacios $$D$$-dimensionales. Tu tarea es ayudar a Warrencio en su noble tarea.

## Input

La entrada del problema contiene varios casos de prueba. La primera línea es un entero $$T$$ indicando el número de casos de prueba. Para cada caso, se sigue el siguiente formato de entrada:

  * Una línea que contiene 2 enteros $$M$$ y $$D$$ siendo $$M$$ el número de figuras geométricas regulares de dimensión $$\underbrace{1\times 1\times \dots \times 1}_{D~veces}$$ en un espacio $$D$$-dimensional ($$1 \leq M \leq 16807$$ y $$1 \leq D \leq 5$$).

## Output

Para cada caso de prueba, imprimir en una línea el máximo número de figuras geométricas regulares que se pueden formar. 

## Example

<div class="panel panel-default">
  <table class="table" style="font-family:'Lucida Console',monoscape;">
    <tr>
      <th> Input </th>
      <th> Output </th>
    </tr>
    <tr>
      <td>
        3<br>
        4 2<br>
        8 3<br>
        81 4<br>
      </td>
      <td> 
        5<br>
        9<br>
        98<br>
      </td>
    </tr>
  </table>
</div>

## Observación

Considerando un muro en 2 dimensiones de tamaño $$3\times 3$$, el número de figuras geométricas regulares de dimensión $$1\times 1$$ es igual a 9.
