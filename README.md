# 🔍 PriyankaBot AI — Multi-Source Search Engine

A full-stack AI-powered search platform that aggregates results from **Google Web, Google Scholar, News, Books, and YouTube** — all in one place, with secure OAuth 2.0 authentication and production-ready security features.

Built with **Python Flask** · **HTML/CSS/JS** · **Serper API** · **OAuth 2.0**

---

## ✨ Features

### 🔎 Multi-Source Search
- **Google Web** — General web results via Serper API
- **Google Scholar** — Academic papers and research articles
- **News Articles** — Latest news from multiple publishers
- **Google Books** — Books and publications
- **YouTube Videos** — Video content with metadata

### 🔐 Secure Authentication
OAuth 2.0 login with:
- 🟦 Google
- ⚫ GitHub
- 🟦 Microsoft

Plus username/password login with secure session management (HttpOnly cookies, 7-day persistent sessions).

### ⚡ Performance & Security
| Feature | Detail |
|---|---|
| Rate Limiting | 200 requests/day, 50/hour per user |
| Caching | 5-minute cache — reduces API calls by ~60% |
| Input Sanitisation | XSS and injection prevention |
| CORS Protection | Configured cross-origin policies |
| Retry Mechanism | Exponential backoff on failures |
| User Agent Rotation | Prevents scraping blocks |

---

## 🛠️ Tech Stack

**Backend:** Python 3.8+, Flask, Authlib, BeautifulSoup4, Requests  
**Frontend:** HTML5, CSS3, JavaScript (Responsive UI)  
**APIs:** Google Serper API, Google Books API, YouTube (scraping)  
**Security:** Flask-Limiter, Flask-Caching, Flask-CORS, python-dotenv

---

## 🚀 Getting Started

### 1. Clone the repository
```bash
git clone https://github.com/priyanka20041012ai-cloud/priyankabot-ai.git
cd priyankabot-ai
```

### 2. Create a virtual environment
```bash
python -m venv venv

# Windows
venv\Scripts\activate

# Linux / Mac
source venv/bin/activate
```

### 3. Install dependencies
```bash
pip install -r requirement.txt
```

### 4. Set up environment variables

Create a `.env` file in the root directory:

```env
# Flask
SECRET_KEY=your_super_secret_key_min_32_chars

# Google OAuth
GOOGLE_CLIENT_ID=your_google_client_id
GOOGLE_CLIENT_SECRET=your_google_client_secret

# GitHub OAuth
GITHUB_CLIENT_ID=your_github_client_id
GITHUB_CLIENT_SECRET=your_github_client_secret

# Microsoft OAuth
MICROSOFT_CLIENT_ID=your_microsoft_client_id
MICROSOFT_CLIENT_SECRET=your_microsoft_client_secret

# Serper API (Google Search)
SERPER_API_KEY=your_serper_api_key

# App URL
APP_URL=http://localhost:5000
```

### 5. Configure OAuth providers

**Google** → [Google Cloud Console](https://console.cloud.google.com)  
Add redirect URI: `http://localhost:5000/auth/google/callback`

**GitHub** → [GitHub Developer Settings](https://github.com/settings/developers)  
Add callback URL: `http://localhost:5000/auth/github/callback`

**Microsoft** → [Azure Portal](https://portal.azure.com)  
Add redirect URI: `http://localhost:5000/auth/microsoft/callback`

**Serper API** → [serper.dev](https://serper.dev) (free tier: 2,500 searches/month)

### 6. Run the app
```bash
python app.py
```

Visit: `http://localhost:5000`

---

## 📁 Project Structure

```
priyankabot-ai/
│
├── app.py               # Main Flask application
├── requirement.txt      # Python dependencies
├── .env                 # Environment variables (create this — do not commit)
│
└── templates/
    ├── index.html       # Search interface
    └── login.html       # Login page
```

---

## 🔌 API Endpoints

### Search
```
POST /search
Content-Type: application/json

{ "query": "machine learning", "search_type": "all" }
```

**search_type options:** `all`, `web`, `scholar`, `news`, `books`, `youtube`

### Other
```
GET /api/user     → Current user info
GET /health       → Health check
GET /logout       → Log out
```

---

## ⚠️ Known Limitations

- Google Scholar and News scraping may break if Google changes its HTML structure
- YouTube results rely on JavaScript parsing — may need updates
- Serper API free tier is limited to 2,500 searches/month
- Some results may be blocked by anti-scraping measures

---

## 🚧 Planned Features

- [ ] User search history
- [ ] Filter and sort results
- [ ] Dark mode
- [ ] Export results (PDF / CSV)
- [ ] More sources (Reddit, Stack Overflow)
- [ ] Browser extension
- [ ] Multi-language support

---

## 🔒 Security Notes

- Never commit your `.env` file — add it to `.gitignore`
- In production, uncomment `SESSION_COOKIE_SECURE = True` in `app.py` (requires HTTPS)
- Rotate your `SECRET_KEY` periodically

---

## 👩‍💻 Author

**Priyanka Mathiyalakan**  
📧 priyankamathiyalakan@gmail.com  
🔗 [LinkedIn](https://www.linkedin.com/in/priyankamathiyalakan123)  
🐙 [GitHub](https://github.com/priyanka20041012ai-cloud)

---

## 📝 License

This project is licensed under the MIT License.
