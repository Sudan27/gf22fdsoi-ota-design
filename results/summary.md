# OTA Simulation Results

## Open-Loop AC Analysis

The OTA open-loop frequency response was simulated using Cadence Virtuoso and Spectre with the specified load capacitance of 0.25 pF.

### Measured Results

| Parameter                                                     | Simulated result |
| Low-frequency open-loop gain                                  | 38.12 dB |
| Open-loop gain (linear)                                       | Approximately 80.5 V/V |
| Unity-gain frequency                                          | 53.05 MHz |
| Phase at unity-gain frequency                                 | -282.9° |
| Average gain slope between 20.7411 MHz and 87.2156 MHz        | Approximately -19.0 dB/decade |

### Observations

- The measured low-frequency gain exceeds the minimum requirement of 40 V/V.
- The measured unity-gain frequency exceeds the specified 50 MHz minimum.
- The average gain slope between the two selected frequency markers is close to -20 dB/decade.
- The unwrapped phase at the unity-gain frequency is -282.9°. Further investigation of the phase response and stability characteristics is required before drawing conclusions about stability.

### Figures

- `figures/open_loop_gain.png` — Open-loop gain magnitude.
- `figures/open_loop_phase.png` — Open-loop phase response.

## DC Operating Point

The following table summarizes the simulated DC operating-point parameters of the six OTA transistors.

| Transistor | Width (µm) | Length (nm) | \|ID\| (µA) | \|VGS\| (mV) | \|VDS\| (mV) | Region of operation |
|---|---:|---:|---:|---:|---:|---:|
| M1 | 110 | 160 | 3.419 | 292.1 | 218.6 |weak-inversion|
| M2 | 110 | 160 | 3.399 | 291.2 | 291.2 |weak-inversion|
| M3 | 7.8 | 320 | 3.419 | 373.4 | 373.4 |weak-inversion|
| M4 | 7.8 | 320 | 3.400 | 373.4 | 300.8 |weak-inversion|
| M5 | 0.78 | 320 | 6.819 | 568.4 | 568.3 |saturation|
| M6 | 0.50 | 320 | 5.000 | 568.4 | 207.8 |saturation|

### Static DC Power

Using the supply-current expression from the design calculation:

Static power: P_DC = V_DD × (I_5 + I_6)

With V_DD = 0.8 V, I_5 = 6.819 µA, and I_6 = 5 µA, the calculated value is 9.4552 µW.



## Closed-Loop AC Analysis

The OTA was configured as a unity-feedback voltage follower and simulated using AC analysis in Cadence Virtuoso.

### Measured Results

| Parameter | Simulated result |
|---|---:|
| Closed-loop DC gain, \(A_{f,0}\) | 0.988211 V/V |
| Closed-loop DC gain | Approximately -0.103 dB |
| Closed-loop -3 dB bandwidth, \(f_{p,f}\) | 55.63 MHz |

### Observations

- The low-frequency closed-loop gain is close to unity, consistent with voltage-follower operation.
- The measured -3 dB bandwidth is 55.63 MHz.

### Figure

- `figures/closed_loop_gain.png` — Closed-loop AC gain magnitude.
