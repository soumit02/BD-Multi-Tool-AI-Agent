# BD Multi-Tool AI Agent 

An intelligent AI agent built with LangChain that can autonomously answer queries by interacting with three specific Bangladesh-related datasets (Institutions, Hospitals, Restaurants) and fallback to a Web Search tool for general knowledge. 

The agent uses a Text-to-SQL workflow to analyze local databases and fetches real-time web results for broader context (e.g., healthcare policies, general definitions).

## 🎯 Features
*   **Text-to-SQL Routing:** Automatically converts natural language questions into SQL queries to fetch data.
*   **Multi-Database Management:** Handles three distinct SQLite databases:
    *   `institutions.db` (Educational and Govt. Institutions)
    *   `hospitals.db` (Hospitals and Bed Capacities)
    *   `restaurants.db` (Dining and Food options)
*   **Web Search Fallback:** Uses Tavily API to browse the internet for queries outside the databases.
*   **Token Optimization:** Prevents LLM token limit errors by fetching only essential schema data.


## 🛠️ Prerequisites
Before running the project, ensure you have the following installed:
*   Python 3.8 or higher
*   Jupyter Notebook (or VS Code with Jupyter extension)
*   API Keys for your LLM (e.g., Groq, OpenAI) and Web Search Tool (Tavily).

## 🚀 Step-by-Step Setup Instructions

**Step 1: Clone the Repository**
Clone this project to your local machine:
```bash
git clone https://github.com/soumit02/BD-Multi-Tool-AI-Agent.git
cd BD-Multi-Tool-AI-Agent
```

**Step 2: Set up a Virtual Environment**
It is highly recommended to use a virtual environment to manage dependencies.
```bash
python -m venv venv
# Activate on Windows:
venv\Scripts\activate
# Activate on Mac/Linux:
source venv/bin/activate
```

**Step 3: Install Dependencies**
Install all required libraries using the `requirements.txt` file (or run the pip command manually).
```bash
python -m pip install langchain==0.2.10 langchain-community==0.2.10 langchain-openai==0.1.17 pandas python-dotenv datasets tavily-python
```

**Step 4: Configure Environment Variables**
Create a `.env` file in the root directory and add your API keys:
```env
GROQ_API_KEY=your_groq_api_key_here
BASE_URL=https://api.groq.com/openai/v1
MODEL_NAME=llama3-70b-8192  # Or any compatible model
TAVILY_API_KEY=your_tavily_api_key_here
```

**Step 5: Add the Datasets**
Download the datasets from Hugging Face and place them inside the `csvfile/` folder. Ensure the file names match the code (`institution.csv`, `bangladesh_hospitals.csv`, `restaurants.csv`).

**Step 6: Run the Agent**
Open `agent.ipynb` in VS Code or Jupyter Notebook. Run the cells sequentially:
1.  **Cell 1:** Loads APIs and initializes the LLM.
2.  **Cell 2:** Converts the CSV files into SQLite databases and saves them in the `sql/` folder.
3.  **Cell 3:** Builds the Custom LangChain Tools (`InstitutionsDBTool`, `HospitalsDBTool`, `RestaurantsDBTool`, `WebSearchTool`).
4.  **Cell 4:** Initializes the main Agent Executor and runs test queries.

## 💡 Example Queries to Try
*   *Database Query:* "How many government institutions are in Rajshahi?"
*   *Web Search Query:* "What is the current healthcare policy of Bangladesh?"

## 🤝 Acknowledgments
*   Datasets provided by Mahadih534 on Hugging Face.
*   Built using LangChain and OpenAI SDK.