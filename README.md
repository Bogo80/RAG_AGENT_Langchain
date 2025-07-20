
# 🧠 Setup Guide for RAG Agent with LLM Grading + Web Fallback

Follow these instructions to get your environment ready for using the RAG agent with document grading and web fallback.

If you run into issues with the setup (corporate firewall, permissions, etc.), contact your LangChain representative and we’ll help with a workaround.

---

## ✅ Create a Python Environment & Install Dependencies

```bash
$ cd rag-agent-project
$ python3 -m venv rag-env
$ source rag-env/bin/activate
$ pip install -r requirements.txt
```

---

## 📓 Running the Notebook

```bash
$ jupyter notebook
```

Then open `RAG_with_RAGPrompt_and_FunctionDescriptions.ipynb`.

---

## 🔐 API Keys Setup

Create a `.env` file in the project root and set:

```env
OPENAI_API_KEY=your-openai-key
TAVILY_API_KEY=your-tavily-key
LANGCHAIN_API_KEY=your-langsmith-key
LANGCHAIN_TRACING_V2=true
```

> 🔑 You can get your OpenAI API key [here](https://platform.openai.com/account/api-keys)  
> 🧭 Tavily signup is [here](https://www.tavily.com) — free and fast  
> 🔍 LangSmith setup guide is [here](https://docs.smith.langchain.com/)

---

## 🔄 Workflow Summary

1. Documents are loaded from `Dublin_Restaurants_2025.csv`
2. Top matches are retrieved using vector search
3. A GPT-4-based LLM checks document relevance (`grade_documents`)
4. If relevant → answer using RAG  
   If not → search the web via Tavily and answer
5. The result is shown in clean Markdown format

---

## 🧪 Run a Sample Query

```python
result = rag_app.invoke({
    "question": "Any recommendations for a Polish restaurant in Dublin?"
})
Markdown(result["generation"])
```

---

Enjoy building smart, hybrid RAG agents! 🚀
