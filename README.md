# NET-WATCH // Digital Sovereignty & Privacy Audit Tool

![Status](https://img.shields.io/badge/Status-Active-success)
![Compliance](https://img.shields.io/badge/Compliance-DPDP%20Act%202023-blue)
![Engine](https://img.shields.io/badge/Engine-Puppeteer%20%7C%20Node.js-yellow)
![AI](https://img.shields.io/badge/AI-Google%20Gemini-orange)

**NET-WATCH** is a real-time forensic auditing tool that performs Application-Layer Deep Packet Inspection (DPI) on web traffic. It empowers regulators, auditors, and everyday users to verify website data practices against the **Digital Personal Data Protection (DPDP) Act 2023**.

---

## 🚨 The Problem

Modern websites declare their privacy compliance through static, dense privacy policies. However, users and regulators have no automated way to verify if a website's *actual behavior* matches its *stated commitments*. 
* **Data Exfiltration:** Where is my data actually going? Is it secretly leaving the country?
* **Hidden Tracking:** How are tech giants disguising third-party trackers as first-party assets?
* **Obfuscated Payloads:** What Personally Identifiable Information (PII) is hidden inside encrypted API calls?

## 🛡️ Our Solution

NET-WATCH shifts privacy from "policy reading" to **behavior verification**. Unlike simple ad-blockers that rely on static URL blocklists, NET-WATCH orchestrates a headless Chrome browser to execute dynamic JavaScript, intercepting and analyzing network traffic in real-time before it is encrypted by TLS/SSL.

---

## ✨ Key Capabilities

### 1. 🤖 GenAI Compliance Auditor (Phase 2 Feature)
* **Explainable Privacy:** Acts as an automated privacy lawyer. It feeds raw, intercepted network packets into a Google Gemini LLM reasoning layer.
* **Contextual Verdicts:** Detects when companies use opaque domains to bypass standard tracker rules and generates a plain-English DPDP compliance verdict in seconds.

### 2. 🌍 3D Data Sovereignty Map
* **Real-Time Geo-Tracing:** Resolves the IP addresses of every API request to physical lat/long coordinates.
* **Sovereignty Meter:** Calculates the exact percentage of data remaining localized versus foreign exfiltration, rendered on an interactive WebGL globe.

### 3. 🕵️ Deep Packet Forensics
* **Payload Interception:** Captures raw `POST`/`GET` data leaving the browser.
* **Auto-Decryption Heuristics:** Built-in engine that automatically detects and decodes Base64-obfuscated payloads, revealing hidden PII (emails, IDs, passwords) in plain text via the "Evidence Locker".

### 4. 🍪 Storage & Security Audit
* **Cookie Forensics:** Distinguishes between Session (Transient) and Persistent (Tracking) storage vectors.
* **Infrastructure Inspection:** Verifies the cryptographic integrity of the connection (e.g., ensuring modern TLS 1.3 handshakes).

---

## 🛠️ System Architecture & Tech Stack

* **Backend / Orchestration:** Node.js, Express.js
* **Traffic Interception:** Puppeteer (Headless Chrome DPI)
* **Real-Time Telemetry:** Socket.io (Bi-directional event streaming)
* **AI Reasoning Layer:** Google Gemini SDK (`gemini-2.5-flash`)
* **Frontend / Visualization:** Vanilla JS, Three.js / Globe.gl (3D Geospatial), Chart.js
* **Geolocation:** IP-API integration

---

## 🚀 Installation & Local Deployment

Follow these steps to run NET-WATCH on your local machine.

### Prerequisites
* **Node.js** (v18+ recommended)
* **Google Gemini API Key** ([Get one for free here](https://aistudio.google.com/app/apikey))

### 1. Clone the Repository
```bash
git clone https://github.com/Yashwin-i/NetWatch-GenAI-Auditor.git
cd NetWatch-GenAI-Auditor
```

### 2. Install Dependencies
```bash
npm install
```

### 3. Configure the AI Engine (Securely)
**SECURITY WARNING:** Never hardcode your API key into `server.js`. NET-WATCH expects the key to be provided as an environment variable to prevent accidental exposure on GitHub.

**Option A: Using Terminal Export (Quickest for one-time testing)**
For Windows (PowerShell):
```powershell
$env:GEMINI_API_KEY="your_secret_api_key_here"
```

For Mac/Linux:
```bash
export GEMINI_API_KEY="your_secret_api_key_here"
```

**Option B: Using a .env file (Best for continuous development)**
Create a file named `.env` in the root directory of the project. Add your key inside the file like this:
```env
GEMINI_API_KEY=your_secret_api_key_here
```
Make sure `.env` is listed in your `.gitignore` file.

### 4. Run the Platform
Once your key is set, start the server:
```bash
node server.js
```
Open your web browser and navigate to `http://localhost:3000`.

---

## 🎯 How to Run an Audit (Demo Guide)
* **Target:** Enter a URL (e.g., `https://netflix.com`) into the command center and click **SCAN**.
* **Monitor:** Watch the Live Traffic Feed as the headless engine bypasses bot detection and intercepts packets.
* **Analyze:** Check the Sovereignty Meter to see the ratio of localized vs. exfiltrated data.
* **Forensics:** If a payload is caught, click **VIEW EVIDENCE** to see the decoded Base64 hidden data.
* **AI Reasoning:** Click the **✨ GenAI Audit** button to synthesize the raw packet data into a plain-English DPDP compliance report.
* **Visualize:** Click **LIVE MAP ➔** to watch data paths render in 3D in real-time.
