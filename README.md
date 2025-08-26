# 🚀 Ad Violation Reporting System

This is a **full-stack hackathon project** for detecting and reporting billboard advertisement violations.  
It consists of three parts:  

- 📱 **Ad Violation Mobile App** → Capture billboard photos, scan QR codes, and submit violation reports.  
- 🤖 **Ad Violation Backend (FastAPI)** → Processes reports using AI, validates data, and stores results in Supabase.  
- 📊 **Ad Violation Dashboard** → View and analyze reports online:  
  👉 [Ad Violation Dashboard](https://technova-hackathon.github.io/ad-violation-portal/)  

---

## ⚡ Quick Start

### Start Backend (FastAPI)
Run the server inside `ad-violation-backend/`:

```bash
python -m uvicorn main:app --host 0.0.0.0 --port 8000 --reload
```

Server will be available at:  
👉 `http://127.0.0.1:8000` (with docs at `/docs`)

---

### Start Mobile App (Expo)
Run the app inside `ad-violation-mobile/`:

```bash
npx expo start
```
## Remember this is being locally hosted so the ip of the host and the android device must be same. you can change that in
## /ad-violation-mobile/utils/api.ts

Open in:  
- **Expo Go App** (scan QR code)  
- **Android/iOS emulator**

---

## 📂 Project Structure

```
ad-violation-project/
│── ad-violation-backend/     # FastAPI server
│   ├── main.py
│   ├── requirements.txt
│   └── .env.example
│
│── ad-violation-mobile/      # React Native (Expo) mobile app
│   ├── screens/
│   ├── components/
│   ├── utils/
│   └── App.js
│
│── ad-violation-portal/      # Dashboard (GitHub Pages)
│   └── index.html
│
│── README.md                 # This file
```

---

## ✨ Features

### 📱 Mobile App (React Native + Expo)
- **Camera & Location Services** → Capture billboard photos with geotags.  
- **QR Code Scanner** → Detect & validate QR codes on billboards.  
- **Real-time Feedback** → Popup shows AI result: ✅ No Issues, 🚫 Violation, ⚠️ Invalid Image.  
- **Reports Tab** → View past reports with thumbnails, status & details.  
- **Infinite Scrolling** → Efficient report history loading.  

---

### 🤖 Backend (FastAPI)
- **Image Analysis with Gemini AI** → Detects billboards, text, sensitive material.  
- **Geolocation & Time Fencing** → Ensures reports are valid by location & time.  
- **QR Code Verification** → Uses HMAC signatures to confirm authenticity.  
- **Supabase Integration** → Updates reports table with AI results.  
- **REST API** → Simple `/analyze` endpoint for mobile app.  

---

### 📊 Dashboard
- **Web-based Reports Viewer** hosted on GitHub Pages.  
- View all reports submitted from the mobile app.  
- Provides status, metadata, and analytics.  

👉 Live Dashboard: [https://technova-hackathon.github.io/ad-violation-portal/](https://technova-hackathon.github.io/ad-violation-portal/)

---

## 🔑 Environment Setup

Backend requires a `.env` file inside `ad-violation-backend/`:

```env
SUPABASE_URL="https://[your-project-id].supabase.co"
SUPABASE_SERVICE_ROLE_KEY="[your-supabase-service-role-key]"
QR_HMAC_SECRET="[your-secret-key-for-qrs]"
GOOGLE_API_KEY="[your-gemini-api-key]"
```

---

## 📌 API Endpoint

### `POST /analyze`

**Request Parameters:**
- `image_url` → Public image URL  
- `lat` → Latitude  
- `lon` → Longitude  
- `qr_value` → (Optional) QR code  
- `report_id` → Supabase report ID  

**Response Example:**

```json
{
  "status": "success | violation | error",
  "message": "Detailed outcome message"
}
```

---

## 📜 License

This project is licensed under the **MIT License**.
