# 🎮 Control of the Monza System with Non-linear Methods

This project is part of the **Final Assignment** of the course **Non-linear Systems** from the Master’s in Automation and Robotics. Its goal is to model and control the Spanish mechanical arcade game **Monza** (1979) using non-linear control techniques.

---

## 📖 Description

**Monza** is an arcade game where the player inserts a coin at the top and must guide it to the bottom exit using a steering wheel that tilts a parabolic track. The challenge is to prevent the coin from falling off the sides.

This work includes:

- ✅ **Dynamic modeling** of the coin in its two phases: rail rolling and free fall.  
- ✅ **Linearization** of the non-linear system.  
- ✅ **Design and implementation** of an **adaptive controller** based on the **MIT Rule**.  
- ✅ **Simulink simulations** for different difficulty levels.  
- ✅ Comparison with a **PD controller** for higher difficulty levels.  

---

## 🧮 Model Equations

### Rolling on the rails

\[
g \cdot \sin\left(\arctan(-1.08x_{\text{parabola}}) + \theta\right) - \frac{\mu \cdot v_{\text{coin}}}{m} = a_{\text{coin}}
\]

### Free fall between rails

\[
y(t) = y_0 + V_{Y0} \cdot t + \frac{1}{2} g t^2
\]
\[
x(t) = x_0 + V_{X0} \cdot t
\]

### Transformation between reference systems

\[
x_{\text{parabola}} = x_{\text{reference}} \cdot \cos(\theta) + y_{\text{reference}} \cdot \sin(\theta)
\]
\[
y_{\text{reference}} = x_{\text{parabola}} \cdot \sin(\theta) + y_{\text{parabola}} \cdot \cos(\theta)
\]

---

## 🎯 Adaptive Control

A **model reference controller** was implemented using the **MIT Rule** to adjust controller parameters in real time.

### Linearized transfer function

\[
G(s) = \frac{-9.8}{s^2 + 0.89s - 10.584}
\]

### Underdamped reference model

\[
H(s) = \frac{1}{s^2 + 3.6s + 9}
\]

### Control law

\[
u = \theta_1 u_c - \theta_2 y
\]

### Adaptation rules (MIT Rule)

\[
\frac{d\theta_1}{dt} = -\gamma e \frac{\partial e}{\partial \theta_1}
\]
\[
\frac{d\theta_2}{dt} = -\gamma e \frac{\partial e}{\partial \theta_2}
\]

---

## 🧪 Results

### Completed levels

- ✅ Level 1: [Watch simulation](https://youtu.be/Re7pp1ZF9PQ)  
- ✅ Level 2: [Watch simulation](https://youtu.be/-ibi1006t-s)  
- ✅ Level 3: [Watch simulation](https://youtu.be/53Se8Av7464)  
- ✅ Level 4: [Watch simulation](https://youtu.be/xv7gUm6D_tI)  

### PD controller used at higher levels

\[
P + D \frac{N}{1 + N \frac{1}{s}}
\]

Parameters used: `P = 0.2`, `D = 0.05`, `N = 10`

---

## 🛠️ Tools Used

- MATLAB R2023a  
- Simulink  
- Control System Toolbox  

---

## 📁 Project Structure
```text
Monza_Control/
├── Simulink_Models/
│   ├── MiMonza.slx
├── MATLAB_Scripts/
│   ├── calculo.m
│   ├── pistas_completas.m
│   └── finalRieles.m
├── Report/
│   └── MartinLoring_NonlinearSystems_FinalProject.pdf
└── README.md
```

---

## 👨‍💻 **Author**

**Martín Loring Bueno**  
**Master’s in Automation and Robotics**  
**Polytechnic University of Madrid**  
**January 2025**  

---

## 📚 **References**

The references used are listed in the **attached PDF report**.  

---

## 📄 **License**

This project is for **academic purposes**. Any use outside this context must reference the **author**.  
