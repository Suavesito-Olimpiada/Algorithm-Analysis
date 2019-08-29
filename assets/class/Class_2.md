---
title:
 - Clase 2
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
 - Class_2.pdf
abstract:
 - Notación asintótica y su uso en complejidad.
---

# Nota asintótica


## Notación $\Theta()$

Se usa para acotar la función por arriba y por abajo por una clase de funciones.

### Definición.

Dada una función $g(n)$, denotamos $\Theta(g(n))$ al conjunto de funciones tales que

 - $\Theta(g(n)) = \{f(n): \text{existen constantes positivas } c_1,c_2 \text{ y } n_0 \text{ tales que }\\ 0 \leq c_1g(n) \leq f(n) \leq c_2g(n)\ \forall n \geq n_0\}$

de lo que se dice que $f(n) \in \Theta(g(n))$.

### Ejemplo

Dada $f(n) = \frac{1}{2}n^2-3n$, tenemos que $f(n) \in \Theta(n^2)$, esto porque
$$
\begin{aligned}
    \frac{1}{14}n^2 \leq \frac{1}{2}n^2-3n \leq \frac{1}{2}n^2 \quad\forall n > 7.
\end{aligned}
$$

## Notación $O()$

Se usa para acotar una función asintótica por arriba.

## Notación $\Omega()$

Se usa para acotar una función asintóticamente por abajo.

## Más notaciones

_Donald Knuth_ completa la notación asintótica de funciones con las notaciones

 - $o()$, que corresponde a la cota superior «apretada» de la función-
 - $\omega()$, que corresponde a la cota inferior «apretada» de la función.

Lo que diferencia las notaciones mayores y menores es que en las notaciones menores
la complejidad debe de ser válida para **todas** las constantes.

## Propiedades

Las propiedades de la notación asintótica son

 - **transitiva**
   - Si $f(n) \in O(g(n))$ y $g(n) \in O(h(n))$, entonces $f(n) \in O(h(n))$.
   - Si $f(n) \in \Omega(g(n))$ y $g(n) \in \Omega(h(n))$, entonces $f(n) \in \Omega(h(n))$.
 - **suma**: permanece el de máxima complejidad.
 - **producto**: la complejidad del producto de funciones es el producto
    de sus complejidades.
 - **reflexiva**:
   - $f(n) \in \Theta(g(n)) \Leftrightarrow g(n) \in \Theta(f(n))$
   - $f(n) \in O(g(n)) \Leftrightarrow g(n) \in \Omega(f(n))$
   - $f(n) \in o(g(n)) \Leftrightarrow g(n) \in \omega(f(n))$

