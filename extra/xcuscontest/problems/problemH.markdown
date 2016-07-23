---
layout: problem
title: "Problem H: Un viaje de ensueño"
date: 2016-07-22 21:12 -0500
categories: cuscontest
color: "#ff294d"
showinmenu: true
---

## Problem description

Warren y sus amigos piensan ir de paseo hacia Arequipa, para celebrar sus buenas notas en todos los cursos. Ellos contrataron un omnibus interprovincial para realizar el viaje, hicieron el contrato para viajar a las $$5:00$$ am y todos debian estar puntuales. 

Llegado el día del viaje Warren se quedó dormido así que se apresuro en alistarse, y como es una persona ahorradora decidió irse en combi pues confiaba que llegaría a tiempo. Cuando llegó terminal terrestre, el omnibus al que debía embarcar ya había salido y se encontraba a una distancia $$d$$ del terminal (considerar que todo el trayecto es una línea recta). Sin embargo, aún tiene la opción de realizar el viaje con sus amigos tomando un taxi e intentar dar alcance al omnibus. El taxi va a una velocidad constante de $$v_t$$ y Waren quiere saber si es posible alcanzar al omnibus que tiene una velocidad constante de $$v_o$$, y si fuera así en cuanto tiempo podría alcanzar al bus.

Ayuda a Warren con su dilema.

## Input

La entrada del problema contiene varios casos de prueba. La primera línea es un entero $$T$$ ($$1 \leq T \leq 10^4$$) indicando el número de casos de prueba. Para cada caso, se sigue el siguiente formato de entrada:

  * Una línea que contiene 3 enteros $$v_t, v_o$$ y $$d$$ indicando la velocidad del taxi, velocidad del omnibus, y la distancia entre la terminal y el omnimus ($$0 \leq v_t, v_o, d$$).

## Output

Para cada caso de prueba, el programa deber\'a imprimir el tiempo en el cual el taxi puede alcanzar al omnibus con 10 dígitos de precisión, si fuese imposible entonces deber\'a imprimir $$-1$$.

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
      2 2 2<br>
      5 3 11<br>
      </td>
      <td> 
        -1<br>
        5.5000000000<br>
      </td>
    </tr>
  </table>
</div>

## Observación

Para imprimir un número con 10 dígitos de precisión:

  + **C** `printf("%.10f", valor);`

  + **C++** `std::cout << std::set_precission(10) << valor;`

  + **C#** `System.Console.WriteLine("{0:F10}", valor);`

  + **Python** `print "%.10f" % valor`

  + **Java** `System.out.printf("%.10f", valor);`
