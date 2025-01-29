# Higher dimensional problem

## Problem statement

$$
-\nabla\cdot\left({\bf K}\nabla u\right)+\alpha u=f\text{ in }\Omega
$$

$$
u=u_{g}\text{ on }\Gamma_{g}
$$

$$
{\bf K}\nabla u\cdot{\bf n}=h\text{ on }\Gamma_{h}
$$

## Variation form

$$
\begin{aligned}\int_{\Omega_{e}}\delta u\left(-\nabla\cdot\left({\bf K}\nabla u\right)+\alpha u-f\right)d\Omega\\ =\int_{\Omega_{e}}\nabla\delta u\cdot{\bf K}\nabla u+\int_{\Omega_{e}}\alpha\delta uu-\int_{\partial\Omega_{e}}\delta u{\bf K}\nabla u\cdot{\bf n}-\int_{\Omega_{e}}\delta ufd\Omega \end{aligned}
$$

Summing up for all elements

$$
\sum_{e}\int_{\Omega_{e}}\nabla\delta u\cdot{\bf K}\nabla u+\sum_{e}\int_{\Omega_{e}}\alpha\delta uu-\sum_{e}\int_{\partial\Omega_{e}}\delta u{\bf K}\nabla u\cdot{\bf n}-\sum_{e}\int_{\Omega_{e}}\delta ufd\Omega=0
$$

$$
\begin{aligned}\sum_{e}\int_{\partial\Omega_{e}}\delta u{\bf K}\nabla u\cdot{\bf n} & =\sum_{\Gamma_{e}\in\mathcal{E}_{int}}\int_{\Gamma_{e}}\left[\delta u\right]\left\{ {\bf K}\nabla u\cdot{\bf n}\right\} +\sum_{\Gamma_{e}\in\mathcal{E}_{int}}\int_{\Gamma_{e}}\left\{ \delta u\right\} \left[{\bf K}\nabla u\cdot{\bf n}\right]\\ & +\sum_{\Gamma_{e}\in\mathcal{E}_{g}}\int_{\Gamma_{e}}\delta u{\bf K}\nabla u\cdot{\bf n}+\int_{\Gamma_{h}}\delta uh \end{aligned}
$$

$$
\begin{aligned}\sum_{e}\int_{\Omega_{e}}\left(\nabla\delta u\cdot{\bf K}\nabla u+\alpha\delta uu\right)\\ -\sum_{\Gamma_{e}\in\mathcal{E}_{int}}\int_{\Gamma_{e}}\left[\delta u\right]\left\{ {\bf K}\nabla u\cdot{\bf n}\right\} \\ -\sum_{\Gamma_{e}\in\mathcal{E}_{int}}\int_{\Gamma_{e}}\left\{ \delta u\right\} \left[{\bf K}\nabla u\cdot{\bf n}\right]\\ -\sum_{\Gamma_{e}\in\mathcal{E}_{g}}\int_{\Gamma_{e}}\delta u{\bf K}\nabla u\cdot{\bf n}-\int_{\Gamma_{h}}\delta uh\\ -\sum_{e}\int_{\Omega_{e}}\delta ufd\Omega=0 \end{aligned}
$$

Noting that $\left[{\bf K}\nabla u\cdot{\bf n}\right]=0$, and adding penalty term for weak boundary condition.

$$
\begin{aligned}\sum_{e}\int_{\Omega_{e}}\left(\nabla\delta u\cdot{\bf K}\nabla u+\alpha\delta uu\right)\\ -\sum_{\Gamma_{e}\in\mathcal{E}_{int}}\int_{\Gamma_{e}}\left[\delta u\right]\left\{ {\bf K}\nabla u\cdot{\bf n}\right\} \\ -\sum_{\Gamma_{e}\in\mathcal{E}_{g}}\int_{\Gamma_{e}}\delta u{\bf K}\nabla u\cdot{\bf n}\\ +\varepsilon\sum_{\Gamma_{e}\in\mathcal{E}_{int}}\int_{\Gamma_{e}}\left[u\right]\left\{ {\bf K}\nabla\delta u\cdot{\bf n}\right\} \\ +\varepsilon\sum_{\Gamma_{e}\in\mathcal{E}_{g}}\int_{\Gamma_{e}}\left(u-u_{g}\right){\bf K}\nabla\delta u\cdot{\bf n}\\ -\int_{\Gamma_{h}}\delta uh-\sum_{e}\int_{\Omega_{e}}\delta ufd\Omega=0 \end{aligned}
$$

After adding jump penalty

$$
\begin{aligned}\sum_{e}\int_{\Omega_{e}}\left(\nabla\delta u\cdot{\bf K}\nabla u+\alpha\delta uu\right)\\ -\sum_{\Gamma_{e}\in\mathcal{E}_{int}\cup\mathcal{E}_{g}}\int_{\Gamma_{e}}\left[\delta u\right]\left\{ {\bf K}\nabla u\cdot{\bf n}\right\} \\ +\varepsilon\sum_{\Gamma_{e}\in\mathcal{E}_{int}\cup\mathcal{E}_{g}}\int_{\Gamma_{e}}\left[u\right]\left\{ {\bf K}\nabla\delta u\cdot{\bf n}\right\} \\ +J_{0}^{\sigma_{0},\beta_{0}}\left(\delta u,u\right)+J_{1}^{\sigma_{1},\beta_{1}}\left(\delta u,u\right)\\ -\varepsilon\sum_{\Gamma_{e}\in\mathcal{E}_{g}}\int_{\Gamma_{e}}{\bf K}\nabla\delta u\cdot{\bf n}u_{g}\\ -\sum_{\Gamma_{e}\in\mathcal{E}_{g}}\frac{\sigma_{0}}{\vert e\vert^{\beta_{0}}}\int_{\Gamma_{e}}\delta uu_{g}\\ -\int_{\Gamma_{h}}\delta uh-\sum_{e}\int_{\Omega_{e}}\delta ufd\Omega=0 \end{aligned}
$$

## Bilinear form

$$
\begin{aligned}a_{\varepsilon}(\delta u,u):= & \sum_{e}\int_{\Omega_{e}}\left(\nabla\delta u\cdot{\bf K}\nabla u+\alpha\delta uu\right)\\ & -\sum_{\Gamma_{e}\in\mathcal{E}_{int}\cup\mathcal{E}_{g}}\int_{\Gamma_{e}}\left[\delta u\right]\left\{ {\bf K}\nabla u\cdot{\bf n}\right\} \\ & +\varepsilon\sum_{\Gamma_{e}\in\mathcal{E}_{int}\cup\mathcal{E}_{g}}\int_{\Gamma_{e}}\left[u\right]\left\{ {\bf K}\nabla\delta u\cdot{\bf n}\right\} \\ & +J_{0}^{\sigma_{0},\beta_{0}}\left(\delta u,u\right)+J_{1}^{\sigma_{1},\beta_{1}}\left(\delta u,u\right) \end{aligned}
$$

$$
\begin{aligned}L(\delta u)= & \sum_{e}\int_{\Omega_{e}}\delta ufd\Omega+\int_{\Gamma_{h}}\delta uh\\ & +\varepsilon\sum_{\Gamma_{e}\in\mathcal{E}_{g}}\int_{\Gamma_{e}}{\bf K}\nabla\delta u\cdot{\bf n}u_{g}\\ & +\sum_{\Gamma_{e}\in\mathcal{E}_{g}}\frac{\sigma_{0}}{\vert e\vert^{\beta_{0}}}\int_{\Gamma_{e}}\delta uu_{g} \end{aligned}
$$

## Mixed DGFEM

### Problem statement

$$
\mathbf{v}=\nabla{p}, \text{ in } \Omega
$$

$$
-\nabla \cdot \mathbf{v}=f, \text{ in } \Omega
$$

$$
p=p_{g}, \text{ on } \Gamma_{g}
$$

$$
\mathbf{v} \cdot \mathbf{n} = u_{gn}, \text{ on } \Gamma_{h}
$$
