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

### Problem B. Brigada de Ataque <a id="Problem-B"/>
* Dados $$N$$ soldados con fuerzas $$F=\{f_1, f_2, \dots, f_N\}$$ tal que $$f_i$$ indica la fuerza del $$i$$-ésimo soldado. El problema pide encontrar la máxima longitud de un subconjunto $$L \subseteq F$$ tal que $$L = \{f_{s_1}, f_{s_2}, \dots, f_{s_M} \}$$ donde $$S = \{s_1, s_2, \dots, s_M\}$$ siempre y cuando se cumpla:

\begin{align}
  0 < s_p < s_q \leq N \iff p < q \cr
  0 \leq M \leq N \cr
  f_{s_p} > f_{s_q}, ~~ \forall f_{s_p}, f_{s_q} \in F \text{ s.t. } 1 \leq p < q \leq M
\end{align}
  
  $$F$$ será conocida como una subsecuencia decreciente de longitud máxima (LDS: *longest decreasing subsequence*), y por tanto la respuesta que nos piden hallar viene a ser dada por $$M$$.

* Sea $$H = \{h_1=f_N, h_2=f_{N-1}, \dots, h_N=f_1\}$$ el conjunto $$F$$ pero invertido. Ahora el problema consiste en obtener la longitud de la subsecuencia creciente máxima (LIS: *longest increasing subsequence*). Dado que la longuitud del LIS de $$H$$ es la misma que la longitud del LDS de $$F$$. Podemos encontrar el LIS de $$H$$ y así poder resolver el problema.

* El cómo resolver el problema de LIS se va a obviar dado que existen mucha información disponible en libros y sitios web. Se recomienda leer uno de los siguientes artículos:
  * [LIS (@geeksforgeeks)](http://www.geeksforgeeks.org/longest-monotonically-increasing-subsequence-size-n-log-n/)
  * [LIS (@algorithmist)](http://www.algorithmist.com/index.php/Longest_Increasing_Subsequence)
  * [LIS (princeton slides)](https://www.cs.princeton.edu/courses/archive/spring13/cos423/lectures/LongestIncreasingSubsequence.pdf)

* La idea para encontrar el valor de $$M$$ es enfocarnos en ubicar para cada elemento de $$H$$ la mejor posición en una subsecuencia creciente $$R$$ que a cada iteración va formándose. 

  Por ejemplo, sea `H = {3, 5, 6, 2, 7, 10, 8, 9}`:

    * Para $$h_1 = 3$$: `R = {3}`. Caso base.
    * Para $$h_2 = 5$$: `R = {3, 5}`. Dado que `5` es mayor al último elemento de $$R$$, la subsecuencia puede aumentar.
    * Para $$h_3 = 6$$: `R = {3, 5, 6}`. Dado que `6` es mayor al último elemento de $$R$$, la subsecuencia puede aumentar.
    * Para $$h_4 = 2$$: `R = {2, 5, 6}`. La mejor posición de `2` en una subsecuencia creciente es la primera dado que es menor a `3`.
    * Para $$h_5 = 7$$: `R = {2, 5, 6, 7}`. Dado que `7` es mayor al último elemento de $$R$$, la subsecuencia puede aumentar.
    * Para $$h_6 = 10$$: `R = {2, 5, 6, 7, 10}`. Dado que `10` es mayor al último elemento de $$R$$, la subsecuencia puede aumentar.
    * Para $$h_7 = 8$$: `R = {2, 5, 6, 7, 8}`. La mejor posición de `8` en una subsecuencia creciente es la ultima dado que es menor a `10`. Quiere decir que nos combiene tener a `8` en esa posición en lugar de `10`.
    * Para $$h_8 = 9$$: `R = {2, 5, 6, 7, 8, 9}`. Dado que `9` es mayor al último elemento de $$R$$, la subsecuencia puede aumentar.

  Como resultado final, $$M = length(R) = 6$$. Sin embargo, $$R$$ no es el LIS de $$H$$, sólo se ha llegado a determinar la longitud que nos piden como respuesta.
* Por lo tanto, la estrategia a usar es la siguiente:
  * Crear $$R$$
  * Si el último elemento de $$R$$ es menor a $$h_i$$, agregar $$h_i$$ a $$R$$.
  * Caso contrario, buscar la posición de $$h_i$$ en $$R$$ y reemplazar el elemento en esa posición por $$h_i$$.

* **Ejercicio:**  Demostrar $$R$$ es una subsecuencia creciente en cada paso.
* **Ejercicio:**  Demostrar que al reemplazar un elemento en $$R$$ por $$h_i$$, el LIS que contenga al elemento $$h_i$$ tendrá longitud igual a la posición del elemento de $$R$$ que será reemplazado por $$h_i$$.
* **Ejercicio:**  Sea $$L = LIS(H)$$, demostrar que $$length(L)$$, bajo la anterior estratégia, es igual a $$length(R)$$.
* Código en Python:

```python
# Leer T (numero de casos de prueba)
T = int(raw_input())
# Procesar cada caso
for i in xrange(T):
  # Leer N (longuitud de F)
  N = int(raw_input())
  # Leer F (las fuerzas de los soldados)
  F = map(int, raw_input().split(' '))
  # Crear H (invertir F)
  H = F[::-1]
  # Init R
  R = [H[0]]
  # Procesar el resto de elementos de H
  for h_i in H[1:]:
    # Si el ultimo elemento de R es menor a h_i, agregar h_i a R
    if R[-1] < h_i:
      R.append(h_i)
    # Buscar la posicion de h_i en R mediante búsqueda binaria (esto es posible
    # dado que R es una subsecuencia creciente)
    low, high = 0, len(R)
    while high - low > 1:
        mid = (low + high) / 2
        if h_i < R[mid]:
            high = mid
        else:
            low = mid
    # Reemplazar h_i por el elemento que corresponde dentro de R, de esta forma
    # h_i se encontrara en la mejor posicion dentro de R
    R[mid] = h_i
  # Mostrar M = len(R), la longitud del LIS de H
  print len(R)
```


### Problem C. Cuadradolandia <a id="Problem-C"/>

* Se tiene una figura $$D$$-dimensional, y nos piden contar el número de hypercubos de $$\underbrace{K\times K\times \dots \times K}_{D~veces}$$ para $$1 \leq K \leq N$$.
* Como dato de entrada nos dan un número $$M$$ que indica el número de hypercubos de $$\underbrace{1\times 1\times \dots \times 1}_{D~veces}$$ que hay para un determinado espacio $$D$$-dimensional, por lo que:
\begin{equation}
\begin{split}
  N ^ D &= M \cr
  N &= \sqrt[D]{M}
\end{split}
\end{equation}
* Suponiendo que $$D=2$$:
  * Para cuadrados de dimension $$1\times 1$$ se tienen $$N \times N $$ cuadrados.
  * Para cuadrados de dimension $$2\times 2$$ se tienen $$(N - 1) \times (N - 1) $$ cuadrados.
  * Para cuadrados de dimension $$3\times 3$$ se tienen $$(N - 2) \times (N - 2)$$ cuadrados.

    $$\vdots$$

  * Para cuadrados de dimension $$N\times N$$ se tienen $$(N - (N - 1)) \times (N - (N - 1)) $$ cuadrados.
  * Siendo el número total de cuadrados igual a:
  \begin{equation}
    \sum_{K=1}^{N}{K^2}
  \end{equation}
* De manera general, para un espacio $$D$$ dimensional, el número de hipercubos estará expresado mediante:
\begin{equation}
  \sum_{K=1}^{N}{K^D}
\end{equation}

* Código Python:

```python
# Leer T (número de casos de prueba)
T = int(raw_input())
# Procesar cada caso
for iT in xrange(T):
  # Leer M, D (el numero de figuras de 1x1x...x1 (D-veces), y la dimension en la
  # que se encuentran el espacio)
  M, D = map(int, raw_input().split(' '))
  # Calcular N
  N = M ** (1. / D)
  # Obtener el número de hypercubos
  ans = sum([K ** D for K in xrange(1, N + 1)])
  # Mostrar la respuesta
  print ans

```


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
  S = sentence[:-1].lower().split(' ')
  # Invertir S (el conjunto de palabras en la oración)
  S.reverse()
  # Crear una nueva oración uniendo las palabras en S mediante espacios en blanco
  answer = ' '.join(S)
  # Mostrar la nueva oración considerando que el primer caracter debe de estar
  # en MAYUSCULA y la oracion tiene que terminar con un punto
  print answer[:1].upper() + answer[1:] + '.'
```


### Problem E. <a id="Problem-E"/>

### Problem F. Baile de Invierno <a id="Problem-F"/>
* Dados dos conjuntos $$X=\{ x_1, x_2, \dots, x_N\}$$ y $$Y=\{ y_1, y_2, \dots, y_M$$ representando las habilidades de baile de $$N$$ hombres y $$M$$ mujeres respectivamente, se pide hallar un subjconjunto $$S \subset X \times Y$$, tal que $$\forall s_k = (x_i, y_j) \in S$$, se cumpla lo siguiente:
\begin{equation}
  (x_i - y_j)^2 \leq D^2
  \label{eqF:D}
\end{equation}
  En otras palabras, $$S$$ es un conjunto de tuplas $$(x_i, y_j)$$ indicando que es posible formar una pareja entre el $$i$$-ésimo varón y la $$j$$-ésima mujer cumpliendo que sus habilidades de baile no sean diferentes por más de una diferencia de $$D$$.
* El problema nos pide hallar la longitud del máximo $$S$$ que se puede formar cumpliendo con la condición en \eqref{eqF:D}
* Suponiendo que tanto $$X$$ como $$Y$$ están ordenados ascendentemente, definamos una función $$f(i, j)$$ que determine la longitud del subconjunto $$S \subset X_{1\dots i} \times Y_{1\dots j}$$ que puede ser obtenido utilizando los $$i$$ primeros elementos de $$X$$ y $$j$$ primeros elementos de $$Y$$. La solución al problema está dado por $$f(N, M)$$.

$$
\begin{equation}
  f(i,j) =\left\{
    \begin{matrix}
      0 & \text{if} & i == 0 \text{ or } j == 0\\ 
      1 + f(i - 1, j - 1) & \text{if} &  (x_i - y_j)^2 \leq D\\
      f(i, j - 1) & \text{if} & x_i < y_j \\
      f(i - 1, j) & \text{otherwise} & x_i > y_j 
    \end{matrix}\right.
    \label{eqF:f}
  \end{equation}
$$

* *TODO: prueba de la solucion*
* Código Python

```python
# Leer T (número de casos de prueba)
T = int(raw_input())
# Procesar cada caso
for iT in xrange(T):
  # Leer M, N, D (nro de varones, nro de mujeres, la máxima diferencia permitida
  # para formar parejas de baile)
  M, N, D = map(int, raw_input().split(' '))
  # Leer X (habilidades de baile de los varones)
  X = map(int, raw_input().split(' '))
  # Leer Y (habilidades de baile de las mujeres)
  Y = map(int, raw_input().split(' '))
  # Inicializar punteros i, j (Notar que se trabaja con arreglos con índice 0
  # como inicio)
  i, j = N - 1, M - 1
  # Inicializar el contador de parejas formadas hasta el momento
  n_parejas = 0
  # Intentar formar las parejas
  while i >= 0 and j >= 0:
    if (X[i] - Y[j]) ** 2 <= D**2:
      n_parejas += 1
      i -= 1
      j -= 1
    elif X[i] < Y[j]:
      j -= 1
    else:
      i -= 1
  # Mostrar el resultado
  print '# maximo de parejas equilibradas = %d' % n_parejas
```

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
    u_dig = (u_dig * (a_i % 10)) % 10

  # Mostrar los resultados
  print p_dig, u_dig
```

### Problem H. Un viaje de ensueño <a id="Problem-H"/>

* Se tiene un omnibus con una velocidad constante $$v_o$$ que parte de un punto de inicio $$P$$ y al cabo de un tiempo, un taxi con una velocidad constante $$v_t$$ parte desde el mismo punto de inicio $$P$$ para intentar alcanzar al omnibus que ya se encuentra a una distancia $$d$$ de $$P$$.
* El problema nos pide averguar si el taxi podrá alcanzar al omnibus, si es así mostrar el tiempo que demorará y caso contrario mostrar $$-1$$.
* Suponiendo que existe un punto $$D$$ en el que el taxi logra a alcanzar al omnibus en un tiempo $$T$$, entonces las siguientes relaciones (considerando el movimiento rectilíneo uniforme) tanto para el omnibus como para el taxi tenemos:
\begin{align}
  D &= d + v_o T \label{eqH:Domn} \cr
  D &= v_t T \label{eqH:Dtaxi}
\end{align}

  Reemplazando \eqref{eqH:Dtaxi} en \eqref{eqH:Domn}:
\begin{equation}
\begin{split}
  v_t T &= d + v_o T \cr
  (v_t - v_o) T &= d \cr
  T &= \frac{d}{v_t - v_o}
\end{split}
\label{eqH:sol}
\end{equation}

  Por lo tanto, si ambos vehículos llegan a encontrarse, estos lo harán después de un tiempo $$T$$.
* Dado que se ha partido de la supocisión que existe un punto de encuentro, se debe de cumplir:
\begin{equation}
  0 < v_t - v_o
\end{equation}
  Caso contrario, si dicha condición no se cumple, podemos deducir que el punto de encuentro no existe.

* Código Python:

```python
# Leer T (número de casos de prueba)
T = int(raw_input())
# Procesar cada caso
for iT in xrange(T):
  # Leer v_t, v_o, y d (velocidad del taxi, velocidad el omnibus, y la distancia
  # entre el punto inicial y el punto donde se encuentra actualmente el omnibus)
  v_t, v_o, d = map(int, raw_input().split(' '))
  # Determinar si existe punto de encuentro, y si es el caso, mostrar el tiempo
  # que demorará el taxi en alcanzar al omnibus
  if v_t - v_o <= 0:
    print "-1"
  else:
    print "%.10f" % (d * 1.0 / (vt - vo))
```
