# Problem 2
## Investigating the Dynamics of a Forced Damped Pendulum

### Motivation
The forced damped pendulum exhibits complex dynamics due to the interplay of damping, restoring forces, and external periodic forcing. Understanding this system provides insights into resonance, chaos, and quasiperiodic motion, relevant in fields such as energy harvesting, climate systems, and mechanical vibrations.

### Theoretical Foundation
The equation of motion for a forced damped pendulum is:

$$
\frac{d^2\theta}{dt^2} + \gamma \frac{d\theta}{dt} + \omega_0^2 \sin(\theta) = A \cos(\omega t)
$$

For small angles, we approximate 

$$
 \sin(\theta) \approx \theta 
 $$
 
 , reducing the equation to a linear form:

$$
\frac{d^2\theta}{dt^2} + \gamma \frac{d\theta}{dt} + \omega_0^2 \theta = A \cos(\omega t)
$$

The resonance condition occurs when 

$$
 \omega \approx \omega_0 
 $$
 
 , leading to maximum amplitude.

### Numerical Simulation
We solve the nonlinear equation numerically using the Runge-Kutta method.

```python
import numpy as np
import matplotlib.pyplot as plt
from scipy.integrate import solve_ivp

# Define the forced damped pendulum equations
def forced_damped_pendulum(t, y, gamma, omega0, A, omega):
    theta, omega_t = y
    dtheta_dt = omega_t
    domega_dt = -gamma * omega_t - omega0**2 * np.sin(theta) + A * np.cos(omega * t)
    return [dtheta_dt, domega_dt]

# Parameters
gamma = 0.5   # Damping coefficient
omega0 = 1.0  # Natural frequency
A = 1.2       # Forcing amplitude
omega = 2.0   # Forcing frequency

# Initial conditions and time span
t_span = (0, 50)
y0 = [0.2, 0] # Initial angle and angular velocity
t_eval = np.linspace(0, 50, 1000)

# Solve the ODE
sol = solve_ivp(forced_damped_pendulum, t_span, y0, t_eval=t_eval, args=(gamma, omega0, A, omega))

# Plot results
plt.figure(figsize=(10,5))
plt.plot(sol.t, sol.y[0], label="Theta (angle)")
plt.xlabel("Time")
plt.ylabel("Angle (radians)")
plt.title("Forced Damped Pendulum Motion")
plt.legend()
plt.grid()
plt.show()
```

![alt text](image-11.png)

### Analysis of Dynamics
- **Effects of Parameters:**
  - Increasing 
  
  $$ 
  \gamma 
  $$ 
  
  leads to faster damping.
  - Higher 
  
  $$
   A 
   $$
   
    induces chaotic behavior at certain frequencies.
  - When 
  
  $$
   \omega \approx \omega_0 
   $$
   
   , resonance occurs.
- **Chaos and Transitions:**
  - A phase portrait can illustrate chaotic behavior.
  - Poincaré sections help identify quasiperiodic or chaotic states.

### Practical Applications
- **Energy Harvesting:** Used in piezoelectric devices.
- **Engineering:** Suspension bridges under periodic loads.
- **Biomechanics:** Modeling human gait oscillations.

### Conclusion
This study demonstrates the transition from simple periodic motion to chaos. Future extensions can include nonlinear damping or stochastic driving forces.

[visit website](https://colab.research.google.com/drive/1Q9YGNhFdYVcKoypTtUA0A64rQVRPXZso?usp=sharing)
