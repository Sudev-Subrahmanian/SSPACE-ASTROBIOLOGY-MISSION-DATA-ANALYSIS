# Absorbance Growth Analysis Using Cumulative Absorbance and Derivative Trends

## Overview

This project analyzes time-dependent absorbance measurements collected over multiple experimental runs. The script processes raw absorbance data, smooths measurement noise, computes cumulative absorbance trends, and studies the relationship between cumulative absorbance and its rate of change.

The primary objective is to identify growth dynamics and transition regions by examining the derivative of cumulative absorbance with respect to time and fitting linear models to selected time windows.

## Features

* Converts timestamped absorbance measurements into elapsed time.
* Interpolates irregularly sampled data onto a uniform time grid.
* Applies moving-average smoothing to reduce noise.
* Computes cumulative absorbance evolution.
* Calculates the derivative of cumulative absorbance using numerical gradients.
* Generates annotated derivative-vs-cumulative-absorbance plots.
* Performs linear regression on user-defined time intervals.
* Visualizes fitted trends and reports slope/intercept values.


## Methodology

### 1. Time Conversion

Experimental timestamps are converted into minutes elapsed from the first measurement:
This creates a common time axis for analysis.

### 2. Interpolation
Since measurements are not equally spaced in time, linear interpolation is used to generate a regular time grid.

### 3. Smoothing

A moving-average filter is applied, where (N) is the window size.

### 4. Cumulative Absorbance

The cumulative absorbance is calculated as a running average
This helps reveal long-term growth behavior while suppressing short-term fluctuations.

### 5. Derivative Calculation

The rate of change of cumulative absorbance is obtained using numerical differentiation:
using NumPy's gradient function.

### 6. Linear Regression

Selected time regions are analyzed using linear regressio
The slope provides insight into growth kinetics within the selected interval

## Dependencies

Install the required packages:

```bash
pip install numpy matplotlib pandas scipy
```

Required libraries:

* NumPy
* Matplotlib
* Pandas
* SciPy

---

## Input Format

Data is provided as a Python dictionary:

```python
data = {
    "Date": [
        ("HH:MM", absorbance),
        ("HH:MM", absorbance),
        ...
    ]
}
```

Example:

```python
data = {
    "6/11/24": [
        ("10:55", 0.092),
        ("11:40", 0.096),
        ("12:16", 0.098)
    ]
}
```

---

## Output

The notebook generates:

1. Derivative vs cumulative absorbance scatter plots.
2. Time annotations for each data point.
3. Linear regression fits for specified time windows.
4. Slope and intercept values displayed on plots.


Developed for exploratory analysis of absorbance-growth experiments using cumulative trend and derivative-based characterization.
