# Problem 1
# # Orbital Period and Orbital Radius

## Motivation
Kepler's Third Law reveals a powerful and elegant relationship between the time a planet takes to complete an orbit (its orbital period) and its average distance from the body it orbits (orbital radius). This relationship helps astronomers estimate distances in the Solar System and beyond, calculate masses of planets and stars, and understand orbital dynamics.

## Derivation of Kepler's Third Law for Circular Orbits

For a body of mass `m` orbiting a much larger mass `M` (like a planet around the Sun), the centripetal force is provided by gravity:

**Gravitational Force = Centripetal Force**

$$
 \frac{GMm}{r^2} = \frac{mv^2}{r} 
 $$

Solving for orbital velocity `v`:

$$
 v = \sqrt{\frac{GM}{r}} 
 $$

The orbital period `T` is the time it takes to make one full orbit:

$$
 T = \frac{2\pi r}{v} = \frac{2\pi r}{\sqrt{\frac{GM}{r}}} = 2\pi \sqrt{\frac{r^3}{GM}} 
 $$

Squaring both sides:

$$
 T^2 = \frac{4\pi^2}{GM} r^3 
 $$

Thus:

$$
 T^2 \propto r^3 
 $$

This is Kepler's Third Law.

## Implications in Astronomy
- Helps determine the mass of celestial bodies.
- Allows estimation of distances between planets and stars.
- Provides a method for understanding satellite trajectories.

## Real-World Examples

### 1. Moon's Orbit Around Earth
```python
import numpy as np
import matplotlib.pyplot as plt

# Constants
G = 6.67430e-11  # m^3 kg^-1 s^-2
M_earth = 5.972e24  # kg
r_moon = 384400e3  # m

# Calculate orbital period
T_moon = 2 * np.pi * np.sqrt(r_moon**3 / (G * M_earth))
T_moon_days = T_moon / (60 * 60 * 24)
print(f"Orbital Period of Moon: {T_moon_days:.2f} days")
```

### 2. Planets in the Solar System
```python
# Data: semi-major axes (AU) and periods (years) of some planets
radii_au = np.array([0.39, 0.72, 1.0, 1.52, 5.2, 9.58])  # Mercury to Saturn
periods_years = np.array([0.24, 0.61, 1.0, 1.88, 11.86, 29.46])

# Verify Kepler's Third Law
plt.figure(figsize=(8, 6))
plt.plot(radii_au**3, periods_years**2, 'o-', label="T^2 vs r^3")
plt.xlabel("Orbital Radius^3 (AU^3)")
plt.ylabel("Orbital Period^2 (Years^2)")
plt.title("Kepler's Third Law for Planets")
plt.grid(True)
plt.legend()
plt.show()
```

## Simulation of Circular Orbits
```python
# Simulate a simple circular orbit
from matplotlib.animation import FuncAnimation

fig, ax = plt.subplots(figsize=(5, 5))
ax.set_xlim(-1.2*r_moon, 1.2*r_moon)
ax.set_ylim(-1.2*r_moon, 1.2*r_moon)
planet, = ax.plot([], [], 'bo')

# Orbit path
theta = np.linspace(0, 2*np.pi, 100)
x_orbit = r_moon * np.cos(theta)
y_orbit = r_moon * np.sin(theta)
ax.plot(x_orbit, y_orbit, 'k--')

# Animation
n_frames = 100
orbit_time = np.linspace(0, T_moon, n_frames)
positions = [(r_moon * np.cos(2*np.pi*t/T_moon), r_moon * np.sin(2*np.pi*t/T_moon)) for t in orbit_time]

def update(frame):
    planet.set_data(*positions[frame])
    return planet,

ani = FuncAnimation(fig, update, frames=n_frames, blit=True)
plt.show()
```

## Extension to Elliptical Orbits
Kepler's Third Law also applies to elliptical orbits when using the semi-major axis `a` instead of radius `r`:

$$
 T^2 = \frac{4\pi^2}{GM} a^3 
 $$

This version holds true for all elliptical orbits, making the law universally applicable to binary stars, moons, and exoplanets.

---
**Conclusion:**
Kepler's Third Law connects orbital periods and radii through gravity's universal law. Whether examining artificial satellites or exoplanets, this principle guides modern astronomy and space science.


```python
import numpy as np
import matplotlib.pyplot as plt

# Orbital radius in AU and orbital period in years for some planets
radii_au = np.array([0.39, 0.72, 1.0, 1.52, 5.2, 9.58])  # Mercury to Saturn
periods_years = np.array([0.24, 0.61, 1.0, 1.88, 11.86, 29.46])

# Calculate r^3 and T^2
r_cubed = radii_au**3
T_squared = periods_years**2

# Plotting
plt.figure(figsize=(8, 6))
plt.plot(r_cubed, T_squared, 'o-', color='royalblue', label=r"$T^2$ vs $r^3$")
plt.xlabel(r"Orbital Radius$^3$ (AU$^3$)", fontsize=12)
plt.ylabel(r"Orbital Period$^2$ (Years$^2$)", fontsize=12)
plt.title("Kepler's Third Law: $T^2 \propto r^3$", fontsize=14)
plt.grid(True)
plt.legend()
plt.tight_layout()
plt.show()
```
![alt text](image.png)

```python
import numpy as np
import matplotlib.pyplot as plt
from matplotlib.animation import FuncAnimation

# Constants
r = 384400e3  # Radius of Moon's orbit in meters
T = 27.3 * 24 * 3600  # Period in seconds

# Time values
n_frames = 200
time_vals = np.linspace(0, T, n_frames)

# Orbital position calculations
x_vals = r * np.cos(2 * np.pi * time_vals / T)
y_vals = r * np.sin(2 * np.pi * time_vals / T)

# Set up the plot
fig, ax = plt.subplots(figsize=(6, 6))
ax.set_xlim(-1.2*r, 1.2*r)
ax.set_ylim(-1.2*r, 1.2*r)
ax.set_aspect('equal')
ax.plot(0, 0, 'yo', markersize=12, label='Earth')
orbit_path, = ax.plot([], [], 'k--', alpha=0.5)
moon, = ax.plot([], [], 'bo', label='Moon')

def init():
    orbit_path.set_data(x_vals, y_vals)
    moon.set_data([], [])
    return orbit_path, moon

def update(frame):
    moon.set_data(x_vals[frame], y_vals[frame])
    return moon,

ani = FuncAnimation(fig, update, frames=n_frames, init_func=init, blit=True)
plt.title("Circular Orbit: Moon Around Earth")
plt.legend()
plt.show()
```

![alt text](image-1.png)

```python
# Linear regression (for illustrative best-fit)
from scipy.stats import linregress

slope, intercept, r_value, _, _ = linregress(r_cubed, T_squared)
fit_line = slope * r_cubed + intercept

plt.figure(figsize=(8, 6))
plt.plot(r_cubed, T_squared, 'o', label="Observed")
plt.plot(r_cubed, fit_line, '-', label=f"Best Fit: $T^2 = {slope:.2f}r^3 + {intercept:.2f}$")
plt.xlabel(r"Orbital Radius$^3$ (AU$^3$)")
plt.ylabel(r"Orbital Period$^2$ (Years$^2$)")
plt.title("Kepler's Third Law Linear Fit")
plt.legend()
plt.grid(True)
plt.tight_layout()
plt.show()
```

[visit website](https://colab.research.google.com/drive/1lC0fSYjPGOVDlkhdXnOgy7qaNo2snoWs?usp=sharing)

