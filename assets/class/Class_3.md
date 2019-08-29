---
title:
 - Clase 3
subtitle: |
 | Análisis de algoritmos
 | Introducción a matemáticas discretas
 | (Comp. 420)
author:
 - José Joaquín Zubieta Rico
institute:
 - $^1$Universidad de Guanajuato
logo:
 - img/escudo.jpg
theme:
 - metropolis
output:
 - Class_3.pdf
abstract:
 - Introducción en ecuaciones en diferencias.
---

# Ecuaciones en diferencias

## Ejemplo

Tenemos una caja de $2 \times n$ y fichas de $2 \times 1$, y se tienen las
siguientes preguntas.

 - Encontrar un algoritmo para generar las distintas
   maneras para llenar la caja con las fichas.
 - Calcular $a_n$, que se define como la cantidad de
   maneras distintas en las que se pueden acomodar
   las fichas.

### Hechos

Tenemos que $a_1 = 1$, $a_2 = 2$. Tenemos que en general
$$
    a_n = a_{n-1} + a_{n-2}
$$

### ¿Cómo resolverlo?

**Observación 1**, si fijamos $\overrightarrow{x} = (a_1, a_2)$, toda la recurrencia
es fija.

Para tratar con el problema pasamos a un _problema más general_, es decir
$$
    a_n = a_{n-1} + a_{n-2}
$$ {#eq:eqn1}
con $a_1, a_2$ libres.

**Observaciones 2**

 1. $a_n(x+y) = a_n(x) + a_n(y)$
 2. $a_n(cx) = ca_n(x)$

**Observaciones 3**

Sean $a_n$ y $a_n^2$ dos soluciones independientes, entonces, cualquier
solución de @eq:eqn1 es de la forma
$$
    a_n = c_1 a_n + c_2 a_n^2 \qquad c_1,c_2 \in \mathbb{R}
$$

**Iluminación divina**

Trata $a_n = r^n$ con $r \in \mathbb{R}$. Substituyendo en lo anterior
$$
    r^n = r^{n-1} + r^{n-2}, \quad n \geq 3
$$
dividiendo por $r^{n-2}$
$$
    r^2 = r + 1.
$$
Resolviendo por la fórmula general obtenemos dos soluciones
$$
\begin{aligned}
    r_1 & = & \frac{1 + \sqrt{5}}{2} \\
    r_2 & = & \frac{1 - \sqrt{5}}{2}
\end{aligned}
$$
de esto obtenemos que la solución general del problema es
$$
    a_n = c_1 r_1^{n-1} + c_2 r_2^{n-2}
$$

## Caso general

Tenemos interés en ecuaciones de la forma
$$
    a_{n+k} + b_1 a_{n+k-1} + \cdots + b_k a_n = f_n, \quad n \in {\mathbb{N}}_0
$$

Notemos las siguientes dos cosas acerca de la ecuación

 - la ecuación es lineal (en $a_n$) con coeficientes constantes
   ($b$'s no dependen de $n$) de orden $k$.
 - si para todo $n$ se da que $f_n = 0$ entonces la ecuación se llama
   homogénea, en caso contrario se llama no-homogénea.

### Caso homogéneo

Solución es totalmente determinado por $\overrightarrow{x}$.

#### Observación 1

#### Observación 2

Sean ${a_n^{\textrm'}}, \cdots {a_n^k}$, $k$ solución independiente, entonces cualquier
solución es de la forma
$$
    a_n = \sum_{i=1}^{k}{c_i a_n^i} \quad c_i \in \mathbb{R}
$$

 - $\textrm`\textrm`\Rightarrow\textrm'\textrm'$ Supongamos ${a_n^{*}}$ es solución
   - $\exists\ \overrightarrow{x}^{*} \in \mathbb{R}; \quad a_n^{*} = a_n(\overrightarrow{x}^{*})$
   - $\exists\ \overrightarrow{x}^{*} \in \mathbb{R}; \quad a_n^{*} = a_n(\overrightarrow{x}^{*})$

