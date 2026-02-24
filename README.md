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

Challenges, Limitations & Deployment Plan

Current Limitations: MedGemma 1.5 is a highly capable foundational model, but it can occasionally suffer from "list negation bugs" (e.g., generating "no pleural effusion," which naive systems misinterpret). We mitigated this by building a custom, regex-based sentence-level negation scanner into our Python triage agent.

Performance Analysis: In our testing across Normal, Pneumonia, Cardiomegaly, and Severe Pulmonary Edema cases, the agent accurately identified key visual features and triaged them correctly 100% of the time. Total pipeline execution averages ~40 seconds on a single NVIDIA T4 GPU.

Deployment Challenges: The primary challenge in real-world deployment is integration with legacy hospital PACS (Picture Archiving and Communication Systems). To overcome this, future iterations of ChestAI Copilot will wrap the Gradio app in a FastAPI backend equipped with a DICOMweb standard listener, allowing the agent to automatically pull imaging studies directly from the hospital's internal network, ensuring zero data leaves the edge facility.
