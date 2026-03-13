# 🔗 Distributed URL Shortener with Analytics

<div align="center">

![Python](https://img.shields.io/badge/Python-3.x-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-2.x-000000?style=for-the-badge&logo=flask&logoColor=white)
![DynamoDB](https://img.shields.io/badge/DynamoDB-Global_Tables-4053D6?style=for-the-badge&logo=amazondynamodb&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-Cache-DC382D?style=for-the-badge&logo=redis&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

**A high-availability, multi-region URL shortener built with Flask, DynamoDB Global Tables, and Redis caching.**

[Live Demo](#) · [Report Bug](https://github.com/Ganesh-a0576/Distributed-URL-Shortener-with-Analytics/issues) · [Request Feature](https://github.com/Ganesh-a0576/Distributed-URL-Shortener-with-Analytics/issues)

</div>

---

## 📌 Table of Contents

- [About the Project](#-about-the-project)
- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Architecture](#-architecture)
- [Getting Started](#-getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
  - [Configuration](#configuration)
- [Usage](#-usage)
- [Project Structure](#-project-structure)
- [API Endpoints](#-api-endpoints)
- [Contributing](#-contributing)
- [License](#-license)
- [Contact](#-contact)

---

## 📖 About the Project

The **Distributed URL Shortener with Analytics** is a production-grade web application designed to convert long URLs into compact, shareable short links — all while tracking analytics and ensuring global availability.

Built with a focus on **scalability** and **high availability**, this project leverages:
- **DynamoDB Global Tables** for multi-region data replication
- **Redis caching** for ultra-fast redirect resolution
- **Flask** as the lightweight and extensible web framework

Whether you're sharing marketing links, tracking campaign performance, or just simplifying long URLs, this tool handles it all with resilience and speed.

---

## ✨ Features

- 🌍 **Multi-region availability** via DynamoDB Global Tables
- ⚡ **Redis caching** for low-latency URL lookups
- 📊 **Click analytics** — track how often each link is used
- 🔐 **Custom short codes** or auto-generated slugs
- 🧾 **Form validation** using Flask-WTF
- 🖥️ **Clean web UI** with templated HTML pages
- 🔁 **RESTful redirects** with proper HTTP status codes

---

## 🛠 Tech Stack

| Layer         | Technology              |
|---------------|-------------------------|
| Backend       | Python 3.x, Flask       |
| Form Handling | Flask-WTF               |
| Database      | AWS DynamoDB (Global Tables) |
| Cache         | Redis                   |
| Templating    | Jinja2 (HTML Templates) |
| Frontend      | HTML5, CSS3             |

---

## 🏗 Architecture

```
User Request
     │
     ▼
 Flask App (app.py)
     │
     ├──▶ Redis Cache (Check for short URL)
     │         │
     │    Hit ◄─┴─► Miss
     │         │         │
     │    Return URL    DynamoDB Global Tables
     │                       │
     │              Retrieve & Cache URL
     │                       │
     └───────────────────────┘
                 │
          Redirect User
```

---

## 🚀 Getting Started

### Prerequisites

Make sure you have the following installed:

- **Python 3.x** — [Download here](https://www.python.org/downloads/)
- **pip** — comes bundled with Python
- **Redis** — [Install guide](https://redis.io/docs/getting-started/)
- **AWS Account** (for DynamoDB) — [Sign up](https://aws.amazon.com/)
- **Git** — [Download here](https://git-scm.com/)

### Installation

1. **Clone the repository:**

```bash
git clone https://github.com/Ganesh-a0576/Distributed-URL-Shortener-with-Analytics
```

2. **Navigate into the project directory:**

```bash
cd WorkFlow
```

3. **Create a virtual environment (recommended):**

```bash
python -m venv venv
source venv/bin/activate        # On macOS/Linux
venv\Scripts\activate           # On Windows
```

4. **Install the required dependencies:**

```bash
pip install flask
pip install flask-wtf
```

Or install all at once using a requirements file (if available):

```bash
pip install -r requirements.txt
```

### Configuration

Before running the app, configure your environment variables:

```bash
# Flask
export FLASK_APP=app.py
export FLASK_ENV=development
export SECRET_KEY=your_secret_key_here

# AWS DynamoDB
export AWS_ACCESS_KEY_ID=your_access_key
export AWS_SECRET_ACCESS_KEY=your_secret_key
export AWS_REGION=your_region

# Redis
export REDIS_HOST=localhost
export REDIS_PORT=6379
```

> ⚠️ **Never commit your credentials to version control.** Use `.env` files or environment variables.

---

## 💻 Usage

1. **Start the Flask development server:**

```bash
python app.py
```

2. **Open your browser and visit:**

```
http://localhost:5000
```

3. **Shorten a URL:**
   - Enter a long URL in the input field
   - Click **Shorten**
   - Copy and share your new short link!

---

## 📁 Project Structure

```
Distributed-URL-Shortener-with-Analytics/
│
├── app.py                  # Main Flask application entry point
├── forms.py                # Flask-WTF form definitions
├── requirements.txt        # Python dependencies
├── .env.example            # Example environment variables
│
├── templates/              # Jinja2 HTML templates
│   ├── base.html           # Base layout with common HTML structure
│   └── index.html          # Home page template
│
├── static/                 # Static assets (CSS, JS, images)
│   ├── css/
│   └── js/
│
└── README.md               # Project documentation
```

---

## 🔌 API Endpoints

| Method | Endpoint          | Description                        |
|--------|-------------------|------------------------------------|
| GET    | `/`               | Home page — URL shortening form    |
| POST   | `/shorten`        | Shorten a given URL                |
| GET    | `/<short_code>`   | Redirect to the original URL       |
| GET    | `/analytics/<id>` | View click analytics for a link    |

---

## 🤝 Contributing

Contributions are welcome! Here's how to get started:

1. **Fork** the repository
2. Create a new branch: `git checkout -b feature/your-feature-name`
3. Make your changes and **commit**: `git commit -m 'Add some feature'`
4. **Push** to your branch: `git push origin feature/your-feature-name`
5. Open a **Pull Request**

Please make sure your code follows PEP 8 style guidelines and includes appropriate comments.

---

## 📄 License

Distributed under the **MIT License**. See `LICENSE` for more information.

---

## 📬 Contact

**Ganesh** — [@Ganesh-a0576](https://github.com/Ganesh-a0576)

Project Link: [https://github.com/Ganesh-a0576/Distributed-URL-Shortener-with-Analytics](https://github.com/Ganesh-a0576/Distributed-URL-Shortener-with-Analytics)

---

<div align="center">

⭐ If you found this project helpful, please consider giving it a star!

</div>
