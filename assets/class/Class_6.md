---
title:
 -  Clase 6
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
 -  Análisis de recursión y reducción (continuación).
header-includes: |
    \usepackage{tikz}
    \usetikzlibrary{shapes,arrows}
---

#

$$
\begin{aligned}
    T(n) & = 2T(n/2)+O(n) \to O(n\log(n)) \\
    T(n) & = T(\lceil \frac{n}{2} \rceil ) + T(\lfloor \frac{n}{2} \rfloor ) + O(n)
\end{aligned}
$$

Transformación de dominio.

Como estamos estimando una cota superior, podemos sobre-estimar $T(n)$
$$
    T(n) \leq 2T(\lceil \frac{n}{2} \rceil) + n \leq 2T( \frac{n}{2} + 1) + n
$$

Definimos $S(n) = T(n + \alpha)$, donde $\alpha$ es una constante tal que
$S(n)$ satisface
$$
    S(n) \leq 2S( \frac{n}{2} ) + O(n)
$$
Para encontrar $\alpha$ escribimos $S$ en términos de de $T$
$$
\begin{aligned}
    S(n)    & = T(n+\alpha) \quad \text{definición de $S(n)$} \\
            & \leq 2T(\frac{n}{2}+\frac{\alpha}{2}+1) + n + \alpha \quad \text{recurrencia para $T$} \\
            & = 2S(\frac{n}{2}-\frac{\alpha}{2}+1) + n + \alpha \quad \text{de la def. de $S$} \\
    \alpha  & = 2 \to s(n) \leq 2S(\frac{n}{2})+n+2 \to O(n\log(n)) \\
    T(n)    & = S(n-2)=O((n-2)\log(n-2)) = O(n\log(n))
\end{aligned}
$$
