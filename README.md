# 1. Executive Summary: Why Narrative Finance?

While traditional financial statement-driven fundamental analysis excels at explaining historical performance, it faces structural limitations when attempting to immediately capture capital shifts and sector rotations driven by technological paradigm shifts or collective market sentiment.

Beyond basic sentiment analysis or news mining, **BIZNEYS Narrative Finance** identifies and quantifies the four foundational narrative factors shaping the modern economic system. This framework offers a multi-horizon quantitative approach, enabling long-term capital allocation, sector synchronization tracking, and short-term trading opportunity detection.

---

# 2. Core Principles: Objective & Ex-Ante Classification

To ensure transparency and eliminate subjective bias, the system operates under strict analytical principles:

* **Ex-Ante Mapping Framework**: Relies on a Standard Industrial Classification (SIC) mapping system without relying on external data biases or arbitrary post-hoc LLM interpretations.
* **Strict Point-in-Time (PiT) Compliance**: Point-in-Time SEC EDGAR Database eliminates survival and look-ahead bias by systematically reconstructing historical market populations from raw public filings at each exact point in time.
* **Noise Reduction**: Systematically excludes entities with overly narrow or excessively broad business scopes, as well as sectors lacking clear representation among the 4 core narratives (e.g., financial institutions, holding companies, real estate).

---

# 3. The 4 Structural Narratives

Reconstructing traditional equity classifications (growth, value, defensive, etc.) through the dual axes of **Technological Innovation** and **Human-Centric Consumption** within the context of the Singularity era:

| Narrative Factor | Definition & Scope | Primary Economic Intuition |
| :--- | :--- | :--- |
| **Singularity Core (SC)** | AI, Semiconductors, Compute Infrastructure, Cloud Foundations | **Pure Compute Engine**: Intensive computing power and technological infrastructure driving the Singularity. |
| **Augmented Humanity (AH)** | Novel Biopharma, Precision Medical Devices, Robotics, SaaS, EdTech | **Interface & Productivity**: Solutions expanding human physical/intellectual capabilities and maximizing productivity. |
| **Humanity (H)** | Media & Content, Fashion, Offline Retail, Leisure, Luxury Goods | **Human Experience**: Goods and services shaping human life experiences, cultural consumption, and emotional value. |
| **Foundation (F)** | Energy, Basic Materials, Civil Infrastructure, Logistics, Public Utilities | **Physical Baseline**: Essential physical assets required for societal and economic systems to function. |

---

# 4. Narrative Indices & Synchronization Architecture

A dedicated index architecture designed to systematically construct factor indices and measure market-wide narrative dispersion:

## 1) Universe Hierarchy Pipeline
* **Point-in-Time SEC EDGAR Database**: The raw, Point-in-Time (PiT) managed universe of all corporate filings and historical entities.
* **Asset Universe**: All tradable assets (Equities, Fixed Income, ETFs, etc.) listed across major U.S. exchanges (NYSE, NASDAQ, NYSE American).
* **Research Universe**: A filtered universe strictly restricted to U.S. domestic common equities.
* **Narrative Research Universe**: Equities from the Research Universe mapped strictly to one of the 4 core narratives via SIC code classifications.
* **Narrative Index Universe**: The final constituent universe formed by filtering the top 30 securities per factor based on 63-day Average Daily Trading Volume ($\text{ADTV}_{63}$, Dollar Volume), rebalanced quarterly.

## 2) Indices & Synchronization Analytics
* **Narrative Indices Calculation**: Daily continuous equal-weighted indices constructed from the Narrative Index Universe (Base Date: Year 2000 = 1,000pt).
* **Narrative Correlations**: Tracks the 6 pairwise rolling correlations across the 4 core narrative indices without removing multicollinearity, preserving raw macro factor interactions.
* **Narrative Synchronization Index (NSI)**: Applies Principal Component Analysis (PCA) to the 6 pairwise correlation dynamics to evaluate capital concentration and structural market regime transitions.

---

# 5. Narrative Asset Pricing Model (NAPM)

A core quantitative asset pricing framework that decomposes individual asset returns, prices, and volatility into narrative-driven and firm-specific idiosyncratic components.

## 1) Core Concepts & Terminology

* **Narrative Exposure ($\beta_{\text{SC}}, \beta_{\text{AH}}, \beta_{\text{H}}, \beta_{\text{F}}$)**: Asset sensitivity to each of the 4 narrative factor returns, estimated via Ordinary Least Squares (OLS) regression.
* **Alpha ($\alpha$) & Residual ($e_{i,t}$)**: Unexplained asset-specific return components representing corporate fundamentals and firm-specific events.
* **Uniform 63-Day Rolling Window ($W = 63$)**: All rolling analytics, volatility estimations, and valuation metrics strictly adhere to a standardized 63-trading-day window (~1 quarter / 3 months).

## 2) Mathematical Formulation

**Return Decomposition (Daily Log Returns)**  
An asset's daily log return ($r_{i,t}$) is decomposed into narrative-driven returns and idiosyncratic returns (alpha + residual):

$$r_{i,t} = \underbrace{\sum_{k \in \{\text{SC, AH, H, F}\}} \beta_{i,k} \cdot f_{k,t}}_{\text{Narrative Return}} + \underbrace{(\alpha_i + e_{i,t})}_{\text{Idiosyncratic Return}}$$

**Continuous Cumulative Compounding (Price Decomposition)**  
Asset price is expressed as a multiplicative combination of Narrative Price and Idiosyncratic Price ($P_{\text{Obs}} = P_{\text{Narrative}} \times P_{\text{Idio}}$). Reconstructed via continuous compounding from inception ($t_0$):

$$\ln P_{\text{Obs}, t} = \ln P_{t_0} + \sum_{\tau=t_0+1}^{t} r_{i,\tau}$$

$$\ln P_{\text{Narrative}, t} = \ln P_{t_0} + \sum_{\tau=t_0+1}^{t} \left( \sum_{k \in \{\text{SC, AH, H, F}\}} \beta_{i,k,\tau} \cdot f_{k,\tau} \right)$$

$$\ln P_{\text{Obs}, t} = \ln P_{\text{Narrative}, t} + \ln P_{\text{Idio}, t}$$

The idiosyncratic log price ($\ln P_{\text{Idio}, t}$) is derived directly as the difference between total observed log price and narrative log price:

$$\ln P_{\text{Idio}, t} = \ln P_{\text{Obs}, t} - \ln P_{\text{Narrative}, t}$$

**Volatility Decomposition**  
Total risk is decomposed into narrative risk (derived via factor covariance matrix and beta vector) and firm-specific idiosyncratic volatility:

$$\text{Total Volatility} = \text{Narrative Volatility} + \text{Idiosyncratic Volatility}$$

**Narrative Premium (NP)**  
Evaluates whether an asset is overextended or undervalued relative to its narrative baseline. Calculated over a rolling 63-day window using Geometric Brownian Motion (GBM) volatility scaling ($\times \sqrt{W}$):

$$\text{NP}_t = \frac{\ln P_{\text{Obs}, t} - \ln P_{\text{Narrative}, t}}{\text{Total Vol}_t \times \sqrt{W}} = \frac{\ln P_{\text{Idio}, t}}{\text{Total Vol}_t \times \sqrt{W}} \quad (W = 63)$$

---

# 6. How to Use: Terminal Analytics Application

Practical application strategies for BIZNEYS Quant Terminal metrics:

* **Narrative Exposure Profile Analysis**: Quantify whether a stock aligns with AI technology momentum ($\beta_{\text{SC}}$) or consumer demand recoveries ($\beta_{\text{H}}$) to adjust portfolio factor weights.
* **Return & Price Decomposition**: Disambiguate whether recent stock price movements stem from broader narrative tailwinds ($\text{Narrative Return}$) or company-specific fundamentals ($\text{Idiosyncratic Return}$).
* **Narrative Premium Signals**: Identify overextended (High NP) or underperforming (Low NP) assets relative to their underlying narrative trend to locate short-term swing and pair-trading setups.
* **Narrative Synchronization Index (NSI) Application**: Monitor broader market regimes using NSI. High synchronization signals uniform macro-driven market moves where factor exposure strategies dominate, whereas low synchronization indicates a stock-picker's market where idiosyncratic driver analysis takes priority.

---

## Citation

If you use this methodology or quantitative framework in your research, please cite as:

```text
BIZNEYS Narrative Finance Research. (2026). Narrative Asset Pricing Model (NAPM) Framework.
