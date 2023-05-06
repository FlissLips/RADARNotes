# RADAR Notes 113 Page
## Introduction

### History
- Began in 1930s with radio frequencies of 30MHz
- Increased to 1-10GHz in the 40s due to military requirements
- Transferred to the civil sector in 1950s, with improvements made in the 60s and 70 with the advent of digital computers and signal processing
### Types of RADAR systems

![Types of RADAR Systems Diagram](images/TypesOfRADAR.png)

- **Primary RADAR**: antenna transmitts a signal, bounces of target, returns to the base. Detects object using only the reflection of the radio waves
- **Secondary RADAR**: RADAR sends a signal, collected by onboard antenna, and uses a two-way communication system that allows the RADAR to identify and track the object. (Not really covered in the course)
- **Monostatic apporach**: transmit and reciever path are the same path. Single antenna does both broadcast and recieve
- **Bistatic/Multistatic approach**: seperate antennas for broadcasting and recieving the echo. The advantage of this is stelth technology. The majority of stelth-designed targets will be designed so that the transmitted energy (RADAR beam) will be reflected in a direction that is not the original one. Therefore, if it's seperate, then it's more likely to be able to pick up those targets. Also with multistatic, in military operations, you have multiple antennas to transmit/recieve if one goes down (gets blown up)
- **Tracking RADAR**: Used to precisely locate and track a specific object
- **Scanning RADAR**: Used to detect the presence of objects within a large area
- **TWS/ADT**: Covered in target tracking.
- **Imaging RADAR SAR**

### Pulse RADAR System Components

#### Display to Operator
![Display to Operator Diagram](images/DisplaytoOperator.png)

- **Waveform generator**: generates the carrier waveform
- **Pulse modulator**: contains rect function.
- **Power amplifier**: inputs WG and Pulse, and does what it says. Outputs the transmit signals
- *Duplexer*: Dotted line shows it works for both transmit and reciever. Acts like a switch between them. When transmitting, there is 0 impedance across the power amplifier and $\infin$ impedance on the LNRFA. Vice versa for recieving.
- circlely thing AKA the antenn: Sends the signal
- **Low Noise RF Amplifier**: amplifies the reciever pulse, without introducing significant noise caused at high frequencies. Operating at radio frequencies, so limited components can be used. 
- *Superhetrodyne*: converts RF pulse to an Intermediate Frequency (IF) pulse by multplying it with the signal from the local oscillator.
    - We convert to improved selectivity, easier gain, demodulation and filtering.
- **Demodulator/Envelope detector**: truns the IF pulse into a video pulse.

#### Automatic Tracking

![Automatic Tracking](images/AutomaticTracking.png)

Differences between display operator
- **Detection logic** : Meant to replace a trained operator
- **Tracking algorithm**: find where our target is and where it's going
- **Sightline control**: moves depending on where the target is

### Super Hetrodyne Reciever
Def: A reciever that using the heterodyning technique to convert RF to IF, by combining the RF signal with a local oscillator at a difference frequency. When combined, the 2 new signals are produced: the sum frequency and the difference frequency. The sum frequency is then filtered out, leaving the desired IF frequency.

The equation of the superhetrodyne reciever:

$s_c(t) * s_{lo}(t) = \sin(2\pi f_{lo}t)$ **(1)**

Using Euler's theroem $\sin x = Im(e^{ix}) = \frac{e^{ix} - e^{-ix}}{2i}$:

$s_c(t) * s_{lo}(t) = \frac{i^2}{2} (\frac{e^{i2\pi (f_c + f_{lo})t} + e^{-i2\pi (f_c + f_{lo})t}}{2} - \frac{e^{i2\pi (f_c - f_{lo})t} + e^{-i2\pi (f_c - f_{lo})t}}{2})$

= 

$\frac{1}{2} \cos(2 \pi (f_c - f_{lo})t) - \frac{1}{2} \cos(2 \pi (f_c + f_{lo})t) $

Therefore:

$f_{IF} = f_c - f_{lo}$
___

## Radar Equation
### Introduction
The radar equation is a function made up of 2 parts: the **deterministic** parts which are under the designers control, and the **probabilistic** part which are not.

In this section, I've decided to to order it by each RADAR equation (Simplest, Simple, Complex), then explain the components that make up the equations and why they are important.

## Simplest Equation

Equation:

Reflected Power flux density recievd = $\frac{P_t G_t \sigma}{(4 \pi R^2)^{2}}$ Watts/m^2

Where
- $P_t$ = Power at isotropic source 
- $G_t$ = Gain at the source
- $\sigma$ = Radar Cross Section
- R = range 

### Components
1. Well, you start with an Isotropic antenna, which is an antenna which is one whcih radiates uniformly in directions. Assuming there's no attenuation loss: Power density at range R $ = \frac{P_t}{4 \pi R^{2}}$
2. Then, you include the antenna gain. This is the ratio of the radiation intnsity of an antenna in a given direction, compared to that of an isotropic radiatior. We need to add this term, as in practice, we won't be using isotropic antennas. The equation then becomes: Max Power Density at Range R $= \frac{P_t G_t}{4 \pi R^{2}}$
___
##