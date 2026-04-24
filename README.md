# Mwenyura AI [ A smiling child is a learning child ] - An Adaptive Multilingual Math Tutor for Early Learners (P1-P3)

## 📌 Project Overview
Mwenyura AI is an on-device, offline EdTech solution designed for children aged 5-9 in low-resource settings. It provides personalized numeracy support (number recognition, counting, and basic operations) using adaptive intelligence. It specifically addresses the "language transition" hurdle for learners moving from Kinyarwanda/French to English instruction.

### Core Pillars
* **Adaptive Learning:** Uses [BKT/DKT] Knowledge Tracing to adjust difficulty in real-time based on learner mastery.
* **Edge AI Performance:** Fully quantized model suite running on CPU under a **75MB footprint**.
* **Child-Centric UX:** Voice-first interaction adapted for child speech patterns with multilingual code-switching support.
* **Privacy-First:** Local progress tracking with differentially private syncing for shared devices.

---

## 🚀 Quick Start (Reproducibility)
To run the tutor demo on a standard Colab CPU environment or local machine:


### 1. Install dependencies (Optimized for on-device CPU inference)

```bash
pip install -r requirements.txt
```

### 2. Launch the Gradio child-facing interface
```bash
python demo.py
```

---

## 📊 Technical Specifications & Footprint
The system is strictly optimized to meet the **< 75MB** constraint for deployment on low-cost hardware.

| Component | Choice | Optimization | Size (MB) |
| :--- | :--- | :--- | :--- |
| **LLM Engine** | TinyLlama-1.1B | GGUF 4-bit Quantization | ~XX MB |
| **ASR (Voice)** | Whisper-Tiny | Adapted for Child Pitch | ~XX MB |
| **Knowledge Tracing**| Bayesian Knowledge Tracing | Probabilistic Inference | < 1 MB |
| **TOTAL** | | | **[Insert Total] MB** |

* **Hardware Target:** CPU-only (No GPU required).
* **Latency:** < 2.5s end-to-end response time on standard Colab CPU.

---

## 🧠 Knowledge Tracing & Adaptive Logic
The tutor tracks learner progress across three mastery nodes: **Number Recognition**, **Addition**, and **Subtraction**. 

* **Model Type:** Bayesian Knowledge Tracing (BKT).
* **Evaluation:** Next-response correctness prediction achieved an **AUC of [Insert Score]**.
* **Adaptation Strategy:** If mastery probability $P(L_n) < 0.7$, the tutor provides visual scaffolding; if $P(L_n) > 0.95$, it transitions the learner to the next complexity level or instruction language.

---

## 🌍 Product & Business Adaptation
### 1. The First 90 Seconds
The onboarding starts with a friendly voice greeting in **Kinyarwanda** to reduce learner anxiety. The first task is a "non-punishing" counting exercise. If the child is silent for 10 seconds, the tutor provides a verbal "scaffolded hint" rather than an error message to encourage persistence.

### 2. Community Deployment (Shared Tablets)
Designed for the "1 tablet per 3 children" classroom model:
* **Differential Privacy:** Local SQLite progress data is injected with Laplacian noise before any potential sync to protect individual learner identities.
* **Profile Switching:** High-contrast visual avatars allow children to select their profile without needing to read text.

### 3. Parent/Teacher Reporting
A 1-page visual report is generated for parents:
* **Low-Literacy Design:** Uses progress bars and agricultural icons (growth symbols) to represent academic progress.
* **Audio Summary:** Includes a text-to-speech button that reads the child's strengths and areas for improvement in the local dialect.

---

## 📂 Repository Structure
```text
├── data/                # Generated data script 
├── models/              # Quantized weights and BKT parameters
├── tutor/               # Core modules: ASR, LLM, and Knowledge Tracing
├── demo.py              # Gradio-based child interaction demo
├── parent_report.py     # Visual/Audio report generation script
├── requirements.txt     # Minimal dependencies for CPU inference
├── process_log.md       # MANDATORY: Timeline and LLM usage declaration
├── SIGNED.md            # Verbatim Honor Code signature
├── BUSINESS_STRATEGY.md # Product & Business adaptation
├── LICENSE.md 
├── README.md 
└── .gitignore          

