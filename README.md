# Amazon Electronics Recommender Bot 🔍

The **Amazon Electronics Recommender Bot** is an AI-powered chatbot that enhances the shopping experience by providing product recommendations based on user queries. The chatbot leverages natural language processing (NLP) techniques and semantic search to understand user queries and generate appropriate responses. The chatbot integrates with a pre-loaded product database stored in AstraDB Vector Store to provide personalized recommendations and information about available products. By leveraging advanced AI technologies, this bot supports text and voice inputs to offer personalized product insights.

---
![image](https://github.com/user-attachments/assets/2b9d3a34-1a95-47b8-b3a9-9f75f9c787a6)


## Features 🚀

### Analyze & Recommend

- Submit text or voice inputs to receive product recommendations.
- Combines multimodal inputs (text and voice) for better user interaction.

### Pre-loaded Product Database

- Uses a pre-loaded CSV dataset containing product information including titles, descriptions, prices, and ratings.
- Data is stored in AstraDB Vector Store for efficient semantic search and retrieval.

### Semantic Search & Embeddings

- Uses OpenAI embeddings to convert product descriptions and queries into vector representations.
- Enables semantic search, allowing the bot to understand and respond to user queries based on meaning rather than exact keyword matches.

### Product Information Retrieval

- Access detailed product descriptions, reviews, and ratings using AstraDB Vector Store.
- Provides personalized shopping assistance based on user needs.

### Multimodal Processing

- **Text Input:** Processed directly by OpenAI's language model.
- **Voice Input:** Converted to text using Whisper AI, then processed by OpenAI's language model.
- **Audio Response:** Text responses can be converted to speech using gTTS.

---

## Technologies Used 🧰

- **Frontend:** HTML, CSS, JavaScript (jQuery)
- **Backend:** Flask (Python)
- **AI Models:** OpenAI (GPT models), Whisper (speech-to-text)
- **Vector Store:** AstraDB VectorStore
- **Multimodal Tools:** gTTS (text-to-speech), Pandas, LangChain
- **Embeddings:** OpenAI Embeddings API

---

## How It Works 📚

1. **User Input (Text/Voice):**
   - Users provide input through an interactive web interface.
   - Voice input is recorded and sent to the backend.

2. **Frontend (HTML/CSS/JS):**
   - The input is captured through a web-based user interface.
   - Audio recording is handled using the MediaRecorder API.

3. **Backend (Flask App):**
   - The Flask application processes requests and manages AI model interactions.
   - Routes user queries to the appropriate processing pipeline.

4. **Multimodal Processing:**
   - **Voice Input:** Audio is transcribed to text using Whisper AI.
   - **Text Input:** Processed directly by the language model.

5. **Semantic Search with Embeddings:**
   - User queries are converted into embeddings using OpenAI models.
   - The system searches the vector store for the top 5 most relevant products.
   - Allows the bot to understand user intent and provide more relevant responses.

6. **AI Model (OpenAI):**
   - Processes queries with retrieved context to provide intelligent responses.
   - Uses advanced prompting patterns for enhanced user interactions.

7. **Vector Store (AstraDB):**
   - Stores pre-loaded product data as vector embeddings.
   - Enables fast semantic search and retrieval of relevant products.

8. **Response to User:**
   - The bot returns a response in text format.
   - For voice queries, responses can be converted to audio using text-to-speech.

---

![image](https://github.com/user-attachments/assets/9988a276-c70b-48af-8fdd-04c329de192f)


## Installation 💻

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/anjalikabra/AmazonElectronicsBot.git
   cd AmazonElectronicsBot
   ```

2. **Create a Virtual Environment:**
   ```bash
   python -m venv myenv
   source myenv/bin/activate  # On Windows: myenv\Scripts\activate
   ```

3. **Install Dependencies:**
   ```bash
   pip install flask langchain-openai langchain-astradb openai python-dotenv pandas transformers whisper gtts pillow nltk
   ```
   
   **Note:** If a `requirements.txt` file is not present, install the dependencies listed above manually.

4. **Set Up Environment Variables:**
   Create a `.env` file in the project root with the following keys:
   ```env
   OPENAI_API_KEY=your_openai_api_key
   ASTRA_DB_API_ENDPOINT=your_astra_db_endpoint
   ASTRA_DB_APPLICATION_TOKEN=your_astra_db_token
   ASTRA_DB_KEYSPACE=your_astra_db_keyspace
   ```

5. **Prepare the Dataset:**
   - The project expects a CSV file with product data containing columns: `Title`, `Price`, `Category`, `Ratings (out of 5)`, `Recommended`, `Product Link`, `Product Description`, and `Customer Reviews`.
   - Update the file path in `ecommbot/ingest.py` (line 32) to point to your dataset.
   - On first run with `ingestdata(None)`, the data will be ingested into AstraDB.
   - For subsequent runs, the app uses `ingestdata("done")` to load the existing vector store.

6. **Run the Flask App:**
   ```bash
   python app.py
   ```

---

## Usage ✨

1. **Launch the Application:**
   ```bash
   python app.py
   ```

2. **Interact with the Bot:**
   - Open your browser and go to `http://localhost:5000`.
   - Type queries or record audio for personalized recommendations.
   - The bot will search the pre-loaded product database and provide relevant recommendations.

---

## Workflow Flowchart 📊

**User Input (Text/Voice) ➡️ Frontend (HTML/CSS/JS) ➡️ Flask Backend ➡️ Multimodal Processing (Whisper for voice) ➡️ Semantic Search & Embeddings ➡️ Vector Store Retrieval (AstraDB) ➡️ AI Model (OpenAI) ➡️ Response to User**

---

## Dataset Requirements 📋

The project requires a CSV file with the following columns:
- `Title`: Product name
- `Price`: Product price
- `Category`: Product category
- `Ratings (out of 5)`: Product rating
- `Recommended`: Recommendation status
- `Product Link`: URL to the product
- `Product Description`: Detailed product description
- `Customer Reviews`: Customer review text

The dataset is loaded once during initial setup and stored in AstraDB Vector Store for efficient retrieval.

---
