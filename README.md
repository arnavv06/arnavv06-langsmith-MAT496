# **Intro to Langsmith**

---

## Module 0

[arnavv06-langsmith-MAT496/notebooks/module_0 at main · arnavv06/arnavv06-langsmith-MAT496](https://github.com/arnavv06/arnavv06-langsmith-MAT496/tree/main/notebooks/module_0)

Cloned a github repository and implemented a basic RAG application by running it. Learned how to implement a basic RAG application, loading a .env file instead of hardcoding variables. Created a retriever vector that creates and provides a searchable knowledge base from the LangSmith documentation. Pretty much all of the basics were taught in class.

##### rag_application.ipynb

[arnavv06-langsmith-MAT496/notebooks/module_0/rag_application.ipynb at main · arnavv06/arnavv06-langsmith-MAT496](https://github.com/arnavv06/arnavv06-langsmith-MAT496/blob/main/notebooks/module_0/rag_application.ipynb)

Changes made:

* Used **groq** model provider since i'm familiar with it in class.
* Used a free and fast **llama-3.1-8b-instant** model
* Udded more test questions of my own to check the the working of the application

##### utils.py

[arnavv06-langsmith-MAT496/notebooks/module_0/utils.py at main · arnavv06/arnavv06-langsmith-MAT496](https://github.com/arnavv06/arnavv06-langsmith-MAT496/blob/main/notebooks/module_0/utils.py)

Changes made:

* Changed the entire code to use a **HuggingFaceEmbeddings** embedder
* Used model sentence-transformers/all-MiniLM-L6-v2.
* Created a retriever vector to go through Langsmith docs

---

## Module 1

[arnavv06-langsmith-MAT496/notebooks/module_1 at main · arnavv06/arnavv06-langsmith-MAT496](https://github.com/arnavv06/arnavv06-langsmith-MAT496/tree/main/notebooks/module_1)

### Video1: Tracing basics

[arnavv06-langsmith-MAT496/notebooks/module_1/tracing_basics.ipynb at main · arnavv06/arnavv06-langsmith-MAT496](https://github.com/arnavv06/arnavv06-langsmith-MAT496/blob/main/notebooks/module_1/tracing_basics.ipynb)

Learned how to implement **@traceable** decorator from langsmith package.

If a function with traceable decorator is called, a run tree is created. Detection of root run(run trace) or parent run is also done, if parent run is detected then new run is nested function call. If called function and parent function are traceable, then new run is inserted in parent run tree. Run tree are built this way.

Important thing to know is background threading is used so there is no latency.

Changes made:

* Implemented RAG application used in module 0
* provided meta data

![1759597117382](image/README/1759597117382.png)

1. Retrieved 4 documents for user input which are helpful.
2. Passed questions along with documents as input to model
3. Called groq and received return response.

### Video2:  Types of Runs

[arnavv06-langsmith-MAT496/notebooks/module_1/types_of_runs.ipynb at main · arnavv06/arnavv06-langsmith-MAT496](https://github.com/arnavv06/arnavv06-langsmith-MAT496/blob/main/notebooks/module_1/types_of_runs.ipynb)

Learned how to use different types of tracing in Langsmith and why tracing is better than logging because logging makes it more difficult to find the root cause.

Types:

**LLM:** invokes an LLM

**Retriever:** Retrieve docs froom databases and owhather resources

**Tool:** Executes actions with function calls

**Chain:** Combines multiple runs (Default type)

**Prompt:** Creates prompt from template

**Parser:** Extracts structed data

Changes Made:

Added a retriver to go through a list of constellations.

### Video 3: Alternative Tracing Methods

[arnavv06-langsmith-MAT496/notebooks/module_1/alternative_tracing_methods.ipynb at main · arnavv06/arnavv06-langsmith-MAT496](https://github.com/arnavv06/arnavv06-langsmith-MAT496/blob/main/notebooks/module_1/alternative_tracing_methods.ipynb)

Learned alternative tracing ways in Langsmith. Tracing is done by default after setting up our environment variables and leveraging langchain and langgraph.**@traceabel** decorator is the default way to set up tracing. Also learned about wrap_openai() which is for users who want to use OpenAi SDK directly and trace all openai calls.

Changes made:

* Used **Open AI** model since wrap_openai() was not available within groq
* Used model **gpt-4o-mini**
* Implemented a chatbot using wrap_openai() and observed changes reflected on langsmith portal
