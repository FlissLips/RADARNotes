# RADAR Range Measurement & Spatial Resolution

## Introduction

Monostatic pulsed RADAR diagram:

![RADAR Waveform](images/RADARW.png)

Where:
- $\tau$ = time of pulse
- $T_p$ = time between pulses
- $P_t$ = peak power
- $P_{av}$ = average power

Average power of a pulse-train waveform:

$P_{av} = \frac{P_{t} \tau}{T_p} = P_t \tau f_p$

Duty Cycle:

$ = \frac{\tau}{T_p} = \tau f_p = \frac{P_{av}}{P_t}$

## Range to Target

- The frequency and duration of a RADAR pulse determines the range and range resolution of the RADAR. 
- Equation: $R = \frac{c \Delta t}{2}$
    - $\Delta t$ = time between transmit and receipt of pulses
    - $c$ = speed of light

### Timing (Unambiguous Case)
![Range to Target Timing Diagram unambiguous](images/UnambiguousTimingDiagram.png)
- From the diagram we can se that the pulses are not sent until the previous pulse is recieved, so that there is no ambiguity in which pulse it is. 
- This means you are always restrainted by the time taken to return.


### Timing (Ambiguous Case)
![Range to Target Timing Diagram ambiguous](images/AmbiguousTimingDiagram.png)
- In this case, the time berween the transmitted pulse and recieved echo is uncertian, as the RPF is too low to provide a unique measurement.
- This can make the echoes appear to have a closer range that they actually are.

### Maximum Unambiguous Range
- Def: The maximum distance that can be measured without encountering range ambiguity.
- Equation: $R_{un} = \frac{c T_p}{2} = \frac{c}{2 f_p}$
    - $T_p$ is the pulse repetition period
    - $f_p$ is the pulse repetition frequency (PRF)

- From this equation, we can see that is $T_p < \Delta T$, the range measurement is ambiguous.

### Eliminating Ambiguous Returns

#### PRF Jittering

- If there are targets which ranges are beyond $R_{un}$ are not considered, we can solve the problem of ambiguities by rejecting all returns beyond $R_{un}$.
- PRF Jittering can do this by varying the PRF in a controlled way, which makes the echoes from different ranges to be spread out over a range of time, rather than being compressed into a single time interval.
- If the PRF is changed, the apparent range of the target beyond $R_{un}$ will change as well.
- Targets at ranges below $R_{un}$ are unaffected

#### Multiple PRFs Come back to

- But what if the

___

## Range Resolution

![Range Resolution Diagram](images/RangeResolutions.png)
 
 - $\tau$ = pulse width (seconds)
 - $c \tau$ = propagation distance (m)

 Range resolution equation:

 $resolution = \frac{c \tau}{2}$

### RADAR Datacube

- Range measurements are always quantised, therefore normally you would seperate target range into discrete range elements known as *cells*.
- This information is then stored in a software structure known as the *datacube*.
___

## Angle Resolution

The diagram below shows 2 targets at the sae range and seperated by an angle $\theta$.

![Angle Resolution Diagram](images/AngleResolution.png)

Where:
- $D_A$ = Antenna Diameter
- $D_B$  = Distance between targets
- $R_X$ = Range

Therefore:

$D_B = R_X \theta$ (rads)
