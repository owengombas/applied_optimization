$$
\begin{equation}
\begin{aligned}
& \text{minimize}
& & f^T x \\
& \text{subject to}
& & \left\| A_i x + b_i \right\|_2 \leq c_i^T x + d_i, \quad i = 1, \ldots, m, \\
& & & A_0 x = b_0 \\
& \text{with} & & A_i \in \mathbb{R}^{n_i \times n}
\end{aligned}
\end{equation}
$$

- For $n_i = 0$ it reduces the program to an [[Linear Program (LP)]]
- For $c_i = 0$ it reduces the program to a [[Quadratically Constrained Quadratic Program (QCQP)]]
- Very general $\text{SOCP} \supset \text{QCQP} \supset \text{QP} \supset \text{LP}$
