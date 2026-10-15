# 🧟 Project Frankenstein: Repo 1 - The Body (Frontend Portal)

Welcome to the **Frankenstein Web Challenge**!

> *"It's alive! ... Or is it?"*  
> The creature has been severed in half. This repository contains **The Body** — the user interface, styling, bilingual localization, and interaction layers of the PM Internship Portal. However, its nervous system is broken, and its connection to the AI Brain (Repo 2) is dead.
>
> **Your Goal:** Stitch this frontend back together with the backend brain so the full portal comes alive!

---

## 📁 Repository Structure
```
repo_1_frontend/
├── index.html              # Landing Page (Overview & Scheme info)
├── dashboard.html          # Main Dashboard & "Intern Sevak" AI Assistant Widget
├── auth.html               # Registration & Login Page
├── styles/                 # Modular CSS stylesheets
│   ├── main.css
│   ├── dashboard.css
│   ├── landing.css
│   └── auth.css
├── js/                     # Client JavaScript
│   ├── dashboard.js        # ⚡ CONTAINS CRITICAL SEVERED SYNAPSES!
│   ├── auth.js             # Form validation & auth helpers
│   ├── firebase-config.js  # Firebase client configuration
│   ├── language.js         # Bilingual dictionary (English/Hindi)
│   └── landing.js          # Landing page interactions
└── vercel.json             # Deployment routing config
```

---

## ⚡ Your Stitching Challenges in this Repo

Search for the `⚡ [FRANKENSTEIN CHALLENGE]` markers inside `js/dashboard.js`:

### 🎯 Challenge 1: The Severed Nerve Cord (API Base URL)
* **File:** `js/dashboard.js` (Line ~7)
* **Problem:** The frontend `API_BASE_URL` points to an unreachable port (`http://localhost:9999_SEVERED_PORT`).
* **Your Task:** Point this to where your backend brain is running (typically `http://localhost:8000` during local development, or a relative path `/api` if you unify the repos behind a proxy).

### 🎯 Challenge 2: The Severed Synapse (Recommendation Pipeline)
* **File:** `js/dashboard.js` in `finishConversation()` (Line ~470)
* **Problem:** When the user completes the questions in the chat assistant, the function throws an error because the POST request to `/api/recommend` has been severed.
* **Your Task:** 
  1. Restore the `fetch` POST call to `${API_BASE_URL}/api/recommend`.
  2. Send the user profile JSON payload containing:
     ```json
     {
       "name": "Candidate Name",
       "academic_background": "Computer Science",
       "skills": ["python", "sql"],
       "sector_interest": ["IT"],
       "location_preference": ["Remote"],
       "prefers_remote": true,
       "is_fresher": true
     }
     ```
  3. Parse the JSON response and pass `data.recommendations` into `updateDashboardWithRecommendations(data.recommendations)`.

### 🎯 Challenge 3: Muted Vocal Cords (TTS Route)
* **File:** `js/dashboard.js` in `speakText(text)` (Line ~715)
* **Problem:** The audio synthesizer queries a broken endpoint `/api/broken_voice_tts` instead of the backend's speech route.
* **Your Task:** Align this route with the backend TTS endpoint (`/api/speak`) so "Intern Sevak" can speak audio responses.

---

## 🚀 How to Run the Frontend Locally

You can serve this frontend using any static file server:

### Option A: VS Code Live Server
* Open this folder in VS Code, right click `index.html` or `dashboard.html`, and select **Open with Live Server**.

### Option B: Python HTTP Server
```bash
python -m http.server 3000
```
Then visit `http://localhost:3000` in your browser.

---

> 💡 **Stitching Clue:** To complete the creature, you must run **Repo 2 (The Brain)** simultaneously and ensure both halves can communicate without CORS errors or broken schemas!
