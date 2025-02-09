+++
title = 'What is a Fractional Integral?'
date = 2023-05-28T09:30:05-07:00
draft = false
tags = ["fractional integral", "analysis", "theory"]
categories = ["analysis"]
+++

# Hermann Weyl
Hermann Klaus Hugo Weyl was a german mathematician born in 1885. His doctorate was awarded at the University of Göttingen under the supervision of David Hilbert. Moreover, Weyl was an important member of the Institute for Advanced Study, in Princeton.

![Hermann Weyl](/images/what_is_a_fractional_integral/weyl.jpg)

In the paper *Bemerkungen zum Begriff des Differentialquotienten gebrochener Ordnung* Weyl introduced the concept of fractional integral. The paper's title can be unofficially and amateurly translated as *Notes on the Concept of Fractional Derivative*.

![Bemerkungen zum Begriff des Differentialquotienten gebrochener Ordnung](/images/what_is_a_fractional_integral/bermerkungen_pg01.jpg)

# Going Deeper into Mathematics

## Defining the Notation
Let $f_0:[0,+\infty) \rightarrow \mathbb{R}$  be a continuous function. It is well known that one can define its primitive as

$$
f_1(x_1) := \int_0^{x_1} f_0(x_0) \\: dx_0.
$$

## The case $ n=2 $
Now one can proceed defining the primitive of its primitive as
$$
\begin{align}
    f_2(x_2)
    &:= \int_0^{x_2} f_1(x_1) dx_1 \\\\\\
    &= \int_0^{x_2} \int_0^{x_1} f_0(x_0) \\: dx_0 \\: dx_1.
\end{align}
$$

**Property**. Now note that using integration by parts it holds that
$$
\begin{split}
    \int_0^{x_2} (x_2 - x_1) f_0(x_1)  dx_1
    &= \int_0^{x_2} f_1(x_1) dx_1 \\
    &= f_2(x_2).
\end{split}
$$

The importance of this equality lies in the fact that it gives a representation of the second order primitive $f_2$ in terms of an integral of the function $f_0$ itself times a polynomial, namely
$$
    \int_0^{x_2} (x_2 - x_1) f_0(x_1)  dx_1 = f_2(x_2).
$$

## The case {{< math >}}$ n \in \mathbb{N} ${{< /math >}}
Now one wants to define the $n$-th order primitive and obtain a representation of it in the form of an integral of the underlying function $f_0$ and a certain polynomial.

First, one needs to formally define the $n$-th order primitive of $f_0$.
$$
f_{n+1}(x_{n+1}) := \int_0^{x_{n+1}} f_n(x_n) dx_n = \int_0^{x_{n+1}} \cdots \int_0^{x_1} f_0(x_0) \\: dx_0 \cdots dx_n.
$$

Now the representation is proven using integration by parts.

**Property**. The following equalities hold.
$$
\begin{align}
    \int_0^{x_{n+1}} (x_{n+1} - x_n)^n f_0(x_n)  dx_n
    &= n\int_0^{x_{n+1}} (x_{n+1} - x_n )^{n-1} f_1(x_n) dx_n \\\\\\
    &= n(n-1)\int_0^{x_{n+1}} (x_{n+1} - x_n )^{n-2} f_2(x_n) dx_n \\\\\\
    &= (\cdots) \\\\\\
    &= n!\int_0^{x_{n+1}} f_n(x_n) dx_n \\\\\\
    &= n! f_{n+1}(x_{n+1}).
\end{align}
$$

Now the main equation is stated separately due to its importance.

## The Main Equation
Finally, one has
$$
    f_{n+1}(x_{n+1}) = \frac{1}{n!} \int_0^{x_{n+1}} (x_{n+1} - x_n)^n f_0(x_n) dx_n.
$$

This is the equation used to generalize the concept of a $n$-th order primitive, where $n$ is an element of $\mathbb{N}$, to an $\alpha$-th order primitive, where $\alpha$ is an element of the non-negative real numbers.

## The case $ \alpha \in \mathbb{R_+} $
In order to define the fractional order primitive, one needs to recall a basic property of the $\Gamma$ function.

**Property**. If $n$ is a positive integer, then $ \Gamma(n+1) = n!$.

Now let $\alpha$ be a positive real number.The $\alpha$-th order integral of $f_0$ can be defined as
$$
\begin{split}
    f_{\alpha}(x) := \frac{1}{\Gamma(\alpha)} \int_0^{x} (x - s)^{\alpha-1} f_0(s) ds.
\end{split}
$$

**Property**. Of course when $\alpha \in \mathbb{N}$ the fractional integral coincides with the usual $n$-th order primitive.