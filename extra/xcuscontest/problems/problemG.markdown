---
layout: problem
title: "Problem G: El viaje de Adam"
date: 2016-07-22 21:12 -0500
categories: cuscontest
color: "#ff294d"
showinmenu: true
---

## Problem description

Adam es una persona a quien le gusta conocer nuevos lugares, actualmente él se encuentra en la ciudad $$1$$ y quiere llegar a la ciudad de $$N + 1$$ pasando por $$N$$ sitios durante su recorrido. 

Adam sabe que para ir de la ciudad $$i$$  a la ciudad $$i + 1$$ existen $$a_i$$ formas de llegar. Adam desea saber el número de caminos distintos de llegar a la ciudad $$N + 1$$ desde la ciudad $$1$$. 

Sin embargo Adam solo desea saber el primer y último dígito del número de caminos posibles, ya que el número de caminos puede ser un número muy grande.

## Input

La entrada del problema contiene varios casos de prueba. La primera línea es un entero $$T$$ ($$1 \leq T \leq 10^3$$) indicando el número de casos de prueba. Para cada caso, se sigue el siguiente formato de entrada:

  * La primera línea contiene un entero $$N$$ indicando el número de ciudades por las cuales Adam debe de pasar ($$1 \leq N \leq 10^3$$).
  * La segunda línea contiene $$N$$ enteros distintos $$a_1, a_2, \dots, a_N$$ representando el número de caminos posibles para ir de la ciudad $$i$$ a la ciudad $$i+1$$ ($$1 \leq a_i \leq 10^9$$).

## Output

Para cada caso de prueba, el programa deberá imprimir el primer y último dígito de número de caminos posibles para ir de la ciudad $$1$$ a la ciudad $$N$$.

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
        1<br>
        10<br>
        3<br>
        3 5 7<br>
        2<br>
        123 45<br>
      </td>
      <td> 
        1 0<br>
        1 5<br>
        5 8<br>
      </td>
    </tr>
  </table>
</div>
