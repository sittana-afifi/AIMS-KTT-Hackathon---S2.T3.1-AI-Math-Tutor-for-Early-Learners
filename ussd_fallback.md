# 📱 USSD Fallback & Field-UX Design

## 1. Problem Statement: The Connectivity Gap
While the **INT8 Quantized Model** is optimized for edge devices, many smallholder farmers in rural areas use feature phones (non-smartphones) or have limited access to mobile data. The USSD fallback ensures that AI-driven diagnostics are inclusive and accessible to 100% of the community.

## 2. System Architecture
Our solution uses a **"Village Lead"** model to bridge the digital divide:

1.  **Local Inference:** A Village Extension Officer (with a smartphone) uses the app to scan a crop. The <10MB model runs **completely offline**.
2.  **Data Sync:** When the officer reaches a 2G/3G signal area, the results (Disease Class + Confidence + Farm ID) are pushed to the central database.
3.  **USSD Retrieval:** The farmer accesses these results on their own basic phone by dialing a shortcode (**`*123#`**).

## 3. USSD Menu Map (*123#)
The USSD gateway (integrated via Irembo or a local Telco API) provides the following interface in Kinyarwanda/English:

**Main Menu:**

`1. Reba Ubuzima bw'Imyaka (View Crop Health)`

`2. Inama ku buhinzi (Treatment Advice)`

`3. Hamagara Umuhinzi-mwiza (Request Call from Agronomist)`

**If '1' is selected:**

`Last Scan: 2024-04-24`

`Result: Maize Rust (89% Confidence)`

`Status: Action Required`

`Press 1 for Treatment Steps.`

## 4. Automated SMS Alert Logic
To provide proactive support, the system triggers an SMS immediately after the Village Officer's data syncs:

> **SMS Template:** > "AMAKURU [Farmer Name]! Ikizamini cy’ibigori cyo kuwa kabiri cyerekanye **Maize Rust**. Inama: Tera umuti wa [Product Name] vuba. Irinde kuvomera amababi hejuru kugira ngo indwara idakwira. Kanda *123# usobanukirwa birambuye."

## 5. Field Robustness & Human-in-the-Loop
Given the noisy nature of field shots (blur/lighting), we implement a **Confidence Threshold**:
* **High Confidence (>85%):** Automated SMS/USSD result sent immediately.
* **Medium Confidence (50-85%):** Flagged for review by a remote agronomist via a web dashboard before the farmer is notified.
* **Low Confidence (<50%):** The Village Lead is prompted to retake the photo with better lighting.
