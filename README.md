# Ollama & OpenAI Web Summarization

A Jupyter notebook implementation that uses either a locally hosted Llama3.2 model via Ollama or OpenAI's API to summarize web content. This project demonstrates how to interact with both Ollama and OpenAI APIs to perform web scraping and content summarization.

## 📋 Overview

This project uses:
- BeautifulSoup for web scraping
- Ollama API for interacting with local LLM models
- OpenAI API for cloud-based language models (alternative implementation)
- Llama3.2 as the default local language model

## 🔧 Requirements

- Python 3.10+
- Ollama running locally (for Ollama implementation)
- OpenAI API key (for OpenAI implementation)
- Llama3.2 model downloaded in Ollama
- Required Python packages:
  - requests
  - beautifulsoup4
  - python-dotenv
  - ipython
  - openai (for OpenAI implementation)

## ⚙️ Setup Instructions

1. Install required Python packages:
   ```
   pip install requests beautifulsoup4 python-dotenv ipython openai
   ```

2. For Ollama implementation:
   - Install Ollama from [https://ollama.com/](https://ollama.com/)
   - Pull the Llama3.2 model: `ollama pull llama3.2`
   - Start Ollama server: `ollama serve`

3. For OpenAI implementation:
   - Create an OpenAI account if you don't have one
   - Generate an API key
   - Store your API key in a `.env` file: `OPENAI_API_KEY=your_api_key_here`

4. Open the Jupyter notebook:
   ```
   jupyter notebook Ollama_web_summarisation.ipynb
   ```

## 🚀 Usage

The notebook provides a `Website` class that handles web scraping and content extraction. The main function `summarize(url)` takes a URL as input and returns a markdown-formatted summary of the website's content.

The project demonstrates two implementations:
1. Using Ollama with locally-hosted Llama3.2
2. Using OpenAI's API (referenced as "day1" implementation)

Example usage:
```python
from IPython.display import Markdown, display

# Get summary as text
summary = summarize("https://github.com/Ziad-Tamim")

# Or display nicely formatted summary
display_summary("https://github.com/Ziad-Tamim")
```

## 🔄 How It Works

1. The `Website` class fetches a webpage and extracts its title and text content
2. The extracted content is formatted into a prompt for the language model
3. The prompt is sent to either Ollama API or OpenAI API
4. The API returns a summarized version of the webpage
5. The summary is displayed in markdown format

## 📚 Resources

- [Ollama Documentation](https://github.com/ollama/ollama)
- [Llama Models](https://ollama.com/library/llama3.2)
- [OpenAI API Documentation](https://platform.openai.com/docs/api-reference)
- [BeautifulSoup Documentation](https://www.crummy.com/software/BeautifulSoup/bs4/doc/)

## 📝 Notes

- The notebook starts with an introduction to the OpenAI API and transitions to demonstrating the Ollama implementation
- The original OpenAI implementation ("day1" code) is referenced but not directly included in the notebook
- There is currently a small issue in the Ollama `summarize` function where it uses an undefined `ollama` variable. To fix this, either import the ollama package or use the direct API approach with `requests.post()` as shown in the earlier cells.
