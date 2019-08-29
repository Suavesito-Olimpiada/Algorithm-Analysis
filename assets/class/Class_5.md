---
title:
 -  Clase 5
subtitle: |
 |  Análisis de algoritmos
 |  Introducción a matemáticas discretas
 |  (Comp. 420)
author:
 -  José Joaquín Zubieta Rico
institute:
 -  $^1$Universidad de Guanajuato
logo:
 -  img/escudo.jpg
theme:
 -  metropolis
output:
 -  Class_5.pdf
abstract:
 -  Análisis de recursión y reducción.
header-includes: |
    \usepackage{tikz}
    \usetikzlibrary{shapes,arrows}
---

#

Reducción

:   Reducir un problema $X$ a otro problema $Y$ significa escribir un algoritmo
    para $X$ que use un algoritmo $Y$ como caja negra a subrutina.

    Para probar que $X$ es correcto, supongo que $Y$ correcto.

Recursión

:   Es un tipo de reducción muy poderoso que se describe:

     -  Si una instancia dada del problema se puede resolver directamente,
        resolverla directamente.
     -  Si no, reducirla a una o más instancias _más simples_ del mismo
        problema (Hada de la recursión = Hipótesis inductiva).



No debe de haber una secuencia infinita de reducciones a instancias más simples
Eventualmente las reducciones recursivas deben llegar a un _caso base_ que se puede
resolver con otro método.

Como ejemplo podemos definir el producto de dos número enteros de forma
recursiva como
$$
    x \cdot y = \left\lbrace\begin{aligned}
        0 \quad & \text{if} x=0 \\
        \left\lfloor \frac{x}{2} \right\rfloor \cdot (y+y) \quad & \text{if } 2\ |\ x \\
        \left\lfloor \frac{x}{2} \right\rfloor \cdot (y+y) + y \quad & \text{if } 2\nmid x
    \end{aligned}\right.
$$

\newpage

Y podemos escribir su algoritmo como

```
Multiply(x,y):
    prod = 0
    if x=0:
        prod = 0
    else
        x' = $\lfloor$ x/2$\rfloor$
        y' = y+y
        prod = Multiply(x', y')
        if x if odd
            prod = prod+y
    return prod
```

## Divide and Conquer

 1. Dividir la instancia del problema en varias instancias más pequeñas
     _INDEPENDIENTES_.
 2. Delegar cada instancia más pequeña al hada de la recursión.
 3. Combinar las soluciones para resolver la instancia general.

## Árboles recursivos

Considerar un algoritmo de tipo _D&C_ que toma $O(f(n))$ tiempo en su trabajo
no recursivo y hace $r$ llamadas recursivas, cada una a una instancia de
tamaño $\frac{n}{c}$.
$$
    T(n) = rT\left(\frac{n}{c}\right) + f(n)
$$

```{.dot caption="Árbol recursivo." scale=0.5}
digraph recursiveTree {
    L1 [label="f(n)"]

    L21 [label="f(n)"]
    L22 [label="f(n)"]
    L23 [label="f(n)"]

    L311 [label="..."]
    L312 [label="..."]
    L313 [label="..."]

    L321 [label="..."]
    L322 [label="..."]
    L323 [label="..."]

    L331 [label="..."]
    L332 [label="..."]
    L333 [label="..."]

    L1 -> L21
    L1 -> L22
    L1 -> L23

    L21 -> L311
    L21 -> L312
    L21 -> L313

    L22 -> L321
    L22 -> L322
    L22 -> L323

    L23 -> L331
    L23 -> L332
    L23 -> L333
}
```

