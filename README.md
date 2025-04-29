# 🧠 CrewAI Use Cases: Article Generation & Stock Recommendation

This project demonstrates the power of [CrewAI](https://docs.crewai.com/) to manage collaborative autonomous agents working together to complete complex tasks. It includes two main examples:

- ✍️ **Article Generation Crew**  
- 📈 **Stock Recommendation Crew**

Each example uses multiple agents, custom tasks, and LLM-powered workflows. Environment variables (such as `OPENAI_API_KEY`) are managed securely with a `.env` file.

---

## 📦 Requirements

Install required dependencies using:

```bash
pip install -r requirements.txt
```

Or use the pip commands within the notebook.

---

## 🔐 Environment Variables

To use this project securely:

1. Create a `.env` file in the same directory as the notebooks.
2. Add your OpenAI API Key:

```dotenv
OPENAI_API_KEY=your_api_key_here
```

The notebooks use the `python-dotenv` package to load this key into the environment automatically.

---

## ✍️ Article Generation Crew

**Goal:** Automatically generate a blog article on a given topic using 3 collaborative agents:

- `Content Planner`: Plans the article structure and audience.
- `Content Writer`: Writes the full article based on the plan.
- `Editor`: Edits the content to match journalistic style.

### 🔧 How it works:

1. Input a topic (e.g., `"Artificial Intelligence"`).
2. Each agent performs their task in sequence.
3. The final Markdown article is displayed and ready for publishing.

### 🔁 Workflow Example:

```python
crew.kickoff(inputs={"topic": "Artificial Intelligence"})
```

---

## 📈 Stock Recommendation Crew

**Goal:** Analyze a customer's stock portfolio, price trends, and news to give a Buy/Sell/Hold recommendation.

### 👥 Agents:

- `Customer Manager`: Retrieves stock info from a CSV wallet file.
- `Stock Price Analyst`: Analyzes price trends using Yahoo Finance.
- `News Analyst`: Collects and summarizes news sentiment using DuckDuckGo and calculates a fear/greed score.
- `Stock Recommender`: Aggregates all insights and provides a final investment recommendation.

### 🛠️ Features:

- Uses `yfinance` to fetch historical stock data.
- Uses `DuckDuckGoSearchResults` for real-time news.
- Interprets CSV wallet info via `crewai-tools`.

### 📝 Example Input:

```python
crew.kickoff(inputs={"ticket": "AAPL"})
```

---

## 📄 Output Example

Each agent outputs structured insights, and the final result is a Markdown-formatted recommendation or article. Use `IPython.display.Markdown` for clean display in notebooks.

---

## 🧪 Tested Versions

| Library              | Version       |
|----------------------|---------------|
| `crewai`             | 0.70.1        |
| `crewai-tools`       | 0.12.1        |
| `langchain`          | 0.2.16        |
| `langchain-openai`   | 0.1.25        |
| `yfinance`           | 0.2.44        |
| `python-dotenv`      | latest        |
| `duckduckgo_search`  | 6.3.0         |

---

## 📁 Folder Structure

```
├── my-first-crew.ipynb         # Article Generation
├── stockRecommendation.ipynb   # Stock Recommendation
├── wallet.csv                  # Customer stock wallet
├── .env                        # Environment variable file (not shared)
└── README.md
```

---

## 📌 Notes

- This is an educational and experimental project for understanding multi-agent orchestration with LLMs.
- Always validate financial recommendations with professional analysts before taking action.
