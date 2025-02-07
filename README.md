#

# Small Language Model (SLM) for Question Answering

## 📌 Project Overview

This project implements a **Small Language Model (SLM)** designed to answer questions based on a book provided as context. The system leverages:

- **PDF Text Extraction** for preprocessing.
- **FAISS-based Retrieval** to find relevant passages efficiently.
- **T5 Transformer Model** for generating answers.

By combining **retrieval-based search** with **generative modeling**, the system ensures accurate and contextual responses.

---

## 🚀 Features

✅ Extracts and preprocesses text from a book (PDF format).
✅ Uses **FAISS** for efficient context retrieval.
✅ Fine-tuned **T5-small** model for generating precise answers.
✅ Works with multiple user queries for interactive Q&A.
✅ Easy-to-run script with minimal dependencies.

---

## ⚙️ Installation

Clone the repository and install dependencies:

```sh
# Clone the repository
git clone https://github.com/your-username/slm-qa.git
cd slm-qa

# Create a virtual environment (optional but recommended)
python -m venv venv
source venv/bin/activate  # On Windows use: venv\Scripts\activate

# Install required libraries
pip install -r requirements.txt
```

---

## 📜 Dependencies

This project requires the following Python libraries:

```sh
pip install torch transformers sentencepiece faiss-cpu spacy pymupdf sentence-transformers
```

Additionally, download the **spaCy language model**:

```sh
python -m spacy download en_core_web_sm
```

---

## 🎯 How It Works

1. **Extract Text from Book (PDF)**
   - The text is extracted and tokenized using **spaCy**.
2. **Build FAISS Index for Fast Retrieval**
   - Sentences are converted into embeddings using **MiniLM**.
   - FAISS is used to store and efficiently search relevant sentences.
3. **Generate Answers Using T5 Model**
   - The system retrieves top-K relevant sentences.
   - It forms an input prompt: `"question: <query> context: <retrieved_text>"`.
   - The **T5-small** model generates the best possible answer.

---

## 🛠 Usage

### **1️⃣ Index the Book**

```python
from process_book import build_faiss_index
build_faiss_index("ebook.pdf")  # Generates FAISS index
```

### **2️⃣ Ask Questions**

```python
from qa_system import ask_question
question = "What is the main theme of the book?"
answer = ask_question(question)
print(f"Q: {question}\nA: {answer}")
```

---

## 📊 Sample Output

```
Q: What is the main theme of the book?
A: The book explores the concept of resilience and human perseverance.
```

---

## 📈 Evaluation

The system is evaluated based on:
✅ **Retrieval Accuracy**: FAISS retrieves the most relevant sentences.
✅ **Answer Coherence**: T5 generates meaningful, well-formed responses.
✅ **Performance on Different Queries**: Tested with factual, descriptive, and inference-based questions.

---

## 🔥 Key Learnings

- **Text Preprocessing is Crucial**: Clean text improves model performance.
- **Efficient Retrieval is Necessary**: FAISS significantly speeds up context search.
- **Context Matters**: Answer accuracy depends on relevant passage retrieval.
- **Limitations**: The model might struggle with ambiguous or extremely detailed queries.

---

## 🤝 Contributing

Feel free to open issues or pull requests for improvements!

---

## 📜 License

This project is licensed under the MIT License.

---

## 📩 Contact

For any queries, reach out at [your.email@example.com](mailto\:your.email@example.com).

