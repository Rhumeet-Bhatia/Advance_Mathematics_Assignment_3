# Assignment-3: Probability Density Function Estimation

## 1. Objective

The objective of this assignment is to analyze environmental air-quality data by applying a roll-number-based non-linear transformation and learning the parameters of a probability density function using Maximum Likelihood Estimation (MLE).

The $NO_2$ feature from the India Air Quality dataset is used for this study.

---

## 2. Data Transformation

Each original data point x ($NO_2$ concentration) is transformed into a new variable $z$ using the following transformation:

$$z = T_{r}(x) = x + a_r \sin(b_r x)$$

where the constants $a_r$ and $b_r$ depend on the university roll number.

For **Roll Number: 102317171**:

- $a_r = 0.05 \times (102317171 \pmod 7) = \mathbf{0.25}$
- $b_r = 0.3 \times (102317171 \pmod 5 + 1) = \mathbf{0.6}$ 

This transformation introduces a controlled non-linear variation in the data.

---

## 3. Probability Density Model

The transformed variable $z$ is modeled using the following probability density function:

$$\hat{p}(z) = c \cdot e^{-\lambda(z-\mu)^2}$$

where:
- $\mu$ represents the mean of the distribution,
- $\lambda$ controls the spread of the distribution,
- $c$ is the normalization constant.

---

## 4. Parameter Estimation (MLE)

The parameters $\lambda$, $\mu$, and $c$ are learned using **Maximum Likelihood Estimation (MLE)**.

During optimization:
- $\lambda$ and $\mu$ are estimated by minimizing the negative log-likelihood.
- the normalization constant $c$ is computed automatically to ensure that the probability density integrates to 1.

This approach guarantees a valid probability density function and stable parameter estimates.

---

## 5. Dataset

- Dataset: India Air Quality Data  
- Source: Kaggle  
- Feature Used: $NO_2$ 
- Link: https://www.kaggle.com/datasets/shrutibhargava94/india-air-quality-data  

The dataset is downloaded locally and loaded using pandas.

---

## 6. Results

The final parameters learned using Maximum Likelihood Estimation are:

| Parameter | Value |
|---------|-------|
| Normalization constant ($c$) | 0.021562 |
| Precision ($\lambda$) | 0.001461 |
| Mean ($\mu$) | 25.812662 |

A visualization is included in the notebook showing:
- the empirical distribution of the transformed data $z$, and
- the estimated probability density function $p̂(z)$.

The fitted curve closely follows the data distribution, indicating a good model fit.

---

## 7. Conclusion

This assignment demonstrates how non-linear transformations influence data distributions and how Maximum Likelihood Estimation can be used to reliably learn probability density parameters. The learned model effectively captures the central tendency and spread of the transformed $NO_2$ data.
