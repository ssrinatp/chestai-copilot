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
