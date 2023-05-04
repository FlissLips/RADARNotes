# Electro Optics Systems Design Notes

## Introduction

So what constitutes and EO System? Well, there are 4 main components in each system:

1. A Sensor
2. Optics (either reflective or refractive)
3. Pointing or stabilisation
4. Electronics (this includes sightline control, processing and tracking)

Benefits of EO
- **Passive technology**, meaning they don't need to emmit any illumination in order to detect. This means they can be more stealthy.
- **Shorter wavelength**, which improves the resolution as there is less diffraction

Problems with EO
- **Limited range** (10-20km)
- **Can't work in all weathe**r, particularly water, as it absorbs the infrared radation/visible light

Airbone EO - Basic Principle of Operation
- Better precision than RADAR, as it uses a beam to provide good resolution
- Downside, the range is lesser (very fine, like looking through a drinking straw)

Targeting Pods
- Uses a IR camera as a sensor to accurately track a ground target in order to place laser energy onto it ('laser designation')
- This reflected energy then collected into the lens of an LGB (laser guided bomb)
- Whats requried here?
    - High Resolution camera,  because you're dealing with bombs. 
    - High LoS stabiliation, as with the high resolution, you will have really small FoV   
    - Narrow field of regard (FoR, meaning the field where you place the sightline). 
    - Slew rates (how fast the gimbal system moves) are slow

Directed Infra-red Countermeasures
How it works
- Detects the launch of a SAM using the UV burst at launch
- Accurately tracks the missile seeker
- Places modulated IR energy onto the seeks to force it to break lock

What's required here?
- Good resolution camera, but it's a smaller range
- Good LoS, not as neccessary as the targeting pods though due to smaller range
- Wide FoR, you need to reach **everywhere**,
- Aggressive slew rate, again for the reaching and the tracking performance

EO System Performance
- Calculated with a fully integrated model
- 2 systems that we can look in isolation: **Optical train** and **sightline pointing and stabilisation**

