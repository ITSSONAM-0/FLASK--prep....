<p align="center">
  <h1>📌 Flask</h1>
</p>

#  Introduction
Flask is a lightweight and powerful Python web framework used to build web applications, APIs, dashboards, and backend services.
It is simple, flexible, and great for beginners.

# Features
- 🚀 Lightweight & fast
- 🧩 Easy routing
- 🔧 Built-in development server
- 🟦 Jinja2 template engine
- 📡 Supports APIs (JSON)
- 🗄️ Works with SQL / NoSQL databases
- 🔐 Easy authentication & sessions

  # Installation
# 1️⃣ Install Flask
```bash
pip install flask
```
# 2️⃣ Create Your Project Folder
```cpp
my_flask_app/
│── app.py
│── templates/
│── static/
```
# Project Structure
```cpp
my_flask_app/
│── app.py
│── requirements.txt
│── templates/
│     └── index.html
│── static/
      ├── css/
      ├── js/
      └── images/
```
# Running the App
Run:
```bash
python app.py
```
# Output:
```csharp
* Running on http://127.0.0.1:5000/
```
Open in browser → http://127.0.0.1:5000

# Core Concepts
# Routes

app.py
```python
from flask import Flask

app = Flask(__name__)

@app.route("/")
def home():
    return "Hello, Flask!"

if __name__ == "__main__":
    app.run(debug=True)
```
# Templates

# templates/index.html
```html
<h1>Hello from Template!</h1>
```
# app.py
```python
from flask import render_template

@app.route("/home")
def homepage():
    return render_template("index.html")
```
# Static Files (CSS/JS/Images)

# templates/index.html
```html
<link rel="stylesheet" href="{{ url_for('static', filename='css/style.css') }}">
```
# GET & POST Methods

# app.py
```python
from flask import request

@app.route("/login", methods=["GET", "POST"])
def login():
    if request.method == "POST":
        username = request.form["username"]
        return f"Welcome {username}"
    return "Login Page"
```
# Using Flask with JSON / APIs
```python
from flask import jsonify

@app.route("/api/data")
def api_data():
    return jsonify({"message": "Hello API", "status": 200})
```
# Database (SQLite Example)

# app.py
```python
import sqlite3

def get_db():
    conn = sqlite3.connect("database.db")
    return conn

@app.route("/users")
def users():
    db = get_db()
    rows = db.execute("SELECT * FROM users").fetchall()
    return jsonify(rows)
```
# Environment Variables

# Create .env:
```ini
FLASK_APP=app.py
FLASK_ENV=development
```
# Run:

```bash
flask run
```
# Best Practices
- Use virtual environments
- Store secrets in .env
- Use blueprints for large projects
- Keep templates & static organized
- Use requirements.txt
 # Generate requirements:
 ```bash
pip freeze > requirements.txt
```

# Common Errors
| Error                                        | Meaning                    |
| -------------------------------------------- | -------------------------- |
| ModuleNotFoundError: No module named 'flask' | Flask not installed        |
| TemplateNotFound                             | Wrong template folder name |
| 404 Not Found                                | Wrong route/path           |
| 500 Internal Server Error                    | Python code error          |

# Useful Commands

| Purpose          | Command                         |
| ---------------- | ------------------------------- |
| Start server     | `flask run`                     |
| Create env       | `python -m venv venv`           |
| Install packages | `pip install package_name`      |
| Freeze packages  | `pip freeze > requirements.txt` |

# Good luck....
