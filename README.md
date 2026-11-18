# Pipeline Leak Detection

A Python simulation of oil pipeline leak detection.

## What this project does
- Simulates a pipeline (Darcy-Weisbach pressure drop)
- Adds sensor noise and a leak
- Tests two detectors: simple threshold and moving average

## Results so far
- Simple threshold: detection and false alarms trade off
  (0.004: 87.6% / 6.4%, 0.010: 20.6% / 0.0%)
- Moving average (window 10, threshold 0.005): about 99% detection, 0% false alarms

## Files
- pipeline_leak_detection.ipynb: full code and graphs

## Limitations
- Simple model, approximate parameters
- Single simulated run so far

## Status
Work in progress.

