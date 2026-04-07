# 🐍 Python Backend API

A Flask REST API with user authentication, a SQLite product database, and free deployment on Render.

## 📖 What this is
This project is a Python Flask backend that exposes REST endpoints for user registration, login, and product management. Passwords are hashed with SHA-256, product writes are protected by a Bearer token, and the database is SQLite with auto-initialization on first run. It's designed to be deployed for free on Render using gunicorn.

## ✅ Why you'd use it
- **Full auth flow included** — register and login endpoints with hashed passwords, ready to connect to a SwiftUI or web frontend
- **Token-protected writes** — the POST /products endpoint requires a Bearer token set via environment variable, showing a real API security pattern
- **Free deployment out of the box** — includes a `Procfile` and `requirements.txt` for one-click deploy on Render

[![Watch on YouTube](https://img.shields.io/badge/YouTube-Watch%20the%20Tutorial-red?style=for-the-badge&logo=youtube)](https://youtube.com/watch?v=PLACEHOLDER)

## 🚀 Getting Started

### Run locally
1. Clone the repo
   ```bash
   git clone https://github.com/NDCSwift/PythonBackedExample.git
   cd PythonBackedExample
   ```
2. Create a virtual environment and install dependencies
   ```bash
   python3 -m venv venv
   source venv/bin/activate
   pip install -r requirements.txt
   ```
3. Create a `.env` file and set your API token
   ```
   API_TOKEN=your_secret_token_here
   ```
4. Run the server
   ```bash
   python3 app.py
   ```
5. Initialize the database (first run only)
   ```
   GET http://localhost:5000/init
   ```

### Deploy to Render
1. Push to GitHub
2. Create a new **Web Service** on [Render](https://render.com)
3. Set the `API_TOKEN` environment variable in Render's dashboard
4. Render will detect the `Procfile` and deploy automatically

## 📝 API Endpoints

| Method | Endpoint | Auth | Description |
|--------|----------|------|-------------|
| GET | `/` | None | Health check |
| GET | `/init` | None | Initialize database tables |
| GET | `/products` | None | List all products |
| POST | `/products` | Bearer token | Add a new product |
| POST | `/register` | None | Register a new user |
| POST | `/login` | None | Login with username/password |

## ⚙️ Requirements
- Python 3.9+
- Flask, gunicorn, python-dotenv, flask-cors (see `requirements.txt`)
