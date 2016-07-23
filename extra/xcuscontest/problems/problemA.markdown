---
layout: problem
title: "Problem A: Horarios"
date: 2016-07-22 21:12 -0500
categories: cuscontest
color: "#ff294d"
showinmenu: true
---

## Problem description

En la carrera profesional de Ingeniería Informática y de Sistemas muchos alumnos llevan cursos en diferentes horarios. Algunos cursos pueden ser en la mañana, tarde o noche y no siempre se tiene un horario consecutivo.

Warnoldo, es un estudiante de la carrera que estaba preocupado en determinar cuanto es el máximo intérvalo libre y el máximo intervalo consecutivo de cursos que tiene. No es difícil averiguar para una sóla persona dicha información, pero muchos estudiantes al enterarse de la idea de Warnoldo también sienten curiosidad para determinar dichos valores. Por tanto, ahora se necesita diseñar un programa que realice la tarea mencionada.

Dados $$N$$ cursos y el intérvalo de tiempo (en minutos) de cada curso, tu tarea es determinar el máximo intérvalo libre entre cursos($$t_{libre}$$) y el máximo intérvalo donde estarás ocupado en los cursos($$t_{ocupado}$$). Por conveniencia, todos los cursos comienzan a las 7am, los minutos se contarán a partir de las 7am y por tanto, la información de cada curso tendrá un <span class="texttt">tiempo<sub>inicio</sub></span> ($$t_o$$) y <span class="texttt">tiempo<sub>fin</sub></span> ($$t_f$$) ambos en minutos. Si un curso comienza a las 7am y termina a las 9am, $$t_o$$ será igual a 0 y $$t_f$$ igual a 120.  

Existe la posibilidad de que los horarios para algunos cursos se sobrepongan.

## Input

La entrada del problema contiene varios casos de prueba. La primera línea es un entero $$T$$ $$(1\leq T \leq 10)$$ indicando el número de casos de prueba. Para cada caso, se sigue el siguiente formato de entrada:

  * La primera línea contiene contiene un número entero $$N$$ indicando la cantidad de cursos ($$0<N\leq 5\times10^3$$).

  * Las siguientes $$N$$ líneas contienen dos enteros $$t_o$$ y $$t_f$$ indicando el tiempo de inicio y fin de cada curso ($$0 \leq t_o < t_f$$).

## Output

Para cada caso de prueba, el programa deberá imprimir una línea mostrando los valores de $$t_{libre}$$ y $$t_{ocupado}$$ por un espacio en blanco.

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
        2<br>
        0 120<br>
        240 360<br>
        3<br>
        30 100<br>
        70 120<br>
        150 210<br>
      </td>
      <td> 
        120 120<br>
        30 90<br>
      </td>
    </tr>
  </table>
</div>
