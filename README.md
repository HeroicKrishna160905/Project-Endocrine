# **PROJECT–ENDOCRINE**
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

──────────────────────────────┐
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

Clone the repository:

```bash
git clone https://github.com/HeroicKrishna160905/Project-Endocrine.git
cd Project-Endocrine
pip install -r requirements.txt
