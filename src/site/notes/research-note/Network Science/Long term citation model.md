---
{"dg-publish":true,"permalink":"/research-note/network-science/long-term-citation-model/","dgHomeLink":true,"dgPassFrontmatter":false}
---


# Long term citation model
updated: 2022-11-18


## Model

The long-term citation model characterizes citation dynamics of a paper $i$ during $[0, T]$ by a set of time moments $\{t_{i\ell}\}_{\ell=1} ^{c_i}$, where $t_{i\ell}$ represents the time of $\ell$ th citation, and $c_i$ is the total number of citations during $[0, T]$. One models $\{t_{i\ell}\}_{\ell=1} ^{c_i}$ as an inhomogeneous Poisson process with rate function $\lambda_i(t)$ given by 
$$
\lambda_i (t) = \eta_i (c_i(t) + m)S(t;\theta_i) 
$$ 
where $\eta_i$ is the fitness and $c_i(t)$ is accumulated number of citations up to time $t$. Variable $m$ accounts for offset attention, which is also called initial attractiveness (see [[research-note/Network Science/Preferential attachment model|Preferential attachment model]]). Function $S(t;\theta_i)$ characterizes the aging effect given by the log-normal distribution: 
$$
S(x; \mu, \sigma) = \frac{1}{x \sigma \sqrt{2\pi}}\exp\left[ - \frac{\left(\ln x - \mu_i\right)^2}{2\sigma^2 _i}\right]
$$
shaped by paper-specific parameters $\theta_i = (\mu_i, \sigma_i)$.

The long-term citation model predicts citations by the following differential equation:
$$
\frac{ {\rm d}c(t) }{ {\rm d}t} = \eta_i (c_i(t) + m) S(t;\theta_i) 
$$
with boundary condition $c(T) = c_i$.  By solving the differential equation, we obtain the prediction of citations by the long-term citation at time $t$:
$$
c(t) = (c_i + m)\exp\left[F(t;\theta_i) - F(T;\theta_i) \right] - m
$$
Note that I follow the derivation by [a follow-up study](https://ojs.aaai.org/index.php/AAAI/article/view/8739), which amends a mathematical leap in [the original paper](https://www.science.org/doi/abs/10.1126/science.1237825).
## Simulations 
The long-term citation model is an inhomogeneous Poisson process, which has been a subject of long tradition. Here, I use a rejection sampling approach referred to as the thinning method. See [here](https://www.math.fsu.edu/~ychen/research/Thinning%20algorithm.pdf) for the details.

```python 
import numpy as np
import pandas as pd


def simulate_poisson_process_LTCM(eta, mu, sig, m, T, bins_per_unit_time=5):
    """Simulate the long-term citation model.

    We use a rejection sampling called the thinning 
    method to simulate the inhomogeneous Poisson process: 
    https://www.math.fsu.edu/~ychen/research/Thinning%20algorithm.pdf
    """
    ct = 0
    sm = 0
    epsilon = 1e-12
    S = lambda t: np.exp(-((np.log(t + epsilon) - mu) ** 2) / (2 * sig ** 2)) / (
        (t + epsilon) * np.sqrt(2 * sig * np.pi)
    )
    ts_list = []
    while sm < T:
        Smax = 1 / ((sm + epsilon) * np.sqrt(2 * sig * np.pi))
        lam_max = eta * (ct + m) * Smax
        u = np.random.rand()
        w = -np.log(u) / lam_max
        sm += w
        u2 = np.random.rand()
        if u2 < (eta * (ct + m) * S(sm) / lam_max):
            ts_list.append(sm)
            ct += 1
    return ts_list
```


##  Critiques
The long-term citation model demonstrated an excellent predictive capacity of citations, which is later questioned [Comment on “Quantifying long-term scientific impact” | Science](https://www.science.org/doi/10.1126/science.1248770). Furtheremore, the derivation of the model contains a critical error and unjustified assumptions [(see here)](https://drive.google.com/file/d/1BRfXVSbMV4SZy24PsP21KPidWnyppVCl/view?usp=sharing)  .


# References
- [Quantifying Long-Term Scientific Impact | Science](https://www.science.org/doi/abs/10.1126/science.1237825) 
- [Modeling and Predicting Popularity Dynamics via Reinforced Poisson Processes | Proceedings of the AAAI Conference on Artificial Intelligence](https://ojs.aaai.org/index.php/AAAI/article/view/8739)
 