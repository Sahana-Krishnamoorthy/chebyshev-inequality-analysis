# chebyshev-inequality-analysis

This project analyzes atmospheric carbon monoxide (CO) concentration data using **Chebyshev's Inequality** to understand data dispersion without assuming a normal distribution.

## 📊 Dataset

ATom: Observed and GEOS-5 Simulated CO Concentrations with Tagged Tracers for ATom-1
The dataset was obtained from [NASA Earth Data website](https://earthdata.nasa.gov/)

### Dataset Description
This dataset provides carbon monoxide (CO) observations at 10-second intervals from the Atmospheric Tomography Mission (ATom-1) flights conducted in 2016. It also includes simulated CO concentrations from the Goddard Earth Observing System version 5 (GEOS-5) model, matched to the same locations along the ATom flight tracks. The ATom mission is a NASA Earth Venture Suborbital-2 mission aimed at studying the impact of human-produced air pollution on greenhouse gases and chemically reactive gases in the atmosphere.

The observations were collected using the Quantum Cascade Laser System (QCLS), a high-frequency laser spectroscopy instrument for in situ atmospheric gas sampling. The dataset contains both observed CO data and simulated tagged-CO tracer concentrations, which represent contributions from specific regional sources. This data helps inform future atmospheric modeling experiments and contributes to creating an observation-based chemical climatology of important atmospheric constituents and their reactivity in the remote troposphere.

### Columns Description
- **time**: Time in seconds since the start of the measurement.
- **Lat (Latitude)**: The latitude coordinate where the measurement was taken.
- **Lon (Longitude)**: The longitude coordinate where the measurement was taken.
- **Pressure**: Atmospheric pressure in hPa (hectopascals) at the measurement point.
- **QCLS_CO**: Observed CO concentration in parts per billion (ppb) from the Quantum Cascade Laser System (QCLS).
- **GEOS_CO**: Simulated CO concentration from the GEOS-5 model at the same location.
- **CO_bbGlobal**: Simulated CO from global biomass burning sources.
- **CO_bbNAm**: Simulated CO from North American biomass burning.
- **CO_bbSAm**: Simulated CO from South American biomass burning.
- **CO_bbAfrica**: Simulated CO from African biomass burning.
- **CO_bbEuras**: Simulated CO from Eurasian biomass burning.
- **CO_nbGlobal**: Simulated CO from global non-biomass burning sources (e.g., fossil fuels, industry).
- **CO_nbAsia**: Simulated CO from Asian non-biomass sources.
- **CO_nbNam**: Simulated CO from North American non-biomass sources.
- **CO_nbEuro**: Simulated CO from European non-biomass sources.

### Purpose
This dataset enables a direct comparison of observed and simulated CO concentrations. It helps:
- Inform future atmospheric modeling experiments.
- Understand the contributions of various regional and global sources to atmospheric CO levels.
- Create an observation-based chemical climatology of critical atmospheric constituents.

### Instrumentation
The dataset was collected using the Quantum Cascade Laser System (QCLS), a high-precision laser spectroscopy instrument for in situ atmospheric gas sampling.

### ATom Mission
The Atmospheric Tomography Mission (ATom) is a NASA Earth Venture Suborbital-2 mission that investigates:
- The impact of human-produced air pollution on greenhouse gases.
- The reactivity of chemically important gases in the atmosphere.

The ATom-1 campaign specifically aimed to collect data from various atmospheric regions to understand the global distribution and sources of atmospheric constituents.


## 🔍 Analysis Overview

1. **Data Merging:** Combined 10 datasets into a single DataFrame.  
2. **Distribution Check:** Verified non-normality using:
   - **Skewness:** 2.1173 → Right-skewed  
   - **Kurtosis:** 8.0638 → Heavy tails  
   - **Shapiro-Wilk Test:** p-value = 0.0000 → Not normal  
   - **D'Agostino and Pearson's Test:** p-value = 0.0000 → Not normal  
3. **Chebyshev's Inequality Validation:**  
   - Proportions within standard deviations were compared with Chebyshev's bounds.

### 📈 Results Summary

| Standard Deviation (k) | Proportion of Data | Chebyshev's Bound |
|------------------------|-------------------|-------------------|
| 1                      | 0.8298            | Not Defined       |
| √2 ≈ 1.41              | 0.9082            | 0.5000           |
| 2                      | 0.9588            | 0.7500           |
| 3                      | 0.9806            | 0.8889           |

## 🤔 Why This Matters

Chebyshev's Inequality applies to **all distributions**, making it vital for datasets like this where normality cannot be assumed. This ensures more **reliable insights** about data spread, even with outliers.



