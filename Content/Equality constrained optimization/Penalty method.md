- Replace constrained problems by **sequence** of unconstrained ones
- For each constraint $\rightarrow$ add a **penalty** term to the objective function
$$
\begin{equation} \begin{aligned} & \text{minimize} & & f(x) \\ & \text{subject to} & & h_i(x) = 0, \quad i = 1, \ldots, p \end{aligned} \end{equation}
$$
is replaced by a sequence of $F(x, \mu)$ with penalty parameters $\mu_1, < \mu_2 < \cdots$

$$
\begin{equation}
\text{minimize} \quad F(x, \mu) = f(x) + \mu \sum_{i=1}^{p} P(h_i(x))
\end{equation}
$$

A penatly function $P(y)$ penalize constraint violation (typically $P(y) > 0$ for $y \neq 0$ and $P(0) = 0$). Here is some examples:
- non-smooth $l_1, P(y) = |0|$
- some quadratic $P(y) = y^2$

# Quadratic penalty method
$$
\begin{equation} \begin{aligned} & \text{minimize} & & f(x) \\ & \text{subject to} & & h_i(x) = 0, \quad i = 1, \ldots, p \end{aligned} \end{equation}
$$
is replaced by a sequence of $Q(x, \mu)$ with penalty parameters $\mu_1, < \mu_2 < \cdots$
$$
\begin{equation}
\text{minimize} \quad Q(x, \mu) = f(x) + \frac{1}{2} \mu \sum_{i=1}^{p} h_i^2(x)
\end{equation}
$$
So the penalty method is $P = \frac{1}{2}y^2$
- Smooth if $f(x)$ and $h_i(x)$ are smooth (e.g. use Newton Method) 
- Constrained problem and $Q(x, \mu)$ are equivalent if $\mu \rightarrow \infty$
- Solve sequence of problems with increasing $\mu_1 < \mu_2 < \cdots$ (because for small $\mu$ it's easier to solve but there's a large constraint violation)
<iframe src="https://slides.cgg.unibe.ch/aopt23/10-EqualityConstrainedOptimization-II-deck.html#/example/0" allow="fullscreen" allowfullscreen="" style="height:100%;width:100%; aspect-ratio: 16 / 9; "></iframe>
<iframe src="https://slides.cgg.unibe.ch/aopt23/10-EqualityConstrainedOptimization-II-deck.html#/example-different-mu" allow="fullscreen" allowfullscreen="" style="height:100%;width:100%; aspect-ratio: 16 / 9; "></iframe>
<iframe src="https://slides.cgg.unibe.ch/aopt23/10-EqualityConstrainedOptimization-II-deck.html#/example-optimization-1" allow="fullscreen" allowfullscreen="" style="height:100%;width:100%; aspect-ratio: 16 / 9; "></iframe>

# Non-smooth exact penalty method
$$
\begin{equation} \begin{aligned} & \text{minimize} & & f(x) \\ & \text{subject to} & & h_i(x) = 0, \quad i = 1, \ldots, p \end{aligned} \end{equation}
$$
is replaced by a sequence of $Q(x, \mu)$ with penalty parameters $\mu_1, < \mu_2 < \cdots$
$$
\begin{equation}
\text{minimize} \quad \phi_1(x, \mu) = f(x) + \mu \sum_{i=1}^{p} |h_i(x)|
\end{equation}
$$
So the penalty method is $P = |y|$
- Isn't differentiable (non-smooth) so it complicates the optimization
- Exact solution method (do not requires that $\mu \rightarrow \infty$ for an exact solution)
<iframe src="https://slides.cgg.unibe.ch/aopt23/10-EqualityConstrainedOptimization-II-deck.html#/nonsmooth-exact-penalty-functions/7" allow="fullscreen" allowfullscreen="" style="height:100%;width:100%; aspect-ratio: 16 / 9; "></iframe>
# Augmented Lagrangian Method
The original Lagragian formula is
$$\mathcal{L}(x, \nu, \mu) = f(x) + \sum_{i=1}^{p} \nu_i h_i(x)$$
We can incorporate a new term corresponding to the penalty method ($\mu\frac{1}{2} \sum_{i=1}^{p} h_i^2(x)$) that we call **Augmentation**
$$\mathcal{L}_A(x, \nu, \mu) = f(x) + \sum_{i=1}^{p} \nu_i h_i(x) + \mu\frac{1}{2} \sum_{i=1}^{p} h_i^2(x)$$
Constraint violation $h_i(x_k)$ (finite $\mu_k$ sufficient if $\nu_k \rightarrow \nu^*$)
## Properties
- Resolve systematic bias of quadratic penalty method
- Constraint violation $h_i(x_k) \approx \frac{\nu_i^*}{\mu_k}$ (requires $\mu \rightarrow \infty$)
- Primal-dual method
## Simultaneously Iterate on
- $x_k \in \mathbb{R}^n$, $\nu_k \in \mathbb{R}^p$ and $\mu_k \in \mathbb{R}$
- Update primal variables $x_{k+1}$ by minimizing $\mathcal{L}_A(x, \nu_k, \mu_k)$ in $x$
- Update dual variables $\nu_{i}^{k+1} = \nu_{i}^k + \mu_k h_i(x_k)$
- Increase $\mu_{k+1}$ only if infeasibility measure does not decrease sufficiently
