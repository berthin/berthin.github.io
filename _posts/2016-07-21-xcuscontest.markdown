---
layout: post
title:  "X CusContest"
date:   2016-07-21 12:36:13 -0500
categories: cuscontest
edit_link: 2016-07-21-xcuscontest.markdown
---
<style type="text/css">
.circle {
    width: 14px;
    height: 14px;
    border-radius: 50%;
    border: solid 1px black;
    display: inline-block;
}
.score_correct   { background: #60e760; }
.score_first     { background: #1daa1d !important; }
.score_incorrect { background: #e87272; }
</style>


<!---
<ul class="nav nav-pills">
  <li role="presentation" class="dropdown">
    <a class="dropdown-toggle" data-toggle="dropdown" href="#" role="button" aria-haspopup="true" aria-expanded="false">Problems Analysis <span class="caret"></span></a>
    <ul class="dropdown-menu">
      <li><a href="#Problem-C">H</a></li>
    </ul>
  </li>
  <li role="presentation"><a href="../../../../extra/xcuscontest/board/Scoreboard.html">Scoreboard</a></li>
  <li role="presentation"><a href="../../../../extra/xcuscontest/problems/problemA.html">Extras</a></li>
</ul>
-->

# Scoreboard 

<div class="panel panel-default">
  <div class="panel-heading">
  Top 3
  <a href="#" onclick="return popitup('../../../../extra/xcuscontest/board/Scoreboard.html', 'Scoreboard')">(scoreboard completo)</a>
  </div>
  <table class="table">
    <tr>
      <th>RANK</th>
      <th>TEAM</th>
      <th>SCORE</th>
      <th>A <div class="circle" style="background: #ff294d;"></div></th>
      <th>B <div class="circle" style="background: #ff1cca;"></div></th>
      <th>C <div class="circle" style="background: #f7ff0f;"></div></th>
      <th>D <div class="circle" style="background: #71ff12;"></div></th>
      <th>E <div class="circle" style="background: #19ffc2;"></div></th>
      <th>F <div class="circle" style="background: #0a33ff;"></div></th>
      <th>G <div class="circle" style="background: #b012ff;"></div></th>
      <th>H <div class="circle" style="background: #eeeddf;"></div></th>
    </tr>
    <tr>
      <th>1</th><td>[ACM] 1BUCLE + Rick </td><td> <b>6</b> &nbsp;&nbsp;830</td><td class="score_correct"> 4/199 </td><td class="score_correct"> 2/229 </td><td class="score_correct"> 1/206 </td><td class="score_correct"> 3/36 </td><td class="score_incorrect"> 1  </td><td class="score_incorrect"> 2 </td><td class="score_correct"> 1/31 </td><td class="score_first"> 1/9 </td>
    </tr>
    <tr>
      <th>2</th><td> InflACMe un Globo</td><td> <b>5</b> &nbsp;&nbsp;815 </td><td class="score_correct"> 6/213 </td><td class="score_first"> 1/117 </td><td class="score_correct"> 1/199 </td><td class="score_correct"> 1/72 </td><td class="score_incorrect"> 1 </td><td class="score_incorrect"> 1 </td><td class="score_incorrect"> 2 </td><td class="score_correct"> 2/34 </td>
    </tr>
    <tr>
      <th>3</th><td> Team C# ONE</td><td><b>4</b> &nbsp;&nbsp;297 </td><td> 0 </td><td> 0 </td><td class="score_first"> 1/114 </td><td class="score_correct"> 1/86 </td><td class="score_incorrect"> 2 </td><td> 0 </td><td class="score_correct"> 1/59 </td><td class="score_correct"> 1/38 </td>
    </tr>
  </table>
</div>

# Problem Set 

* [Problem A. Horarios](#Problem-A) ....................... [(descripción del problema)](
../../../../extra/xcuscontest/problems/problemA.html)
* [Problem B. Brigada de Ataque](#Problem-B) ......... [(descripción del problema)](
../../../../extra/xcuscontest/problems/problemB.html)
* [Problem C. Cuadradolandia](#Problem-C) ............. [(descripción del problema)](
../../../../extra/xcuscontest/problems/problemC.html)
* [Problem D. Invertidor de Cadenas](#Problem-D) .... [(descripción del problema)](
../../../../extra/xcuscontest/problems/problemD.html)
* [Problem E. Warrencio y el Dota](#Problem-E) ........ [(descripción del problema)](
../../../../extra/xcuscontest/problems/problemE.html)
* [Problem F. Baile de Invierno](#Problem-F) ............ [(descripción del problema)](
../../../../extra/xcuscontest/problems/problemF.html)
* [Problem G. El viaje de de Adam](#Problem-G) ....... [(descripción del problema)](
../../../../extra/xcuscontest/problems/problemG.html)
* [Problem H. Un viaje de ensueño](#Problem-H) ...... [(descripción del problema)](
  ../../../../extra/xcuscontest/problems/problemH.html)

# Problem Set Analysis

### Problem A. Horarios <a id="Problem-A"/>
* Sea $$ H = \lbrace (t_{o_1}, t_{f_1}), (t_{o_2}, t_{f_2}), \dots (t_{o_N}, t_{f_N}) \rbrace $$ un conjunto indicando los horarios de $$ N $$ cursos tal que: $$ (t_{o_p}, t_{f_p}) $$ indica el tiempo de inicio y tiempo fin para el $$ p $$-ésimo curso ($$ 1 \leq p \leq N $$). Nos piden obtener el máximo intérvalo libre entre cursos ($$ t_{libre} $$) y el máximo intérvalo consecutivo de cursos ($$ t_{ocupado}$$).
* Por conveniencia, vamos a definir que $$ H $$ es un conjunto ordenado crecientemente considerando que $$ (t_{o_p}, t_{f_p}) <= (t_{o_q}, t_{f_q}) $$ si $$ t_{o_p} \leq t_{o_q} \wedge t_{o_q} \leq t_{f_p} $$ para todo $$ 1 \leq p < q \leq N $$.
* Suponiendo que no hay intersección entre los horarios, es decir $$t_{f_p} < t_{o_q}$$, la respuesta sería:


\begin{equation}
\begin{split}
  t_{libre} &= \max_{1 \leq p < q \leq N}{( t_{f_{q}} - t_{o_{p}})}\cr
  t_{ocupado} &= \max_{1 \leq p \leq N}{( t_{f_p} - t_{o_p})}
\end{split}
\label{eqA1}
\end{equation}

* Sin embargo, el problema indica que esta condición no siempre se cumple y hay casos donde los cursos de sobreponen. Pero dado que a nosotros únicamente nos importa averiguar los valores de $$t_{libre}$$ y $$t_{ocupado}$$ podemos combinar aquellos cursos que se sobreponen de tal forma que obtengamos un nuevo conjunto $$\hat{H}$$ que contenga horarios que no tengan sobreposición.
* Finalmente, hemos logrado reducir el problema inicial que tiene horarios con sobreposición a un problema donde no hay intersección de horarios, por consiguiente la obtención de la respuesta está dada mediante las fórmulas en \eqref{eqA1}.

* Codigo Python:

```python
# Determina si 2 horarios se sobreponen
def exists_overlapping((t_o_p, t_f_p), (t_o_q, t_f_q)):
  return (t_o_p <= t_o_q and t_o_q <= t_f_p)

# Combinar 2 horarios que tienen sobreposición 
def merge((t_o_p, t_f_p), (t_o_q, t_f_q)):
  return (t_o_p, max(t_f_p, t_f_q))

# Leer T (numero de casos de prueba)
T = int(raw_input())

# Procesar cada caso 
for iT in xrange(T):
  # Leer N (number cursos)
  N = int(raw_input())
  # Inicializar H que contrendrá los N cursos 
  H = []
  # Leer el horario inicio(t_o) y fin(t_f) de cada curso 
  for i in xrange(N):
    t_o, t_f = map(int, raw_input().split(' ')) 
    H.append((t_o, t_f))
  # Ordenar los horarios 
  H.sort()
  # Inicializar Ĥ como H2
  H2 = []
  # El caso base indica que H2 estará formado por al meno el primer curso en H
  H2.append(H[0])
  # Iterar sobre el resto de cursos (desde el índice 1 al N-1) e intentar
  # combinar los horarios de los cursos cuando sea posible 
  for (t_o, t_f) in H[1:]:
    if exists_overlapping(H2[-1], (t_o, t_f)):
      H2[-1] = merge(H2[-1], (t_o, t_f))
    else:
      H2.append((t_o, t_f))
  # Obtener el nuevo número de horarios formados en H2
  len_H2 = len(H2)
  # Calcular t_libre
  t_libre = max([(t_o_q - t_f_p)
    for ((t_o_p, t_f_p), (t_o_q, t_f_q)) in zip(H2[:len_H2], H2[1:])
  ])
  # Calcular t_ocupado
  t_ocupado = max([(t_f - t_o) for (t_o, t_f) in H2])
  # Mostrar las respuestas 
  print t_libre, t_ocupado
```

### Problem B. <a id="Problem-B"/>

### Problem C. Cuadradolandia <a id="Problem-C"/>

### Problem D. Invertidor de Cadenas <a id="Problem-D"/>

* Dada una oración compuesta con un conjunto de palabras y un punto final, el objetivo del problema es invertir el orden de las palabras considerando que la oración resultante deba de tener la primera letra de la primera palabra en **MAYUSCULA** y la oración termine con un **PUNTO FINAL**.
* Sea $$S=\{ w_1, w_2, \dots, w_N \}$$ el conjunto de palabras en **MINUSCULA** obtenidas de la oración inicial que nos dan como dato de entrada. Por ejemplo, si la oración es `Facil ser de antes dificil es todo.` entonces $$S = \{\text{facil, ser, de, antes, dificil, es, todo} \} $$, la respuesta que nos piden es mostrar las palabras del conjunto $$S$$ en orden invertido.
* Código Python:

```python
# Leer T (número de casos de prueba)
T = int(raw_input())
# Procesar cada caso
for iT in xrange(T):
  # Leer la oración
  sentence = raw_input()
  # Convertir la oración a minúsculas, y dividirla en palabras sin considerar
  # el punto final
  S = sentence[:-1].lower()split(' ')
  # Invertir S (el conjunto de palabras en la oración)
  S.reverse()
  # Crear una nueva oración uniendo las palabras en S mediante espacios en blanco
  answer = ' '.join(S)
  # Mostrar la nueva oración considerando que el primer caracter debe de estar
  # en MAYUSCULA y la oracion tiene que terminar con un punto
  print answer[:1].upper() + answer[1:] + '.'
```


### Problem E. <a id="Problem-E"/>

### Problem F. <a id="Problem-F"/>

### Problem G. El viaje de Adam <a id="Problem-G"/>

* Dadas $$N+1$$ ciudades y sea $$A=\{a_1, a_2, \dots, a_N \}$$ un conjunto tal que $$a_i$$ indica el número de caminos de la $$i$$-ésima ciudad a la ciudad $$i+1$$. El problema nos piden contar el número de caminos posibles que hay desde la ciudad $$1$$ hasta la ciudad $$N+1$$, sin embargo dado que dicho número puede ser muy grande ($$10^{9000}$$ en el peor de los casos), sólo debemos de mostrar el primer y último dígito.
* Sea $$P$$ el número de caminos posibles entras las ciudades $$1$$ y $$N+1$$, y $$K$$ el número de dígitos que tiene $$P$$:

  El primer dígito de $$P$$ será igual a:
  \begin{equation}
    d_{\text{digito}}^{\text{1er}} = \frac{P}{10^{K-1}} \label{eqG:1}
  \end{equation}
  y el último dígito será 
  \begin{equation}
    d_{\text{digito}}^{\text{ult}} = P \mod 10 \label{eqG:2}
  \end{equation}
  donde:
  \begin{align}
    P &= \prod_{i=1}^{N}{a_i} \label{eqG:P}\cr
    K &= 1 + \lfloor{\log_{10}(P)}\rfloor \label{eqG:K}
  \end{align}
* Por lo consiguiente, el problema consta de 2 sub-problemas: 

  1. **Obtener el primer dígito de $$P$$**

      Expresando \eqref{eqG:1} en términos de logaritmos, tenemos:

      \begin{equation}
        \begin{split}
          d_{\text{digito}}^{\text{1er}} &= e^{\log\({\frac{P}{10^{K-1}}}\)}   \cr
                                         &= e^{\log(P) - \log(10^{K-1})} \cr
                                         &= e^{\log(P) - (K-1)\log(10)}
        \end{split}
        \label{eqG:1log}
      \end{equation}
      del mismo modo con $$P$$, sea $$S=\log(P)$$ entonces:
      \begin{equation}
        P = e^{\log(P)} = e^{S} \label{eqG:logP}
      \end{equation}
      Reemplazando \eqref{eqG:logP} en \eqref{eqG:1log}:
      \begin{equation}
        \begin{split}
          d_{\text{digito}}^{\text{1er}} &= e^{\log(P) - (K-1)\log(10)}    \cr
                                         &= e^{\log(e^{S}) - (K-1)\log(10)}\cr
                                         &= e^{S - (K-1)\log(10)}
        \end{split}
        \label{eqG:1f}
      \end{equation}
      $$K$$ también puede ser representado mediante:
      \begin{equation}
        K = 1 + \lfloor{\sum_{i=1}^{N}{\log_{10}{(a_i)}}}\rfloor \label{eqG:K2}
      \end{equation}
      y aplicando propiedades de logaritmos en \eqref{eqG:P}:
      \begin{equation}
        S = \log{\(\prod_{i=1}^{N}{a_i}\)} = \sum_{i=1}^{N}{(\log(a_i))} \label{eqG:S}
      \end{equation}

      Finalmente, dado que $$d_{\text{digito}}^{\text{1er}}$$ es un número flotante, pero a nosotros únicamente nos interesa saber la parte entera, el primer dígito de $$P$$ será:
      \begin{equation}
        d_{\text{digito}}^{\text{1er}} = d_{\text{digito}}^{\text{1er}} - (d_{\text{digito}}^{\text{1er}} \mod 1)
      \end{equation}

  2. **Obtener el último dígito de $$P$$**
  
      Dado que la operación módulo por derecha es distributida con respecto a la multiplicación, es decir $$(A\cdot B) \mod M = ((A \mod M) \cdot (B \mod M)) \mod M$$, para obtener $$d_{\text{digito}}^{\text{ult}}$$ usaremos los valores de $$a_i \mod 10$$. Es importante realizar la operación módulo en cada iteración para la obtención del último dígito dado que en algún instante podríamos estar en un caso de *overflow* dados los límites de un número entero de 32 bits (ver código para mejor aclaración).

* Código en Python:

```python
# Importar libreria math que contiene la funcion log, log10, floor, y el valor
# de e (neperiano)
import math

# Leer T (número de casos de prueba)
T = int(raw_input())
# Procesar cada caso
for iT in xrange(T):
  # Leer N (número de ciudades - 1)
  N = int(raw_input())
  # Leer A (el número de caminos entre ciudades) 
  A = map(int, raw_input().split(' '))

  # Primer subproblema: primer dígito de P
  # Calcular S
  S = sum(map(math.log, A))
  # Calcular K
  K = 1 + math.floor(sum(map(math.log10, A)))
  # Calcular el primer digito
  p_dig = math.e ** (S - (K - 1) * math.log(10))
  # Obtener la parte entera de p_dig
  p_dig = int(p_dig - (p_dig % 1))

  # Segundo subproblema: ultimo digito de P
  # Obtener el ultimo digito usando la propiedad distributiva por derecha del
  # modulo para la multiplicacion
  u_dig = 1
  for a_i in A:
    u_dig = (u_dig * a_i) % 10

  # Mostrar los resultados
  print p_dig, u_dig
```

### Problem H. <a id="Problem-H"/>
