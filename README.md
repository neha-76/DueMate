# DueMate

DueMate is a Streamlit-based AI deadline assistant designed to help students and learners track academic deadlines, assignment due dates, exams, and schedule reminders from photos, text, or conversation.

It uses Google Gemini for date extraction and Twilio WhatsApp to send a reminder summary to the user.

## Features

- Upload images of timetables, assignment sheets, syllabus pages, or exam schedules
- Chat with the AI about deadlines and academic tasks
- Extract dates, tasks, and subject names when available
- Generate a short summary of all discussed deadlines
- Send the summary to the user via WhatsApp using Twilio
- Friendly onboarding flow with name and WhatsApp number collection

## Tech Stack

- Python
- Streamlit
- Google Gemini API
- Twilio WhatsApp API

## Project Structure

```text
DueMate/
├── app.py                 # Main Streamlit application
├── prompts.py             # AI prompts and onboarding messages
├── requirements.txt       # Python dependencies
├── .streamlit/
│   └── secrets.toml       # API keys and Twilio configuration
└── README.md              # Project documentation
```

## Requirements

- Python 3.10 or above
- A Google Gemini API key
- A Twilio account with WhatsApp enabled
- A valid Twilio WhatsApp sender number and Content SID

## Installation

1. Clone the repository:

```bash
git clone <your-repo-url>
cd DueMate
```

2. Create and activate a virtual environment:

```bash
python -m venv .venv
.venv\Scripts\activate
```

3. Install dependencies:

```bash
pip install -r requirements.txt
```

## Configuration

Create a `.streamlit/secrets.toml` file in the project root with the following values:

```toml
GEMINI_API_KEY = "your-google-gemini-api-key"
TWILIO_ACCOUNT_SID = "your-twilio-account-sid"
TWILIO_AUTH_TOKEN = "your-twilio-auth-token"
TWILIO_WHATSAPP_FROM = "whatsapp:+1234567890"
TWILIO_CONTENT_SID = "your-twilio-content-sid"
```

> `TWILIO_WHATSAPP_FROM` should be your Twilio WhatsApp-enabled sender number, and `TWILIO_CONTENT_SID` should be a valid Twilio content template ID configured for your account.

## Run the App

```bash
streamlit run app.py
```

Then open the local URL shown in the terminal (usually http://localhost:8501).

## How It Works

1. The user enters their name and WhatsApp number.
2. They upload an image or type a question about academic dates.
3. The app sends the content to Gemini with a system prompt focused on deadlines and academic scheduling.
4. Gemini extracts deadlines, dates, and tasks.
5. The user can generate a reminder summary.
6. That summary is sent through Twilio to the configured WhatsApp number.

## Important Notes

- The app is designed specifically for academic deadlines, exams, schedules, and assignments.
- Non-academic questions are politely redirected back to deadline-related tasks.
- No dates or tasks are fabricated; the AI must rely on visible or provided information only.

## License

This project is for educational and personal use. Add your preferred license here if you plan to distribute it.

## Future Improvements

- Add a calendar export feature
- Support task saving in a local database
- Add notifications beyond WhatsApp
- Improve deadline categorization and sorting
- Add user authentication for multi-user support
