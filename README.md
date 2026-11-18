# Pipeline Leak Detection

A Python simulation of oil pipeline leak detection using fluid dynamics and statistical signal processing.

## What This Project Does
- Simulates a 10 km oil pipeline using the **Darcy-Weisbach** pressure drop equation with time-varying flow.
- Adds realistic Gaussian sensor noise and injects a 5% leak at $t = 500\text{s}$.
- Evaluates two causal leak detection methods: **Simple Threshold** and **Moving Average**.
- Validates reliability using a **100-run Monte Carlo simulation** measuring detection rate, false alarm rate, and detection delay.

## Results (100-Run Monte Carlo Average)
Using a causal **Moving Average** filter (`window = 10`, `threshold = 0.005 m³/s`):
- **Average Detection Rate:** 98.41%
- **Average False Alarm Rate:** 0.01%
- **Average Detection Delay:** 6.4 seconds

## Files
- `pipeline_leak_detection.ipynb`: Complete simulation code, statistical evaluation, and visualizations.
