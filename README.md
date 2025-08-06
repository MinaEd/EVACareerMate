# 🤖 EVA CareerMate

Welcome to **EVA CareerMate** — a smart, conversational assistant designed for **EVA Pharma**'s career platform. The bot provides detailed and interactive guidance about available job roles, required skills, growth opportunities, and much more using a combination of **NLP**, **RAG pipelines**, **semantic matching**, and **voice features**.

![Bot Logo](assets/botlogobig.png)

---

## 🚀 Features

### 📌 1. Job Scraping (Egypt-Only)
We dynamically **scrape the latest 10 job openings** from EVA’s official job board, filtering by **location = Egypt**, to keep our **manually collected dataset** fresh and relevant.

### 🧠 2. Intent & Entity Recognition
Using `spaCy`'s `en_core_web_sm` model, we've built:
- Custom **EntityRuler patterns** for job titles, degrees, locations, etc.
- An **intent detection function** that maps user input to known query types (e.g. welcome, job ask, compare, career growth, etc.)

This allows the bot to understand natural language queries with high accuracy.

### 🔍 3. Fuzzy Matching for Misspelled Job Titles
We implemented **partial and fuzzy string matching** using `RapidFuzz` to match even poorly typed or abbreviated job names — ensuring high tolerance for user typos and informal language.

### 📚 4. RAG Pipeline (Retrieval-Augmented Generation)
We use a full **LangChain RAG pipeline**:
- Text loading + chunking with `RecursiveCharacterTextSplitter`
- Vector storage with **ChromaDB**
- Semantic search using **HuggingFace sentence-transformers**
- LLM response generation using **T5-Large**

✅ Implemented chains for:
- `job_info`
- `career_path`
- `comparison between jobs`

⚠️ **Limitations:**
- **T5-Large** has response quality limitations; can be upgraded to a more fluent LLM.
- Prompt templates and chain routing need more tuning.
- Introduced a `rag_fallback` method to cover **"welcome"**, **"compare"**, or **"growth"** intents when traditional logic fails.

### 🧠 5. Contextual Awareness
The assistant **remembers the last job title and location**, enabling it to answer follow-up questions like "What are the skills for that?" without re-mentioning the job.

### 🎤 6. Audio Input & Output
Supports:
- **Speech-to-text (STT)** using `OpenAI Whisper`
- **Text-to-speech (TTS)** using `gTTS`

⚠️ Works fully in **Colab or Jupyter environments**, partial support in `.py` scripts.

### 🎨 7. Complete Gradio UI
A user-friendly **Gradio interface** is included with:
- Chat window
- Voice input button
- Bot avatar and emojis for enhanced UX
- Ready Examples

### ⚖️ 8. Job Comparison (LLM-Powered)
Users can compare 2 jobs side by side using our custom prompt chain.

⚠️ Limitation: Because we rely on an **open-source LLM**, some comparisons may be generic or miss subtle differences. More fine-tuning needed.

### 🧭 9. Career Path Guidance *(Work in Progress)*
A separate RAG chain is built to help users explore **career growth paths** based on job roles.

⚠️ Currently in development: needs better prompts and real-world datasets.

### 🧠 10. Full Intent-Based Routing
The bot detects and handles **all major intents**, such as:
- Welcome messages
- Job role inquiries
- Skills and requirements
- Location-specific queries
- Job comparisons
- Career advice
- Voice-based interactions

---


## 🗂️ Project Structure

- EVACareerMate/
  - `eva_careers_chatbot.ipynb` - Main notebook
  - `eva_careers_chatbot.py` - Converted script
  - `eva_current_openings.json` - Job dataset
  - `evaCareerMateUI.png` - UI sample
  - `requirements.txt` - Dependencies
  - `README.md` - Project documentation
  - assets/
    - `botlogobig.png`
    - `botlogoemoji.png`
    - `user.png`
  - conversation_samples_ss/
    - `conversationS1.png`
    - `conversationVoices1.png`
  - architecture/
    - `eva.drawio`
    - `raggg.png`
    - `evarag.png`

---

## ⚙️ Installation

```bash
git clone https://github.com/MinaEd/EVACareerMate.git
cd EVACareerMate
pip install -r requirements.txt
```

---

## 🧩 Limitations & Future Work
Replace T5-Large with a more fluent open LLM like Mistral or Zephyr

Improve job comparison quality and prompt design

Expand career path guidance

Support Arabic or multilingual input

--- 

## 🤝 Contributors
Mina Edwar Dawood – AI Engineer

---