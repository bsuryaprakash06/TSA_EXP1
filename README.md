# Time Series Plotting and Stationarity Analysis with Augmented Dickey-Fuller Test

A comprehensive statistical implementation demonstrating time series ingestion, resampling, interpolation, and stationarity diagnostics using the Augmented Dickey-Fuller (ADF) test across financial and environmental datasets.

---

## Objective

Evaluate the behavior and stationarity properties of continuous time series data. The implementation covers time-based indexing, frequency resampling, and the transformation of non-stationary series into weak stationary processes through regular and seasonal differencing and logarithmic variance stabilization.

---

## Datasets Utilized

This experiment examines two distinct empirical time series exhibiting contrasting dynamics:

1. **Adani Ports Equity Closing Prices (`ADANIPORTS-selected-columns.csv`)**:
   - **Domain**: Financial Econometrics (National Stock Exchange of India - NSE).
   - **Frequency / Span**: Daily trading records resampled to Business Days (`B`).
   - **Characteristics**: Random-walk stochastic trends with localized volatility clustering. Missing weekend and holiday records handled via time-based linear interpolation.
   - **Seasonality Period**: 252 trading days per calendar year.

2. **Daily Minimum Temperatures in Melbourne (`daily-min-temperatures.csv`)**:
   - **Domain**: Climatology / Meteorology.
   - **Frequency / Span**: Daily records over a 10-year span (1981–1990) in Melbourne, Australia.
   - **Characteristics**: Deterministic annual periodicity and cyclic variation.
   - **Seasonality Period**: 365 calendar days.

---

## Methodology & Mathematical Formulation

### 1. Resampling and Interpolation
Non-uniform timestamps are normalized to uniform business-day frequency:
```python
df_resampled = df['Close'].resample('B').last()
df_resampled = df_resampled.interpolate(method='time', limit_area='inside')
```

### 2. Transformations for Stationarity
- **First-Order Regular Differencing**:
  $$\Delta y_t = y_t - y_{t-1}$$
- **Seasonal Differencing** ($s = 252$ or $s = 365$):
  $$\Delta_s y_t = y_t - y_{t-s}$$
- **Logarithmic Variance Stabilization**:
  $$z_t = \ln(y_t)$$
- **Combined Regular and Seasonal Log-Differencing**:
  $$w_t = \Delta \Delta_s \ln(y_t) = (\ln y_t - \ln y_{t-1}) - (\ln y_{t-s} - \ln y_{t-s-1})$$

### 3. Augmented Dickey-Fuller (ADF) Unit Root Test
The ADF test models the series as:
$$\Delta y_t = \alpha + \beta t + \gamma y_{t-1} + \sum_{i=1}^p \delta_i \Delta y_{t-i} + \epsilon_t$$
- **Null Hypothesis ($H_0$)**: $\gamma = 0$ (Unit root present; series is non-stationary).
- **Alternative Hypothesis ($H_1$)**: $\gamma < 0$ (Unit root absent; series is stationary).
- Rejection threshold: $p \le 0.05$.

---

## Results & Visualizations

### Sample Ingestion
<img width="109" height="166" alt="Sample Data Head" src="https://github.com/user-attachments/assets/7ae782b1-edab-4b4c-b91c-fd2a57b7519e" />

### Daily Minimum Temperatures Plot
<img width="1151" height="470" alt="Melbourne Temperature Time Series" src="https://github.com/user-attachments/assets/290a5ca9-f4d1-4423-a1fc-1e9efd2d0ade" />

---

## License

This project is licensed under the GNU General Public License v3.0. See the [LICENSE](LICENSE) file for details.
