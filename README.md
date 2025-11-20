<!-- PROJECT BANNER -->
<p align="center">
  <img src="https://raw.githubusercontent.com/HeroicKrishna160905/Project-Endocrine/main/1763680295928~2.jpg" 
       alt="Project Endocrine Banner" width="100%">
</p>

<!-- BADGES -->
<p align="center">
  <img src="https://img.shields.io/badge/Status-Active-brightgreen?style=for-the-badge">
  <img src="https://img.shields.io/badge/Python-3.10%2B-blue?style=for-the-badge&logo=python">
  <img src="https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge">
  <img src="https://img.shields.io/badge/Platform-Colab-orange?style=for-the-badge&logo=google-colab">
  <img src="https://img.shields.io/badge/AI/RL-Ready-purple?style=for-the-badge">
  <img src="https://img.shields.io/github/stars/HeroicKrishna160905/Project-Endocrine?style=for-the-badge">
</p>

<!-- OPTIONAL: OPEN IN COLAB BADGE -->
<p align="center">
  <a href="https://colab.research.google.com/github/HeroicKrishna160905/Project-Endocrine/blob/main/Project_Endocrine.ipynb">
    <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab">
  </a>
</p>

<br>


# **Project–Endocrine**
### *A Complete Artificial Pancreas Simulator (APS) for Intelligent Glucose Regulation*

**Project-Endocrine** is a research-grade, end-to-end **Artificial Pancreas System (APS)** simulator.  
It models realistic Type-1 Diabetes physiology and implements intelligent controllers  
(PID, adaptive basal, safety layers, and Reinforcement Learning).

The framework serves as a **teaching tool**, **physiological simulator**, and a **research platform** for:

- Biomedical engineering  
- Control theory  
- Computational physiology  
- Machine Learning / Reinforcement Learning  
- Safety-critical systems  

The aim is to create a **transparent, interpretable, modular APS simulator** with academic and practical value.

---

# ⚙️ **System Architecture Overview**

```text
               ┌───────────────────────────────┐
               │         Meal Input             │
               └──────────────┬─────────────────┘
                              ↓
                   ┌────────────────────┐
                   │   Gut Absorption   │
                   └──────────┬─────────┘
                              ↓
                  ┌──────────────────────┐
                  │  Glucose Dynamics    │───► CGM Sensor (Noise)
                  └──────────┬───────────┘
                              ↑
             ┌──────────────────────────────────────┐
             │        Insulin Action (X)            │
             │  PK/PD + Delays + Nonlinear Effects  │
             └──────────────────┬───────────────────┘
                                ↑
                        ┌───────────────┐
                        │  Controller    │
                        │ PID / RL / APID│
                        └──────┬────────┘
                               ↑
                   ┌────────────────────────┐
                   │   Safety Layer (IOB,   │
                   │  Suspend, Rate Limits) │
                   └──────────┬────────────┘
                              ↑
                        Insulin Delivery
```

This is the closed-loop APS cycle used in research systems such as UVA/Padova, Control-IQ, and DiAs.

---

# 🧬 **1. Physiological Model (PK/PD)**

The simulator implements a realistic Type-1 Diabetes physiology model built from scratch.

### **Glucose Dynamics**
- Plasma glucose compartment  
- Endogenous glucose production (EGP)  
- Meal appearance via gut “carb pool”  
- Nonlinear glucose clearance  

### **Insulin Dynamics**
- Subcutaneous insulin absorption  
- Delayed plasma → effect-model transitions  
- Nonlinear insulin sensitivity  
- “Insulin effect” compartment (X)  

### **Variability & Noise**
Each patient is unique due to parameter randomization:

- insulin sensitivity  
- carb absorption rate  
- glucose clearance  
- insulin clearance  
- sensor noise  

This enables **true population-level generalization testing**.

---

# 🎛️ **2. Controller Architecture — Adaptive, Interpretable, Safe**

Project-Endocrine implements a **modular, interpretable controller**, featuring:

### **Adaptive PID Control**
- **P:** reacts to current glucose error  
- **I:** corrects long-term drift  
- **D:** anticipates trends  

### **Adaptive Basal Tuning**
Continuously adjusts basal insulin from historic glucose profiles.

### **Safety System**
- Predictive low-glucose suspend  
- Rapid-drop veto  
- Insulin-On-Board (IOB) constraints  
- Hard caps on insulin  
- Fail-safe clamps  
- Sensor noise protection  

The control system is modular so RL agents can replace or augment parts of the loop.

---

# 🤖 **3. Reinforcement Learning Compatibility**

The simulator is **fully RL-ready**, providing:

- Gym-style `step()` environment  
- Observation + state extraction  
- Reward functions  
- Multi-episode support  
- Multi-patient evaluation  

Designed for RL algorithms such as:

- PPO  
- SAC  
- TD3  
- Model-Based RL  

---

# 👥 **4. Cohort Simulation Engine (Population Testing)**

A key requirement for APS research is **robustness across diverse patients**.  
Project-Endocrine supports cohort evaluations with:

- **10**, **50**, **100**, or **200+ virtual subjects**

Each subject differs in:

- insulin sensitivity  
- glucose dynamics  
- meal timing & digestion  
- basal metabolic rate  
- noise seed  

Example 200-subject results:

- **Mean Time-in-Range:** ~86%  
- **TBR:** 0%  
- **Mean glucose:** ~141 mg/dL  
- **CV:** ~17%  

These results match early academic APS systems.

---

# 📊 **5. Visualisation Tools**

### **Single Subject**
- Glucose trajectory  
- Insulin delivery  
- Meal events  
- Prediction & variability  

### **Cohort Visuals**
- 50–200 subject overlays  
- TIR/TAR/CV histograms  
- Outlier detection  
- Animated glucose trajectories  

These visuals are ideal for research papers and demos.

---

# 🔧 **6. Installation**

```bash
git clone https://github.com/HeroicKrishna160905/Project-Endocrine.git
cd Project-Endocrine
pip install -r requirements.txt
```

Or use the included Colab notebook.

---

# 🚀 **7. Quickstart Examples**

### 👉 **Simulate a Single Subject**

```python
from endocrine.simulator import APS_Simulator

sim = APS_Simulator()
results = sim.run()
sim.plot()
```

### 👉 **Run a Multi-Subject Cohort**

```python
from endocrine.evaluation import run_cohort

stats, df = run_cohort(n_subjects=50)
print(stats)
df.head()
```

---

# 🔭 **8. Future Roadmap**

- Integration with FDA-approved **UVA/Padova simulator** (simglucose)  
- RL algorithms (PPO, SAC, MBRL)  
- CGM drift + bias modeling  
- Multi-day closed-loop simulation  
- Streamlit-based interactive dashboard  
- Documentation website  

---

# 🎯 **9. Why This Project Matters**

Automated diabetes control requires synergy across:

- physiology  
- control theory  
- reinforcement learning  
- safety engineering  
- human-centered design  

Project-Endocrine offers a **transparent, modular, research-grade playground**  
for understanding and advancing APS algorithms.

It serves as a:

- **teaching tool**  
- **research platform**  
- **prototype of next-generation closed-loop controllers**

---

# 🤝 **10. Contributions**

Pull requests, enhancements, bug reports, and discussions are welcome!

---

# 📝 **11. License**

**MIT License** — open for personal, academic, and research use.

---

# ❤️ **12. Acknowledgments**

Inspired by foundational work in:

- UVA/Padova T1D models  
- simglucose  
- Control-IQ & DiAs APS systems  
- Reinforcement Learning for APS  
- Biomedical control engineering  

Special appreciation to the global diabetes research community.
