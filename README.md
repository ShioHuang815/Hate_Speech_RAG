# **Retrieval-Augmented Generation (RAG) with LLMs**

## **Project Overview**
This project implements **Retrieval-Augmented Generation (RAG)** to improve the performance of **Large Language Models (LLMs)** in answering questions related to **hate speech detection and offensive language classification**. The system integrates **vector-based retrieval from Pinecone** with advanced retrieval and summarization techniques to enhance response accuracy, contextual depth, and efficiency.

## **Features**
### ✅ **Multiple Approaches to LLM Question-Answering**
We compare four different approaches to generating responses:
1. **Baseline LLM (No Retrieval)** – Uses a standard LLM without external knowledge.
2. **Simple RAG** – Retrieves relevant documents from a Pinecone vector store before generating responses.
3. **HyDE-Enhanced RAG** – Uses **Hypothetical Document Embeddings (HyDE)** to improve retrieval.
4. **Summarization-Enhanced RAG** – Summarizes retrieved documents before passing them to the LLM.

### ✅ **Key Enhancements**
- **HyDE (Hypothetical Document Embeddings):** Generates a hypothetical response to improve retrieval quality.
- **Summarization:** Reduces noise in retrieved documents, ensuring concise and relevant outputs.
- **Query Filtering:** Improves retrieval by selecting the most informative documents.

## **Dataset Used**
The dataset consists of tweets classified into:
- **Hate Speech (Class 0)**
- **Offensive Language (Class 1)**
- **Neutral Speech (Class 2)**
Each tweet is embedded and stored in **Pinecone** to enable efficient similarity-based retrieval.

## **Pipeline Architecture**
1. **User Query →** The user inputs a question.
2. **Query Processing →** Optionally restructured using HyDE.
3. **Vector Retrieval →** Relevant tweets are retrieved from Pinecone.
4. **Summarization (if enabled) →** Condenses key points from retrieved text.
5. **LLM Response Generation →** The final answer is generated using an LLM (e.g., GPT-4).

## **Installation & Setup**
### **Prerequisites**
Ensure you have the following installed:
- Python 3.8+
- `pip install -r requirements.txt`
- OpenAI API key (for LLM calls)
- Pinecone API key (for vector retrieval)

### **Setup Instructions**
1. **Clone the Repository:**
   ```bash
   git clone https://github.com/your-repo/rag-project.git
   cd rag-project
   ```
2. **Install Dependencies:**
   ```bash
   pip install -r requirements.txt
   ```
3. **Configure API Keys:**
   - Set your OpenAI & Pinecone API keys in an `.env` file or export them as environment variables.

## **Usage**
### **Running the Pipeline**
To execute the RAG system:
```python
python main.py --method rag_hyde  # Options: baseline, rag_simple, rag_hyde, rag_summarization
```
### **Jupyter Notebook Option**
You can also explore and test the different approaches using:
```bash
jupyter notebook rag_experiments.ipynb
```

## **Results and Comparisons**
We evaluated the effectiveness of each approach using **10-15 complex prompts**. The results are as follows:

| Approach               | Specificity | Context Relevance | Conciseness | Computational Cost |
|------------------------|-------------|------------------|------------|------------------|
| **Baseline LLM**       | ❌ Low      | ❌ Low           | ✅ High     | ✅ Low           |
| **Simple RAG**        | ✅ Medium   | ✅ Medium        | ✅ High     | ✅ Low           |
| **HyDE RAG**          | ✅ High     | ✅ High          | ❌ Medium  | ❌ High         |
| **Summarization RAG** | ✅ High     | ✅ High          | ✅ High     | ✅ Medium       |

## **Future Improvements**
- 🔍 **Hybrid Search**: Combining keyword search with vector retrieval for better accuracy.
- 🏎️ **Performance Optimization**: Reducing inference time through caching techniques.
- 🛠️ **Fine-Tuned LLM**: Training a domain-specific model for better classification.

## **License**
This project is licensed under the **MIT License**.


