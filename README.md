# Introduction to Basic Signal Processing for Neurotechnology

## Table of Contents
1. [Introduction to Signal Processing](#introduction-to-signal-processing)
2. [Fundamentals of Signals and Systems](#fundamentals-of-signals-and-systems)
3. [Fourier Transform](#fourier-transform)
4. [Convolution](#convolution)
5. [Filters](#filters)
6. [Sampling and Quantization](#sampling-and-quantization)
7. [Time-Frequency Analysis](#time-frequency-analysis)
8. [Practical Applications and Tools](#practical-applications-and-tools)
9. [Additional Resources](#additional-resources)
10. [Hands-On Exercise Example](#hands-on-exercise-example)

---

## 1. Introduction to Signal Processing

### What is Signal Processing?
Signal processing involves the analysis, interpretation, and manipulation of signals. Signals are functions that convey information about phenomena. In neurotechnology, signal processing is crucial for interpreting neural signals such as EEG (electroencephalography) and MEG (magnetoencephalography).

### Types of Signals
- **Continuous Signals**: Defined for all time (e.g., analog signals).
- **Discrete Signals**: Defined at discrete time intervals (e.g., digital signals).

**Figure 1: Continuous and Discrete Signals**

---

## 2. Fundamentals of Signals and Systems

### Signal Characteristics
- **Amplitude**: The strength or magnitude of the signal.
- **Frequency**: How often the signal oscillates in a unit time.
- **Phase**: The position of a point in time on a waveform cycle.
- **Periodic Signals**: Repeat after a fixed time period $T$.
- **Aperiodic Signals**: Do not repeat over time.

### Basic System Properties
- **Linearity**: System output is directly proportional to input.
- **Time-Invariance**: System properties do not change over time.
- **Causality**: Output depends only on present and past inputs.
- **Stability**: Bounded input leads to bounded output.

---

## 3. Fourier Transform

### Concept of Frequency Domain
Signals can be represented in both time and frequency domains. The frequency domain representation provides insight into the signal's spectral content.

**Figure 2: Time and Frequency Domain Representations**

### Continuous Fourier Transform (CFT)
The Fourier Transform of a continuous signal $x(t)$ is given by:

$$
X(f) = \int_{-\infty}^{\infty} x(t) e^{-j 2 \pi f t} dt
$$

Where:
- $X(f)$: Frequency domain representation.
- $f$: Frequency variable.

### Discrete Fourier Transform (DFT) and Fast Fourier Transform (FFT)
For discrete signals, the DFT is defined as:

$$
X[k] = \sum_{n=0}^{N-1} x[n] e^{-j \frac{2 \pi k n}{N}}
$$

The FFT is an efficient algorithm to compute the DFT.

### Applications in Neurotechnology
- **Analyzing Brain Rhythms**: Identifying alpha (8–12 Hz), beta (13–30 Hz), gamma (>30 Hz) waves.
- **Frequency Filtering**: Removing noise components from EEG data.

---

## 4. Convolution

### Definition and Mathematical Representation
- **Continuous Signals**:  
  $$
  y(t) = (x * h)(t) = \int_{-\infty}^{\infty} x(\tau) h(t - \tau) d\tau
  $$
- **Discrete Signals**:  
  $$
  y[n] = (x * h)[n] = \sum_{k=-\infty}^{\infty} x[k] h[n - k]
  $$

### Properties of Convolution
- **Commutative**: $x * h = h * x$
- **Associative**: $x * (h * g) = (x * h) * g$
- **Distributive**: $x * (h + g) = x * h + x * g$

### Convolution Theorem
Convolution in the time domain equals multiplication in the frequency domain:

$$
x(t) * h(t) \xleftrightarrow{\mathcal{F}} X(f) \cdot H(f)
$$

### Applications
- **Signal Filtering**: Applying filters by convolving the signal with the filter's impulse response.
- **System Analysis**: Understanding how systems modify input signals.

---

## 5. Filters

### Types of Filters
- **Low-Pass Filter**: Allows frequencies below a cutoff frequency.
- **High-Pass Filter**: Allows frequencies above a cutoff frequency.
- **Band-Pass Filter**: Allows frequencies within a specific range.
- **Band-Stop Filter**: Blocks frequencies within a specific range.

**Figure 3: Frequency Responses of Different Filters**

### Filter Design
- **Finite Impulse Response (FIR)**: Impulse response settles to zero in finite time.
- **Infinite Impulse Response (IIR)**: Impulse response continues indefinitely.

#### Common Filter Types:
- **Butterworth**: Maximally flat frequency response.
- **Chebyshev**: Sharper cutoff but with ripples in the passband or stopband.
- **Elliptic**: Steepest cutoff but with ripples in both passband and stopband.

### Digital Filtering Techniques
- Implement filters using software algorithms.
- Consider real-time processing requirements.

### Applications in Neurotechnology
- **Noise Reduction**: Remove unwanted noise from neural recordings.
- **Artifact Removal**: Eliminate artifacts like eye blinks or muscle movements from EEG.

---

## 6. Sampling and Quantization

### Nyquist-Shannon Sampling Theorem
To prevent aliasing, the sampling frequency $f_s$ must be at least twice the maximum frequency $f_{\text{max}}$ of the signal:

$$
f_s \geq 2f_{\text{max}}
$$

**Figure 4: Demonstration of Aliasing**

### Analog-to-Digital Conversion
- **Quantization**: Mapping continuous amplitude values to discrete levels.
- **Quantization Error**: Difference between actual analog value and quantized value.

---

## 7. Time-Frequency Analysis

### Short-Time Fourier Transform (STFT)
Used for non-stationary signals by applying the Fourier Transform over short time windows:

$$
STFT\{x(t)\} = X(t, f) = \int_{-\infty}^{\infty} x(\tau) w(\tau - t) e^{-j 2 \pi f \tau} d\tau
$$

Where $w(t)$ is a window function.

### Wavelet Transform
Provides multi-resolution analysis by decomposing signals into scaled and shifted versions of a mother wavelet.

---

## 8. Practical Applications and Tools

### Software for Signal Processing
- **MATLAB**: Powerful tool with extensive signal processing libraries.
- **Python**:
  - **NumPy**: Fundamental package for numerical computations.
  - **SciPy**: Additional signal processing functions.
  - **Matplotlib**: Plotting library for visualizations.

### Hands-on Projects
- **Processing Neural Data**: Apply filters to real EEG data.
- **Building Filters**: Design and implement digital filters.

---

## 9. Additional Resources

- **Textbooks**:
  - *Signals and Systems* by Alan V. Oppenheim and Alan S. Willsky.
  - *Understanding Digital Signal Processing* by Richard G. Lyons.
- **Online Tutorials**:
  - MATLAB and Python official tutorials.
  - Khan Academy's videos on Fourier Transform and convolution.

---

## 10. Hands-On Exercise Example

### Objective
Filter out 60 Hz power line noise from an EEG signal.

### Steps

#### 1. Load Sample EEG Data
Use a dataset containing EEG recordings.

```python
import numpy as np
import matplotlib.pyplot as plt
from scipy import signal

eeg_data = np.load('eeg_sample.npy')
fs = 256  # Sampling frequency in Hz
```

(cont)
