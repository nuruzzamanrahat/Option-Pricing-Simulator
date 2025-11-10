# 📉 Option Pricing Simulator: Monte Carlo vs. Black-Scholes

## Overview

This application is a **European Option Pricing Simulator** built using a single-page HTML/JavaScript file.  
It allows users to estimate the fair price of both **European Call** and **Put options** using two powerful financial techniques:

- **Monte Carlo Simulation** (using the Geometric Brownian Motion model for stock paths).  
- **Black-Scholes Formula** (for an analytical benchmark).

The tool helps visualize the distribution of potential future stock prices and quantifies the accuracy of the Monte Carlo estimate via **standard error** and **confidence intervals**.

---

## ✨ Features

- **Dual Pricing:** Calculates both Monte Carlo (MC) and Black-Scholes (BS) prices for European Call and Put options.  
- **Geometric Brownian Motion (GBM):** Simulates thousands of terminal stock prices ($S_T$) using GBM, which is the underlying process assumed by the Black-Scholes model.  
- **Error Metrics:** Provides crucial metrics for validating the Monte Carlo result:
  - **Standard Error (SE):** Measures the statistical precision of the MC estimate.  
  - **95% Confidence Interval:** The range where the true theoretical price is expected to fall 95% of the time.  
  - **Pricing Error:** The absolute and percentage difference between the MC and BS prices.  
- **Visualization:** Generates a real-time histogram of the simulated terminal stock prices, colored to instantly show In-the-Money (ITM) and Out-of-the-Money (OTM) outcomes relative to the strike price ($K$).  
- **Responsive Design:** Styled using **Tailwind CSS** for a clean, professional, and mobile-friendly interface.

---

## 🛠️ Usage

This is a **self-contained HTML file**.  
No installation or complex setup is required — just open the file in any modern web browser.

---

### Model Parameters (Inputs)

| **Parameter** | **ID** | **Description** | **Default** |
|----------------|--------|-----------------|-------------|
| **Stock Price** | `S0` | Current stock price ($S_0$). | 100 |
| **Strike** | `K` | Option strike price ($K$). | 100 |
| **Time to Maturity** | `T` | Time until expiration, in years. | 1.0 |
| **Volatility** | `sigma` | Annualized volatility of the stock ($\sigma$). | 0.20 |
| **Risk-Free Rate** | `r` | Annualized risk-free interest rate ($r$). | 0.05 |
| **Simulations** | `M` | Number of simulation paths to run. Higher values increase accuracy but take longer. | 50,000 |

---

### Steps to Run

1. Enter or adjust the desired financial parameters in the **Model Parameters** section.  
2. Click either **Simulate Call Price** or **Simulate Put Price** button.  
3. The progress bar will show the simulation running.  
4. The results section will update with the calculated prices and metrics, and the chart will display the $S_T$ distribution.

---

## 📈 Financial Concepts and Visualization

### Monte Carlo Simulation

The Monte Carlo method estimates the option price by averaging the discounted payoff of a large number of simulated stock price paths.  
The stock price at time $T$ is modeled using the **Geometric Brownian Motion (GBM)** equation:

$$
S_T = S_0 \cdot \exp\left(\left(r - \frac{\sigma^2}{2}\right)T + \sigma \sqrt{T} Z\right)
$$

Where $Z$ is a standard normal random variable generated using the **Box-Muller Transform** within the JavaScript code.

---

### Terminal Price Distribution Chart

The bar chart visualizes the frequency distribution of the simulated terminal stock prices ($S_T$).

- **Red Bars:** Represent outcomes where the option is **Out-of-the-Money (OTM)** (i.e., the payoff is zero).  
  - **Call:** $S_T < K$ (Stock price is below the strike).  
  - **Put:** $S_T > K$ (Stock price is above the strike).  

- **Green Bars:** Represent outcomes where the option is **In-the-Money (ITM)** (i.e., the payoff is positive).  
  - **Call:** $S_T > K$ (Stock price is above the strike).  
  - **Put:** $S_T < K$ (Stock price is below the strike).  

- **Annotations:** Vertical lines mark the **Initial Stock Price ($S_0$)** and the **Strike Price ($K$)**.

---

## 💻 Tech Stack

- **HTML5/CSS3:** Core structure.  
- **Tailwind CSS:** Utility-first framework for all styling and responsive layout.  
- **JavaScript (ES6):** Implements the Box-Muller transform, Monte Carlo simulation logic, and Black-Scholes formula.  
- **Chart.js:** Used for generating the interactive, responsive histogram.  
- **chartjs-plugin-annotation:** Used to draw the vertical lines for $S_0$ and $K$ on the chart.

---
