# AI-Powered RAG Chatbot with Semantic Memory & Web Search Fallback

A full-stack Retrieval-Augmented Generation (RAG) chatbot that delivers accurate, context-aware answers by combining semantic document retrieval with intelligent web search fallback.

The system first attempts to answer queries using embedded knowledge stored in a vector database. When relevant context is unavailable or confidence is low, it automatically falls back to live web search to ensure reliable responses even for out-of-distribution questions.

---

## Key Capabilities

- Retrieval-Augmented Generation (RAG) for grounded responses  
- Semantic memory using vector embeddings  
- Intelligent web search fallback for unseen queries  
- Confidence-aware response selection  
- FastAPI backend with modular service design  
- React + Vite frontend for interactive chat experience  
- Environment-based configuration for secure secret handling  
- Fully Dockerized for reproducible local execution  

---

## High-Level Architecture

User queries flow through a React frontend to a FastAPI backend.  
The backend performs semantic retrieval against a vector database, evaluates retrieval confidence, and either generates a response from retrieved context or augments the response with live web search results before passing the final answer back to the user.

This hybrid design ensures both accuracy and robustness.

---

## Running the Application (Without Docker)
Start Backend
bash
Copy code
pip install -r requirements.txt
uvicorn app.main:app --reload
Backend runs at:

http://localhost:8000

http://localhost:8000/docs (API documentation)

Start Frontend
bash
Copy code
npm install
npm run dev
Frontend runs at:

http://localhost:5173

## Running with Docker (Recommended)
The entire system can be launched using Docker Compose:

bash
Copy code
docker-compose up --build
This starts both frontend and backend services with all dependencies configured automatically.

## Retrieval & Fallback Logic
User query is embedded and searched in the vector database

Retrieved results are scored for semantic relevance

If relevance exceeds a confidence threshold, a response is generated using retrieved context

If relevance is low, the system performs live web search and augments the response

The final answer is generated using an LLM and returned to the user

This design improves answer quality while gracefully handling unseen or evolving topics.