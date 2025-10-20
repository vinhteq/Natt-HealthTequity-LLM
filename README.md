# 🩺 HealthTequity Voice Processing Pipeline

This repository demonstrates an end-to-end **Voice-to-Insight** system for the **HealthTequity case study**, which processes **Spanish medical speech** into **English insights** using ASR, translation, GPT-based analysis, and TTS.  
It also evaluates transcription performance through **WER, CER, and SER metrics**.

---

## 📘 Project Overview

| Stage | Description | Technology |
|-------|--------------|-------------|
| **1️⃣ Synthetic Data Generation** | Creates a 30-day blood pressure dataset for one individual | Python + Pandas |
| **2️⃣ Spanish Audio Generation** | Converts questions to Spanish speech and generates ground truth | gTTS + Deep Translator |
| **3️⃣ Voice Pipeline (Main Notebook)** | Runs transcription → translation → GPT analysis → TTS → ASR evaluation | Whisper, GPT-4o-mini, JiWER |

> The pipeline computes **Word Error Rate (WER)**, **Character Error Rate (CER)**, and **Sentence Error Rate (SER)** for both input and output sides.

---

## 📂 Repository Structure

```text
HealthTequity-LLM/
│
├── data/
│   ├── synthetic_csv/              ← Synthetic BP data + ground truth
│   │   ├── synthetic_bp_one_person.csv
│   │   └── ground_truth.csv
│   │
│   └── Spanish_audio/              ← Input Spanish audio files
│       ├── question_1_es.wav
│       ├── question_2_es.wav
│       └── ...
│
├── results/
│   ├── llm_outputs/                ← Transcriptions + LLM responses
│   ├── tts_audio/                  ← Spanish audio answers
│   └── evaluation_metrics/         ← WER/CER/SER + comparison chart
│
├
│ 1_BloodPressure_Generator.ipynb
│ 2_SpanishAudio_Generator.ipynb
│ 3_HealthTequity_VoicePipeline.ipynb
│
├── requirements.txt
└── README.md
