# Pipeline Leak Detection

**Simulation-Based Oil Pipeline Leak Detection Using Flow Mass Balance and Statistical Methods**

<p align="center">
  <b>Automation Engineering Project</b>
</p>

---

## Overview

Pipeline leakage is a major challenge in oil transportation systems. Early leak detection is essential for minimizing product loss, environmental damage, and operational risks.

This project presents a Python-based simulation of a 10 km oil pipeline to investigate leak detection using flow mass balance and statistical techniques.

The system uses the Darcy–Weisbach equation for hydraulic modeling, Gaussian noise to simulate sensor uncertainty, and two detection methods to identify potential pipeline leaks.

## Key Features

- 10 km simulated oil pipeline
- Darcy–Weisbach hydraulic model
- Time-varying flow simulation
- Gaussian sensor noise
- Artificial leak simulation
- Simple Threshold Detection
- Moving Average Detection
- 100-run Monte Carlo evaluation
- Performance comparison across different leak sizes

## Methodology

### 1. Hydraulic Modeling

The Darcy–Weisbach equation is used to estimate friction-related pressure loss:

\[
\Delta P=f\frac{L}{D}\frac{\rho v^2}{2}
\]

### 2. Leak Detection

The detection system uses flow mass balance:

\[
Q_{\text{imbalance}}=Q_{\text{in}}-Q_{\text{out}}
\]

An abnormal flow imbalance indicates a potential leak.

### 3. Detection Algorithms

**Simple Threshold Detection**

Identifies a potential leak when flow imbalance exceeds a predefined threshold.

**Moving Average Detection**

Smooths noisy measurements before applying the detection threshold to improve detection stability.

### 4. Monte Carlo Simulation

A 100-run Monte Carlo simulation is performed to evaluate detection performance under repeated simulated conditions.

## Simulation Results

### Main Performance — 5% Leak

<|placeholder|>

| Performance Metric | Result |
|---|---:|
| Detection Rate | 98.41% |
| False Alarm Rate | 0.01% |
| Detection Delay | 6.4 seconds |
| Reported Missed Leaks | 0 of 100 runs |

### Detection Performance vs. Leak Size

| Leak Size | Detection Rate | False Alarm Rate | Mean Delay |
|---|---:|---:|---:|
| 1% | 0.0% | 0.01% | Not detected |
| 2% | 1.3% | 0.01% | Not reliable |
| 3% | 28.7% | 0.01% | 20.7 s |
| 5% | 98.4% | 0.01% | 6.4 s |
| 10% | 99.4% | 0.01% | 3.0 s |

### Key Findings

- Detection performance improves with increasing leak size.
- Smaller leaks are more difficult to distinguish from sensor noise.
- The moving-average method performs well in the tested 5% leak scenario.
- Detection sensitivity depends strongly on the selected threshold.

## Limitations

- Simplified hydraulic modeling.
- Synthetic sensor measurements instead of real industrial data.
- Limited detection algorithms.
- Reduced sensitivity to smaller leaks.
- Limited representation of real-world operating conditions.
- No experimental validation using an actual pipeline.

## Future Improvements

- Testing under different sensor noise conditions.
- Improving small-leak detection sensitivity.
- Evaluating additional operating conditions.
- Comparing advanced statistical detection techniques.
- Validating results using real pipeline datasets.

## Conclusion

This project demonstrates the application of hydraulic modeling and statistical detection techniques to a simulated oil pipeline leak detection problem.

The results show promising detection performance for larger leak scenarios while highlighting the challenges of detecting smaller leaks under measurement uncertainty.

The study provides a foundation for understanding flow-based pipeline monitoring and statistical leak detection.

---

**Author:** Md. Ifat Hassan

**Field:** Automation Engineering

**Project:** Pipeline Leak Detection
