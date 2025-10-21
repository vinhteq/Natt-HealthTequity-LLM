# 🧩 HealthTequity Case Study: Voice-Based Health Analytics Pipeline

This project showcases a **voice-enabled AI pipeline** where Spanish-language medical questions are answered using **GPT‑4o** and grounded in a personalized **blood pressure dataset**. It integrates **speech recognition (ASR)**, **translation**, **text-to-speech (TTS)**, and **LLM-based reasoning** into one seamless workflow.

---

## 🔧 Project Structure

The pipeline is implemented across **three Jupyter notebooks**, each responsible for a key step in the data generation and question-answering process.

---

### 📘 Notebook 1: `Generate_Synthetic_BP_Dataset.ipynb`

Generates a **synthetic 30-day blood pressure dataset** for an older adult.  
It simulates realistic fluctuations between normal and hypertensive readings and produces a structured CSV.

**Key Functions**
- Randomly generates systolic/diastolic readings by date
- Includes demographic information (age, sex)
- Saves reproducible CSV for downstream tasks

#### 🗂️ Outputs:
/data/synthetic_csv/synthetic_bp_95_female.csv


---

### 📘 Notebook 2: `Generate_Spanish_Audio.ipynb`

Processes a list of English questions and performs the following:

- 🌐 **Translates** them into Spanish using `deep-translator`
- 🔊 **Generates Spanish audio** (.wav) with `gTTS`
- 🧾 Creates a `ground_truth.csv` linking each audio file to its Spanish transcription

#### 🗂️ Outputs:
/data/synthetic_csv/ground_truth.csv
/data/Spanish_audio/*.wav


---

### 📘 Notebook 3: `Run_Audio_QA_Pipeline.ipynb` (Main Pipeline)

This notebook orchestrates the **end-to-end voice-to-insight flow**:

#### 🔹 Steps
1. **Transcription (ASR)** – Transcribes Spanish audio using OpenAI Whisper  
2. **Translation** – Converts Spanish → English (using Whisper or GPT-4o)  
3. **Question Answering** – Uses GPT-4o to analyze the blood-pressure CSV and answer each question  
4. **Speech Synthesis** – Generates Spanish audio answers via gTTS  
5. **Evaluation** – Computes WER / CER / SER metrics for input and output  
6. **Visualization** – Compares ASR performance via a bar-chart summary  

#### 📥 Inputs:
- `synthetic_bp_*.csv` (blood pressure data)
- `*.wav` files
-  `ground_truth.csv` (for ASR evaluation)

#### 🗂️ Outputs:
/results/llm_outputs/pipeline_results.csv ← full Q&A mapping
/results/tts_audio/answer_.wav ← synthesized Spanish answers
/results/evaluation_metrics/.csv ← WER / CER / SER scores
/results/evaluation_metrics/asr_comparison.png


---

---

## ⚙️ Technologies Used

| Component | Purpose | Tool |
|------------|----------|------|
| **ASR** | Speech-to-text for Spanish audio | OpenAI Whisper |
| **Translation** | Spanish → English or vice versa | Whisper / GPT-4o-mini |
| **LLM Reasoning** | Medical Q&A grounded in blood-pressure data | GPT-4o-mini |
| **TTS** | Spanish speech generation | gTTS + pydub |
| **Evaluation** | Computes WER / CER / SER metrics | JiWER + Levenshtein |
| **Visualization** | Displays comparative ASR accuracy | Matplotlib |

---

## 🗂 Folder Structure (Simplified)

```text
HealthTequity-LLM/
│
├── data/
│   ├── synthetic_csv/              ← CSV datasets + ground truth
│   └── Spanish_audio/              ← Input audio questions
│
├── results/
│   ├── llm_outputs/                ← GPT answers and translations
│   ├── tts_audio/                  ← Generated Spanish answers
│   └── evaluation_metrics/         ← WER/CER/SER + charts
│
├── Generate_Synthetic_BP_Dataset.ipynb
├── Generate_Spanish_Audio.ipynb
└── Run_Audio_QA_Pipeline.ipynb


## 📊 Flow Diagram

<p align="center">
  <img src="./assets/pipeline_diagram.png" width="900">
  <br>
  <em>End-to-end voice-to-insight pipeline integrating ASR, translation, LLM reasoning, and TTS.</em>
</p>

