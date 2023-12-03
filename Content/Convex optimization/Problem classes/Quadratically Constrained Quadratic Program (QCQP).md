$$
\begin{equation}
\begin{aligned}
& \text{minimize}
& & \frac{1}{2}x^T P_0 x + q_0^T x + r_0 \\
& \text{subject to}
& & \frac{1}{2}x^T P_i x + q_i^T x + r_i \leq 0, \quad i = 1, \ldots, m, \\
& & & Ax = b \\
& \text{convex if }
& & P_i \in S^n_+ \\
& & & P_1, \ldots, P_m \in S_{++}^n \text{ a feasible region is intersection of } m \text{ ellipsoid and an affine set}
\end{aligned}
\end{equation}
$$