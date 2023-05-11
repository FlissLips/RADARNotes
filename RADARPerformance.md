# Radar Peformance
## Matched Filter
### Introduction

- It is almost universally employed in the IF amplifier of modern RADAR systems.
- This is because it yields the highest Signal-To-Noise Ratio at the output, which is important when identifying targets in noisy conditions

### Matched Filter Derivation

1. Consider the noisy input to the IF = the signal to be recovered + white Gauissian Noise:
$r(t) = s(t) + n(t)$, where $n(t)$ has a spectral height $\frac{N_0}{2}$ and $s(t)$ is a signal with finite duration $T$.
2. Let $r(t)$ be the input to a filter with $h(t)$ and let $y(t)$ be the output. Therefore the output of the filter will be given by the convolution integral: $y(t) = \int_{0}^{t} r(\tau) h(t - \tau) d\tau$. 
    - This then means the signal part of the output is: $y_s(t) = \int_{0}^{t} s(\tau) h(t - \tau) d\tau$
    - The noise part is then: $y_n(t) = \int_{0}^{t} n(\tau) h(t - \tau) d\tau$
3. The Signal-to-Noise ratio is then: $SNR = \frac{y_{s}^{2}(t)}{E[y_{n}^{2}(t)]}$ where $E[y_{n}^{2}(t)]$ is the expected part of the noise signal. Then subsitute the equations from part (2) here: $\frac{[\int_{0}^{t} s(u) h(t-u) du]^{2}}{E[\int_{0}^{t} n(u) h(t-u) du]^{2}}$
    - It's squared here, as we need positive values to determine the power
4. The objective here is to find $h(t)$ that maximises this SNR. To do this, we try to simply the noise term: 
    - $E[y_{n}^{2}(t)] = E\left \{ \left [ \int_{0}^{t} n(u) h(t-u) du \right ] \left [ \int_{0}^{t} n(v) h(t-v) dv \right ] \right \}$ *(a)*
    - $E[y_{n}^{2}(t)] = \int_{0}^{t} \int_{0}^{t} E\left \{ n(u)n(v) \right \} h(t-u)h(t-v) dudv$ *(b)*
    - $E[y_{n}^{2}(t)] = \int_{0}^{t} \int_{0}^{t} \frac{N_0}{2} \delta (u-v) h(t-u)h(t-v) dudv$ *(c)*
    - $E[y_{n}^{2}(t)] = \frac{N_0}{2}  \int_{0}^{t} h^{2}(t-u)du$ *(d)*
        - To transition from (b) to (c), we had to assume the noise sources are uncorrelated. Therefore the expected value of the noise will always be 0 EXCEPT for when v = u. This is why we use the dirac delta function with the expected value $\frac{N_0}{2}$
    - Finally we sub (d) into step 3: $SNR = \frac{\left [ \int_{0}^{t} s(u)h(t-u)du \right ]^{2}}{\frac{N_0}{2}  \int_{0}^{t} h^{2}(t-u)du}$

5. Now to maximise the numerator, we use the Cauchy-Schwarz inequality, which states that $\left \langle S, Q \right \rangle^{2} \leq |S|^{2} |Q|^{2}$ where $\left \langle S, Q \right \rangle^{2}$ is the dot product of $S$ and $Q$. Equality is then reached when $cs(u) = q(u)$. If we then sub the $q(u)$ and for $cs(u)$ in the equation, SNR then becomes: 
    - $SNR^{opt}(t) = \frac{\left [ c\int_{0}^{t} s^2(u)du \right ]^2}{\frac{N_{0}c^{2}}{2} \int_{0}^{t} s^{2}(u) du} = \frac{\int_{0}^{t} s^{2}(u)du}{\frac{N_0}{2}}$
6. Finally, as we discussed in step 1, $s(t)$ is a signal with finite duration $T$. Therefore:
    - $SNR^{opt}(t) = \frac{\int_{0}^{T}s^{2}(u)du}{\frac{N_0}{2}} = \frac{2\varepsilon_s}{N_0}$ where $\varepsilon_S$ is the energy of the signal.

