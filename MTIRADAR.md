# MTI RADAR

## Introduction

- Def: MTI = Moving Target Indicator
- This RADAR allows us to get motion information of the targets (velocity, acceleration)

## Detection of Moving Targets

- Noise level of the natural environment (*clutter*) is many orders of magnitude larger than aircraft/target echoes.
- These are usually from the side lobes which are directed towards the ground, even though the main lobe will be directed at the aircraft. This means you will get returns from the ground which are closer in range than the target, which increases the noise.
- If the clutter and aircraft are both in the same RADAR resolution cell, then a missed detection may occur.
- We can remove the cutter easily using the Doppler effect, as we can assume our targets are going to be moving much faster than the clutter elements, and thus produce a different frequency to them.
    - Doppler Effect = the change in frequency of an echo signal due to the relative velocity between the transmitter and the target.
! [Example of the Doppler Effect](images/DopplerEffect.png)
