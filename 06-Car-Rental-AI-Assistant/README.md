# DriveEasy — AI Car Rental Chatbot

A conversational AI assistant for a car rental service, built with Google Gemini, function calling, SQLite, and a Gradio chat interface.

## Demo
![Example_screenshot](/06-Car-Rental-AI-Assistant/Screenshot.png)
![screenshot2](/06-Car-Rental-AI-Assistant/Screenshot2.png)

## What it does

Users chat with an AI agent that can answer questions about car pricing, check availability for specific dates, and make bookings — all through natural conversation. The agent calls real database functions under the hood to look up live data and persist reservations.

## Fleet


| Car Type    | Price/Day | Units Available |
| ----------- | --------- | --------------- |
| Sedan       | $40       | 3               |
| SUV         | $70       | 2               |
| Truck       | $90       | 1               |
| Convertible | $120      | 2               |




## Tech stack

- **LLM**: Google Gemini 2.5 Flash (via the OpenAI-compatible endpoint)
- **Function calling**: Three tools the model can invoke — `get_car_price`, `check_availability`, `make_booking` 
- **Database**: SQLite (`carrental.db`) with `cars` and `booking` tables
- **UI**: Gradio `ChatInterface` 
- **Local model fallback**: Ollama endpoint also configured (not used by default)



## Setup

1. **Install dependencies**
  ```bash
   pip install openai gradio python-dotenv
  ```
2. **Set your API key**
  Create a `.env` file in the project root:
3. **Run the notebook**
  Open `rental.ipynb` in Jupyter and run all cells. A Gradio interface will launch in your browser.



## How it works

The `chat()` function sends the conversation history plus a system prompt to Gemini with the three tools available. When the model decides to call a tool, `handle_tool_calls()` dispatches to the appropriate Python function, appends the result to the message history, and sends everything back to the model. This loop continues until the model returns a plain text response, which is shown to the user.

## Example interactions

- *"How much does an SUV cost for 3 days?"*
- *"Is a sedan available on 2026-08-15?"*
- *"Book a convertible for John Smith on 2026-09-01 for 2 days."*

