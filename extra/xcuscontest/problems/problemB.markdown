---
layout: problem
title: "Problem B: Brigada de Ataque"
date: 2016-07-22 21:12 -0500
categories: cuscontest
color: "#ff294d"
showinmenu: true
---

## Problem description

El general Fujimori esta planeando su ataque contra su enemigo mortal: el general Kuczynski.

Después de muchos meses de arduo trabajo de inteligencia Fujimori a descubierto que la mejor forma de romper la resistencia enemiga es poner soldados más fuertes al frente de las filas de manera que cada soldado tiene delante suyo a algún compañero que lo supera en fuerza. Formalmente, se tienen $$N$$ soldados de fuerzas $$f_1, f_2, \dots, f_N$$ donde $$f_i > f_j$$ siempre que $$1 \leq i < j \leq N$$.

Inicialmente los $$N$$ soldados del ejército forman una fila y debido a que el campo de batalla es accidentado, Fujimori sólo podrá enviar a un pequeño grupo que denominará *Brigada de Ataque*. Este grupo se formará a partir de la fila original extrayendo algunos soldados para formar una nueva fila, Fujimori recorre la fila de izquierda a derecha y cada vez que desea que un soldado entre en la *Brigada de Ataque* lo pone al final de la nueva fila.

Fujimori desea aniquilar a Kuczynski por lo que esta nueva fila debe cumplir con la estructura óptima que fue descubierta por el equipo de inteligencia. Además Fujimori desea que el tamaño de la *Brigada de Ataque* sea máximo.

Tú eres el jefe de inteligencia del general Kuczynski y has descubierto el plan de Fujimori, Kuczynski desea saber cuantos soldados enemigos lo atacarán y te encarga esta tarea.

## Input

La entrada del problema contiene varios casos de prueba. La primera línea es un entero $$T$$ $$(1\leq T \leq 50)$$ indicando el número de casos de prueba. Para cada caso, se sigue el siguiente formato de entrada:

  * La primera contiene un número $$N$$ indicando el tamaño de todo el ejército de Fujimori ($$1 \leq N \leq 10^4$$).

  * La segunda línea contiene $$N$$ enteros $$f_1, f_2, \dots, f_N$$ representando la fuerza de cada soldado de Fujimori ($$1 \leq f_i \leq 10^9$$).

## Output

Para cada caso de prueba se debe imprimir una única línea que contiene el tamaño de la *Brigada de Ataque* que debe esperar Kuczynski.

## Example

<div class="panel panel-default">
  <table class="table" style="font-family:'Lucida Console',monoscape;">
    <tr>
      <th> Input </th>
      <th> Output </th>
    </tr>
    <tr>
      <td>
        2<br>
        7<br>
        14 15 4 7 3 3 1<br>
        5<br>
        1 1 1 1 1<br>
      </td>
      <td> 
        4<br>
        1<br>
      </td>
    </tr>
  </table>
</div>

## Observación

Para el primer caso la *Brigada de Ataque* podría estar formada por: `14 7 3 1` ó `15 7 3 1`.

Para el segundo caso la *Brigada de Ataque* sólo puede estar formada por: `1`.
