---
title:
 - Clase 4
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
 - Class_4.pdf
abstract:
 - Continuación en ecuaciones en diferencias.
---

# Ecuaciones en diferencias

Las ecuaciones en diferencias tiene la forma general
$$
    a_{n+k} + b_1 a_{n+k-1} + \cdots + b_k a_{n} = f_n
$$

## Caso homogéneo

En el caso homogéneo se cumple que
$$
    f_n = 0
$$

### Estrategia de solución

La estrategia general para resolver las ecuaciones en diferencia homogénea
es la siguiente

 * busca k soluciones particulares, es decir
   $a_n = r^k,\ n^jr^n,\ \left\lbrace\begin{aligned}&{|r|}^n \cos(n\theta)\\
                                                &{|r|}^n \sin(n\theta)
                                 \end{aligned}\right.$
 * solución general es una combinación lineal

#### Ejemplo

Tomando el caso
$$
\begin{aligned}
    x_{n+2} = x_{n+1} - x_n
\end{aligned}
$$

## Caso no homogéneo

**Proposición**

:   La solución de una ecuación lineal no homogénea es siempre la suma de una
    solución de la homogénea asociada y una solución particular.

### Estrategia de solución

Definimos un operador $T : T(a_{n+1}) = a_{n+1}$. Definido el operador $T$,
podemos realizar las siguientes observaciones
$$
\begin{aligned}
    T \circ T \circ T \cdots T & := T^k \\
    T^k(a_n) & = a_{n+k} \\
    T^0(a_n) & = a_n \quad \Rightarrow T^0 = I
\end{aligned}
$$
Por lo tanto se tiene que las ecuaciones lineales en diferencias se convierten
en polinomios en $T$ (un poco de abuso de notación).

#### Ejemplo de uso de notación

Se tiene la siguiente ecuación no homogénea
$$
\begin{aligned}
    D        & = T^2 + 3T \\
             & \Rightarrow \\
    D(a_n)   & = T^2(a_n)+3T(a_n) \\
             & = a_{n+2} + 2a_{n+1} \\
             & \Rightarrow \\
    D        & = T + 2 \\
             & = T +2 T^0
\end{aligned}
$$

Podemos escribir $(T^k + b_1T^{k-1} + \cdots + b_kT^0)[a_n] = f_n$.

_Idea divina_
$$
    D_0[D(a_n)]  = d_0[f_n],\text{ se busca }D_0 : D_0(f_n) = 0
$$ {#eq:eq1}
$$
    (D_0D)[a_n]  = 0
$$ {#eq:eq2}

De lo anterior tenemos que la estrategia es buscar la solución de la ecuación 1
@eq:eq1 y sustituir la solución en la ecuación general @eq:eq2.

#### Ejemplo de solución

Se tiene la siguiente ecuación no homogénea
$$
    x_{n+1} = x_n + 2n
$$

