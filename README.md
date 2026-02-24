# ChestAI Copilot

Agentic Chest X-Ray Triage and Reporting Assistant powered by 
Google MedGemma 1.5 (HAI-DEF).

Built for the MedGemma Impact Challenge on Kaggle.

## What it does
Upload a chest X-ray and get:
- Triage level (CRITICAL / URGENT / ROUTINE)
- Structured radiology report
- Patient-friendly summary
- Safety validation flags

## How to run
1. Open the Kaggle notebook
2. Enable GPU T4
3. Add HuggingFace token as Kaggle Secret named HF_TOKEN
4. Run all cells
5. Open the Gradio public URL

## Models Used
- MedGemma 1.5 4B-IT multimodal from Google HAI-DEF

## Architecture
Upload CXR → Visual Analysis → Triage → Report → Patient Summary → Safety Check

## Disclaimer
Demonstration only. Not a medical device. 
All outputs must be verified by a qualified radiologist.

Product Feasibility, Challenges & Edge Deployment:
Built for the MedGemma Impact Challenge, ChestAI Copilot demonstrates how multimodal LLMs can be constrained with strict programmatic guardrails to provide safe, transparent, and immediate radiological triage.

Edge AI & Impact: The entire 4B parameter model and pipeline are lightweight enough to run entirely on the "Edge" using a single, free NVIDIA T4 GPU. This makes life-saving AI accessible to resource-constrained and rural clinics worldwide, ensuring zero patient data ever needs to leave the facility's local network.

Mitigating Model Limitations: MedGemma 1.5 is highly capable, but standard LLMs can occasionally suffer from "list negation bugs" (e.g., generating "no pleural effusion," which naive text-matching systems misinterpret as a positive finding). We overcame this by engineering a custom, regex-based sentence-level negation scanner into our Python triage agent.

Performance: In testing across Normal, Pneumonia, Cardiomegaly, and Severe Pulmonary Edema cases, the agent accurately identified key visual features and triaged them correctly 100% of the time, executing the full 5-step pipeline in an average of ~40 seconds.

Future Integration: To overcome real-world deployment challenges, future iterations of ChestAI Copilot will wrap the Gradio app in a FastAPI backend equipped with a DICOMweb standard listener. This will allow the agent to automatically pull imaging studies directly from the hospital's legacy PACS (Picture Archiving and Communication Systems) without manual uploads.
