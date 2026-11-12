# MCBP Support Dashboard 🚀

A lightweight, serverless **Issue Tracking & Support Dashboard** designed for the Mother and Child Beneficiary Program (MCBP) Intern Team. 

The application features a modern, responsive frontend built with Vanilla HTML/CSS/JS, hosted on **Vercel**, and uses **Google Apps Script** + **Google Sheets** as a free, serverless database and backend.

## ✨ Key Features

- **🔐 Secure Authentication:** User login system backed by Google Sheets. Includes session timeout (auto-logout) and "Sign-in" status tracking.
- **🛡️ Role-Based Access Control (RBAC):**
  - **Admin:** Can view, edit, update status, and delete *all* issues.
  - **Intern:** Can only view and edit their *own* created issues.
- **📊 Interactive Analytics:** Dynamic KPI cards and charts (Issues by type, Issues by month, Resolution by group) built with pure CSS/JS.
- **📝 Issue Management:** Separate tracks for **Union/Upazila** and **Factory** (BGMEA, BKMEA, FLAXA) issues.
- **🔄 Real-time Sync:** Auto-refreshes data every 30 seconds to ensure the whole team stays updated.
- **🔑 Password Reset:** Users can securely reset their passwords by verifying their old password and email.
- **🎨 Responsive UI:** Clean, modern design with Dark Mode support, fully responsive for desktops, tablets, and mobile devices.

## 🏗️ Architecture

This project uses a modern **Serverless** architecture:
- **Frontend:** Single-page HTML/CSS/JS (No build step required).
- **Backend:** Google Apps Script (`Code.gs`) handling API routing, logic, and security.
- **Database:** Google Sheets (3 Tables: `user`, `Union_Upazila`, `Factory`).
- **Hosting:** Vercel / Netlify (for the frontend).

## 🚀 Setup & Deployment Guide

### Phase 1: Backend & Database Setup
1. **Create a Google Sheet** named `MCBP Support Dashboard Database`.
2. Open **Extensions > Apps Script**.
3. Paste the `Code.gs` provided in this repository into the Apps Script editor.
4. Update the `SPREADSHEET_ID` in the `CONFIG` object inside `Code.gs`.
5. Run the `initializeDatabase()` function once. This will auto-create the 3 required sheets (`user`, `Union_Upazila`, `Factory`).
6. Deploy as a **Web App**:
   - Execute as: **Me**
   - Who has access: **Anyone** *(Important for CORS)*
7. Copy the **Web App URL** (ending in `/exec`).

### Phase 2: Frontend Configuration
1. Download or clone this repository.
2. Open `index.html` in your code editor.
3. Locate the `CONFIG` object at the top of the `<script>` tag:
   ```javascript
   const CONFIG = {
     API_URL: "YOUR_GOOGLE_APPS_SCRIPT_URL_HERE",
     AUTO_REFRESH_INTERVAL: 30000,
     REQUEST_TIMEOUT: 25000
   };
