# One-Dimensional Problem

## Model problem

Let $\Omega=[0,L]$, and $f:=f(x)\in C^{0}(\Omega)$, and $k:=k(x)\in C^{1}(\Omega)$
such that $0<k_{min}\le k(x)\le k_{max},\forall x\in\Omega$, then

$$
-\frac{d}{dx}\left(k\frac{du}{dx}\right)=f,\text{ in }\Omega
$$

$$
u(0)=u_{0},u(L)=u_{L}
$$

The classical solution of above problem belongs to $C^{2}(\Omega)$.

## DG Methods

Partition $\Omega$ into $N$ line elements $\Omega_{k}=(x_{k},x_{k+1}),k=1,2,\cdots,N$,
with $x_{1}=0$ and $x_{N+1}=L$. Let $h_{k}=x_{k+1}-x_{k}$, and
$h=\max_{1\le k\le N}{h_{k}}$. 
\begin{quote}
Note: there are $N+1$ nodes, and $N-1$ internal nodes.
\end{quote}
Let $\mathcal{P}^{k}(\Omega_{n})$ be the space of polynomials of
degree $k$ on $\Omega_{n}$ (i.e., in the interior of nth element).
Then we can define the following piecewise discontinuous polynomial
of degree $k$.

$$
S^{k}\Omega=\left\{ u:u\vert_{\Omega_{n}}\in\mathcal{P}^{k}\left(\Omega_{n}\right),\forall n=1,2,\cdots,N\right\} 
$$

Because $u$ is discontinuous at node $n$, we can define $u_{n}^{(1)}$
and $u_{n}^{(2)}$ as follows.

$$
u_{n}^{(1)}=\lim_{\varepsilon\rightarrow0}u(x_{n}+n^{(1)}\varepsilon)
$$

$$
u_{n}^{(2)}=\lim_{\varepsilon\rightarrow0}u(x_{n}+n^{(2)}\varepsilon)
$$

where, $\varepsilon>0$ and $n^{(1)}=+1$ and $n^{(2)}=-1$.

Now we can define the jump and average at the internal nodes $n=2,\cdots,N$.

$$
\left[\!\left[u_{n}\right]\!\right]=u_{n}^{(1)}n^{(1)}+u_{n}^{(2)}n^{(2)}
$$

$$
\left\{ u(x_{n})\right\} =\frac{1}{2}\left(u_{n}^{(1)}+u_{n}^{(2)}\right)
$$


## Variational form

Let $\delta u\in S^{k}(\Omega)$, then for $n=1,\cdots,N$:

$$
\begin{aligned} & \int_{\Omega_{n}}\delta u\left(-\frac{d}{dx}\left(k\frac{du}{dx}\right)-f\right)d\Omega\\
 & =\int_{\Omega_{n}}\frac{d\delta u}{dx}k\frac{du}{dx}-\int_{\Omega_{n}}\delta ufd\Omega-\left(\delta uk\frac{du}{dx}\right)_{x_{n}^{(2)}}n^{(2)}-\left(\delta uk\frac{du}{dx}\right)_{x_{n+1}^{(1)}}n^{(1)}
\end{aligned}
$$

The above form is defined over an element $\Omega_{n},$by summing
up these terms over all the elements, i.e. $n=1,2\cdots,N$, we obtain
the following equation. 

$$
\begin{aligned}\sum_{n=1}^{N}\int_{\Omega_{n}}\frac{d\delta u}{dx}k\frac{du}{dx}-\sum_{n=2}^{N}\left[\!\left[\delta uk\frac{du}{dx}\right]\!\right]_{x_{n}}\\
-\left(\delta uk\frac{du}{dx}\right)_{x_{1}^{(2)}}n^{(2)}-\left(\delta uk\frac{du}{dx}\right)_{x_{N+1}^{(1)}}n^{(1)} & =\int_{\Omega}\delta ufd\Omega
\end{aligned}
$$

Let us extend the definition of the jump and the average to the end
points

$$
\left[\!\left[u\right]\!\right]_{x_{1}}=u_{1}^{(2)}n^{(2)}
$$

$$
\left[\!\left[u\right]\!\right]_{x_{N+1}}=u_{N+1}^{(1)}n^{(1)}
$$

$$
\left\{ u\right\} _{x_{1}}=u_{1}^{(2)}
$$

$$
\left\{ u\right\} _{x_{N+1}}=u_{N+1}^{(1)}
$$

Then we can write the above variation form by the following equation. 

$$
\sum_{n=1}^{N}\int_{\Omega_{n}}\frac{d\delta u}{dx}k\frac{du}{dx}-\sum_{n=1}^{N+1}\left[\!\left[\delta uk\frac{du}{dx}\right]\!\right]_{x_{n}}=\int_{\Omega}\delta ufd\Omega
$$

Now for each internal nodes $n=2,\cdots,N$, we have following identity

$$
\left[\!\left[ab\right]\!\right]_{n}=\left[\!\left[a\right]\!\right]_{n}\left\{ b\right\} _{n}+\left\{ a\right\} _{n}\left[\!\left[b\right]\!\right]_{n}
$$

Therefore,

$$
\left[\!\left[\delta uk\frac{du}{dx}\right]\!\right]_{n}=\left[\!\left[\delta u\right]\!\right]_{n}\left\{ k\frac{du}{dx}\right\} _{n}+\left\{ \delta u\right\} _{n}\left[\!\left[k\frac{du}{dx}\right]\!\right]_{n}
$$

Now the variation form becomes:

$$
\begin{aligned}\sum_{n=1}^{N}\int_{\Omega_{n}}\frac{d\delta u}{dx}k\frac{du}{dx}-\sum_{n=1}^{N+1}\left[\!\left[\delta u\right]\!\right]_{n}\left\{ k\frac{du}{dx}\right\} _{n}\\
-\sum_{n=1}^{N+1}\left\{ \delta u\right\} _{n}\left[\!\left[k\frac{du}{dx}\right]\!\right]_{n}=\int_{\Omega}\delta ufd\Omega
\end{aligned}
$$

From the above equation it is clear that the jump and the average
terms are responsible for coupling the adjacent elements, in other
words the information between $\Omega_{n-1}$ and $\Omega_{n}$ is
exchanged through the jump and average defined at node $x_{n}$. 

From the view point of physics, the solution should not contain any
jump in the flux at the element boundary. However, within FEM, it
is a very strong condition (due to piecewise polynomial approximation
over finite element mesh), the weak form of this condition is given
by: 

$$
\sum_{n=1}^{N+1}\left\{ \delta u\right\} _{n}\left[\!\left[k\frac{du}{dx}\right]\!\right]_{n}=0
$$

By using this relationship in the variation form we can obtain following
equation. 

$$
\sum_{n=1}^{N}\int_{\Omega_{n}}\frac{d\delta u}{dx}k\frac{du}{dx}-\sum_{n=1}^{N+1}\left[\!\left[\delta u\right]\!\right]_{n}\left\{ k\frac{du}{dx}\right\} _{n}=\int_{\Omega}\delta ufd\Omega
$$

At this point we have added to variation form a mechanism to minimize
the jump of gradient of solution at element boundary. However, the
method is neither stable nor convergent. This is because, we should
also minimize the jump in the trace of solution at the element boundary.
This can be achieved by adding penalty terms to above-mentioned variation
form. 

$$
\begin{aligned} & \sum_{n=1}^{N}\int_{\Omega_{n}}\frac{d\delta u}{dx}k\frac{du}{dx}-\sum_{n=1}^{N+1}\left[\!\left[\delta u\right]\!\right]_{n}\left\{ k\frac{du}{dx}\right\} _{n}\\
 & +\varepsilon\sum_{n=1}^{N+1}\left[\!\left[u\right]\!\right]_{n}\left\{ k\frac{d\delta u}{dx}\right\} _{n}\\
= & \int_{\Omega}\delta ufd\Omega-\varepsilon u\left(0\right)\left\{ k\frac{d\delta u}{dx}\right\} _{1}+\varepsilon u\left(L\right)\left\{ k\frac{d\delta u}{dx}\right\} _{N+1}
\end{aligned}
$$

The second and third term on the right hand side feed the boundary
condition into the formulation.

\subsubsection{Jump penalty terms}

$$
J_{0}(u,v)=\sum_{n=1}^{N+1}\frac{\sigma_{0}}{max(h_{n-1},h_{n})}\left[\!\left[u\right]\!\right]_{n}\left[\!\left[v\right]\!\right]_{n}
$$

$$
J_{1}(u,v)=\sum_{n=1}^{N+1}\frac{\sigma_{1}}{max(h_{n-1},h_{n})}\left[\!\left[\frac{du}{dx}\right]\!\right]_{n}\left[\!\left[\frac{dv}{dx}\right]\!\right]_{n}
$$

here, $\sigma_{0}$ and $\sigma_{1}$ are nonnegative numbers. It
clear that $J_{0}$ penalizes the jump in test and trial functions
at the boundary of finite element, and $J_{1}$ penalizes the jump
in the gradient of test and trial functions at the boundary of finite
element. Also note that these terms are boundary integrals in 1D setting.

:::{.callout-note title="Final variational form"}

$$
\begin{aligned} & \sum_{n=1}^{N}\int_{\Omega_{n}}\frac{d\delta u}{dx}k\frac{du}{dx}-\sum_{n=1}^{N+1}\left[\!\left[\delta u\right]\!\right]_{n}\left\{ k\frac{du}{dx}\right\} _{n}\\
 & +\varepsilon\sum_{n=1}^{N+1}\left[\!\left[u\right]\!\right]_{n}\left\{ k\frac{d\delta u}{dx}\right\} _{n}\\
 & +J_{0}\left(\delta u,u\right)+J_{1}\left(\delta u,u\right)\\
= & \int_{\Omega}\delta ufd\Omega-\varepsilon u\left(0\right)\left\{ k\frac{d\delta u}{dx}\right\} _{1}+\varepsilon u\left(L\right)\left\{ k\frac{d\delta u}{dx}\right\} _{N+1}\\
 & +\frac{\sigma_{0}}{max(h_{0},h_{1})}u\left(0\right)\delta u_{1}+\frac{\sigma_{0}}{max(h_{N},h_{N+1})}u\left(L\right)\delta u_{N+1}
\end{aligned}
$$
:::

## Bilinear forms

The bilinear form of Discontinuous Galerkin method presented above
is denoted by $a_{\varepsilon}:S^{k}(\Omega)\times S^{k}(\Omega)\rightarrow R$
, and it is given by:

$$
\begin{aligned}a_{\varepsilon}(\delta u,u) & =\sum_{n=1}^{N}\int_{\Omega_{n}}\frac{d\delta u}{dx}k\frac{du}{dx}-\sum_{n=1}^{N+1}\left[\!\left[\delta u\right]\!\right]_{n}\left\{ k\frac{du}{dx}\right\} _{n}\\
 & +\varepsilon\sum_{n=1}^{N+1}\left[\!\left[u\right]\!\right]_{n}\left\{ k\frac{d\delta u}{dx}\right\} _{n}+J_{0}\left(\delta u,u\right)+J_{1}\left(\delta u,u\right)
\end{aligned}
$$

Depending upon the choices of parameters $\varepsilon,\sigma_{0},\sigma_{1}$
we obtain several variations of DG methods.

\begin{itemize}
\item If $\varepsilon=0$, then we get Incomplete Interior Penalty Galerkin
(IIPG) method
\item If $\varepsilon=-1$, then we get Symmetric Interior Penalty Galerkin
(SIPG) method 
\item If $\varepsilon=+1$, then we get Non-symmetric Interior Penalty Galerkin
(NIPG) method
\end{itemize}

## Incomplete Interior Penalty Galerkin (IIPG)

The DG bilinear form presented in the previous chapter is given by 

$$
\begin{aligned}a_{\varepsilon}(\delta u,u) & =\sum_{n=1}^{N}\int_{\Omega_{n}}\frac{d\delta u}{dx}k\frac{du}{dx}-\sum_{n=1}^{N+1}\left[\!\left[\delta u\right]\!\right]_{n}\left\{ k\frac{du}{dx}\right\} _{n}\\
 & +\varepsilon\sum_{n=1}^{N+1}\left[\!\left[u\right]\!\right]_{n}\left\{ k\frac{d\delta u}{dx}\right\} _{n}+J_{0}\left(\delta u,u\right)+J_{1}\left(\delta u,u\right)
\end{aligned}
$$

Dawson and coworkers obtained IIPG by setting $\varepsilon=0$ in
above bilinear form \cite{dawson2004}, 

$$
\begin{aligned}a_{0}(\delta u,u) & =\sum_{n=1}^{N}\int_{\Omega_{n}}\frac{d\delta u}{dx}k\frac{du}{dx}-\sum_{n=1}^{N+1}\left[\!\left[\delta u\right]\!\right]_{n}\left\{ k\frac{du}{dx}\right\} _{n}\\
 & +J_{0}\left(\delta u,u\right)+J_{1}\left(\delta u,u\right)
\end{aligned}
$$

then,

$$
\begin{aligned}a_{0}(u,u) & =\sum_{n=1}^{N}\int_{\Omega_{n}}k\left(\frac{du}{dx}\right)^{2}-\sum_{n=1}^{N+1}\left[\!\left[u\right]\!\right]_{n}\left\{ k\frac{du}{dx}\right\} _{n}\\
 & +J_{0}\left(u,u\right)+J_{1}\left(u,u\right)
\end{aligned}
$$


## Symmetric interior penalty Galerkin method (SIPG)

The DG bilinear form presented in the previous chapter is given by 

$$
\begin{aligned}a_{\varepsilon}(\delta u,u) & =\sum_{n=1}^{N}\int_{\Omega_{n}}\frac{d\delta u}{dx}k\frac{du}{dx}-\sum_{n=1}^{N+1}\left[\!\left[\delta u\right]\!\right]_{n}\left\{ k\frac{du}{dx}\right\} _{n}\\
 & +\varepsilon\sum_{n=1}^{N+1}\left[\!\left[u\right]\!\right]_{n}\left\{ k\frac{d\delta u}{dx}\right\} _{n}+J_{0}\left(\delta u,u\right)+J_{1}\left(\delta u,u\right)
\end{aligned}
$$

We can obtain SIPG by setting $\varepsilon=-1$ and $\sigma_{1}=0$
and $\sigma_{0}$ should be greater than or equal to a large enough
constant. This method was presented by Wheeler \cite{wheeler1978}
and Arnold \cite{arnold1982}.

$$
\begin{aligned}a_{-1}(\delta u,u) & =\sum_{n=1}^{N}\int_{\Omega_{n}}\frac{d\delta u}{dx}k\frac{du}{dx}-\sum_{n=1}^{N+1}\left[\!\left[\delta u\right]\!\right]_{n}\left\{ k\frac{du}{dx}\right\} _{n}\\
 & -\sum_{n=1}^{N+1}\left[\!\left[u\right]\!\right]_{n}\left\{ k\frac{d\delta u}{dx}\right\} _{n}\\
 & +\sum_{n=1}^{N+1}\frac{\sigma_{0}}{max(h_{n-1},h_{n})}\left[\!\left[u\right]\!\right]_{n}\left[\!\left[v\right]\!\right]_{n}
\end{aligned}
$$

then,

$$
\begin{aligned}a_{-1}(u,u) & =\sum_{n=1}^{N}\int_{\Omega_{n}}k\left(\frac{du}{dx}\right)^{2}-\sum_{n=1}^{N+1}2\left[\!\left[u\right]\!\right]_{n}\left\{ k\frac{du}{dx}\right\} _{n}\\
 & +\sum_{n=1}^{N+1}\frac{\sigma_{0}}{max(h_{n-1},h_{n})}\left[\!\left[u\right]\!\right]_{n}^{2}
\end{aligned}
$$

:::{.callout-note appearance="Simple"}
If we set $\sigma_{0}=0$, then this method is not stable.
:::

\section{Non-symmetric interior penalty Galerkin method (NIPG)}

The DG bilinear form presented in the previous chapter is given by 

$$
\begin{aligned}a_{\varepsilon}(\delta u,u) & =\sum_{n=1}^{N}\int_{\Omega_{n}}\frac{d\delta u}{dx}k\frac{du}{dx}-\sum_{n=1}^{N+1}\left[\!\left[\delta u\right]\!\right]_{n}\left\{ k\frac{du}{dx}\right\} _{n}\\
 & +\varepsilon\sum_{n=1}^{N+1}\left[\!\left[u\right]\!\right]_{n}\left\{ k\frac{d\delta u}{dx}\right\} _{n}+J_{0}\left(\delta u,u\right)+J_{1}\left(\delta u,u\right)
\end{aligned}
$$

We can obtain NIPG by setting $\varepsilon=1$ and $\sigma_{1}=0$
and $\sigma_{0}=1$ . This method was presented by Riviere, Wheeler
and Girault in 1999 \cite{riviere1999}\cite{riviere1999}.

$$
\begin{aligned}a_{1}(\delta u,u) & =\sum_{n=1}^{N}\int_{\Omega_{n}}\frac{d\delta u}{dx}k\frac{du}{dx}-\sum_{n=1}^{N+1}\left[\!\left[\delta u\right]\!\right]_{n}\left\{ k\frac{du}{dx}\right\} _{n}\\
 & +\sum_{n=1}^{N+1}\left[\!\left[u\right]\!\right]_{n}\left\{ k\frac{d\delta u}{dx}\right\} _{n}\\
 & +\sum_{n=1}^{N+1}\frac{1}{max(h_{n-1},h_{n})}\left[\!\left[u\right]\!\right]_{n}\left[\!\left[v\right]\!\right]_{n}
\end{aligned}
$$

then,

$$
\begin{aligned}a_{1}(u,u) & =\sum_{n=1}^{N}\int_{\Omega_{n}}k\left(\frac{du}{dx}\right)^{2}+\sum_{n=1}^{N+1}\frac{1}{max(h_{n-1},h_{n})}\left[\!\left[u\right]\!\right]_{n}^{2}\end{aligned}
$$

:::{.callout-note appearance="Simple"}
If we set $\sigma_{0}=0$, then we get NIPG0, which was proposed by
Babuska and Coworkers in 1999 \cite{babuska1999}.Non-symmetric interior
penalty Galerkin method (NIPG)
:::

The DG bilinear form presented in the previous chapter is given by 

$$
\begin{aligned}a_{\varepsilon}(\delta u,u) & =\sum_{n=1}^{N}\int_{\Omega_{n}}\frac{d\delta u}{dx}k\frac{du}{dx}-\sum_{n=1}^{N+1}\left[\!\left[\delta u\right]\!\right]_{n}\left\{ k\frac{du}{dx}\right\} _{n}\\
 & +\varepsilon\sum_{n=1}^{N+1}\left[\!\left[u\right]\!\right]_{n}\left\{ k\frac{d\delta u}{dx}\right\} _{n}+J_{0}\left(\delta u,u\right)+J_{1}\left(\delta u,u\right)
\end{aligned}
$$

We can obtain NIPG by setting $\varepsilon=1$ and $\sigma_{1}=0$
and $\sigma_{0}=1$ . This method was presented by Riviere, Wheeler
and Girault in 1999 \cite{riviere1999}\cite{riviere1999}.

$$
\begin{aligned}a_{1}(\delta u,u) & =\sum_{n=1}^{N}\int_{\Omega_{n}}\frac{d\delta u}{dx}k\frac{du}{dx}-\sum_{n=1}^{N+1}\left[\!\left[\delta u\right]\!\right]_{n}\left\{ k\frac{du}{dx}\right\} _{n}\\
 & +\sum_{n=1}^{N+1}\left[\!\left[u\right]\!\right]_{n}\left\{ k\frac{d\delta u}{dx}\right\} _{n}\\
 & +\sum_{n=1}^{N+1}\frac{1}{max(h_{n-1},h_{n})}\left[\!\left[u\right]\!\right]_{n}\left[\!\left[v\right]\!\right]_{n}
\end{aligned}
$$

then,

$$
\begin{aligned}a_{1}(u,u) & =\sum_{n=1}^{N}\int_{\Omega_{n}}k\left(\frac{du}{dx}\right)^{2}+\sum_{n=1}^{N+1}\frac{1}{max(h_{n-1},h_{n})}\left[\!\left[u\right]\!\right]_{n}^{2}\end{aligned}
$$

:::{.callout-tip appearance="Simple"}
If we set $\sigma_{0}=0$, then we get NIPG0, which was proposed by
Babuska and Coworkers in 1999 \cite{babuska1999}.
:::