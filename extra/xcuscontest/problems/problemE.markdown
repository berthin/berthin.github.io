---
layout: problem
title: "Problem D: Warrencio y el Dota"
date: 2016-07-22 21:12 -0500
categories: cuscontest
color: "#ff294d"
showinmenu: true
---

## Problem description

Cierto día Warrencio y sus $$N$$ amigos fueron al BZ a jugar Dota. Cada uno tiene preferencia de usar algunas máquinas y no puede usar otras aunque estén disponibles --- al final un jugador sólo puede usar a lo más una máquina pero puede preferir varias. Al llegar a recinto de la sabiduría y las buenas palabras notaron que sólo disponen de M máquinas. Por lo tanto, ayuda a Warrencio a calcular cuantos de sus amigos jugarán con él. Warren siempre va a usar una máquina ya que el vicio le hizo tener un trato especial con el dueño del internet.

## Input

La entrada del problema contiene varios casos de prueba. La primera línea es un entero $$T$$ indicando el número de casos de prueba. Para cada caso, se sigue el siguiente formato de entrada:

  * La primera línea contiene 3 enteros $$N$$, $$M $$ y $$P$$. $$N$$ es el número de amigos de Warren, $$M$$ es el número de máquinas y $$P$$ es el número de preferencias de todos los jugadores ($$0 \leq N \leq 99$$, $$0 \leq M \leq 100$$ y $$0 \leq P \leq N\times M$$).

  * Las siguientes $$P$$ líneas contienen 2 enteros $$u$$ y $$v$$ siendo $$u$$ el índice de los jugadores y $$v$$ es el índice de las máquinas ($$0 \leq u \leq N$$  y $$0 \leq v<M$$). Warrencio tiene el índice $$0$$

## Output

Para cada caso se debe imprirmir el número máximo de amigos de Warrencio que tienen una máquina para jugar. 

## Example

<div class="panel panel-default">
  <table class="table" style="font-family:'Lucida Console',monoscape;">
    <tr>
      <th> Input </th>
      <th> Output </th>
    </tr>
    <tr>
      <td>
        1<br>
        3 4 5<br>
        0 2<br>
        1 0<br>
        2 3<br>
        3 1<br>
        3 2<br>
      </td>
      <td> 
        3<br>
      </td>
    </tr>
  </table>
</div>
