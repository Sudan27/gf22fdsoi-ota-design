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

