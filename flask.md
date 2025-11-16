<p align="center">
  <h1>🔥Flask</h1>
</p>

# 📌 What is Flask?
Flask is a lightweight, micro web framework in Python.
It is used to build web applications, REST APIs, dashboards, and backend services.

- ✔ Fast
- ✔ Easy to learn
- ✔ Minimal code
- ✔ Highly flexible
- ✔ Can add extensions anytime

# 🧩 Why use Flask?

| Feature      | Meaning                                        |
| ------------ | ---------------------------------------------- |
| Lightweight  | Only essential features, not heavy like Django |
| Easy         | Beginner-friendly                              |
| Flexible     | You design your own architecture               |
| API-friendly | Easy REST API development                      |
| Extensions   | Add DB, auth, JWT, login, etc.                 |

# ⚙ Flask Installation
```bash
pip install flask
```
# 🏁 1. Start a Flask Project
Basic “Hello World” App
```python
from flask import Flask

app = Flask(__name__)

@app.route("/")
def home():
    return "Hello, Flask!"

if __name__ == "__main__":
    app.run(debug=True)
```
Run:
```bash
python app.py
```
# 🛣 2. Routing in Flask
Simple Route
```python
@app.route("/about")
def about():
    return "This is the About Page"
```

Dynamic Route

```python
@app.route("/user/<name>")
def user(name):
    return f"Hello {name}"
```

# 📤 3. Handling GET & POST Requests
```python
from flask import request

@app.route("/submit", methods=["POST"])
def submit():
    data = request.json
    return {"received": data}
```
# 🗄 4. Rendering HTML (Templates)
Folder structure:
```arduino
app.py
templates/
    home.html
```
# app.py
```python
from flask import render_template

@app.route("/")
def home():
    return render_template("home.html", name="  ")
```
# home.html

```html
<h1>Hello {{ name }}</h1>
```
# 🛢 5. Using Database (SQLite Example)

Install:
```bash
pip install flask_sqlalchemy
```
# Configure:
```python
from flask_sqlalchemy import SQLAlchemy

app.config['SQLALCHEMY_DATABASE_URI'] = "sqlite:///mydb.db"
db = SQLAlchemy(app)
```
# Define a Model
```python
class Users(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    name = db.Column(db.String(100))
```
# Insert Data
```python
u = Users(name="Sonam")
db.session.add(u)
db.session.commit()
```

# 🔐 6. JWT Authentication
Install: 
```bash
pip install flask-jwt-extended
```
# Usage: 
```python
from flask_jwt_extended import JWTManager, create_access_token

app.config["JWT_SECRET_KEY"] = "secret123"
jwt = JWTManager(app)

@app.post("/login")
def login():
    token = create_access_token(identity="sonam")
    return {"token": token}
```
# 🔗 7. Complete REST API Example
```python
from flask import Flask, request

app = Flask(__name__)

students = []

@app.get("/students")
def get_students():
    return {"students": students}

@app.post("/students")
def add_student():
    data = request.json
    students.append(data)
    return {"message": "Student added"}

if __name__ == "__main__":
    app.run(debug=True)
```
# 🧪 8. Error Handling
```python
@app.errorhandler(404)
def not_found(e):
    return {"error": "Not Found"}, 404
```
# 🧬 9. Middleware
```python
@app.before_request
def before_req():
    print("Request received")
```

# 🧰 10. Popular Flask Extensions
| Extension          | Purpose             |
| ------------------ | ------------------- |
| Flask-SQLAlchemy   | Database ORM        |
| Flask-JWT-Extended | JWT Authentication  |
| Flask-Mail         | Send emails         |
| Flask-Migrate      | DB migrations       |
| Flask-Login        | User authentication |
| Flask-CORS         | Allow cross-origin  |

# 🚀 11. Deployment
Best deployment platforms:
- Render
- Railway
- PythonAnywhere
- Vercel (Serverless)
- Docker

# Run using Gunicorn:
```bash
gunicorn app:app
```
# 📚 12. Important Flask Interview Questions
- What is Flask?
- How is Flask different from Django?
- How routing works in Flask?
- What is the Jinja2 template engine?
- How sessions work in Flask?
- What are Blueprints?
- How to secure API using JWT?
- Explain request & response cycle.
- How to connect Flask with database?
- How to structure a large Flask app?

# 🧱 13. Best Folder Structure
```arduino
project/
│── app.py
│── requirements.txt
│── config.py
│── static/
│── templates/
└── routes/
      └── users.py
```
# 🧩 14. Flask Blueprints (Modular Apps)
```python
from flask import Blueprint

user_bp = Blueprint("users", __name__)

@user_bp.get("/all")
def all_users():
    return {"users": ["Sonam", "Rahul"]}
```
# Register:
```python
app.register_blueprint(user_bp, url_prefix="/users")
```
# ⭐ 15. Flask vs Django
| Flask            | Django                |
| ---------------- | --------------------- |
| Lightweight      | Heavy, feature-rich   |
| More control     | Predefined structure  |
| Perfect for APIs | Great for large sites |
| Manual DB setup  | Built-in ORM          |
| Flexible         | Opinionated           |


# Good Luck...
