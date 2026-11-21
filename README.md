# Pipeline Leak Detection

A Python-based simulation study of oil pipeline leak detection using flow mass balance, hydraulic modeling, and statistical detection techniques.

<p align="center">
  **A Course Project in Automation Engineering**
</p>

---

## Overview

This project investigates how flow measurements can be used to identify leaks in an oil pipeline.

A simplified 10 km pipeline is simulated using the Darcy–Weisbach pressure-drop equation with time-varying flow conditions. Artificial sensor noise is introduced, and a leak is injected into the simulation to study how different detection methods respond.

Two causal detection methods are compared:

- Simple Threshold Detection
- Moving Average Detection

The performance of these methods is evaluated through a 100-run Monte Carlo simulation.

## Objectives

- Simulate a simplified oil pipeline system.
- Study flow imbalance caused by pipeline leakage.
- Investigate the effect of Gaussian sensor noise.
- Compare threshold-based and moving-average detection.
- Evaluate detection performance under different leak sizes.
- Analyze detection rate, false alarm rate, and detection delay.

## Methodology

### 1. Pipeline Simulation

The pipeline is modeled with a length of 10 km.

The Darcy–Weisbach equation is used to represent friction-related pressure drop:

\[
\Delta P=f\frac{L}{D}\frac{\rho v^2}{2}
\]

Where:

| Symbol | Description |
|---|---|
| \(\Delta P\) | Pressure drop |
| \(f\) | Darcy friction factor |
| \(L\) | Pipeline length |
| \(D\) | Pipe diameter |
| \(\rho\) | Fluid density |
| \(v\) | Mean fluid velocity |

The simulation uses a simplified hydraulic model with a constant friction factor.

### 2. Leak Simulation

A leak is introduced at:

- Leak start time: 500 seconds
- Main evaluation leak size: 5%

The leak produces an imbalance between inlet and outlet flow measurements.

### 3. Sensor Noise

Gaussian noise is added to the simulated measurements to represent sensor measurement uncertainty.

This allows the detection methods to be evaluated under noisy measurement conditions.

### 4. Leak Detection Methods

**Simple Threshold Detection**

Detects a possible leak when the measured flow imbalance exceeds a predefined threshold.

**Moving Average Detection**

Uses a moving average filter to smooth noisy measurements before applying the detection threshold.

The moving average method helps reduce the effect of random measurement fluctuations.

## Simulation Results

### Main Results: 5% Leak

The following results are reported for the 100-run Monte Carlo evaluation.

| Performance Metric | Result |
|---|---:|
| Average Detection Rate | 98.41% |
| Average False Alarm Rate | 0.01% |
| Average Detection Delay | 6.4 seconds |
| Reported Missed Leaks | 0 of 100 runs |

**Moving Average Configuration:**

- Window size: 10 readings
- Detection threshold: 0.005 m³/s

### Effect of Leak Size

The same moving-average detector is evaluated under different leak sizes.

| Leak Size | Detection Rate | False Alarm Rate | Mean Delay |
|---|---:|---:|---:|
| 1% | 0.0% | 0.01% | Not detected |
| 2% | 1.3% | 0.01% | Not reliable |
| 3% | 28.7% | 0.01% | 20.7 s |
| 5% | 98.4% | 0.01% | 6.4 s |
| 10% | 99.4% | 0.01% | 3.0 s |

### Key Observation

The detection performance strongly depends on leak size.

Smaller leaks produce a weaker flow imbalance, making them more difficult to distinguish from measurement noise.

With the selected threshold, leaks below approximately 3% of the flow are not reliably detected.

This demonstrates an important trade-off between leak sensitivity and false alarm performance.

### Simple Threshold Performance

The following results illustrate the effect of changing the threshold in a single simulation run (seed 42).

| Threshold (m³/s) | Detection Rate | False Alarm Rate |
|---|---:|---:|
| 0.004 | 87.6% | 6.4% |
| 0.006 | 69.2% | 1.8% |
| 0.008 | 42.8% | 0.2% |
| 0.010 | 20.6% | 0.0% |

A lower threshold increases sensitivity but also increases false alarms.

The moving-average method reduces measurement fluctuations and provides a better balance between detection performance and false alarms in the reported simulation.

## Performance Metrics

The project evaluates three main performance indicators:

- **Detection Rate:** Measures how frequently simulated leak events are detected.
- **False Alarm Rate:** Measures how frequently the detector reports a leak when no leak is present.
- **Detection Delay:** Measures the time between leak initiation and detection.

These metrics help assess both the sensitivity and responsiveness of the detection methods.

## Project Structure

```text
pipeline-leak-detection/
│
├── README.md
│
└── pipeline_leak_detection.ipynb
```

### Main File

`pipeline_leak_detection.ipynb`

Contains:
- Pipeline simulation
- Hydraulic calculations
- Sensor noise generation
- Leak injection
- Detection algorithms
- Monte Carlo evaluation
- Result visualization

## Requirements

- Python 3
- Jupyter Notebook
- NumPy
- Matplotlib

Install the commonly used libraries with:

```bash
pip install numpy matplotlib notebook
```

## How to Run

1. Clone the repository:

```bash
git clone https://github.com/Md-Ifat-Hassan/pipeline-leak-detection.git
```

2. Navigate to the project directory:

```bash
cd pipeline-leak-detection
```

3. Install the required libraries.

4. Launch Jupyter Notebook:

```bash
jupyter notebook
```

5. Open `pipeline_leak_detection.ipynb`.

6. Run the notebook cells sequentially to reproduce the simulation and evaluation.

## Limitations

This project is an educational simulation study and does not represent a fully validated industrial leak detection system.

The main limitations include:

1. **Simplified Hydraulic Model:** The simulation uses a constant friction factor and does not represent every hydraulic behavior of a real pipeline.
2. **Synthetic Measurements:** Sensor data are simulated using Gaussian noise rather than collected from an operating pipeline.
3. **Limited Detection Methods:** Only simple threshold and moving-average methods are investigated.
4. **Small Leak Sensitivity:** The selected detection threshold performs poorly for smaller leak sizes.
5. **Simplified Operating Conditions:** Real-world variations in temperature, fluid properties, and operating conditions are not fully represented.
6. **No Real-world Validation:** The reported performance has not been established through field testing.

## Future Work

Possible directions for further investigation include:

- Testing different sensor noise levels and measurement uncertainties.
- Improving detection sensitivity for smaller leaks.
- Evaluating the model under more varied operating conditions.
- Investigating additional statistical and machine-learning detection techniques.
- Validating the simulation using real pipeline measurement data.

These are potential improvements and are not implemented in the current version.

## Conclusion

This project demonstrates how flow mass balance and simple statistical detection techniques can be applied to a simulated oil pipeline leak detection problem.

The Monte Carlo evaluation shows that the moving-average method achieves strong detection performance for the tested 5% leak scenario, while also highlighting the difficulty of detecting smaller leaks.

The results provide an educational foundation for understanding pipeline leak detection, sensor noise, and the trade-off between detection sensitivity and false alarms.

## Author

**Md. Ifat Hassan**

Course Project — Automation Engineering

GitHub: https://github.com/Md-Ifat-Hassan/pipeline-leak-detection
