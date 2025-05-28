# Problem 2

# 🧮 Estimating π Using Monte Carlo Methods

## 🎯 Motivation

Monte Carlo methods are computational algorithms that rely on **random sampling** to estimate numerical results. One of the most famous applications is estimating the value of π through **geometric probability**. In this project, we explore two approaches:

- **Part 1**: Estimating π by simulating points in a square with an inscribed circle.
- **Part 2**: Estimating π using **Buffon’s Needle**—a classic problem in geometric probability.

Both methods highlight how randomness can be used to derive estimates of constants and solve complex problems.

---

## 🟠 Part 1: Estimating π Using a Circle

### 📐 Theoretical Foundation

Consider a unit circle inscribed in a square of side length 2 (centered at origin, so radius = 1). The area of the square is:

$$
A_{\text{square}} = (2)^2 = 4
$$

The area of the circle is:

$$
A_{\text{circle}} = \pi r^2 = \pi (1)^2 = \pi
$$

The probability that a randomly chosen point in the square lies inside the circle is:

$$
\frac{\text{Area of Circle}}{\text{Area of Square}} = \frac{\pi}{4} \Rightarrow \pi \approx 4 \cdot \frac{\text{points inside circle}}{\text{total points}}
$$

---

### 🧪 Simulation Steps

1. Generate N random (x, y) points in the square [-1, 1] × [-1, 1].
2. Count how many points fall inside the unit circle (i.e., 

$$
 x^2 + y^2 \leq 1 
 $$

3. Estimate π using the formula:

$$
\pi \approx 4 \cdot \frac{\text{inside}}{\text{total points}}
$$

---

### 📊 Visualization

Plot the points:
- Points **inside** the circle: blue.
- Points **outside** the circle: red.
- Also, draw the boundary of the circle.

---

### 📈 Convergence Analysis

As the number of points increases, the estimate converges toward π. We can plot:

- Estimated value of π vs. number of iterations
- Error vs. iterations (e.g., 

$$
 |\pi - \hat{\pi}| 
 $$)

---

## 🧵 Part 2: Estimating π Using Buffon’s Needle

### 📐 Theoretical Foundation

In Buffon’s Needle experiment, a needle of length 

$$
 L 
 $$
 
  is dropped on a floor with parallel lines spaced distance 
  
  $$
   D 
   $$
   
    apart (where 
    
    $$
     L \leq D 
     $$
     
     ). The probability 
     
     $$
      P 
      $$
      
       that the needle crosses a line is:

$$
P = \frac{2L}{\pi D}
\Rightarrow \pi \approx \frac{2L \cdot \text{trials}}{D \cdot \text{crosses}}
$$

---

### 🧪 Simulation Steps

1. Drop a needle at a random angle and position:
   - Random angle 
   
   $$
    \theta \in [0, \pi] 
    $$

   - Random center position between two lines
2. Determine if the needle crosses a line using geometry.
3. Estimate π from the observed frequency of crossings.

---

### 🖼 Visualization

Graphically show:
- Horizontal parallel lines
- Needle positions (crossing lines vs not crossing lines)

---

### 📈 Convergence and Comparison

- Plot π estimates vs number of trials
- Compare convergence rate to the circle-based method
- Discuss stability and variance in estimates

---

## 🔬 Analysis and Discussion

| Method            | Convergence Speed | Accuracy | Simplicity | Visual Appeal |
|------------------|-------------------|----------|------------|----------------|
| Circle-Based     | Fast              | High     | Simple     | High           |
| Buffon’s Needle  | Slower            | Moderate | Tricky     | Moderate       |

- **Circle method** is faster and more intuitive, but less “physical.”
- **Buffon’s Needle** is historically significant and conceptually rich, but has higher variance.

---

## 📁 Deliverables

- Python code for both simulations
- Plots showing estimated π and convergence
- Animated or static visualizations of random points and needles
- A comparative analysis of both methods

---

## 📚 Resources

- [Wikipedia - Monte Carlo Method](https://en.wikipedia.org/wiki/Monte_Carlo_method)
- [Wikipedia - Buffon's Needle](https://en.wikipedia.org/wiki/Buffon%27s_needle)
- Think Stats by Allen B. Downey

[visit web](https://colab.research.google.com/drive/19V3WtC19b258Bnnpy-amlo8_d3M3FIYf?usp=sharing)