**Name:** Manan Koradiya
**Role:** Agent Architect

**Personal Responsibilities & Implemented Components:**
* Engineered the `tools.py` file, wrapping Snowflake SQL queries and Python risk-assessment logic into LLM-callable functions.
* Implemented the dynamic Multi-Factor Authentication (MFA) passthrough from the Streamlit UI to the Snowflake connector.
* Designed the multi-step execution loop in `agent.py` using the `google-genai` SDK.

**Links to Commits:**
* (https://github.com/Manan151179/BIG_DATA_LAB6/commit/7c4ea6ef3a560c1832bbd5e177517ba253e99394#diff-2171db0cf84575462627421658645f2d76c71fb0e13dceb297c41e443bfd8af7)

**Technical Reflection:**
Integrating the new Gemini SDK natively without relying on an external framework like LangChain taught me the mechanics of manual tool dispatching. The biggest technical hurdle was managing the Snowflake MFA requirement within a continuous agent loop. I overcame this by capturing the TOTP code in the Streamlit session state and passing it directly into the tool functions, allowing the agent to authenticate dynamically without crashing.

---

**Name:** Joe Doan
**Role:** Data Engineer

**Personal Responsibilities & Implemented Components:**
* Developed the `ingest.py` data pipeline for parsing, chunking, and embedding raw legal documents (lease agreements).
* Configured the Snowflake data warehouse schema (`CONTRACT_CHUNKS` table) and optimized insert statements for vectorized data.
* Handled the initial vector store implementation and search index creation.


**Technical Reflection:**
Working on the data ingestion pipeline highlighted the challenges of processing unstructured legal text. A key learning outcome was mastering Snowflake's vector data types and efficiently chunking long PDFs/text files to maintain semantic context for the RAG pipeline.

---

**Name:** Aditya Naredla
**Role:** Frontend & Application Integration Lead

**Personal Responsibilities & Implemented Components:**
* Designed and built the Streamlit chat interface in `app.py`, providing a seamless user experience for querying the agent.
* Implemented the chat history state management and integrated the dynamic MFA input form.
* Handled the asynchronous streaming of agent responses back to the UI.


**Technical Reflection:**
Creating the user interface required bridging the gap between a stateless web framework (Streamlit) and a stateful, iterative agent loop. The biggest challenge was managing session state correctly so that context and authentication parameters persisted across user interactions without causing unexpected re-renders.

---

**Name:** Ruixuan Hou
**Role:** Model Evaluation & Prompt Engineer

**Personal Responsibilities & Implemented Components:**
* Conducted comparative analysis between Gemini 2.5 Flash and local models (e.g., Ollama) documented in the Phase 3 evaluation notebooks (`phase_3.ipynb`).
* Generated evaluation datasets (`phase3_eval_results*.csv`) and established performance metrics for risk assessment accuracy and retrieval context relevance.
* Refined the system prompts in `agent.py` to ensure the agent follows the "Recall-Then-Reason" paradigm strictly without hallucinating.


**Technical Reflection:**
Evaluating generative models on domain-specific legal texts taught me that a robust retrieval system is just as crucial as the LLM itself. Iterating on the system prompts, I learned how sensitive the agent's multi-step plan is to constraints formatting, ultimately improving the reliability of the compliance audits.
