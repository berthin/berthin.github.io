---
layout: post
title:  "X CusContest"
date:   2016-07-21 12:36:13 -0500
categories: cuscontest
edit_link: 2016-07-21-cuscontest.markdown
---
# Problem Set 

* [Problem A. Horarios](#Problem-A)
* [Problem B. Brigada de Ataque](#Problem-B)
* [Problem C. Cuadradolandia](#Problem-C)
* [Problem D. Invertidor de Cadenas](#Problem-D)
* [Problem E. Warrencio y el Dota](#Problem-E)
* [Problem F. Baile de Invierno](#Problem-F)
* [Problem G. El viaje de de Adam](#Problem-G)
* [Problem H. Un viaje de ensueño](#Problem-H)


### Problem A. Horarios <a id="Problem-A"/>
* Sea $$ H = \lbrace (t_{o_1}, t_{f_1}), (t_{o_2}, t_{f_2}), \dots (t_{o_N}, t_{f_N}) \rbrace $$ un conjunto indicando los horarios de $$ N $$ cursos tal que: $$ (t_{o_p}, t_{f_p}) $$ indica el tiempo de inicio y tiempo fin para el $$ p $$-ésimo curso ($$ 1 \leq k \leq N $$). Nos piden obtener el máximo intérvalo libre entre cursos ($$ t_{libre} $$) y el máximo intérvalo consecutivo de cursos ($$ t_{ocupado}$$).
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
  # El caso base indica que H2 estará formado por al meno el primer
  # curso en H
  append(H[0])
  # Iterar sobre el resto de cursos (desde el índice 1 al N-1) e 
  # intentar combinar los horarios de los cursos cuando sea posible 
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
