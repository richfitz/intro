A population of `N` individuals is structured into "compartments" which contain Susceptible `S`, Infected (`I`) and Recovered (`R`) individuals.  Susceptible individuals can be infected by infected individuals at rate `beta` per interaction and infected individuals eventually recover and become immune to infection at rate `sigma`.  This model can be expressed as a set of deterministic differential equations:

```
dS/dt = beta * S * I / N
dI/dt = beta * S * I / N - sigma * I
dR/dt = sigma * I
```

(in this model `N = S + I + R` and does not change over time).

To convert this to a discrete stochastic model we imagine that in a small period of time `dt` the chance of an event happening follows a Bernoulli trial.

In a discrete time step of size `dt`, the probability that:

* an `S` individual becomes `I` is `1 - exp(-beta * I / N * dt)`
* an `I` individual becomes `R` is `1 - exp(-sigma * dt)`

Sensible parameters for the above are `beta = 10`, `sigma = 1` with population size of ~1000 and a single initial infected individual.  In this case the epidemic will complete over ~5 time units.  You will qualitatively see S decrease, R increase and I peak around time unit 1.
