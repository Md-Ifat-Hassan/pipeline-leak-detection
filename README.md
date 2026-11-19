# Pipeline Leak Detection

A Python simulation of oil pipeline leak detection using flow mass balance (inlet flow minus outlet flow).
Built as a course project in automation engineering to learn how a leak shows up in flow data and how well simple detectors can catch it.

## What this project does

- Simulates a 10 km oil pipeline using the Darcy-Weisbach pressure drop equation with time-varying flow.
- Adds simulated Gaussian sensor noise and injects a leak at t = 500 s.
- Compares two causal detectors (they use only past and current readings): a simple threshold and a moving average.
- Evaluates detection performance with a 100-run Monte Carlo simulation (a different random seed for each run), measuring detection rate, false alarm rate and detection delay.

## Results

### Main result (5% leak, 100 runs)

Moving average filter, window = 10, threshold = 0.005 m³/s:

- Average detection rate: 98.41%
- Average false alarm rate: 0.01%
- Average detection delay: 6.4 seconds
- Missed leaks: 0 of 100 runs

### Effect of leak size (same detector, 100 runs each)

| Leak size | Detection rate | False alarm rate | Mean delay (s) |
|---|---|---|---|
| 1% | 0.0% | 0.01% | not detected |
| 2% | 1.3% | 0.01% | not reliable |
| 3% | 28.7% | 0.01% | 20.7 |
| 5% | 98.4% | 0.01% | 6.4 |
| 10% | 99.4% | 0.01% | 3.0 |

With this threshold, leaks smaller than about 3% of the flow are not reliably detected.
The leak's flow imbalance is roughly 0.15 m³/s × leak size, so a 3% leak (about 0.0045 m³/s) sits just below the 0.005 m³/s threshold.
A lower threshold would detect smaller leaks but would increase false alarms.

### Simple threshold vs. moving average

A single run (seed 42) with the simple threshold shows the trade-off clearly:

| Threshold (m³/s) | Detection rate | False alarm rate |
|---|---|---|
| 0.004 | 87.6% | 6.4% |
| 0.006 | 69.2% | 1.8% |
| 0.008 | 42.8% | 0.2% |
| 0.010 | 20.6% | 0.0% |

Lowering the threshold catches more of the leak but raises false alarms. Averaging over a window of 10 readings
reduces the noise, so the moving average reaches a high detection rate with almost no false alarms,
at the cost of a few seconds of delay.

## Scope

- Simulation-based study using a simplified pipeline model (constant friction factor).
- Detection uses flow mass balance only.
- Parameters are typical approximate values, not taken from a real pipeline.

## Files

- `pipeline_leak_detection.ipynb`: simulation code, evaluation and plots.
