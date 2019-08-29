---
title:
 - Clase 1
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
 - Class_1.pdf
abstract:
 - Ejemplo de algoritmo (_Gale-Shappley_) y análisis del mismo.
---

# Caso prueba: Algoritmo de _Gale-Shappley_

Algoritmo demostrado por _David Gale_ y _Lloyd Shappley_ en 1962 para resolver el
problema del [matrimonio estable](https://en.wikipedia.org/wiki/Stable_marriage_problem).

## Pseudo-algoritmo

El pseudo-algoritmo correspondiente al algoritmo de _Gale-Shappley_ es

```
Initially all $m \in M$ and "m \in M" are free
While there is a man $m$ who is free and hasn't proposed to every woman
    Choose such a man $m$
    Let $w$ be the highest-ranked woman in $m$'s preference list
        to whom $m$ has not yet proposed
    If $w$ is free then
        (m,w) become engaged
    Else $w$ is currently engaged to $m'$
        If $w$ prefers $m'$ to $m$ then
            $m$ remains free
        Else $w$ prefers
```

## Análisis

---

*Nota*

El análisis aquí encontrado puede ser encontrado en la página $7$ del libro de _Algorithm Analysis_ de **Kleinberg**.

---

El algoritmo de _**G-S**_ se puede realizar de la siguiente forma

### Definiciones

$$
\begin{aligned}
    M &= \langle m_1,...m_n \rangle \qquad\text{conjunto hombres} \\
    W &= \langle w_1,...w_n \rangle \qquad\text{conjunto mujeres} \\
    M \times W & \qquad\text{conjunto de pares ordenados $(m,w)$, $m \in M$ y $w \in W$}
\end{aligned}
$$

### Condiciones

 - Cada elemento sólo una vez.
 - Emparejamiento sin inestabilidades

### Observaciones

 1. $w$ se queda comprometida desde su primera propuesta. Sus prospectos sólo pueden
    mejorar.
 2. La secuencia de $w$'s a quien $m$ se propone solo empeora.
 3. El algoritmo de _G-S_ termina después de a lo más $n^2$ iteraciones de ciclo «while».
    - **Medida de progreso**: manera precisa de decir que cada iteración del algoritmo
        lo acerca a su terminación.
    - **Cada iteración**: un hombre rechazado hace propuesta a su siguiente mujer en la lista.
        $P(T)$ conjunto de pares $(m,w)$ tal que $m$ se haga propuesto a $w$ al final de una
        iteración $t$, vemos que para todo $t$, el tamaño de $P(t)+1$ es estrictamente mayor
      que el tamaño de $P(t)$.
 4. Si $m$ está libre en un punto de la ejecución del algoritmo, entonces significa que hay una
    mujer a quien no le ha propuesto matrimonio.
 5. El conjunto $S$ a la terminación es un _emparejamiento perfecto_.
    - $\mathbf{S}$: conjunto de pares ordenados, todos de $M \times W$
        - cada miembro de $M$ y cada miembro de $W$ aparezca al menos una vez en $S$.
    - **Emparejamiento perfecto**: cada miembro de $M$ y cada miembro de $W$ aparece exactamente
        en un par de $S'$.
