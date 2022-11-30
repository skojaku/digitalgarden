---
{"dg-publish":true,"permalink":"/literature-notes/research-note/network-science/long-term-citation-model/"}
---


# Long term citation model
updated: 2022-11-18

#network-science/citation-dynamics 


## Model

The long-term citation model characterizes citation dynamics of a paper $i$ during $[0, T]$ by a set of time moments $\{t_{i\ell}\}_{\ell=1} ^{c_i}$, where $t_{i\ell}$ represents the time of $\ell$ th citation, and $c_i$ is the total number of citations during $[0, T]$. One models $\{t_{i\ell}\}_{\ell=1} ^{c_i}$ as an inhomogeneous Poisson process with rate function $\lambda_i(t)$ given by 
$$
\lambda_i (t) = \eta_i (c_i(t) + m)S(t;\theta_i) 
$$ 
where $\eta_i$ is the fitness and $c_i(t)$ is accumulated number of citations up to time $t$. Variable $m$ accounts for offset attention, which is also called initial attractiveness (see [[Literature notes/research-note/Network Science/Preferential attachment model\|Preferential attachment model]]). Function $S(t;\theta_i)$ characterizes the aging effect given by the log-normal distribution: 
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

##  Critiques
The long-term citation model demonstrated an excellent predictive capacity of citations, which is later questioned [Comment on “Quantifying long-term scientific impact” | Science](https://www.science.org/doi/10.1126/science.1248770). 

Furtheremore, the derivation of the model contains a critical error and unjustified assumptions [(see here)](https://drive.google.com/file/d/1BRfXVSbMV4SZy24PsP21KPidWnyppVCl/view?usp=sharing)  .

## Code
- [Long-term citation model · GitHub](https://gist.github.com/skojaku/8494552b3012d047f6555b5f322e3eaf)


# References
- [Quantifying Long-Term Scientific Impact | Science](https://www.science.org/doi/abs/10.1126/science.1237825) 
- [Modeling and Predicting Popularity Dynamics via Reinforced Poisson Processes | Proceedings of the AAAI Conference on Artificial Intelligence](https://ojs.aaai.org/index.php/AAAI/article/view/8739)
 