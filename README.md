# Pipeline Leak Detection

A Python simulation of oil pipeline leak detection using flow mass balance (inlet flow minus outlet flow). Developed as a course project in Automation Engineering to study how pipeline leaks affect flow measurements and how simple detection methods can identify them.

## What This Project Does

- Simulates a 10 km oil pipeline using the Darcy–Weisbach pressure drop equation with time-varying flow.
- Adds simulated Gaussian sensor noise and introduces a leak at t = 500 s.
- Compares two causal detection methods: Simple Threshold and Moving Average.
- Evaluates detection performance through a 100-run Monte Carlo simulation using different random seeds.
- Measures detection rate, false alarm rate, and detection delay.

## Results

### Main Result (5% Leak, 100 Runs)

Moving Average filter, window = 10, threshold = 0.005 m³/s:

| Performance Metric | Result |
|---|---:|
| Average Detection Rate | 98.41% |
| Average False Alarm Rate | 0.01% |
| Average Detection Delay | 6.4 seconds |
| Missed Leaks | 0 of 100 runs |

### Effect of Leak Size

Results using the same Moving Average detector, with 100 runs for each leak size:

| Leak Size | Detection Rate | False Alarm Rate | Mean Delay (s) |
|---|---:|---:|---:|
| 1% | 0.0% | 0.01% | Not detected |
| 2% | 1.3% | 0.01% | Not reliable |
| 3% | 28.7% | 0.01% | 20.7 |
| 5% | 98.4% | 0.01% | 6.4 |
| 10% | 99.4% | 0.01% | 3.0 |

With the selected threshold, leaks smaller than approximately 3% of the flow are not reliably detected.

The leak-related flow imbalance is approximately 0.15 m³/s × leak size. Therefore, a 3% leak produces an imbalance of about 0.0045 m³/s, which is slightly below the 0.005 m³/s detection threshold.

A lower threshold may improve small-leak detection but can also increase false alarms.

### Simple Threshold vs. Moving Average

A single simulation run (seed 42) demonstrates the effect of changing the threshold in the Simple Threshold method:

| Threshold (m³/s) | Detection Rate | False Alarm Rate |
|---|---:|---:|
| 0.004 | 87.6% | 6.4% |
| 0.006 | 69.2% | 1.8% |
| 0.008 | 42.8% | 0.2% |
| 0.010 | 20.6% | 0.0% |

Lower thresholds increase leak sensitivity but also increase false alarms.

The Moving Average method reduces measurement noise using a window of 10 readings. This improves detection performance while introducing a small detection delay.

## Scope

- Simulation-based study using a simplified pipeline model with a constant friction factor.
- Pipeline pressure drop is modeled using the Darcy–Weisbach equation.
- Leak detection is based on flow mass balance only.
- Simulation parameters are typical approximate values and are not taken from an actual pipeline.

## Files

- `pipeline_leak_detection.ipynb` — Contains the simulation code, detection methods, Monte Carlo evaluation, and result plots.

## About

A Python-based course project in Automation Engineering focused on understanding oil pipeline leak detection through hydraulic simulation, flow mass balance, and statistical detection methods.

**Author:** Md. Ifat Hassan
