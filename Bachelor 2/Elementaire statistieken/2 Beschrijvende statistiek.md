## 2.1 Introduction to Descriptive Statistics

- **Purpose**: Summarize and visualize data using numerical measures and graphical representations.
- **Exploratory Data Analysis (EDA)**: Identifies patterns and structures using computer-generated plots (e.g., boxplots, QQ-plots).
- **Population vs. Sample**:
  - **Population**: Complete set of data (e.g., all UN-recognized states).
  - **Sample**: Subset of the population (size $n$) used for analysis. Samples must be representative.

## 2.2 Variable Types

### Qualitative Variables

- **Nominal**: Categories without order (e.g., gender, nationality).
- **Ordinal**: Categories with order but no meaningful arithmetic (e.g., education level, rankings).

### Quantitative Variables

- **Discrete**: Finite/infinite numerical values (e.g., number of children).
- **Continuous**: Measurable numerical values (e.g., height, speed).

## 2.3 Frequency Distributions

### Frequency Tables and Bar Charts

- **Absolute Frequency ($n_j$)**: Count of observations in category $j$.
- **Relative Frequency ($h_j$)**: $h_j = \frac{n_j}{n}$, where $n = \text{total observations}$.
- **Graphical Representations**:
  - **Bar Chart**: Height = frequency.
  - **Pie Chart**: Proportions via angles.

### Histograms

- **Classic Histogram**: Equal bin widths; height = frequency.
- **Density Histogram**: Adjusts for unequal bin widths. Height = $\frac{h_j}{\Delta_j}$ (ensures area = 1).
- **Cumulative Frequency Polygon**: Plots cumulative percentages against class boundaries.

## 2.4 Measures of Central Tendency

### Mean ($\overline{x}$)

- **Ungrouped Data**: $\overline{x} = \frac{1}{n} \sum x_i$.
- **Grouped Data**: $\overline{x} = \frac{1}{n} \sum n_j c_j$, where $c_j = \text{class midpoint}$.

### Median

- **Ungrouped Data**: Middle value (or average of two middle values).
- **Grouped Data**: Linear interpolation using cumulative frequencies:
  $\text{Median} = L + \left(\frac{50\% - F}{f}\right) \times \Delta$,
  where $L$ = lower boundary of median class, $F$ = cumulative frequency before $L$, $f$ = frequency of median class.

### Mode

- **Modus**: Most frequent value (for raw data).
- **Modal Class**: Class with highest frequency (for grouped data).

## 2.5 Measures of Spread

### Variance ($s^2$) and Standard Deviation ($s$)

- **Ungrouped Data**:
  $s^2 = \frac{1}{n-1} \sum (x_i - \overline{x})^2$, $s = \sqrt{s^2}$.
- **Grouped Data**:
  $s^2 = \frac{1}{n-1} \sum n_j (c_j - \overline{x})^2$.

### Interquartile Range (IQR)

- $IQR = Q_3 - Q_1$, where $Q_1 = 25^{th}$ percentile, $Q_3 = 75^{th}$ percentile.

### Median Absolute Deviation (MAD)

- $MAD = \text{median}(|x_i - \text{median}(x)|)$.

## 2.6 Boxplots

- **Components**:
  - **Box**: $Q_1$ to $Q_3$ (length = IQR).
  - **Whiskers**: Extend to non-outlier extremes.
  - **Outliers**: Defined as $< Q_1 - 1.5IQR$ or $> Q_3 + 1.5IQR$.
- **Interpretation**:
  - **Skewness**: Median position within the box.
  - **Tail Heaviness**: Number of outliers.

## 2.7 Covariance and Correlation

### Covariance

- $\text{cov}(x,y) = \frac{1}{n-1} \sum (x_i - \overline{x})(y_i - \overline{y})$.

### Pearson Correlation ($r$)

- $r = \frac{\text{cov}(x,y)}{s_x s_y}$ ($-1 \leq r \leq 1$).

## 2.8 Cross-Tables

- **Purpose**: Analyze relationships between two qualitative variables.
- **Expected Frequencies**:
  $\text{Expected} = \frac{\text{row total} \times \text{column total}}{n}$.
- **Chi-Square Test**: Compares observed vs. expected frequencies (see hypothesis testing).

## 2.9 QQ-Plots

- **Purpose**: Assess if data follows a theoretical distribution (e.g., normality).
- **Method**: Plot empirical quantiles ($\widehat{Q}_n(p)$) vs. theoretical quantiles ($F^{-1}(p)$).
- **Interpretation**:
  - Linear points → Distribution matches.
  - Curved patterns → Transformation needed (e.g., log).

---

## Key Points to Remember

- **Variables**: Qualitative (nominal/ordinal) vs. quantitative (discrete/continuous).
- **Central Tendency**: Mean (sensitive to outliers), median (robust), mode (modal class for grouped data).
- **Spread**: Variance/SD (measure deviation from mean), IQR (robust spread), MAD (median-based).
- **Boxplots**: Show median, IQR, outliers, and skewness.
- **Covariance vs. Correlation**: Covariance is unit-dependent; correlation is standardized ($-1$ to $1$).
- **Cross-Tables**: Use expected frequencies to test independence.
- **QQ-Plots**: Check distributional assumptions; linearity indicates alignment with theoretical distribution.
