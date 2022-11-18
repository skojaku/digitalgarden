---
{"dg-publish":true,"permalink":"/research-note/network-science/long-term-citation-model/","dgHomeLink":true,"dgPassFrontmatter":false}
---


# Long term citation model
updated: 2022-11-18


## Model

The long-term citation model characterizes citation dynamics of a paper $i$ during $[0, T]$ by a set of time moments $\{t_{i\ell}\}_{\ell=1} ^{c_i}$, where $t_{i\ell}$ represents the time of $\ell$ th citation, and $c_i$ is the total number of citations during $[0, T]$. One models $\{t_{i\ell}\}_{\ell=1} ^{c_i}$ as a inhomogeneous Poisson process with rate function $\lambda_i(t)$ given by 
$$
\lambda_i (t) = \eta_i (c_i(t) + m)S(t;\theta_i) 
$$ 
where $\eta_i$ is the fitness and $c_i(t)$ is accumulated number of citations up to time $t$. Variable $m$ accounts for offset attention that is independent of the accumulated citation $c_i$.  Function $S(t;\theta_i)$ characterizes the aging effect given by the log-normal distribution: 
$$
S(x; \mu, \sigma) = \frac{1}{x \sigma \sqrt{2\pi}}\exp\left[ - \frac{\left(\ln x - \mu_i\right)^2}{2\sigma^2 _i}\right]
$$
shaped by paper-specific parameters $\theta_i = (\mu_i, \sigma_i)$.

The long-term citation model predicts citations by the following differential equation:
