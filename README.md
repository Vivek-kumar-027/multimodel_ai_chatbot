# Gemini Multimodal Chatbot (Text + Image)

A beginner-friendly Python project using the official Google Gen AI SDK and Streamlit.

## Features
- Text-based chat with Gemini
- Upload an image and ask questions about it
- Keeps text conversation history during the current session
- Clear conversation button

## Requirements
- Python 3.11 or newer
- A Gemini API key from https://aistudio.google.com/app/apikey
- Internet connection

## Setup (Windows PowerShell)

```powershell
# Open this folder in VS Code, then open Terminal
uv venv
.venv\Scripts\activate
uv pip install -r requirements.txt

# Create your private environment file
Copy-Item .env.example .env
```

Open `.env` and replace the placeholder with your own API key:

```env
GEMINI_API_KEY=your_actual_api_key
GEMINI_MODEL=gemini-2.5-flash
```

Do not share `.env` or upload it to GitHub.

## Run the application

```powershell
streamlit run app.py
```

Streamlit usually opens at http://localhost:8501.

## Optional backend test

```powershell
python gemini_bot.py
```

## Project structure

```text
gemini_multimodal_chatbot/
├── app.py
├── gemini_bot.py
├── requirements.txt
├── .env.example
├── .gitignore
├── README.md
└── screenshots/
```

## How it works
1. `app.py` collects text and an optional uploaded image.
2. `gemini_bot.py` loads the API key using `python-dotenv`.
3. The backend converts previous text messages into Gemini conversation content.
4. The backend sends the prompt and optional image bytes to Gemini.
5. Streamlit displays the response and keeps messages in session state.

Note: Uploaded images from earlier turns are not resent as part of later follow-up questions. The conversation history is temporary and is cleared when the Streamlit session resets.

## Troubleshooting
- **API key not found:** Confirm `.env` is in the project root and the variable is spelled `GEMINI_API_KEY`.
- **ModuleNotFoundError:** Activate the virtual environment and run `uv pip install -r requirements.txt`.
- **Invalid API key:** Create or verify the key in Google AI Studio.
- **Model unavailable:** Check the models available to your API key and change `GEMINI_MODEL` in `.env`.

## Documentation
- Google Gen AI Python SDK: https://googleapis.github.io/python-genai/
- Gemini API: https://ai.google.dev/gemini-api/docs
