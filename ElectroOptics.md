# Electro-Optics Systems Design Notes

## Introduction

So what constitutes and EO System? Well, there are 4 main components in each system:

1. A Sensor
2. Optics (either reflective or refractive)
3. Pointing or stabilisation
4. Electronics (this includes sightline control, processing and tracking)

### Benefits of EO
- **Passive technology**, meaning they don't need to emmit any illumination in order to detect. This means they can be more stealthy.
- **Shorter wavelength**, which improves the resolution as there is less diffraction

### Problems with EO
- **Limited range** (10-20km)
- **Can't work in all weather**, particularly water, as it absorbs the infrared radation/visible light

### Airbone EO - Basic Principle of Operation
- Better precision than RADAR, as it uses a beam to provide good resolution
- Downside, the range is lesser (very fine, like looking through a drinking straw)

### Targeting Pods

How it works
- Uses a IR camera as a sensor to accurately track a ground target in order to place laser energy onto it ('laser designation')
- This reflected energy then collected into the lens of an LGB (laser guided bomb)

What's requried here?
- High Resolution camera,  because you're dealing with bombs. 
- High LoS stabiliation, as with the high resolution, you will have really small FoV   
- Narrow field of regard (FoR, meaning the field where you place the sightline). 
- Slew rates (how fast the gimbal system moves) are slow

### Directed Infra-red Countermeasures
How it works
- Detects the launch of a SAM using the UV burst at launch
- Accurately tracks the missile seeker
- Places modulated IR energy onto the seeks to force it to break lock

What's required here?
- Good resolution camera, but it's a smaller range, so it's not as critical as it is in the tracking pods
- Good LoS, not as neccessary as the targeting pods though due to smaller range.
- Wide FoR, you need to reach **everywhere**. (The one part where you can't reach is where the missile will come from)
- Aggressive slew rate, again for the reaching. This means for it will need good tracking performance

### EO System Performance
- Calculated with a fully integrated model
- 2 systems that we can look in isolation: **Optical train** and **sightline pointing and stabilisation**

___

## EO Sensor Modelling
**Def**:  Derivation of performance of a devices taking into account of handling of output

![EO Model](images/EOModelDiag.png)

## Radiometery
- When given a source and optical system configuration, how much power from the source is collected by the detector surface?
- There's a lot of radiometric terms that can be expressed in either energy or photon-based units:

![Radiometry Table](images/RadiometryTable.png)

- You can convert between the two unit bases by remembering that the amount of energy contained per photon:
$E = \frac{hc}{\lambda}$

### Radiometry Terms

- **Radiant flux**: The amount of radiant energy measured over time
     AKA $ \Phi = \frac{dQ}{dt}$
- **Exitance & Irradiance**:      
    - *Exitance* is how much flux is emmited from a source over a given area.
    - *Irradiance* is how much flux is recieved from the source over a given area
    - Both have the same equation: $M = \frac{d\Phi}{dA}$ for Exitance, and $E = \frac{d\Phi}{dA}$ for Irradiance
- **Intensity** : The amount of radiation energy from a point target (per solid angle) AKA $I = \frac{d\Phi}{d\Omega}$
- Radiance: The flux per unit projected area per solid angle AKA $L = \frac{d^2\Phi}{d(A\cos\theta)d\Omega}$ 

### A $\Omega$ Product
Consider the following case:
![AOmegaProductAngle](images/APhiProduct.png)
Where $A_d$ = detector angle, $A_s$ = source angle, $\Omega_s$ = source solid angle, $\Omega_d$ = detector solid angles, and $r$ = range

Therefore, assuming small angles, the flux on the detector: 

$ \Phi = LA_s\Omega_d = L\frac{A_sA_d}{r^2} = LA_d\Omega_s $ 

### Tilted Reciever
If your reciever is tilted wrt the source:
![Tilted Reciever Diagram](images/TiltedReciever.png)
Then:

$ \Phi = LA_s\Omega_d = L\frac{A_sA_d\cos\theta_d}{r^2}$

## Lambertian Radiator
### Introduction
- Relying on reflected energy means you have to create some kind of model for this. 
- This can be done with physics-based rendering, where each material is assigned absorption characteristics to each material, which is very complicated.
- We can instead create a simplication called a **Lambertian surface**
- It's a surface where the radiance $L$ is independemt of view $\theta_s$, and that $L$ is constant
- This doesn't mean that it will radiation an equal amount of flux into all solid angles.
- Here, the relationship between $L$ and $M$ is: $M = L\pi$
### Relationship between Exitance and Radiance
- Assuming a Lambertian surface means any point on this surface radiates into a hemisphere
- The flux is then given by:
  $\phi_{hemisphere} = \int L A \cos \theta_{s} d \Omega_{d}$ **(1)**

- In spherical coordinates:
$d\Omega_d= \frac{dA_d}{r^2}= \frac{r^2\sin \theta d \theta d \phi}{r^2} = sin \theta d \theta d \phi$ **(2)**
- Sub **(2)** into **(1)** :
$\phi_{hemisphere} =  \int_{-\pi}^{\pi}\int_{0}^{\pi/2}L A \cos \theta_{s} sin \theta d \theta d \phi$ **(3)** 
- Evaluate **(3)**
$\phi_{hemisphere} = \pi L A_s = MA_s$

### Off-Axis Detector
 Def: Where the target and detector are not parallel, and instead have non-zero view angles.

An example is shown here:
![Off Axis Detector Diagram](images/OffAxisDetector.png)
 
 Here the detector flux is 

 $\phi_d = L A_s \cos \theta_{s} \Omega_d = L A_s \cos \frac{A_d}{(r/\cos \theta_s)^2\leq }$

### Parallel Surfaces

Occurs in two offset parallel angles. 

An example is shown here:

![Parallel Surfaces Diagram](images/ParallelSurfaces.png)

Looking at the geometry the flux is:
$\phi_d = L A_s \cos \theta_{s} \Omega_d = L A_s \cos \frac{A_d \cos \theta_d}{(r/\cos \theta_s)^2}$

### Point Targets
Def: where the projected target area is much smaller than the range to the target, meaning the solid angle is $\approx 0$

An example is shown here (A model of a point target viewed by a camera)
![PointTarget Diagram](images/PointTargetDiag.png)

For a circular lens:
$\Omega = \frac{\pi D^2}{4r^2}$

Therefore the flux (using the intensity) is: $\phi = I \Omega = I\frac{\pi D^2}{4r^2}$

We use the irradance on the detector here, as we don't need to consider the radiance on a point target.
Therefore, the irradiance is:
$E = \frac{\phi}{A_d} = \frac{I}{r^2}$

This here is known as the **inverse square law**. This showns as the irradiance increases, the range decreases. This is similar to RADAR, where the range is inversely proportional to the power. but is not as affecting.

___
## Atomspheric Transmission

- An important thing to model as, estimating flux losses from propgating through the atomsphere cannot be done just from first-principles. This means that models must have a signficant experimental component.
- It's more important here than in RADAR, as the atomsphere attenuates the optical radiation **a lot** more here.

The 3 main attenuation mechanisms are:

### 1. Absorption
Def: The process where energy contained in the photons are devoured by gas molecules and aerosols. This radiation gets transformed into KE and heat.
- Depends on the wavelength of the radiation
- This can lead to *transmission windows* (spectral bands where the attenuation is minimal). These look like this: ![Atomspheric Transmission Windows](images/AtomsphericTransmissionWindows.png)
### 2. Scattering
Def: where the photons are redirected along a different propagation path
- Scatter will depend on the ratio between the wavelength and the size of the particles obstructing the path of the photons.
### 3. Refraction
Def: Refracts the radiation due to the refractive index (RI) of the atomsphere
- RI is dependent on the current temperatue
- The refraction induces directional errors, which are more pronounced at long ranges and low altitudes over land and sea
---
## Target Models - Sources of Radiation
- 
