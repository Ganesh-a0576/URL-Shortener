 Distributed URL Shortener with Analytics
<div align="center">
Show Image
Show Image
Show Image
Show Image
Show Image
A high-availability, multi-region URL shortener built with Flask, DynamoDB Global Tables, and Redis caching.
Live Demo · Report Bug · Request Feature
</div>

Table of Contents

About the Project
Features
Tech Stack
Architecture
Getting Started

Prerequisites
Installation
Configuration


Usage
Project Structure
API Endpoints
Contributing
License
Contact


About the Project
The Distributed URL Shortener with Analytics is a production-grade web application designed to convert long URLs into compact, shareable short links — all while tracking analytics and ensuring global availability.
Built with a focus on scalability and high availability, this project leverages:

DynamoDB Global Tables for multi-region data replication
Redis caching for ultra-fast redirect resolution
Flask as the lightweight and extensible web framework

Whether you're sharing marketing links, tracking campaign performance, or just simplifying long URLs, this tool handles it all with resilience and speed.

Features

🌍 Multi-region availability via DynamoDB Global Tables
⚡ Redis caching for low-latency URL lookups
📊 Click analytics — track how often each link is used
🔐 Custom short codes or auto-generated slugs
🧾 Form validation using Flask-WTF
🖥️ Clean web UI with templated HTML pages
🔁 RESTful redirects with proper HTTP status codes


Tech Stack
LayerTechnologyBackendPython 3.x, FlaskForm HandlingFlask-WTFDatabaseAWS DynamoDB (Global Tables)CacheRedisTemplatingJinja2 (HTML Templates)FrontendHTML5, CSS3

Architecture
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

Getting Started
Prerequisites
Make sure you have the following installed:

Python 3.x — Download here
pip — comes bundled with Python
Redis — Install guide
AWS Account (for DynamoDB) — Sign up
Git — Download here

Installation

Clone the repository:

bashgit clone https://github.com/Ganesh-a0576/Distributed-URL-Shortener-with-Analytics

Navigate into the project directory:

bashcd WorkFlow

Create a virtual environment (recommended):

bashpython -m venv venv
source venv/bin/activate        # On macOS/Linux
venv\Scripts\activate           # On Windows

Install the required dependencies:

bashpip install flask
pip install flask-wtf
Or install all at once using a requirements file (if available):
bashpip install -r requirements.txt
Configuration
Before running the app, configure your environment variables:
bash# Flask
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

Never commit your credentials to version control. Use .env files or environment variables.


Usage

Start the Flask development server:

bashpython app.py

Open your browser and visit:

http://localhost:5000

Shorten a URL:

Enter a long URL in the input field
Click Shorten
Copy and share your new short link!




Project Structure
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

API Endpoints
MethodEndpointDescriptionGET/Home page — URL shortening formPOST/shortenShorten a given URLGET/<short_code>Redirect to the original URLGET/analytics/<id>View click analytics for a link

Contributing
Contributions are welcome! Here's how to get started:

Fork the repository
Create a new branch: git checkout -b feature/your-feature-name
Make your changes and commit: git commit -m 'Add some feature'
Push to your branch: git push origin feature/your-feature-name
Open a Pull Request

Please make sure your code follows PEP 8 style guidelines and includes appropriate comments.

License
Distributed under the MIT License. See LICENSE for more information.

Contact
Ganesh — @Ganesh-a0576
Project Link: https://github.com/Ganesh-a0576/Distributed-URL-Shortener-with-Analytics

<div align="center">
⭐ If you found this project helpful, please consider giving it a star!
</div>
