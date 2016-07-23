---
layout: problem
title: "Problem D: Invertidor de Cadenas"
date: 2016-07-22 21:12 -0500
categories: cuscontest
color: "#ff294d"
showinmenu: true
---

## Problem description


Reciéntemente, un grupo estudiantil decidió digitalizar todos los documentos de texto en la universidad. Xavier, estudiante de Informática quiso agilizar todo el procedimiento mediante algoritmos de reconocimiento de texto en imágenes. Sin embargo, su algoritmo tenía un error que invertía las oraciones. Por ejemplo, uno de los documentos que necesitan ser digitalizado contenía el siguiente texto:

<div class="alert alert-warning" role="info">
La derrota no es el peor de los fracasos.  No
intentarlo es el verdadero fracaso. La  unica 
decision  valida  es  no  rendirse  y  seguir
continuando la pelea.
</div>

Pero el algoritmo de Xavier retornaba:

<div class="alert alert-success" role="alert">
Fracasos  los  de  peor  el es no derrota la.
Fracaso   verdadero   el  es  intentarlo  no.
Pelea la continuando seguir y rendirse no  es
valida decision unica la.
</div>

Ayuda a Xavier diseñando un algoritmo que reciba como entrada una oración y genere la oración invertida correspondientemente.

Por simplicidad, dentro de una oración sólo el primer caracter de la primera palabra estará en mayúscula, y esto debe de cumplirse siempre. No habrán signos de puntuación a excepción del punto final que indica el fin de una oración. Considerar que entre dos palabras sólo habrá un espacio en blanco de separación.

## Input

La entrada del problema contiene varios casos de prueba. La primera línea es un entero $$T$$ indicando el número de casos de prueba. Para cada caso, se sigue el siguiente formato de entrada:

  * Una línea contieniendo la oración cuyo órden de palabras debe de ser invertido. La longitud total de la oración no será mayor a $$10^3$$ caracteres contando los espacios en blanco y el punto final.

## Output

Para cada caso de prueba, el programa deberá imprimir en una línea la oración en el órden correcto. 

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
        Facil ser de antes dificil es todo.<br>
        Quieres concurso el ganar si.<br>
        Debes pregunta esta resolver.<br>
      </td>
      <td> 
        Todo es dificil antes de ser facil.<br>
        Si ganar el concurso quieres.<br>
        Resolver esta pregunta debes.<br>
      </td>
    </tr>
  </table>
</div>
