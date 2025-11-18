# **Project-Endocrine**
### **A Complete Artificial Pancreas Simulator (APS) for Intelligent Glucose Regulation**

Project-Endocrine is a fully functional **closed-loop Artificial Pancreas System (APS)** designed to simulate blood glucose dynamics and automated insulin delivery in people with Type-1 Diabetes (T1D).  
It combines **physiological modeling**, **adaptive PID control**, **basal learning**, **safety constraints**, and **reinforcement learning compatibility** into a unified, research-grade environment.

This simulator is built to be **transparent**, **modular**, and **easily extendable** — ideal for academic research, experimentation, and future integration with FDA-approved virtual patient models.

---

## ⭐ **Key Features**

### **1️⃣ Physiological Patient Model (PK/PD)**
A realistic glucose–insulin model including:
- Plasma glucose compartment  
- Plasma insulin compartment  
- Insulin action dynamics  
- Gut absorption & digestion  
- Sensor noise  
- Endogenous glucose production  
- Randomized inter-patient variability  
- Meal absorption delays and nonlinearity  

This allows simulation of realistic T1D patient behavior across individuals.

---

### **2️⃣ Adaptive PID-Based Control Algorithm**
The APS controller integrates:
- **Proportional–Integral–Derivative (PID)** regulation  
- **Adaptive basal adjustment**  
- **Derivative smoothing**  
- **Active insulin (IOB) modeling**  
- **Predictive safety constraints**  
- **Insulin-on-board veto system**

The controller is intentionally kept **interpretable** and **clinically aligned**, making it suitable for educational, research, and prototyping applications.

---

### **3️⃣ Safety Layer**
A multi-step safety module prevents dangerous insulin delivery:
- Predictive low-glucose suspend  
- Hypoglycemia veto logic  
- Maximum insulin caps  
- Insulin-on-board moderation  
- Protection against rapid glucose drops  

Safety is a critical element in any APS, and this implementation follows the principles seen in commercial closed-loop systems.

---

### **4️⃣ Reinforcement Learning Ready**
The simulator is fully compatible with RL-based controllers.  
The structure allows:
- Observation/state extraction  
- Reward design  
- Step-by-step environment transitions  
- Multi-patient evaluation  
- Plug-and-play policy integration  

This makes Project-Endocrine suitable for future RL experiments such as PPO, SAC, or hybrid controllers.

---

### **5️⃣ Cohort Simulation Engine**
Run large-scale simulations across **tens or hundreds of virtual patients**:

- Random physiological parameters  
- Random meal schedules  
- Random noise seeds  
- 24-hour or multi-day simulation  
- Batch summary metrics (TIR, TAR, hypo %, mean glucose, CV, etc.)

Example performance across 200 randomized subjects:
- **Mean TIR ≈ 86%**  
- **0% Time Below Range (TBR)**  
- **Stable control across varied patients**

---

### **6️⃣ Visualization Tools**
- Single-patient glucose/insulin plots  
- Multi-subject overlay plots  
- Animated glucose trajectories  
- Cohort heatmaps & statistical summaries  

Animations help inspect controller stability, meal disturbances, and patient variability.

---
Inside, you can:
- Simulate a single virtual patient  
- Run a 200-subject cohort  
- Visualize glucose/insulin trajectories  
- Modify PID parameters  
- Test RL-ready structure  

---

## 📈 **Metrics & Evaluation**
The simulator computes:
- **Time in Range (70–180 mg/dL)**  
- **Time Above Range**  
- **Time Below Range**  
- **Mean glucose**  
- **Standard deviation (variability)**  
- **Coefficient of variation (CV%)**  
- **Total insulin delivered**  

These metrics are standard in T1D APS research.

---

## 🔭 **Future Work**
Project-Endocrine is actively evolving. Planned additions include:
- Integration with **FDA-approved UVA/Padova simulator (simglucose)**
- Full **Reinforcement Learning controller** (PPO / SAC)
- Advanced CGM degradation & calibration error models  
- Multi-day simulation loops  
- Uploadable meal profiles  
- Web-based interactive dashboard  

---

## 🧩 **Why This Project Matters**
This simulator bridges:
- Clinical insight  
- Modern control theory  
- Artificial intelligence  
- Realistic glucose physiology  
- Safety-critical design  

It provides a clean, open-source foundation for students, engineers, and researchers exploring **Artificial Pancreas Systems**, **digital twins**, **RL-based healthcare**, and **cyber-physical systems**.

---

## 🤝 **Contributions**
Contributions, issues, and pull requests are welcome.  
Feel free to fork the repository and build upon it.

---

## 📝 **License**
MIT License — Feel free to use and modify the project with proper attribution.

---

## ❤️ **Acknowledgments**
This project is inspired by academic work in:
- Artificial pancreas research  
- Control theory  
- Reinforcement learning for healthcare  
- Physiological modeling  

Special thanks to the diabetes research community for their foundational contributions.



