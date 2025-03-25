# Problem 1
## Projectile Motion: Analysis of Range Dependence on Launch Angle

### **1. Theoretical Foundation**
Projectile motion is governed by Newton’s laws. Assuming no air resistance, the motion can be described using kinematic equations:

- Horizontal motion:
  \[ x = v_0 \cos(\theta) t \]
- Vertical motion:
  \[ y = v_0 \sin(\theta) t - \frac{1}{2} g t^2 \]

The total time of flight is found by solving for when the projectile returns to its initial height:

\[ t_f = \frac{2 v_0 \sin(\theta)}{g} \]

The horizontal range is given by:

\[ R = \frac{v_0^2 \sin(2\theta)}{g} \]

### **2. Analysis of the Range**
The horizontal range depends on:
- **Launch Angle (θ):** The range is maximized at \( 45^\circ \).
- **Initial Velocity (\( v_0 \)):** Higher velocity increases range quadratically.
- **Gravitational Acceleration (g):** A stronger gravitational field decreases range.

### **3. Practical Applications**
- **Sports:** Understanding ball trajectories in football and basketball.
- **Engineering:** Designing projectile-based systems like rockets or artillery.
- **Astrophysics:** Studying planetary motion under different gravity levels.

### **4. Implementation: Python Simulation**
We use Python to visualize how range varies with launch angle.

```python
import numpy as np
import matplotlib.pyplot as plt

def projectile_range(v0, g):
    angles = np.linspace(0, 90, 100)  # Angles in degrees
    angles_rad = np.radians(angles)   # Convert to radians
    ranges = (v0**2 * np.sin(2 * angles_rad)) / g
    
    plt.figure(figsize=(8,5))
    plt.plot(angles, ranges, label=f'v0 = {v0} m/s')
    plt.xlabel('Launch Angle (degrees)')
    plt.ylabel('Range (m)')
    plt.title('Projectile Range vs. Launch Angle')
    plt.legend()
    plt.grid()
    plt.show()

# Example parameters
v0 = 20  # Initial velocity in m/s
g = 9.81 # Gravity in m/s^2
projectile_range(v0, g)
```

### **5. Discussion on Limitations**
- **Air Resistance:** In real scenarios, drag significantly reduces range.
- **Uneven Terrain:** Changes in landing elevation affect results.
- **Wind Influence:** Can alter trajectory unpredictably.

### **Conclusion**
This analysis demonstrates the relationship between launch angle and range, emphasizing its significance in various real-world applications. Future studies can incorporate drag forces for more realistic modeling.

![alt text](image-1.png)
![alt text](image-2.png)

![alt text](image.png)