
Flask-web-app — Flask DevOps Log Cleaner

A Flask web application with a smart log cleaner built as a DevOps learning project.

---

## Project Structure

my-flask-app/
├── app.py               # Main Flask application and log cleaner logic
├── setup.sh             # Installs Python, creates venv, installs dependencies
├── start_server.sh      # Activates venv and starts the Flask server
├── requirements.txt     # Python package dependencies
├── .env                 # Secret environment variables (never commit this)
├── .env.example         # Safe template showing required env variables
├── .gitignore           # Files and folders excluded from Git
├── templates/           # HTML pages (Jinja2)
│   ├── base.html        # Shared layout (nav, footer)
│   ├── index.html       # Dashboard
│   ├── logs.html        # Log viewer and cleaner
│   └── about.html       # About page
└── logs/
    └── app.log          # Live application log file (auto-created)

---

## Requirements

- Ubuntu / Debian Linux
- Python 3.8+
- Bash shell

---

## Setup Instructions

### 1. Clone the repository
git clone https://github.com/DevMariam/Flask-web-app.git
cd logops

### 2. Make scripts executable
chmod +x setup.sh start_server.sh

### 3. Set up environment variables
cp .env.example .env
vim .env    # Add your own SECRET_KEY

### 4. Run setup
./setup.sh

### 5. Start the server
./start_server.sh

### 6. Open in browser
http://localhost:5000

---

## Environment Variables

| Variable     | Description                        | Example        |
|--------------|------------------------------------|----------------|
| SECRET_KEY   | Flask session signing key          | (generated)    |
| FLASK_ENV    | development or production          | development    |
| FLASK_DEBUG  | Enable auto-reload and error pages | True           |
| PORT         | Port the server runs on            | 5000           |

Generate a secure SECRET_KEY by running:
python3 -c "import secrets; print(secrets.token_hex(32))"

---

## Available Routes

| Route               | Method | Description                  |
|---------------------|--------|------------------------------|
| /                   | GET    | Dashboard with stats         |
| /about              | GET    | Project info and route docs  |
| /logs               | GET    | View and analyse all logs    |
| /logs/clean         | POST   | Run the smart log cleaner    |
| /logs/seed          | POST   | Generate sample log entries  |
| /logs/clear         | POST   | Wipe the log file            |
| /api/logs/analyse   | GET    | JSON log analysis API        |

---

## How the Smart Log Cleaner Works

The cleaner reads logs/app.log and classifies every line by severity:

| Level   | Action        | Reason                            |
|---------|---------------|-----------------------------------|
| ERROR   | Keep          | Critical — needs investigation    |
| WARNING | Keep          | Important signal                  |
| INFO    | Keep          | Audit trail                       |
| DEBUG   | Remove        | Noise — not needed in production  |
| Empty   | Remove        | Wasted space                      |

You can also enter a custom regex pattern to remove any matching lines.

---

## Contributing

This project has three contributors:

- App logic (app.py) — backend routes, log cleaner, API
- Templates (templates/) — HTML pages and UI

---

## Team

Built by DevMariam, Voddy001 and BerryPlays2288 as a DevOps learning project.
