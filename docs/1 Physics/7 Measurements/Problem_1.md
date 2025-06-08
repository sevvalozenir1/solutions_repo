# 🌍 Measuring Earth's Gravitational Acceleration Using a Pendulum

## 🧭 1. Motivation
The acceleration due to gravity, **g**, is a fundamental constant in physics. It affects phenomena ranging from free fall to planetary orbits. A simple pendulum provides an accessible and effective method for estimating **g**. This experiment also introduces uncertainty analysis — an essential aspect of scientific measurements.

---

## 🧪 2. Materials
- A string (~1.14 meters)
- USB power adapter (pendulum bob)
- Smartphone stopwatch
- Ruler or measuring tape (±1 mm resolution)

---

## ⚙️ 3. Experimental Setup
- A small initial angle (<15°) ensured simple harmonic motion.
- Pendulum length **L** was measured from the suspension point to the center of mass of the bob:
  - **L = 1.140 m**, **u<sub>L</sub> = ±0.001 m**
- Ten independent measurements of the time for **10 complete oscillations** were recorded.

```python
# 🔧 Import necessary libraries
import numpy as np
import matplotlib.pyplot as plt
from matplotlib.animation import FuncAnimation

# 📐 Physical Constants
g = 9.81         # gravitational acceleration (m/s²)
L = 1.14         # length of the pendulum (meters)
theta0 = np.radians(10)  # initial angle in radians (10 degrees)

# ⏱️ Time setup
T = 2 * np.pi * np.sqrt(L / g)      # theoretical period
t_max = 2 * T                       # simulate for two full periods
fps = 60                            # frames per second
dt = 1 / fps                        # time step
t = np.arange(0, t_max, dt)        # time array

# 🌀 Small angle approximation: θ(t) = θ₀ cos(√(g/L) t)
theta = theta0 * np.cos(np.sqrt(g / L) * t)

# 📍 Convert to Cartesian coordinates
x = L * np.sin(theta)
y = -L * np.cos(theta)

# 🎬 Create the animation
fig, ax = plt.subplots(figsize=(6, 6))
ax.set_xlim(-L - 0.2, L + 0.2)
ax.set_ylim(-L - 0.2, 0.2)
ax.set_aspect('equal')
ax.grid()

# Draw pendulum components
line, = ax.plot([], [], 'o-', lw=2, color='blue')    # rod + bob
trace, = ax.plot([], [], 'r--', lw=1, alpha=0.5)      # trace of motion
trace_x, trace_y = [], []

# 🖼️ Initialize function for animation
def init():
    line.set_data([], [])
    trace.set_data([], [])
    return line, trace

# 🧩 Animation function
def update(frame):
    this_x = [0, x[frame]]
    this_y = [0, y[frame]]
    line.set_data(this_x, this_y)
    
    trace_x.append(x[frame])
    trace_y.append(y[frame])
    trace.set_data(trace_x, trace_y)
    
    return line, trace

# 🎞️ Run the animation
ani = FuncAnimation(fig, update, frames=len(t),
                    init_func=init, blit=True, interval=1000*dt)

# 🎥 Display in notebook
from IPython.display import HTML
HTML(ani.to_jshtml())
```
![alt text](image-3.png)


---

## 📊 4. Data Collection

### 4.1 Raw Time Measurements (10 Oscillations)

| Trial | Time (s) |
|-------|----------|
| 1     | 18.05    |
| 2     | 17.65    |
| 3     | 18.12    |
| 4     | 17.92    |
| 5     | 17.98    |
| 6     | 18.01    |
| 7     | 17.83    |
| 8     | 18.00    |
| 9     | 17.91    |
| 10    | 18.07    |

---

## 🧮 5. Data Analysis

### 5.1 Mean and Standard Deviation

$$
\bar{T}_{10} = 17.954 \, \text{s}, \quad s = 0.136 \, \text{s}
$$

Uncertainty in the mean:

$$
u_{\bar{T}_{10}} = \frac{0.136}{\sqrt{10}} = 0.043 \, \text{s}
$$

### 5.2 Period of One Oscillation

$$
T = \frac{\bar{T}_{10}}{10} = 1.7954 \, \text{s}, \quad u_T = \frac{0.043}{10} = 0.0043 \, \text{s}
$$

---

## 🌍 6. Estimating Gravitational Acceleration

Using the pendulum formula:

$$
g = \frac{4\pi^2 L}{T^2}
$$

Substituting values:

$$
g = \frac{4\pi^2 \cdot 1.14}{(1.7954)^2} = 13.962 \, \text{m/s}^2
$$

### 6.1 Propagating Uncertainty

$$
u_g = g \cdot \sqrt{\left(\frac{u_L}{L}\right)^2 + \left(2 \cdot \frac{u_T}{T}\right)^2}
$$

$$
u_g = 13.962 \cdot \sqrt{\left(\frac{0.001}{1.14}\right)^2 + \left(2 \cdot \frac{0.0043}{1.7954}\right)^2} = 0.068 \, \text{m/s}^2
$$

---

## 📋 7. Results Summary

| Quantity | Value    | Uncertainty | Units   |
|----------|----------|-------------|---------|
| Length (L) | 1.140  | ±0.001      | m       |
| Period (T) | 1.7954 | ±0.0043     | s       |
| Gravity (g) | 13.962 | ±0.068     | m/s²    |

---

## 📈 8. Visual Data Representation

> *(Note: The following are suggested visuals to include in your report or notebook.)*

- Histogram of 10-oscillation times
- Time vs. trial number plot
- Comparison bar chart between experimental and standard **g**

---

## 🔍 9. Discussion

### 9.1 Comparison with Standard Value

The standard gravitational acceleration at sea level is:

$$
g_0 = 9.80665 \, \text{m/s}^2
$$

Our measured value (**13.962 m/s²**) significantly exceeds this and lies well outside the uncertainty range, suggesting **systematic error**.

### 9.2 Sources of Uncertainty and Error

| Source                 | Effect                                  |
|------------------------|-----------------------------------------|
| Manual timing          | Human reaction time introduces bias     |
| Length measurement     | Small errors significantly affect result |
| Large swing angle      | Violates small-angle assumption          |
| Non-vertical swing     | Introduces complexity and error         |

### 9.3 How to Improve the Experiment

- Use **photogate timers** for accurate timing
- Measure length precisely with **calipers** or **laser tools**
- Keep oscillations under **10°** for harmonic motion
- Increase number of trials and average over larger datasets

---

## ✅ 10. Conclusion

Although simple, this experiment highlights the importance of **precision** and **error analysis**. The discrepancy between measured and expected values underlines the impact of small measurement mistakes. Nevertheless, this process provides valuable insight into how theory and practice meet in experimental physics.

---

## 📚 11. References

- Serway, R. A., & Jewett, J. W. (2014). *Physics for Scientists and Engineers*.
- Taylor, J. R. (1997). *An Introduction to Error Analysis*.
- OpenAI ChatGPT Experimental Lab (2025)

```python
# 1. Import libraries
import numpy as np
import matplotlib.pyplot as plt

# 2. Example Data (replace with your actual measurements)
T10_data = np.array([20.1, 20.3, 20.0, 20.2, 20.4, 20.1, 20.2, 20.3, 20.1, 20.0])  # seconds for 10 oscillations
L = 1.00  # pendulum length in meters
u_L = 0.001 / 2  # uncertainty in length (resolution 1 mm -> half is 0.0005 m)

n = len(T10_data)

# 3. Calculations
mean_T10 = np.mean(T10_data)
std_T10 = np.std(T10_data, ddof=1)
u_mean_T10 = std_T10 / np.sqrt(n)

T = mean_T10 / 10
u_T = u_mean_T10 / 10

g = (4 * np.pi**2 * L) / T**2
u_g = g * np.sqrt((u_L / L)**2 + (2 * u_T / T)**2)

# 4. Plot 1: Raw timing data scatter plot
plt.figure(figsize=(8, 5))
plt.scatter(range(1, n+1), T10_data, color='blue', label='Measurements for 10 oscillations')
plt.hlines(mean_T10, 1, n, colors='red', linestyles='dashed', label=f'Mean = {mean_T10:.3f} s')
plt.fill_between([1, n], mean_T10 - u_mean_T10, mean_T10 + u_mean_T10, color='red', alpha=0.2, label='Uncertainty in mean')
plt.xlabel('Trial Number')
plt.ylabel('Time for 10 oscillations (s)')
plt.title('Pendulum Timing Measurements')
plt.legend()
plt.grid(True)
plt.show()

# 5. Plot 2: Histogram of timing data
plt.figure(figsize=(7, 5))
plt.hist(T10_data, bins=5, color='skyblue', edgecolor='black')
plt.axvline(mean_T10, color='red', linestyle='dashed', label='Mean')
plt.xlabel('Time for 10 oscillations (s)')
plt.ylabel('Frequency')
plt.title('Histogram of Timing Measurements')
plt.legend()
plt.grid(True)
plt.show()

# 6. Plot 3: Final g with uncertainty bar
plt.figure(figsize=(5, 5))
plt.errorbar(1, g, yerr=u_g, fmt='o', color='green', capsize=5, label=f'Measured g = {g:.3f} ± {u_g:.3f} m/s²')
plt.axhline(9.80665, color='blue', linestyle='--', label='Standard g = 9.80665 m/s²')
plt.xlim(0, 2)
plt.xticks([])
plt.ylabel('Acceleration due to gravity (m/s²)')
plt.title('Measured Gravitational Acceleration')
plt.legend()
plt.grid(True)
plt.show()
```

![alt text](image-4.png)

![alt text](image-5.png)

![alt text](image-6.png)

[visit web](https://colab.research.google.com/drive/1VxXZOgqgdD_EpzsYHOODF66vrWvYEJ0F?usp=sharing)
