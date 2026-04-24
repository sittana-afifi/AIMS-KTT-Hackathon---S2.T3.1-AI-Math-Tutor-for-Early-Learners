# Process Log: S2.T3.1 AI Math Tutor (Day 3 Challenge)


## 🕒 Hour-by-Hour Timeline

| Time Segment | Activity | Key Outcome |
| :--- | :--- | :--- |
| **00:00 - 01:00** | Model Selection & Optimization | Selected TinyLlama-1.1B. Performed 4-bit GGUF quantization to meet the ≤ 75MB edge-device constraint. |
| **01:00 - 02:00** | Knowledge Tracing (KT) Logic | Implemented Bayesian Knowledge Tracing (BKT). Defined mastery nodes for Number Recognition, Addition, and Subtraction. |
| **02:00 - 03:00** | Child-Centric Interface & ASR | Developed Gradio demo with multilingual (Kinyarwanda/English) voice-first interaction for children aged 5-9. |
| **03:00 - 04:00** | Reporting & Privacy | Built the Parent/Teacher visual report generator. Implemented differential privacy noise for local SQLite progress syncing. |

---

## 🤖 LLM & Assistant Tool Declaration

I utilized **Gemini (Google)** as a coding assistant for the following technical tasks:
1. **Quantization Optimization:** To find the most aggressive quantization parameters that maintain numeracy logic while staying under the 75MB limit.
2. **Probabilistic Updates:** To verify the Bayesian update formula used in the Knowledge Tracing module.
3. **Multilingual UI Text:** To generate culturally appropriate scaffolding phrases in Kinyarwanda for the first 90 seconds of onboarding.

### Sample Prompts Sent:
1. *"Write a Python function for a Bayesian Knowledge Tracing (BKT) update step that calculates the new mastery probability given a student's binary response (correct/incorrect)."*
2. *"How can I reduce a TinyLlama-1.1B GGUF model to under 70MB without losing basic digit recognition capabilities?"*
3. *"Create a Gradio interface layout suitable for a 6-year-old, using large buttons, high-contrast icons, and an 'Auto-Record' audio feature."*

### Discarded Prompt:
* **Prompt:** *"Explain the entire educational theory of Knowledge Tracing in detail."*
* **Reason for Discarding:** I discarded this because it was too theoretical. I needed to focus on the *implementation* of the logic within the 4-hour time limit. I chose to research the theory independently and only prompt for the specific mathematical code implementation.

---

## 🧠 The Single Hardest Decision
The hardest decision was the **trade-off between ASR accuracy and the 75MB footprint**. I initially wanted to use a more robust Whisper-Small model for better recognition of high-pitched child voices, but it exceeded the footprint limit. I decided to stick with **Whisper-Tiny** and wrote a custom "Pre-processor" to normalize the audio pitch before inference. This decision allowed me to keep the entire tutor offline on a CPU-only tablet while maintaining acceptable (though not perfect) voice recognition for early learners.


