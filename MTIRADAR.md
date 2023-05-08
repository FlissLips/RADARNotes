# MTI RADAR

## Introduction

- Def: MTI = Moving Target Indicator
- This RADAR allows us to get motion information of the targets (velocity, acceleration)

## Detection of Moving Targets

- Noise level of the natural environment (*clutter*) is many orders of magnitude larger than aircraft/target echoes.
- These are usually from the side lobes which are directed towards the ground, even though the main lobe will be directed at the aircraft. This means you will get returns from the ground which are closer in range than the target, which increases the noise.
- If the clutter and aircraft are both in the same RADAR resolution cell, then a missed detection may occur.
- We can remove the cutter easily using the Doppler effect, as we can assume our targets are going to be moving much faster than the clutter elements, and thus produce a higher frequency to them.
    - Doppler Effect = the change in frequency of an echo signal due to the relative velocity between the transmitter and the target.

![Example of the Doppler Effect](images/DopplerEffect.png)

### Derivation of the Doppler Frequency Shift

1. For a target of range R, the phase length of the two-way path: $\phi = \frac{2 \pi}{\lambda} \times 2R$
2. The rate of change of phase of a moving target will be: $\frac{d \phi}{dt} = \omega = \frac{4 \pi}{\lambda} \cdot \frac{dR}{dt} = \frac{4 \pi}{\lambda} v_r rad/sec$
3. The Doppler Frequency shift is therefore: $f_d = \frac{\omega}{2 \pi} = \frac{2v_r}{\lambda} Hz$

Therefore the Doppler shift is function of the range rate $v_r$.

### Pulse RADAR Doppler Shift 

![Pulsed RADAR Doppler Shift](images/PulsedRADARDopplerShift.png)

- Doppler shift extraction is achieved by multiplication of the recieved signal with the transmitted waveform.
- Why does it do this? Well, it needs a reference signal to base the change in phase on. It needs a reference signal to know how much the pulse has changed, and therefore it it added here at the **reciever** block. This reference signal is known as a **coherent reference**.
- You can detect the Doppler Shift in 1 cycle, provided that $f_d \tau > 1$ AKA at least one the cycle of the Doppler Shift is whin the pulse.

## Sweep-to-Sweep Extraction

- Another method for eliminating clutter from moving targets.
- Def of Sweep: time between two transmitted pulses
- Two Sucessive sweeps are shown below:
![Sweeps](images/SweeptoSweep.png)
- From the 2 successive sweeps, it is clear that any cluster/stationary returns are identical across the sweep, but the moving targets show up with different amplitudes on the 2 sweeps. This is due to the Doppler Effect. 
- Therefore, we subtract the sweeps, the stationary targets are removed.

### Delay-line Canceller

![Delay Line Canceller](images/DelayLineCanceller.png)
- Subtraction of the sweeps are accomplished in a delay line canceller, as shown above.
- So, the way it works is it converts the signal to the digital domain, delays it by one time step in order to subtract the previous from the original, take the absolute of the subtraction, then convert it back to analog.
-