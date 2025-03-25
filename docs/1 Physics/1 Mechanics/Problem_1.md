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


# 🚀 Neden En Uzun Menzil 45° Açısında Elde Edilir?

## 📌 Menzil Formülü ve Maksimum Noktası
Bir cismin fırlatma açısına göre yatayda aldığı toplam mesafe (**menzil**) şu formülle verilir:

\[
R = \frac{v_0^2 \sin(2\theta)}{g}
\]

Burada:
- **R** = Menzil (yatayda alınan toplam mesafe)
- **v₀** = İlk hız
- **θ** = Fırlatma açısı
- **g** = Yerçekimi ivmesi
- **sin(2θ)** = Açının menzile etkisini belirleyen fonksiyon

Maksimum menzil için **sin(2θ) fonksiyonunun en büyük olması gerekir**. Matematikte **sin(x) fonksiyonu 1'e ulaştığında maksimum değerini alır**, yani:

\[
\sin(2\theta) = 1 \Rightarrow 2\theta = 90^\]

Buradan:

\[
\theta = 45^
\]

🎯 **Sonuç:** **En uzun menzil, 45° açısında elde edilir!**

---

## 🧐 Daha Düşük ve Daha Yüksek Açılar Neden Daha Kötü?
Farklı açılarda fırlatılan cisimlerin hareketini inceleyelim:

### 🔻 Küçük Açılar (0° - 45°)
- **Daha fazla yatay hız var ama dikey hareket zayıf.**
- Cisim yere çok hızlı düşer ve menzil kısa olur.
- Örneğin, **30° açısında** fırlatma menzil sağlar ama erken düşüş nedeniyle maksimum mesafeye ulaşamaz.

### 🔺 Büyük Açılar (45° - 90°)
- **Daha fazla dikey hız var ama yatay hız azalır.**
- Cisim yükseğe çıkar ama fazla ileri gidemez.
- Örneğin, **60° açısında** fırlatılan cisim daha uzun süre havada kalır, ancak yatay hızı düşük olduğu için menzil kısalır.

📌 **45° açısı en iyi dengeyi sağlar!**

---

## 🎭 İlginç ve Eğlenceli Bilgiler

### 🎾 **Sporlarda 45° Kuralı**
- Futbol, basketbol veya tenis gibi sporlarda **maksimum mesafeye topu göndermek için 45° açısı tercih edilir**.
- Ancak, hava direnci olduğu için pratikte **40° - 43°** arası daha iyi olabilir!

### 🚀 **NASA ve Roket Bilimi**
- Uzay roketleri **doğrudan 45° ile fırlatılmaz** çünkü atmosferin etkisini azaltmak için farklı açılar kullanılır.
- Ancak **top mermileri ve kısa menzilli füzeler için** 45° en etkili açıdır!

### 🏹 **Okçuluk ve Balistik Füzeler**
- Okçular hedefe **en uzağa** atış yapmak istediklerinde **45°'ye yakın açılar kullanır**.
- Askerî topçular da **maksimum menzil için bu açıyı tercih eder**.

---

## 📊 Python ile Simülasyon: Açının Menzile Etkisi
Aşağıdaki Python kodu, farklı açılar için menzili hesaplayıp bir grafik çizer:

```python
import numpy as np
import matplotlib.pyplot as plt

def projectile_range(v0, g):
    angles = np.linspace(0, 90, 100)
    angles_rad = np.radians(angles)
    ranges = (v0**2 * np.sin(2 * angles_rad)) / g
    
    plt.figure(figsize=(8,5))
    plt.plot(angles, ranges, label=f'v0 = {v0} m/s')
    plt.axvline(45, color='r', linestyle='--', label='Maksimum Menzil: 45°')
    plt.xlabel('Fırlatma Açısı (derece)')
    plt.ylabel('Menzil (metre)')
    plt.title('Fırlatma Açısına Göre Menzil')
    plt.legend()
    plt.grid()
    plt.show()

# Örnek parametreler
v0 = 20  # İlk hız (m/s)
g = 9.81 # Yerçekimi (m/s²)
projectile_range(v0, g)
```

---

## 🚀 SONUÇ
✅ **45° açısı, en uzun menzil için ideal açıdır!**
✅ **Hem yatay hem dikey hız dengelendiği için maksimum mesafeye ulaşılır.**
✅ **Hava direnci gibi faktörler gerçek dünyada bu açıyı biraz değiştirebilir.**
✅ **Fizik, spor, askeri mühendislik ve roket bilimi gibi birçok alanda kullanılır!** 🎯🔥

![alt text](image.png)