# OTA Design Methodology

## 1. Design Approach

The objective of this project was to design a single-ended-output operational transconductance amplifier (OTA) in GF22 FDSOI technology while meeting the required gain and bandwidth specifications and minimizing static DC power consumption.

The design process used the NMOS and PMOS characterization results from Part 1 to estimate suitable transistor operating points, current densities, channel lengths, and widths.

The methodology followed these stages:

1. Select the input common-mode voltage using the DC operating constraints.
2. Estimate the required transconductance from the gain-bandwidth requirement and effective output capacitance.
3. Select the input-pair operating point using the gm/ID and intrinsic-gain characterization curves.
4. Determine the bias-transistor dimensions and branch currents.
5. Size the remaining transistors to balance current, voltage headroom, and output resistance.
6. Verify the design using DC operating-point, open-loop AC, closed-loop AC, and transient simulations.

## 2. Design Requirements

The OTA was designed to meet the following project specifications.

| Parameter | Requirement |
|---|---:|
| Supply voltage, VDD | 0.8 V |
| Open-loop DC gain, A0 | At least 40 V/V |
| Gain-bandwidth product (GBW) | At least 50 MHz |
| Open-loop magnitude slope near unity gain | Close to −20 dB/decade |
| Load capacitance, CL | 0.25 pF |
| Ideal bias current, IB | 5 µA |
| Bias voltage, VB | At least 0.1 V |
| Static DC power, PDC | Minimize while meeting the specifications |

The design was evaluated using DC operating-point analysis, open-loop AC analysis, closed-loop AC analysis, and transient simulation.

## 3. Selecting the Input Common-Mode Voltage

For the ideal DC operating condition, the differential input voltages are equal, and the output voltage is equal to the input common-mode voltage:

**V+ = V− = VCM, and VO = VCM**

The following voltage constraints were used to establish a feasible operating range:

- VOV3 < VCM < VDD − VOV1 − VOV5 − |Vtp|
- VOV4 < VO < VCM − |Vtp|

The common-mode voltage was selected as **VCM = 0.3 V**, with the intention of keeping it relatively low to preserve output-voltage swing.

## 4. Estimating the Required Transconductance and Gain

The DC gain was estimated using the effective output resistance and the input-pair transconductance:

**A0 = GM × RO**

The report expresses the gain in terms of the transistor output resistances as:

**A0 = gm1 × ro1 × [ro4 / (ro1 + ro4)]**

Assuming ro1 = ro4, this becomes:

**A0 = gm1 × ro1 / 2**

Therefore, the required intrinsic gain was estimated to be approximately twice the desired overall gain. The characterization curves indicated that channel lengths of 160 nm and 320 nm were suitable candidates.

The input pair was initially assigned:

- L1 = L2 = 160 nm

The channel lengths of the remaining transistors were selected separately to balance gain, output resistance, and operating constraints.

## 5. Estimating the Input-Pair Transconductance

The effective output capacitance was approximated as the load capacitance plus a 15% allowance for parasitic capacitances:

**Cout ≈ 1.15 × CL = 275 fF**

Using the gain-bandwidth relationship from the design calculations:

**GBW ≈ gm1,2 / (2π × Cout)**

The estimated input-pair transconductance was:

**gm1,2 ≈ 94.24 µS**

This value was used to guide the selection of the input-pair operating point.

## 6. Sizing the Input Pair and Main Current Branches

The input transistors were intended to operate near the boundary between weak and strong inversion. This operating point was selected to obtain high intrinsic gain while retaining useful transconductance efficiency.

From the gm/ID characterization curves, an efficiency of approximately 28 S/A was selected at a current density of approximately 0.035 A/m for a channel length of 160 nm.

The estimated drain current per input transistor was calculated as:

**ID ≈ gm / (gm/ID)**

**ID ≈ 94.24 µS / 28 S/A ≈ 3.36 µA**

A 15% design margin was then applied, giving the initial current targets:

- I1 = I2 ≈ 3.9 µA
- I3 = I4 ≈ 3.9 µA

The tail current was estimated as:

**I5 = I1 + I2 ≈ 7.8 µA**

The input-transistor widths were calculated using the selected current density:

**W1 = W2 = ID / (ID/W)**

**W1 = W2 ≈ 3.9 µA / 0.035 A/m ≈ 110 µm**

The initial input-pair dimensions were therefore:

- W1 = W2 = 110 µm
- L1 = L2 = 160 nm

## 7. Sizing the Bias Transistors

The bias transistors M5 and M6 were selected to operate in saturation. The design calculations used a target gm/ID of approximately 10 S/A and selected a channel length of 320 nm to obtain higher output resistance.

At this channel length and operating point, the characterization curves indicated a current density of approximately 10 A/m and a gate-source voltage magnitude near 580 mV.

The estimated width of M5 was calculated as:

**W5 = I5 / (ID/W)**

**W5 = 7.8 µA / 10 A/m = 0.78 µm**

For M6:

**W6 = I6 / (ID/W)**

**W6 = 5 µA / 10 A/m = 0.50 µm**

The initial bias-transistor dimensions were therefore:

- M5: W5 = 0.78 µm, L5 = 320 nm
- M6: W6 = 0.50 µm, L6 = 320 nm

## 8. Sizing the Remaining Transistors

The currents through M3 and M4 were initially estimated to be approximately 3.9 µA.

Using the selected common-mode voltage and the corresponding gate-source voltage estimate, the characterization curves indicated a current density of approximately 0.5 A/m for a channel length of 320 nm.

The widths were calculated as:

**W3 = W4 = ID / (ID/W)**

**W3 = W4 ≈ 3.9 µA / 0.5 A/m ≈ 7.8 µm**

The channel lengths were selected as:

- L3 = L4 = 320 nm

The longer channel length was chosen to increase output resistance and support the DC gain objective.

## 9. DC Operating-Point Verification

After the initial dimensions were calculated, the complete OTA was simulated and the transistor operating points were inspected.

The simulated operating-point values were recorded in `results/summary.md`. These include transistor dimensions, drain-current magnitudes, gate-source voltage magnitudes, and drain-source voltage magnitudes.

The simulated values differ slightly from the initial design estimates because the final operating points are determined by the complete circuit and its device models.

The operating-point analysis was used to verify the transistor operating regions and assess whether the selected dimensions provided suitable voltage headroom.

## 10. Open-Loop AC Analysis

An open-loop AC simulation was performed to evaluate the OTA's low-frequency gain and frequency response.

The analysis was used to obtain:

- Low-frequency open-loop gain, A0
- Unity-gain frequency
- Magnitude-response slope near the unity-gain crossing
- Phase response as a function of frequency

The input AC magnitude was set to 1 V, allowing the output magnitude to represent the voltage gain magnitude when the measured output was taken relative to that input.

The measured frequency-response plots are stored in `results/figures/`. The measured gain and frequency values are documented in `results/summary.md`.

## 11. Closed-Loop AC Analysis

The OTA was then evaluated in a unity-feedback configuration.

The closed-loop AC response was used to measure:

- Closed-loop DC gain, Af,0
- Closed-loop −3 dB frequency, fp,f

These measured results were compared with the theoretical unity-feedback gain:

**Af,0 = A0 / (1 + βA0)**

For unity feedback, β = 1, giving:

**Af,0 = A0 / (1 + A0)**

The measured closed-loop gain and −3 dB frequency are recorded in `results/summary.md`.

## 12. Transient Analysis and Settling Error

A transient simulation was performed using a +1 mV input step to evaluate the closed-loop response.

The transient waveform was inspected to observe the output transition, overshoot, and final steady-state value.

The ideal settling error was calculated from the open-loop DC gain:

**εideal = 1 / (1 + A0)**

Using A0 = 80.528:

**εideal ≈ 1 / (1 + 80.528) ≈ 0.0122**

The actual settling error was calculated from the simulated input and output changes between the initial and final measurement times. The report obtained:

**εactual = 0.011**

The relative settling error was then calculated as:

**Relative settling error = (εideal − εactual) / εideal**

Using the reported values:

**Relative settling error = (0.0122 − 0.011) / 0.011 = 0.1091**

The transient response plot is stored in `results/figures/closed_loop_transient.png`.

## 13. Static DC Power Consumption

The total static DC power was calculated using the supply voltage and the currents drawn from the supply:

**PDC = VDD × (I5 + I6)**

Using the simulated currents reported for M5 and M6:

**PDC = 0.8 × (6.819 + 5) µA**

Therefore:

**PDC ≈ 9.4552 µW**

This value documents the static power consumption of the final simulated design.

## 14. Summary

The OTA was sized using transistor characterization curves and first-order design estimates, followed by simulation-based verification.

The methodology considered the trade-offs between transconductance, intrinsic gain, output resistance, voltage headroom, bandwidth, and static power consumption.

The final transistor dimensions, simulated operating points, measured frequency-response characteristics, closed-loop results, and transient settling error are documented in `results/summary.md`.

The corresponding schematics and simulation plots are available in the `schematics/` and `results/figures/` directories.
