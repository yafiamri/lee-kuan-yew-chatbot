# Lee Kuan Yew RAG Chatbot 🦁

**Live Demo:** [Try the Chatbot Here](https://cloud.flowiseai.com/chatbot/61202ea7-6845-4039-a1a4-296b9011a097)

## 📌 Overview & Capabilities

This project implements a Retrieval-Augmented Generation (RAG) chatbot designed to emulate the pragmatic, analytical, and authoritative persona of Lee Kuan Yew, Singapore's founding father. Based on conversational testing, the system demonstrates two core capabilities:
1.  **Historical Factual Retrieval:** Accurately retrieves specific, nuanced historical details from the source document (e.g., recounting the "empat mata" meetings with President Suharto).
2.  **Principle-Based Extrapolation:** When challenged with modern topics beyond its knowledge cutoff (like regulating AI in 2026), the bot successfully maintains its chronological guardrails while generating logical, character-driven frameworks based on core LKY principles (strict regulation, human capital, and infrastructure).

## 🛠️ Technical Approach & Implementation Notes

The chatbot was built using **Flowise** to construct a visual, no-code RAG pipeline. The architecture is designed to prioritize semantic context retention and strict persona adherence.

*   **Data Source:** The primary knowledge base is Lee Kuan Yew's memoir, *From Third World to First: The Singapore Story 1965-2000*.
*   **Text Splitting:** A **Recursive Character Text Splitter** was utilized instead of a standard token splitter. This is critical for narrative memoirs, as it preserves the semantic integrity of entire paragraphs and thoughts.
*   **Embeddings & Vector Store:** Text chunks are embedded using **HuggingFace Inference Embeddings** (`sentence-transformers/all-MiniLM-L6-v2`) and stored in an **In-Memory Vector Store** for rapid similarity searches.
*   **LLM Configuration:** The core reasoning engine is **Llama 3.1 8B Instant**, accessed via the **Groq API**. This model was selected for its superior capability to process long-context RAG inputs efficiently and its strong instruction-following skills, ensuring the persona remains unbroken.
*   **Memory:** A **Buffer Memory** node is integrated into the Conversational Retrieval QA Chain, allowing the bot to maintain multi-turn context naturally.

## 🚀 How to Run This Chatflow Locally

To interact with this chatbot on your own Flowise instance, follow these steps:

1.  **Prerequisites:** 
    *   Ensure you have [Flowise](https://flowiseai.com/) installed and running.
    *   Obtain a free API Key from [Groq](https://console.groq.com/).
2.  **Import the Chatflow:**
    *   Download the `Lee Kuan Yew Chatbot Chatflow.json` file from this repository.
    *   Open your Flowise dashboard and click **Add New** to create a blank canvas.
    *   Click the **Settings** icon (gear shape) in the top right corner and select **Load Chatflow**.
    *   Select the downloaded `.json` file to load the architecture.
3.  **Configure Credentials & Data:**
    *   Locate the **ChatGroq** node and input your Groq API Key in the credentials section.
    *   Locate the **PDF File** node and upload your copy of the source document (*From Third World to First*).
4.  **Save and Run:**
    *   Click the **Save** icon (floppy disk) in the top right corner. Flowise will process the document and populate the Vector Store.
    *   Click the **Chat** icon (purple dialogue bubble) to start interacting with the persona!
