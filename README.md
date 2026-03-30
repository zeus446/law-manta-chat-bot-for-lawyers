# ⚖ LegalMantra — AI Command Centre for Lawyers

> The AI co-counsel that never sleeps.  
> Research case law. Draft documents. Build strategy. Prep depositions.  
> All from one command centre.

---

## 📌 Overview

**LegalMantra (LexCommand AI)** is a high-end AI legal command interface designed specifically for lawyers and legal professionals.

It provides structured AI modes for:

- 🔬 Legal Research  
- ✍️ Document Drafting  
- 🔍 Document Review  
- ⚔️ Case Strategy  
- 🎙️ Deposition & Cross-Examination  
- 📋 Legal Memo & Brief Writing  
- 📨 Client Communication  
- 💰 Billing & Time Entries  
- 🤝 Negotiation Strategy  
- 🛡️ Compliance & Risk Assessment  

This project is a fully styled, modern legal AI interface powered by **Groq API** (LLM backend), designed to function as an AI co-counsel rather than a generic chatbot.

---

## 🚀 Features

### 🧠 Multi-Mode Legal Intelligence
Each mode changes how the AI thinks and responds:
- Structured outputs
- Litigation-focused reasoning
- Case citations
- Risk scoring
- Negotiation logic
- Formal memo drafting

---

### ⚙️ Lawyer Context Injection
Optional structured context:
- Lawyer / Firm name
- Jurisdiction
- Practice area
- Active matter/client

AI responses automatically adapt to this context.

---

### 📁 Matter Command Panel
- Quick legal actions
- Jurisdiction toggles (India, UK, USA, EU)
- Smart session notes
- Case-aware prompts

---

### 💬 Professional Chat Interface
- Legal-grade formatting
- Structured markdown rendering
- Copy / Download / Expand tools
- Export full transcript
- Conversation reset
- Matter reset

---

### 🔐 Secure API Key Storage
- LocalStorage-based key saving
- No server persistence of credentials
- Manual Groq API configuration

---

## 🏗 Tech Stack

| Component | Technology |
|------------|------------|
| Frontend | HTML5 |
| Styling | Advanced CSS (custom theme) |
| Logic | Vanilla JavaScript |
| AI Backend | Groq API |
| Model | llama-3.3-70b (configurable) |

No frameworks. No dependencies. Pure client-side interface.

---

## 📂 Project Structure

```
project-folder/
│
├── lexcommand-lawyer-ai.html
└── README.md
```

This is a single-file application.

---

## 🛠 Installation

### 1️⃣ Clone or Download

```bash
git clone <your-repository-url>
cd lexcommand-lawyer-ai
```

Or simply download the HTML file.

---

### 2️⃣ Run a Local Backend Proxy

The frontend expects a backend endpoint at:

```
http://localhost:3131/grok
```

You must run a lightweight server that:

- Accepts POST requests
- Injects Groq API key
- Calls Groq API
- Returns `{ reply: "..." }`

Example Node.js proxy (minimal):

```javascript
import express from "express";
import fetch from "node-fetch";

const app = express();
app.use(express.json());

app.post("/grok", async (req, res) => {
  const { apiKey, system, messages } = req.body;

  const response = await fetch("https://api.groq.com/openai/v1/chat/completions", {
    method: "POST",
    headers: {
      "Authorization": `Bearer ${apiKey}`,
      "Content-Type": "application/json"
    },
    body: JSON.stringify({
      model: "llama-3.3-70b",
      messages: [
        { role: "system", content: system },
        ...messages
      ]
    })
  });

  const data = await response.json();
  res.json({ reply: data.choices?.[0]?.message?.content });
});

app.listen(3131, () => console.log("Server running on port 3131"));
```

Run:

```bash
node server.js
```

---

### 3️⃣ Open the App

Simply open:

```
lexcommand-lawyer-ai.html
```

in your browser.

---

## 🔑 Groq API Setup

1. Get API key from Groq.
2. Enter key in sidebar.
3. Click **Save**.
4. Status will change to: ✓ Active — Ready to counsel

---

## 🧠 AI Modes Explained

Each mode modifies the system prompt and response structure.

### 🔬 Legal Research Mode
- Statutory analysis
- Case citations (Name v Name, Year, Court)
- Legal framework breakdown
- Practical takeaways
- Critical considerations

---

### ✍️ Document Drafting Mode
- Professionally structured contracts
- Negotiation notes
- Risk warnings
- Alternative clause options

---

### 🔍 Document Review Mode
- Red Flags (serious risks)
- Amber Flags (negotiation points)
- Risk Score
- Recommended amendments

---

### ⚔️ Case Strategy Mode
- Ranked arguments
- Opposing arguments + rebuttals
- Evidence map
- Litigation roadmap
- Settlement strategy

---

### 🎙️ Deposition Mode
- Strategic cross-examination sequences
- Follow-up traps
- Purpose-tagged questions

---

### 📋 Memo & Brief Mode
- IRAC / CREAC structure
- Formal writing tone
- Appellate-ready drafting

---

### 📨 Client Communication Mode
- Clear language
- Empathetic tone
- Non-overpromising
- Action steps

---

### 💰 Billing Mode
- Defensible time entries
- Anti block-billing guidance
- Narrative clarity

---

### 🤝 Negotiation Mode
- BATNA analysis
- Concession mapping
- Leverage identification
- Tactical language

---

### 🛡️ Compliance Mode
- Regulatory mapping
- Risk matrix (Likelihood × Impact)
- Priority ranking
- Remediation plan

---

## 📤 Exporting Transcripts

- Click **Export**
- Downloads structured legal transcript
- Includes:
  - Counsel name
  - Matter
  - Mode
  - Timestamp
  - Full conversation

---

## ⚠️ Important Notes

- This tool is for **licensed legal professionals**
- AI output must always be independently verified
- Case citations may require manual validation
- No client data should be uploaded unless compliant with your jurisdiction's data protection rules

---

## 🔐 Security Notice

- API keys stored locally in browser
- No authentication layer included
- No encryption layer included
- Intended for local / private use

For production deployment:
- Add HTTPS
- Add auth layer
- Add encrypted key vault
- Add logging controls

---

## 🚀 Future Improvements

- Multi-matter management
- Persistent encrypted session storage
- Citation verification layer
- PDF export
- Integrated legal databases
- Court-rule calendar automation
- AI memory per client
- Secure hosted version

---

## 👨‍⚖️ Who This Is For

- Litigation lawyers
- Corporate counsel
- Criminal defense advocates
- Compliance officers
- Legal researchers
- Boutique law firms
- Solo practitioners

---

## 📜 License

This project is provided for educational and experimental purposes.

You may modify and expand it freely.

For commercial use, ensure:
- API licensing compliance
- Model usage compliance
- Legal data compliance

---

# ⚖ LegalMantra — Because lawyers deserve better tools.
