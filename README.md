Overview
This project implements an AI-powered financial portfolio rebalancer using the LangChain framework and multiple large language models (LLMs), including Groq LLaMA3-70B, Groq LLaMA3-8B, and OpenAI GPT-4. The system analyzes stock portfolios, evaluates market trends, and provides actionable recommendations for rebalancing based on real-time data.

Features
Stock Price Lookup: Fetches real-time stock prices using yfinance.

Portfolio Rebalancer: Analyzes portfolio allocations and suggests adjustments based on an equal-weight strategy.

Market Trend Analyzer: Tracks S&P 500 trends using SPY ETF data to provide market context.

Dynamic LLM Integration: Allows switching between different LLMs (Groq or OpenAI) for analysis.

Setup Instructions
1. Prerequisites
Ensure the following are installed on your system:

Python 3.8 or higher

pip (Python package manager)

2. Clone the Repository
Clone the project repository to your local machine:

bash
git clone <repository_url>
cd <repository_folder>
3. Install Dependencies
Install the required Python packages by running:

bash
pip install langchain langchain-openai langchain-groq langchain-community requests pandas yfinance python-dotenv
4. Set Up API Keys
This project requires API keys for OpenAI, Groq, and Hugging Face models. Follow these steps:

Create a .env file in the root directory of the project.

Add your API keys to the .env file in the following format:

text
OPENAI_API_KEY=your_openai_api_key
GROQ_API_KEY=your_groq_api_key
HUGGINGFACE_API_KEY=your_huggingface_api_key
5. Verify Environment Variables
Ensure that the .env file is loaded correctly by running:

python
from dotenv import load_dotenv
import os

load_dotenv('variables.env')
print(os.getenv("OPENAI_API_KEY"))
print(os.getenv("GROQ_API_KEY"))
print(os.getenv("HUGGINGFACE_API_KEY"))
If the keys are printed correctly, you are ready to proceed.

How to Run
Open the Python notebook or script file (hnawaz_CO3.ipynb) in your preferred IDE.

Execute the cells sequentially to initialize tools, load models, and run test cases.

Alternatively, run the script directly from the terminal:

bash
python hnawaz_CO3.py
Functionality Overview
1. Stock Price Lookup Tool
Fetches real-time stock prices using yfinance. Example usage:

python
stock_price_tool("AAPL")
2. Portfolio Rebalancer Tool
Analyzes portfolio allocations and suggests rebalancing actions based on an equal-weight strategy. Example usage:

python
rebalance_tool("{'AAPL': 0.5, 'TSLA': 0.3, 'GOOGL': 0.2}")
3. Market Trend Analyzer Tool
Provides insights into recent S&P 500 trends using SPY ETF data. Example usage:

python
trend_tool()
4. Dynamic LLM Selection
Switch between OpenAI GPT-4, Groq LLaMA3-70B, and LLaMA3-8B models for analysis:

python
llm = get_llm(provider="groq", model="llama3-70b")
Testing
To test the system with predefined portfolios:

Define test portfolios in run_test_cases() function:

python
user_portfolio_1 = {"AAPL": 0.50, "TSLA": 0.30, "GOOGL": 0.20}
user_portfolio_2 = {"MSFT": 0.25, "NVDA": 0.25, "AMZN": 0.25, "META": 0.25}
Run test cases by executing:

bash
python hnawaz_CO3.py
Observe outputs for each portfolio and LLM configuration.

Known Issues
OpenAI API Limitations: The OpenAI GPT-4 model may fail due to rate limits or insufficient quota.

Tool Misuse by LLaMA3-8B: The Groq LLaMA3-8B model occasionally generates invalid tool inputs (e.g., multi-ticker lookups).

Error in Callback Handlers: Some callback handlers may throw AttributeError due to missing attributes in LangChain's logging framework.

Future Improvements
Implement better error handling for API failures and tool misuse.

Optimize latency for Groq LLaMA3-70B without compromising accuracy.

Explore hybrid approaches that combine multiple models for faster and more reliable results.