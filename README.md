# MediAssist: NLP-Powered Healthcare Chatbot

**MediAssist** is an end-to-end intelligent healthcare assistant designed to bridge the gap between complex medical information and patient understanding. By combining a fine-tuned **BioBERT** classifier with a **FAISS**-powered retrieval system and **LLM-based rewriting**, it delivers reliable, evidence-based medical guidance grounded in authoritative datasets.

## 🚀 System Architecture

The chatbot follows a sophisticated hybrid pipeline to ensure accuracy and minimize hallucinations:

1. **Intent Classification**: A fine-tuned **BioBERT** model categorizes user queries into 7 clinical intents (Definition, Causes, Symptoms, Treatment, Prevention, Risks, or Other).


2. **Semantic Retrieval**: Based on the predicted intent, the system searches intent-specific knowledge bases using **Sentence-BERT** embeddings and **FAISS** for high-speed similarity matching.


3. **Grounded Generation**: The retrieved context is passed to **GPT-4o-mini**, which rephrases the medical data into patient-friendly language while strictly adhering to the provided facts.


4. **Transparency**: Every response includes **source attribution**, citing the original dataset and text snippets used.



## 🛠️ Tech Stack

* **Backend**: FastAPI, Python.


* **NLP & ML**: BioBERT (dmis-lab), Sentence-Transformers (`all-MiniLM-L6-v2`), PyTorch.


* **Vector Database**: FAISS.


* **LLM**: OpenAI GPT-4o-mini (for grounded rewriting).


* **Database**: MongoDB (for conversation history tracking).


* **Frontend**: Expo, React Native (Mobile Application).

## 📊 Dataset & Methodology

The system is trained and grounded on **26,500 QA pairs** from two primary sources:

* **MedQuAD**: Curated from NIH and other authoritative government sources.


* **Medical Meadow MedQA**: Large-scale medical questions for broader linguistic variety.



**Quality Control**: Since the original datasets lacked intent labels, we utilized **Zero-Shot Labeling** with an LLM to interpret semantic meaning and automate the annotation process at scale.

## 📦 Installation & Setup

### Backend (FastAPI)

1. Clone the repository and navigate to the `backend` folder.
2. Install dependencies:
```bash
pip install fastapi uvicorn torch transformers sentence-transformers pandas faiss-cpu openai motor

```


3. Set up your `.env` file:
```env
OPENAI_API_KEY=your_key_here
MONGODB_URL=mongodb://localhost:27017

```


4. Place the trained BioBERT model in `intent_model/biobert_weighted_intent_final/`.
5. Run the server: `uvicorn app:app --reload`.

### Frontend (Expo)

1. Navigate to the `app` folder.
2. Install dependencies: `npm install`.
3. Start the application: `npx expo start`.

## 📡 API Endpoints

* `POST /ask`: Submit a question to receive a classified intent, grounded answer, and citations.
* `GET /history`: Retrieve the last 5 interactions for the current user session.
* `GET /docs`: Interactive Swagger UI documentation.

## 👥 Authors

* **Abdul Rafeh** 


* **Samith Kamarthi** 



