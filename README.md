# ChatScribeYT AI 🎬

**Transform any YouTube video into structured notes, key topics, and an interactive chatbot.**

VidSynth AI is a powerful tool built with Streamlit and Google's Gemini AI that helps you quickly digest and interact with video content. Instead of watching long videos, you can get concise summaries, detailed notes, or even ask specific questions about the video's content.

[![Streamlit App](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://chatscribeyt.streamlit.app/)

**➡️ [Live Demo: ChatScribeYT](https://chatscribeyt.streamlit.app/) ⬅️**

---

## ✨ Features

* **Chat with Video**: Load a video and ask questions directly. The AI provides answers based *only* on the video's content using a Retrieval-Augmented Generation (RAG) pipeline.
* **Automated Note-Taking**: Generate well-structured, bulleted notes that highlight the key takeaways, important facts, and examples from the video.
* **Key Topic Extraction**: Instantly get a list of the 5 most important topics discussed in the video, giving you a high-level overview in seconds.
* **Multilingual Support**: Supports videos in various languages (e.g., `hi`, `es`, `fr`). The tool automatically translates the transcript to English for seamless processing.

---

## ⚙️ How It Works

The application follows a streamlined process to transform video content into interactive formats:

1.  **Video ID Extraction**: It first extracts the unique video ID from the provided YouTube URL.
2.  **Transcript Fetching**: Using the `youtube-transcript-api`, it fetches the full transcript of the video in the specified language.
3.  **Translation (if needed)**: If the source language isn't English, it uses the Gemini model to perform a high-fidelity translation, preserving the original context and nuance.
4.  **Content Generation**:
    * **For Notes & Topics**: The transcript is sent to the Gemini model with carefully crafted prompts to summarize the key topics and generate structured notes.
    * **For Chat**: The transcript is broken down into smaller chunks using `Langchain`. These chunks are then converted into vector embeddings using Google's embedding model and stored in a `Chroma` vector store.
5.  **Interactive Q&A (RAG)**: When you ask a question, the application performs a similarity search on the vector store to find the most relevant context from the video. This context is then passed to the Gemini model along with your question to generate an accurate, context-aware answer.

---

## 🛠️ Tech Stack

* [cite_start]**Frontend**: Streamlit [cite: 1]
* [cite_start]**AI/LLM**: Google Gemini [cite: 1]
* [cite_start]**Core Framework**: LangChain [cite: 1]
* [cite_start]**Embeddings & Vector Store**: Google AI Embeddings & ChromaDB [cite: 1]
* [cite_start]**Transcript Service**: YouTube Transcript API [cite: 1]

---

## 🚀 Getting Started Locally

Follow these steps to set up and run the project on your local machine.

### Prerequisites

* Python 3.8+
* A Google AI API Key. You can get one from [Google AI Studio](https://makersuite.google.com/app/apikey).

### Installation

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/your-username/vidsynth-ai.git](https://github.com/your-username/vidsynth-ai.git)
    cd vidsynth-ai
    ```

2.  **Create a virtual environment:**
    ```bash
    # For macOS/Linux
    python3 -m venv venv
    source venv/bin/activate

    # For Windows
    python -m venv venv
    .\venv\Scripts\activate
    ```

3.  **Install the required dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

4.  **Set up your environment variables:**
    Create a file named `.env` in the root directory of the project and add your Google API key:
    ```
    GOOGLE_API_KEY="YOUR_API_KEY_HERE"
    ```

5.  **Run the Streamlit app:**
    ```bash
    streamlit run app.py
    ```
    The application will now be running at `http://localhost:8501`.

---

## Usage

1.  **Paste YouTube URL**: Enter the full URL of the YouTube video you want to process.
2.  **Enter Language Code**: Provide the language code for the video's audio (e.g., `en` for English, `hi` for Hindi).
3.  **Choose Task**:
    * Select **"Notes For You"** to get key topics and detailed notes.
    * Select **"Chat with Video"** to enable the interactive chatbot.
4.  **Start Processing**: Click the "✨ Start Processing" button and wait for the magic to happen!
5.  **Interact**: Read your notes or start asking questions in the chat interface.

---

## 📁 File Structure
```
.
├── app.py              # Main Streamlit application UI and flow
├── supporting_functions.py # Core logic for transcription, AI tasks, and RAG
├── requirements.txt    # Project dependencies
└── .env                # For storing API keys (not committed to Git)
```
