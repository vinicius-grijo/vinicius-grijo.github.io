+++
title = 'How do RNNs Generalize AR-Models?'
date = 2024-06-16T11:47:21-03:00
draft = false
tags = ["Auto Regressive Model", "AR Model", "RNN", "Recurrent Neural Network"]
categories = ["AI", "Machine Learning"]
+++

# What is an AR Model?
An Auto Regressive Model, or simply an AR-Model, is a statistical model for time series.

The main assumption is that the value in time $t+1$ is a linear combination of the $p$ previous values.

The $p$ parameter is called **the order** of the model. Hence an **auto regressive model of order $p$** can be concisily referred to as an $AR(p)$ model.

Given $\\{x_t\\}_{t=0}^{n}$ data points the main assumption of an AR($p$) model is expresed through the following equation:

$$
x_{t+1} = \alpha_0x_t + \cdots \alpha_{p-1}x_{t-p-1}.
$$

In order to callibrate this model one needs to find the coefficients $alpha_i$, $i=0,\cdots,p-1$ that minimize a given loss function.

# How Can It Be Written Using Matrices?
This section is aimed at expressing the same ideas using matrices and vectors.
$$
X_t := \big( x_{t+p-1}, x_{t+p-2}, \cdots, x_{t+1}, x_t \big)^T,
$$

$$
W_{xy} := (\alpha_0, \alpha_1, \cdots, \alpha_{p-2}, \alpha_{p-1}),
$$

$$
Y_t := \( x_{t+p} \).
$$
Hence, the same $AR(p)$ model is given by
$$
Y_t = W_{xy}X_t.
$$


# What if a Hidden Unit is Added?
Having in a mind a classic neural network architecture, one could add a hidden unit.

Now instead of having a weight that takes $X_t$ straight up to $Y_t$, one decomposes it into $W_{xh}$ and $W_{hy}$ in such a way that $W_{xy} = W_{hy} W_{xh} $.

The equation then becomes
$$
Y_t = W_{xy}X_t = W_{hy} W_{xh} X_t = W_{hy} h_t.
$$

Now one can add **recurrence** between the the hidden units. That is, one can add a term $W_{hh}$ that integrates the value of $h_{t-1}$ into $h_t$:
$$
Y_t = W_{hy} h_t = W_{hy} \big( W_{xh} X_t + W_{hh} h_{t-1} \big).
$$

# What if Activation Functions and Biases are Added?
Finally, one can add activation functions and biases.
$$
\begin{split}
Y_t &= \sigma_y \big( W_{hy} h_t + b_y \big) \\\\\\
&= \sigma_y \Bigg( W_{hy}  \sigma_h \Big(  W_{xh} X_t + W_{hh} h_{t-1} + b_h \Big) + b_y \Bigg).
\end{split}
$$

Now note that
$$
\begin{split}
Y_t &= \sigma_y\big( W_{hy} h_t + b_y \big), \\\\\\
h_t &= \sigma_h \Big( W_{xh} X_t + W_{hh} h_{t-1} + b_h \Big),
\end{split}
$$
is precisily the architecture of an **Elman Network**, introduced by [Jeffrey L. Elman in $1990$]( https://onlinelibrary.wiley.com/doi/10.1207/s15516709cog1402_1 ).

```math
```