# 🧩 HealthTequity Case Study: Voice-Based Health Analytics Pipeline

This project showcases a **voice-enabled AI pipeline** where Spanish-language medical questions are answered using **GPT‑4o** and grounded in a personalized **blood pressure dataset**. It integrates **speech recognition (ASR)**, **translation**, **text-to-speech (TTS)**, and **LLM-based reasoning** into one seamless workflow.

---

## 🔧 Project Structure

The pipeline is implemented across **three Jupyter notebooks**, each responsible for a key step in the data generation and question-answering process.

---

### 📘 Notebook 1: `Generate_Synthetic_BP_Dataset.ipynb`

Generates a **synthetic blood pressure dataset** for an elderly patient (e.g., 95-year-old female) over 30 days, with realistic oscillation between normal and hypertensive readings.

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

### 📘 Notebook 3: `Run_Audio_QA_Pipeline.ipynb`

This is the **core pipeline** that:

1. 🗣️ Transcribes Spanish audio questions using **Whisper ASR**
2. 🤖 Feeds the transcription + CSV data into **GPT‑4o** to answer the question
3. 📊 Evaluates transcription quality via **WER**, **CER**, and **SER**
4. 📝 Saves all results, including generated answers and extracted fields

#### 📥 Inputs:
- `synthetic_bp_*.csv` (blood pressure data)
- `*.wav` files + `ground_truth.csv` (Spanish audio and transcripts)

#### 🗂️ Outputs:
pipeline_results.csv # question → GPT-4o answer + structured fields


---

## 📊 Flow Diagram


<img width="1536" height="1024" alt="ChatGPT Image Oct 20, 2025, 08_15_40 PM" src="https://github.com/user-attachments/assets/f173928a-2788-439a-a986-50ca362a89d7" />
