Let us consider the following optimization problem
$$
\begin{aligned}
& \underset{(x,y) \in \mathbb{R}^2}{\text{min}}
& & x + y, \\
& \text{s.t.}
& & x^2 + y^2 = 2
\end{aligned}
$$
1. Consider a **smooth differentiable equality constraint** $h(X) = 0, X \in \mathbb{R}^n$. The function $|h(X)|$ is however **not** differentiable. Yet, it is possible to compute a **directional derivative**:
$$
D_P (|h(X)|) = \lim_{\epsilon \to 0^+} \frac{|h(X + \epsilon P)| - |h(X)|}{\epsilon}
$$
Prove that
$$
D_P (|h(X)|) = 
\begin{cases} 
P^T \cdot \nabla h(X), & h(X) > 0 \\
-P^T \cdot \nabla h(X), & h(X) < 0 \\
|P^T \cdot \nabla h(X)|, & h(X) = 0 
\end{cases}
$$
hint: $h(X)$ is differentiable, and $\epsilon$ is really small and positive.

2. Sketch the optimization problem, and the **linearized feasible cone** at $(x,y) = (1,1)$.

3. Here is the $l_1$ penalty function
$$
\phi(x,y) = x + y + \mu |x^2 + y^2 - 2|
$$
Which condition does $\mu$ must satisfy such that minimizing this penalty function exactly correspond to the minimization of the initial problem?

4. Express the first order necessary condition(s) for the minimum $x^*$ of the $l_1$ penalty function.

# Solution 1)
#absolute-value-derivation

Considering the Taylor expansion

$f(x) = f(a)+{\frac {f'(a)}{1!}}(x-a)+{\frac {f''(a)}{2!}}(x-a)^{2}+{\frac {f'''(a)}{3!}}(x-a)^{3}+\cdots$

We can use the 1st order Taylor expansion because we know that $h(X)$ is differentiable to estimate $h(x + \epsilon P)$
$$
\begin{align}
h(x + \epsilon P) & \approx h(X) + \nabla h(X)(X + \epsilon P - X) \\
& = h(X) + \nabla h(X)(\epsilon P) \\
& = h(X) + \epsilon P^T \nabla h(X)
\end{align}
$$

## $h(x) > 0$
$$
\begin{align}
D_P (|h(X)|) & = \lim_{\epsilon \to 0^+} \frac{|h(X + \epsilon P)| - |h(X)|}{\epsilon} \\
& = \lim_{\epsilon \to 0^+} \frac{h(X + \epsilon P) - h(X)}{\epsilon} \\
& = \lim_{\epsilon \to 0^+} \frac{h(X) + \epsilon P^T \nabla h(X) - h(X)}{\epsilon} \\
& = \lim_{\epsilon \to 0^+} \frac{\epsilon P^T \nabla h(X)}{\epsilon} \\
& = P^T \nabla h(X)
\end{align}
$$

## $h(x) < 0$
$$
\begin{align}
D_P (|h(X)|) & = \lim_{\epsilon \to 0^+} \frac{(-h(X + \epsilon P)) - (-h(X))}{\epsilon} \\
& = \lim_{\epsilon \to 0^+} \frac{-h(X + \epsilon P) + h(X)}{\epsilon} \\
& = \lim_{\epsilon \to 0^+} \frac{-h(X) - \epsilon P^T \nabla h(X) + h(X)}{\epsilon} \\
& = \lim_{\epsilon \to 0^+} \frac{-\epsilon P^T \nabla h(X)}{\epsilon} \\
& = -P^T \nabla h(X)
\end{align}
$$
## $h(x) = 0$
$$
\begin{align}
D_P (|h(X)|) & = \lim_{\epsilon \to 0^+} \frac{|h(X + \epsilon P)| - |h(X)|}{\epsilon} \\
& = \lim_{\epsilon \to 0^+} \frac{|h(X + \epsilon P)|}{\epsilon} \\
& = \lim_{\epsilon \to 0^+} \frac{|h(X) + \epsilon P^T \nabla h(X)|}{\epsilon} \\
& = \lim_{\epsilon \to 0^+} \frac{|\epsilon P^T \nabla h(X)|}{\epsilon} \\
& = \lim_{\epsilon \to 0^+} \frac{\epsilon|P^T \nabla h(X)|}{\epsilon} \\
& = |P^T \nabla h(X)|
\end{align}
$$
# Solution 2)
Sketch the optimization problem, and the **linearized feasible cone** at $(x,y) = (1,1)$.
$$
\begin{aligned}
& \underset{(x,y) \in \mathbb{R}^2}{\text{min}}
& & x + y, \\
& \text{s.t.}
& & x^2 + y^2 = 2
\end{aligned}
$$
<iframe src="https://www.geogebra.org/calculator/qfygzdfs?embed" width="800" height="600" allowfullscreen style="border: 1px solid #e4e4e4;border-radius: 4px;" frameborder="0"></iframe>

# Solution 3)
Here is the $l_1$ penalty function
$$
\phi(x,y) = x + y + \mu |x^2 + y^2 - 2|
$$
Which condition does $\mu$ must satisfy such that minimizing this penalty function exactly correspond to the minimization of the initial problem?

![[Example 17.3.png]]
![[theoreme17.3.png]]

 
Let's first determine the Lagrangian of the original problem
$$
\begin{aligned}
& \underset{(x,y) \in \mathbb{R}^2}{\text{min}}
& & x + y, \\
& \text{s.t.}
& & x^2 + y^2 = 2
\end{aligned}
$$
The Lagrangian is:
$$
\begin{align}
\mathcal{L}(x, \nu, \mu) & = f(x) + \sum_{i=1}^{p} \nu_i h_i(x) \\
& = x + y + \nu(x^2 + y^2 - 2)
\end{align}
$$
Vanishing gradient to find $\nu^*$
$$
\begin{align}
\nabla\mathcal{L}(x, \nu, \mu)
& =
\begin{pmatrix}
	1 + y^* + 2x^*\nu^* + {y^*}^2 \\
	1 + x^* + 2y^*\nu^* + {x^*}^2
\end{pmatrix} \\
&=
\begin{pmatrix}
	1 + -1 + 2(-1)\nu^* + (-1)^2 \\
	1 + -1 + 2(-1)\nu^* + (-1)^2
\end{pmatrix}
=
\begin{pmatrix}
	-2\nu^* + 1 \\
	-2\nu^* + 1
\end{pmatrix}
=
\begin{pmatrix}
	0 \\
	0
\end{pmatrix}
\end{align}
$$
So 
$$
\begin {align}
-2\nu^* +1 &= 0 \\
\nu^* &= \frac{-1}{-2} = \frac{1}{2}
\end{align}
$$
> The magnitude of $\nu$ gives us an idea of how much the objective function value would change with a unit violation of the constraint.

From [[Merit functions]] we know that $\mu < \mu^* = \text{max}_i(|\nu^*|)$ and here there is only one $\nu^*$ so $\mu <  \mu^* = \text{max}_i(|\nu^*|) = |\nu^*|$


$$
\begin{align}
\mu < |\nu^*| = \frac{1}{2}
\end{align}
$$
## Solution 4)
Using #absolute-value-derivation
$$
\phi(x,y) = x + y + \mu |x^2 + y^2 - 2|
$$
$$
\nabla \phi(x, y) =
\begin{pmatrix}
	1 + 2\mu x \frac{x^2 + y^2 - 2}{\left|x^2 + y^2 - 2\right|} \\
	1 + 2\mu y \frac{x^2 + y^2 - 2}{\left|x^2 + y^2 - 2\right|}
\end{pmatrix}
$$
