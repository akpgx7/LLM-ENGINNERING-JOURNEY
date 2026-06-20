# Website Summarizer (Local LLM via Ollama)

Summarizes a webpage's content using **Gemma3** running locally via
**Ollama** — no paid API required.

## How it works
1. Scrapes the target website's text content (`scraper.py`)
2. Sends it to a locally running Gemma3 model through Ollama's
   OpenAI-compatible API
3. Returns a clean markdown summary, ignoring navigation/junk content

## Setup
\`\`\`bash
# 1. Install Ollama: https://ollama.com
# 2. Pull the model
ollama pull gemma3

# 3. Install Python deps
pip install -r requirements.txt

# 4. Run
summarizer.ipynb
\`\`\`

## Example output
> Here’s a summary of the Coursera website:
>
>**Coursera Overview**
>
>Coursera offers online courses, professional certificates, and degrees for individuals, businesses, universities, and governments. Key features >include over 10,000 programs with savings (currently 40% off) and learning from over 350 leading universities and companies like Google, IBM, >Microsoft, and OpenAI.
>
>**Key Highlights:**
>
>*   **Focus on AI:** Significant emphasis is placed on practical AI skills through courses from organizations like OpenAI, Anthropic, Google, and >DeepLearning.AI.
>*   **Career Paths:**  Programs are designed to get users job-ready with no prior experience needed, spanning fields like Data, Business, Sales & >Marketing, IT, Software Engineering, etc.
>*   **Savings & Flexibility:** The site offers midyear savings (40% off) and a flexible learning model.
>*   **Diverse Offerings:** Courses are available across numerous categories including business, computer science, data science, and personal >development.
>
>**Specific Programs to Explore:**
>
>*   **Google Career Collection:**  Entry-level programs from Google covering multiple career pathways.
>*   **Trending Searches:** Popular courses in Python, Data Analytics, Project Management.
>
>---
>
>Would you like me to summarize another website?

## Notes
- Runs 100% locally — good for privacy and zero API cost
- Swap the `model` param to try other Ollama models