# Lightweight Chatbot with LangChain & HuggingFace

This repository contains a **lightweight chatbot prototype** built using **LangChain** and a Hugging Face **LLM** inside a Jupyter/Colab notebook.  
The chatbot is designed for **educational and testing purposes**, maintaining a conversational history and producing short, clear answers.  

---

## Features
- Conversational chatbot that supports multiple user turns.
- Built with **LangChain** message classes (`SystemMessage`, `HumanMessage`, `AIMessage`).
- Lightweight Hugging Face model integration for easy testing.
- Context preservation across questions and answers.
- Runs seamlessly in **Google Colab** (no API key required).
- Easy to extend with stronger models or a UI (e.g., Streamlit, Gradio).

---

##  Tech Stack
- **Python 3.11**
- [LangChain](https://www.langchain.com/) – for conversation handling
- [Transformers](https://huggingface.co/transformers/) – to load and run the LLM
- **Jupyter / Google Colab** – development environment

---

## Project Structure
```
.
├── Untitled2.ipynb      # Main notebook with chatbot implementation
├── README.md            # Project documentation
└── .gitignore           # Files excluded from version control
```

---

##  How It Works

### 1. System Context
The chatbot starts with a **SystemMessage** that defines its role and behavior:
```python
system_context = SystemMessage(
    content="You are a helpful assistant. Answer clearly and briefly."
)
chat_history = [system_context]
```

### 2. User Interaction
For each turn:
- The user provides input.
- A `HumanMessage` is appended to the history.
- The full conversation is formatted into a prompt.
- The model generates a response, wrapped in `AIMessage`.

### 3. Prompt Construction
```python
prompt_text = "\n".join([f"{m.type}: {m.content}" for m in chat_history])
ai_reply = llm.invoke(prompt_text)
```

### 4. Response Display
Each answer is printed clearly:
```python
print(f"\nAssistant : {ai_reply}")
```

---

##  Running the Notebook

### Step 1 — Clone the Repository
```bash
git clone https://github.com/Souhil301/AI-ChatBot.git
cd AI-ChatBot
```


### Step 3 — Run in Colab / Jupyter
Open `Untitled2.ipynb` in **Google Colab** or **Jupyter Notebook**, then run all cells step by step.

---

##  Example Interaction
```
User (1): What is Machine Learning?
Assistant: Machine learning is a branch of AI where computers learn from data and improve without explicit programming.

User (2): What is Bioinformatics?
Assistant: Bioinformatics applies computational tools to analyze biological data such as DNA and proteins.
```

---

## Next Steps
- Replace the base model with a more advanced Hugging Face LLM for improved accuracy.
- Add a **Streamlit** or **Gradio** interface for a simple web-based chatbot.
- Implement **LangChain ConversationBufferMemory** to preserve longer conversations.
- Fine-tune the model on domain-specific data for specialized Q&A.

---

## 👤 Author
**Souhil**  
---

## License
This project is released under the MIT License.
