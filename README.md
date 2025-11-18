# **Project-Endocrine**
### **A Complete Artificial Pancreas Simulator (APS) for Intelligent Glucose Regulation**

**Project-Endocrine** is a full-scale, research-grade **closed-loop Artificial Pancreas System (APS)** simulation framework built from first principles.  
It models the physiology of Type-1 Diabetes (T1D), implements intelligent insulin control algorithms, and provides a modular platform for experimentation, visualisation, and reinforcement learning research.

This project sits at the intersection of:
- **Biomedical engineering**
- **Control theory**
- **Computational physiology**
- **Machine learning / RL**
- **Safety-critical systems**

The goal is to create a **transparent, modular, academically rigorous APS simulator** that helps researchers explore how insulin automation can be improved for people with diabetes.

---

# 🔍 **1. Introduction & Project Motivation**

Diabetes management is fundamentally a **control problem under uncertainty**.  
Glucose levels fluctuate due to:

- meals  
- digestion variability  
- insulin absorption delays  
- stress, exercise  
- sensor noise  
- patient-specific physiology  

A true artificial pancreas must:
1. **sense** glucose  
2. **predict** physiology  
3. **act** with safe insulin doses  
4. **adapt** to changing conditions  

Project-Endocrine simulates this entire loop by combining:
- A realistic **pharmacokinetic/pharmacodynamic (PK/PD)** model  
- A robust **adaptive PID controller**  
- A multi-layer **safety system**  
- Cohort simulations across **hundreds of randomized virtual patients**  
- Optional integration with **Reinforcement Learning policies**

The goal is not only to simulate glucose regulation —  
but to **explain, teach, and enable experimentation**.

---

# 🧬 **2. Physiological Model (PK/PD) — A Hybrid Scientific Overview**

Most APS research uses the UVA/Padova model (FDA-approved).  
Project-Endocrine builds a similar conceptual core but written cleanly from scratch.

Our patient model includes:

### **Glucose dynamics**
- Plasma glucose compartment  
- Endogenous glucose production (EGP)  
- Meal absorption via a gut “carb pool” model  
- Nonlinear glucose clearance  

### **Insulin dynamics**
- Plasma insulin  
- Subcutaneous insulin absorption  
- Delays in insulin action  
- “Insulin effect” compartment (X)  

### **Noise + variability**
- CGM sensor noise  
- Inter-patient parameter randomization  
- Variability in:
  - insulin sensitivity  
  - gut absorption  
  - insulin clearance  
  - glucose clearance  

This ensures **every patient behaves differently**, just like in real-life diabetes.

A single run simulates one virtual diabetic patient.  
A cohort run (50–500 patients) tests controller generalization.

---

# 🎛️ **3. Controller Architecture — Interpretable, Adaptive, Safe**

Project-Endocrine prioritizes **interpretability** and **clinical realism**.

It uses an **Adaptive PID Controller** with:

### **PID Regulation**
- Proportional → responds to current glucose error  
- Integral → corrects long-term drift  
- Derivative → anticipates glucose trends  

### **Adaptive Basal Tuning**
Basal rate automatically adjusts based on historical glucose patterns —  
mimicking clinical basal titration but done algorithmically.

### **Safety Layers (crucial in APS research)**
- Predictive low-glucose suspend  
- Rapid-drop veto  
- Insulin-on-board (IOB) moderation  
- Hard caps on insulin delivery  
- Fail-safe clamp  

These are inspired by commercial closed-loop algorithms (e.g., Control-IQ, MiniMed, DiAs).

The controller has a clean API that also allows **RL controllers to replace or augment PID**.

---

# 🤖 **4. Reinforcement Learning Compatibility**

The simulator is designed to be fully RL-friendly:

- Step-by-step environment transitions  
- Observation vector extraction  
- Reward functions (glucose stability, TIR, insulin efficiency)  
- Plug-and-play controller interface  
- Multi-episode capability  
- Multi-patient evaluation for robustness  

This prepares Project-Endocrine for algorithms such as:
- PPO  
- SAC  
- TD3  
- Hybrid model-based RL  

The architecture mirrors research frameworks like **GluCoEnv** and **RL4T1D**, but remains more transparent and lightweight.

---

# 👥 **5. Cohort Simulation Engine (Population-Level Testing)**

A key requirement for APS research is generalization across **many** patients.

Project-Endocrine can simulate:
- **10**,  
- **50**,  
- **100**,  
- even **200+ virtual subjects** in a single batch.

Each subject has:
- unique glucose dynamics  
- unique insulin sensitivity  
- unique meal timings  
- unique noise seed  

This creates realistic stress-testing conditions.

### Example (200-subject run):
- **Mean Time-In-Range (TIR)** ≈ *86%*  
- **0% TBR (hypoglycemia)**  
- Strong robustness across random patients  

These results are comparable to early-stage closed-loop academic APS algorithms.

---

# 📊 **6. Visualisation Suite**

Project-Endocrine includes built-in visual tools:

### **Single-subject**
- Glucose vs time  
- Insulin delivery  
- Meal events  
- Glucose prediction  

### **Cohort**
- Overlay plots of 50–200 subjects  
- Heatmaps of control performance  
- Animated glucose trajectories  
- Outlier detection (worst-case dynamics)  

These visualizations are critical for:
- debugging  
- teaching  
- research presentations  
- publications  

---

# 🧪 **7. Metrics & Evaluation Framework**

Every run computes:

- **Time in Range (70–180 mg/dL)**  
- **Time Below Range (hypoglycemia)**  
- **Time Above Range**  
- **Mean glucose**  
- **Glucose variability**  
- **Coefficient of Variation (CV%)**  
- **Total insulin delivered**  
- **Peak glucose**  
- **Minimum glucose**  

These follow clinical standards used in APS trials.

---

# 🚀 **9. Getting Started**

Open the main notebook:


Inside, you can:
- simulate a patient  
- run large cohorts  
- visualize controller performance  
- experiment with PID tuning  
- try different meal conditions  
- prepare for RL-based extensions  

---

# 🔭 **10. Future Work (Roadmap)**

Project-Endocrine is actively evolving. Planned extensions include:

- **Integration with FDA-approved UVA/Padova simulator (simglucose)**  
- **RL-driven glucose control** (PPO, SAC, model-based RL)  
- **Enhanced CGM degradation models**  
- **Multi-day simulation engine**  
- **Continuous subcutaneous insulin absorption variants**  
- **Web-based Streamlit dashboard**  
- **Documentation site with full API**  

---

# 🎯 **11. Why This Project Matters**

Diabetes automation requires deep synergy between:
- physiology  
- control  
- safety  
- machine learning  
- human factors  

This project creates a **research playground** that allows engineers and students to:

- understand APS design  
- test control strategies  
- explore RL applications  
- study patient variability  
- visualize glucose dynamics  
- contribute to next-generation diabetes technology  

It is more than a simulator —  
it is a **teaching tool**, a **research platform**, and a **prototype for future APS algorithms**.

---

# 🤝 **12. Contributions**
Contributions, pull requests, and discussions are welcome!  
Whether you're into physiology, ML, control theory, or visualization — there is space here for exploration.

---

# 📝 **13. License**
MIT License — Permissive and open for academic and personal use.

---

# ❤️ **14. Acknowledgments**
Inspired by foundational work in:
- Artificial Pancreas Systems  
- UVA/Padova T1D models  
- simglucose  
- RL4T1D  
- Control theory & safety engineering  

Special appreciation to the diabetes research community.

---


