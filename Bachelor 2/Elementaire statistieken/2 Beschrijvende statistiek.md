## 2.1 Foundations of Descriptive Statistics

Descriptive statistics focuses on summarizing and visually representing data, often by grouping it into classes. Emerging before the computer era, it uses numerical measures (kentallen) and graphical tools to describe datasets. Exploratory Data Analysis (EDA), a more recent approach since the 1970s, leverages computational tools to uncover patterns and structures, such as through QQ-plots and boxplots. These methods are typically applied to samples, which must represent the population to allow generalizable conclusions.

### Sampling and Representativeness

Sampling involves selecting a subset of $n$ observations from a larger population due to practical constraints like time, cost, or destructive testing. A **representative sample** ensures that findings reflect the population, with larger samples ($n$) providing clearer insights but increasing costs. Descriptive statistics and EDA are primarily used on such samples to summarize and explore data.

#### Example: Population vs. Sample

- **Deterministic data** covers entire populations (e.g., all elements in the periodic table or UN-recognized states).
- **Sample data** represents partial observations, like measuring the speed of 300 cars to infer population driving patterns.

## 2.2 Analyzing Frequency Distributions

Frequency analysis examines how outcomes of a **stochastic variable** are distributed within a sample. It addresses questions about data variability, trends, and outliers, using tools like frequency tables and graphical representations to summarize findings. This connects to later sections on central tendency and dispersion, where numerical summaries complement these visual tools.

### Qualitative Variables

**Qualitative variables** categorize observations and are divided into **nominal** and **ordinal** types. Nominal variables (e.g., gender, nationality) lack order and allow only equality comparisons, while ordinal variables (e.g., education level, military rank) can be ranked but limit arithmetic operations. Understanding these distinctions is crucial for selecting appropriate analytical methods.

#### Nominal vs. Ordinal Examples

- **Nominal**: Classifying cities by region (e.g., North, South) without implying order.
- **Ordinal**: Ranking product quality (e.g., poor, average, excellent), where order matters but differences are not quantifiable.

### Frequency Tables and Bar Charts

For qualitative variables with a finite outcome set $\Omega = \{m_1, \ldots, m_k\}$, **absolute frequencies** ($n_j$) count occurrences of each outcome $m_j$, and **relative frequencies** ($h_j = \frac{n_j}{n}$) normalize these counts, satisfying:

$$
\sum_{j=1}^k n_j = n \quad \text{and} \quad \sum_{j=1}^k h_j = 1.
$$

These are presented in **frequency tables** or visualized via **bar charts** (heights reflect frequencies) or **pie charts** (proportions of the whole).

#### Example: Regional Distribution

For 60 cities across five regions:

- **Frequency Table**:
  $$
  \begin{array}{|c|c|c|}
  \hline
  \text{Region} & n_j & h_j \\
  \hline
  \text{Centrum} & 10 & 16.7\% \\
  \text{Noord} & 15 & 25.0\% \\
  \text{NoordOost} & 24 & 40.0\% \\
  \text{Zuid-Oost} & 5 & 8.3\% \\
  \text{West} & 6 & 10.0\% \\
  \hline
  \end{array}
  $$
- **Bar Chart**: Heights show the frequency of cities per region, e.g., NoordOost has the highest at 24 cities (40%).

### Histograms for Quantitative Data

**Quantitative variables** take numerical values, enabling arithmetic operations, and can be **discrete** or **continuous**. For continuous data with infinite possible outcomes, data is grouped into **classes** (5–20 intervals) with a constant **class width** ($\Delta$). A **histogram** visualizes frequencies, where bar areas (or heights for equal-width classes) represent absolute or relative frequencies.

#### Example: Car Speeds

For 300 car speeds (44.5–94.5 km/h) grouped into 10 classes ($\Delta = 5$):

- **Classes**: [44.5, 49.5], [49.5, 54.5], ..., [89.5, 94.5].
- **Class Midpoints**: $c_1 = 47, \ldots, c_{10} = 92$.
- **Frequencies**: $n_1 = 8, n_2 = 6, \ldots, n_{10} = 2$, with $\sum n_j = 300$, $\sum h_j = 1$.
- **Histogram**: Bar heights reflect frequencies, e.g., the class [69.5, 74.5] has the highest frequency (74 cars, 24.67%).

### Density Histograms

When classes have unequal widths ($\Delta_j$), a **density histogram** adjusts bar heights to $\frac{h_j}{\Delta_j}$, ensuring the total area equals 1:

$$
\text{Total area} = \sum_{j=1}^k \Delta_j \cdot \frac{h_j}{\Delta_j} = 1.
$$

This approximates the population’s density function and avoids misrepresentation from summing frequencies directly.

#### Example: Adjusting for Unequal Classes

Combining sparse classes (e.g., high-speed ranges) requires density adjustments to maintain proportional representation, preventing overestimation in wider classes.

### Empirical Distribution and Quantile Functions

The **empirical distribution function** ($\widehat{F}_n(x) = \frac{\#\{x_i \leq x\}}{n}$) is a step function rising from 0 to 1, approximating the population distribution. The **empirical quantile function** ($\widehat{Q}_n(p)$) is its inverse, defined as the smallest $x$ where $\widehat{F}_n(x) \geq p$. For grouped data, cumulative frequencies are computed to estimate these functions.

#### Example: Cumulative Frequencies

For car speeds:

- **Cumulative Table**:
  $$
  \begin{array}{|c|c|c|c|}
  \hline
  \text{Class} & \text{Speed} \leq \text{Bound} & \text{Number} & \% \\
  \hline
  \leq 44.5 & 0 & 0.00\% \\
  \leq 49.5 & 8 & 2.67\% \\
  \leq 54.5 & 14 & 4.67\% \\
  \vdots & \vdots & \vdots \\
  \leq 94.5 & 300 & 100.00\% \\
  \hline
  \end{array}
  $$
- **Cumulative Polygon**: Plots cumulative percentages, approximating the distribution function.

## 2.3 Measures of Central Tendency and Dispersion

Numerical summaries, or **statistics**, quantify a dataset’s **location** (center) and **scale** (spread). These complement frequency analyses by providing concise metrics, with central tendency measures like mean, median, and mode, and dispersion measures like variance and interquartile range, linking to graphical tools like histograms and boxplots.

### Central Tendency Measures

**Central tendency** describes the dataset’s typical value. The **sample mean** ($\bar{x} = \frac{1}{n} \sum_{i=1}^n x_i$) averages all observations, while for grouped data, it uses class midpoints ($\bar{x} = \frac{1}{n} \sum_{j=1}^k n_j c_j$). The **sample median** ($\widehat{Q}_n(1/2)$) is the middle value for odd $n$, or the average of two middle values for even $n$, approximated via interpolation for grouped data. The **mode**, less common, identifies the most frequent class midpoint but depends heavily on class boundaries.

#### Example: Car Speeds

- **Mean**: $\bar{x} = \frac{20465}{300} = 68.22 \, \text{km/h}$.
- **Median**: Interpolated as $64.5 + \left( \frac{50\% - 35.33\%}{55.33\% - 35.33\%} \right) \cdot 5 = 68.17 \, \text{km/h}$.
- **Mode**: Class [69.5, 74.5] with the highest frequency (74 cars).

### Dispersion Measures

**Dispersion** quantifies data spread. The **empirical variance** ($s^2 = \frac{1}{n-1} \sum_{i=1}^n (x_i - \bar{x})^2$) measures average squared deviation from the mean, with $n-1$ accounting for the loss of a degree of freedom. The **standard deviation** ($s = \sqrt{s^2}$) restores the original units. The **interquartile range** ($\text{IQR}_n = \widehat{Q}_n(3/4) - \widehat{Q}_n(1/4)$) spans the middle 50% of data, and the **median absolute deviation** ($\text{mad}(x) = \text{med}(|x_i - \text{med}(x)|)$) measures typical deviation from the median.

#### Example: Car Speeds

- **Variance**: $s^2 = \frac{23730.9}{299} = 79.36 \, (\text{km/h})^2$.
- **Standard Deviation**: $s = \sqrt{79.36} = 8.91 \, \text{km/h}$.
- **IQR**: Requires quartile interpolation (not provided in source).
- **MAD**: Not calculated but would involve median deviations.

## 2.4 Visualizing Data with Boxplots

The **boxplot**, introduced by Tukey (1977), summarizes a dataset’s distribution using the median, quartiles, and outliers. It displays the **interquartile range** (IQR) as a box, **whiskers** extending to non-outliers, and **outliers** beyond $\widehat{Q}_n(1/4) - 1.5 \cdot \text{IQR}_n$ or $\widehat{Q}_n(3/4) + 1.5 \cdot \text{IQR}_n$. This connects to dispersion measures and aids in comparing datasets.

### Constructing a Boxplot

- **Median**: Plot at $\widehat{Q}_n(1/2)$.
- **Box**: Spans $\widehat{Q}_n(1/4)$ to $\widehat{Q}_n(3/4)$, length = IQR.
- **Whiskers**: Extend to the furthest non-outliers within $1.5 \cdot \text{IQR}$.
- **Outliers**: Points beyond $1.5 \cdot \text{IQR}$; **extreme outliers** beyond $3 \cdot \text{IQR}$.

#### Example: City Populations

For 15 US cities (1960, in 10,000s):

- **Median**: 88.
- **Q1, Q3**: 74, 200; $\text{IQR} = 126$.
- **Outlier**: 778 (New York) beyond $[74 - 1.5 \cdot 126, 200 + 1.5 \cdot 126] = [-115, 389]$.
- **Boxplot**: Shows right-skewness (longer upper whisker, outlier at 778).

## 2.5 Assessing Relationships Between Variables

Analyzing relationships between variables uses graphical (scatterplots) and numerical (covariance, correlation) methods for quantitative data, or **contingency tables** for qualitative data. These methods quantify dependencies, linking to frequency and distribution analyses.

### Scatterplots for Quantitative Variables

**Scatterplots** plot pairs of quantitative variables ($x_i, y_i$) to reveal linear, quadratic, or logarithmic relationships. A narrow scatter indicates strong association; a wide scatter suggests weak association. Outliers can distort patterns.

#### Example: New Orleans Data

- **Original Scatterplot**: Shows a positive, non-linear (logarithmic) relationship with an outlier (New Orleans).
- **Log-Transformed**: Linearizes the relationship, reducing variability.

### Covariance and Correlation

The **sample covariance** measures linear association:

$$
\text{cov}(x, y) = \frac{1}{n-1} \sum_{i=1}^n (x_i - \bar{x})(y_i - \bar{y}).
$$

The **Pearson correlation coefficient** normalizes this:

$$
r = \frac{\text{cov}(x, y)}{s_x s_y}, \quad -1 \leq r \leq 1.
$$

Values near 1 or -1 indicate strong linear relationships; $r \approx 0$ suggests no linear association.

#### Example: Interpretation

- A narrow scatterplot with $r \approx 1$ indicates a strong positive linear relationship.
- Non-linear relationships (e.g., quadratic) may yield $r \approx 0$, requiring scatterplot inspection first.

### Contingency Tables for Qualitative Variables

**Contingency tables** count occurrences of qualitative variable combinations, with row and column totals. Expected frequencies under independence are calculated as:

$$
\text{Expected} = \frac{\text{Row Total} \cdot \text{Column Total}}{n}.
$$

Deviations from expected values suggest dependence.

#### Example: Income and Region

For 60 cities:

- **Original Table**: Shows income classes (1–4) by region (C, N, NO, ZO, W).
- **Grouped Table** (West vs. East):
  $$
  \begin{array}{|c|c|c|c|c|c|}
  \hline
  & 1 & 2 & 3 & 4 & \text{Total} \\
  \hline
  \text{Oost} & 14 & 23 & 6 & 1 & 44 \\
  \text{West} & 2 & 5 & 6 & 3 & 16 \\
  \hline
  \text{Total} & 16 & 28 & 12 & 4 & 60 \\
  \hline
  \end{array}
  $$
- **Expected (Oost, 2)**: $\frac{44 \cdot 28}{60} = 20.53$. Overrepresentation in Oost suggests dependence.

## 2.6 Quantile-Quantile (QQ) Plots

**QQ-plots** compare empirical quantiles ($\widehat{Q}_n(p)$) to theoretical quantiles ($F^{-1}(p)$) to test distributional assumptions, typically normality. Points aligning on a straight line suggest the data follows the assumed distribution. This links to histograms and boxplots for distribution analysis.

### Constructing a QQ-Plot

For ordered data $x_{1:n} \leq \cdots \leq x_{n:n}$, plot:

$$
\left( F^{-1}\left(\frac{i}{n}\right), x_{i:n} \right), \quad i = 1, \ldots, n.
$$

For normality, use $F^{-1}\left(\frac{i}{n}\right) = \mu + \sigma \Phi^{-1}\left(\frac{i}{n}\right)$. A linear plot indicates normality; deviations suggest transformations (e.g., logarithmic).

#### Example: Testing Normality

- **Linear QQ-Plot**: Suggests normality with $\mu = 74.6$, $\sigma = 4.8$.
- **Non-Linear QQ-Plot**: Logarithmic transformation linearizes the plot, indicating lognormal data.

---

## Key Points to Remember

- **Descriptive Statistics → Summarization**: Use kentallen and graphical tools like histograms and boxplots to summarize data. ★★★★☆
- **Sampling → Representativeness**: Ensure samples reflect the population for generalizable conclusions, balancing size and cost. ★★★★★
- **Qualitative Variables → Nominal vs. Ordinal**: Distinguish between non-ordered (nominal) and ordered (ordinal) categories for appropriate analysis. ★★★★☆
- **Histograms → Frequency Visualization**: Use equal-width histograms for quantitative data; adjust heights for unequal widths in density histograms. ★★★★★
- **Central Tendency → Mean, Median, Mode**: Mean and median are robust, but mode depends on class boundaries. ★★★★☆
- **Dispersion → Variance and IQR**: Variance measures spread around the mean; IQR and MAD focus on robust spread measures. ★★★★☆
- **Boxplots → Distribution Summary**: Visualize median, IQR, and outliers to assess skewness and spread. ★★★★★
- **Correlation → Linear Relationships**: Use scatterplots and Pearson’s $r$ to quantify linear associations, checking for non-linear patterns first. ★★★★☆
- **Contingency Tables → Dependence**: Compare observed and expected frequencies to assess qualitative variable dependence. ★★★★☆
- **QQ-Plots → Distribution Testing**: Test normality or other distributions, using transformations to achieve linearity. ★★★★★
