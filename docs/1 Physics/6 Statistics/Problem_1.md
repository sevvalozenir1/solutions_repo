# Problem 1

# 📘 Exploring the Central Limit Theorem through Simulations

## 🎯 Motivation

The **Central Limit Theorem (CLT)** is a fundamental theorem in probability and statistics. It states that the distribution of the sample mean approaches a **normal distribution** as the sample size increases, regardless of the shape of the original population distribution.

This simulation project allows us to visually and computationally explore the CLT in action by drawing samples from different distributions and analyzing their sample means.

---

## 🧰 Tools & Libraries

We will use the following Python libraries:

- `numpy` for numerical computations
- `matplotlib` and `seaborn` for visualization
- `matplotlib.animation` for GIF generation

---

## 🔢 1. Generating Population Distributions

We simulate large populations from:
- **Uniform Distribution**: Equal probability over a range
- **Exponential Distribution**: Skewed distribution
- **Binomial Distribution**: Discrete distribution

---

## 🔄 2. Sampling and Visualization

We repeatedly sample from each population, compute the sample means, and visualize the resulting sampling distribution for increasing sample sizes (5, 10, 30, 50). This allows us to observe how the distribution of the mean converges to normality.

---

## 🔬 3. Parameter Exploration

We also explore how sample size affects:
- The shape of the sampling distribution
- The variance (spread) of the sample means

---

## 🏭 4. Practical Applications

The CLT underpins many statistical methods and real-world applications:
- **Estimation of population parameters**
- **Quality control in manufacturing**
- **Financial modeling and forecasting**

---

## 📈 Visual Results

Each distribution is visualized across different sample sizes. Histograms show the shift towards a bell-shaped normal distribution as the sample size increases.

---

## 🎞️ Bonus: Animation (GIF)

We also create animations to dynamically show how increasing the sample size causes the sample mean distribution to become more normally distributed.

---

## ✅ Summary

| Distribution | Skewness | Convergence Speed |
|--------------|----------|-------------------|
| Uniform      | None     | Fast              |
| Exponential  | High     | Moderate          |
| Binomial     | Low      | Fast              |

---

## 💾 Deliverables

- Python scripts for simulations
- Plots for sampling distributions
- Animated GIFs
- Markdown and notebook documentation


```python
sample_sizes = [5, 10, 30, 50]
distributions = {
    'Uniform': pop_uniform,
    'Exponential': pop_exponential,
    'Binomial': pop_binomial
}

for name, pop in distributions.items():
    plt.figure(figsize=(14, 8))
    for i, size in enumerate(sample_sizes):
        means = sample_means(pop, size)
        plt.subplot(2, 2, i+1)
        sns.histplot(means, kde=True, bins=30, color="skyblue")
        plt.title(f"{name} Distribution - Sample Size {size}")
        plt.xlabel("Sample Mean")
        plt.ylabel("Frequency")
    plt.suptitle(f"Sampling Distribution of Sample Mean for {name} Population", fontsize=16)
    plt.tight_layout(rect=[0, 0, 1, 0.96])
    plt.savefig(f"{name}_CLT_Plot.png")  # Save as picture
    plt.show()
```

![alt text](image.png)

[visit web](https://colab.research.google.com/drive/1FCiVyj3Sk7q_5lIThnXdi-JJ-WPDeHiV?usp=sharing)