# T2.1 Compressed Crop Disease Classifier - AgriTech Edge-AI

## Project Overview
[cite_start]This repository contains a compact, quantized crop disease classifier designed for rural, low-bandwidth environments[cite: 8, 50]. [cite_start]The model identifies five classes: healthy, maize_rust, maize_blight, cassava_mosaic, and bean_spot[cite: 11].

## Technical Highlights
- [cite_start]**Backbone:** [MobileNetV3-Small / EfficientNet-B0 / ShuffleNet] [cite: 20]
- [cite_start]**Quantization:** INT8 [cite: 21]
- [cite_start]**Model Size:** < 10 MB (Actual: [Insert Size] MB) [cite: 21, 28]
- [cite_start]**Macro-F1 Score (Clean):** [Insert Score]% (Target: ≥80%) [cite: 20]
- [cite_start]**Macro-F1 Score (Field Robustness):** [Insert Score]% [cite: 25]

## Quick Start (Reproduction in ≤2 Commands)
Assuming a free Colab CPU environment:

1. **Setup & Install:**
   ```bash
   pip install -r requirements.txt
3. **Run Inference Service:**
   ```bash
   [cite_start]docker-compose up --build (or python service/app.py) [cite: 29, 31]

## API Usage
[cite_start]**Endpoint:** `POST /predict` [cite: 22]
**Example Curl Command:**
```bash
[cite_start]curl -X POST -F 'image=@samples/maize_rust_1.jpg' http://localhost:8000/predict [cite: 79]
