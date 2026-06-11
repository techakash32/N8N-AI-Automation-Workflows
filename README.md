# ⚡ N8N AI Automation Workflows — Complete Collection

A comprehensive collection of **AI-powered automation workflows** built with n8n.
Featuring integrations with LLMs, messaging platforms, databases, cloud APIs, and business tools
to automate real-world processes, improve productivity, and streamline operations.

---

## 📁 Repository Structure

```
N8N-AI-Automation-Workflows/
├── AI Blog Generator.json                ← 3-step AI blog writing pipeline → Gmail delivery
├── AI WhatsApp Appointment.json          ← WhatsApp AI agent that books appointments
├── AI+humanizer Linkedin Post.json       ← AI post generator with human-tone rewriting
├── Appointment Booking AI Agent.json     ← Conversational AI agent for scheduling
├── LINKEDIN POST+IMAGE GENRATER.json     ← LinkedIn post + AI image generation combo
├── Powered Review Analysis System.json   ← Full review pipeline: AI analysis + MySQL storage
└── github akash.json                     ← GitHub automation workflow
```

---

## 🚀 HOW TO USE THESE WORKFLOWS

### Step 1: Install n8n
The easiest way is via npm:
```bash
npm install -g n8n
```
Or run with Docker:
```bash
docker run -it --rm --name n8n -p 5678:5678 docker.n8n.io/n8nio/n8n
```

### Step 2: Open n8n in your browser
```
http://localhost:5678
```

### Step 3: Import a workflow
1. Click **"+"** → **"Import from file"**
2. Select any `.json` file from this repo
3. Click **"Import"**

### Step 4: Add your credentials
Each workflow requires API credentials (Groq, Gmail, WhatsApp, etc.).
Set them up under **Settings → Credentials** in n8n.

### Step 5: Activate & run
Toggle the workflow to **Active** or click **"Test Workflow"** to run manually.

---

## 📋 WORKFLOW CATALOGUE

### 1. 🖊️ AI Blog Generator
**File:** `AI Blog Generator.json`

A 3-step pipeline that takes a form submission and delivers a complete, formatted blog post to the user's Gmail inbox.

| Node | Role |
|------|------|
| Blog Request Form | n8n form trigger — collects topic, audience, tone, email |
| Step 1 — Generate Outline | Groq LLM creates a structured 4-section blog outline |
| Step 2 — Write Blog Post | Groq LLM writes full HTML-formatted content (~800 words) |
| Step 3 — Generate Title | Groq LLM creates a catchy, tone-matched headline |
| Send Blog via Gmail | Styled HTML email delivered to the user's inbox |

**Integrations:** Groq API · Gmail OAuth2  
**Model:** `llama-3.3-70b-versatile`  
**Trigger:** n8n Form (webhook)

---

### 2. 📱 AI WhatsApp Appointment Setter
**File:** `AI WhatsApp Appointment.json`

A live WhatsApp AI agent that qualifies leads and books appointments in real time. Maintains conversation memory across messages and sends a Calendly booking link when the customer is ready.

| Node | Role |
|------|------|
| WhatsApp Trigger | Fires on every incoming WhatsApp message |
| AI SMS Agent | LangChain agent with appointment-setting instructions |
| Groq Chat Model | `llama-3.3-70b-versatile` powers the responses |
| Memory (Buffer Window) | Remembers the last 10 messages per customer session |
| Send Message | Replies to the customer on WhatsApp |

**Integrations:** WhatsApp Business API · Groq API  
**Model:** `llama-3.3-70b-versatile`  
**Trigger:** WhatsApp message webhook (live / active)

---

### 3. 💼 AI + Humanizer LinkedIn Post Generator
**File:** `AI+humanizer Linkedin Post.json`

Generates a professional LinkedIn post using AI, then passes it through a humanizer step to make the tone feel natural and authentic — avoiding the robotic AI writing style.

**Integrations:** Groq API · LinkedIn (optional)  
**Trigger:** Manual / form

---

### 4. 📅 Appointment Booking AI Agent
**File:** `Appointment Booking AI Agent.json`

A conversational AI agent purpose-built for scheduling. Understands natural language booking requests, gathers required details, and confirms appointments.

**Integrations:** Groq API · Calendar service  
**Trigger:** Webhook / chat interface

---

### 5. 🖼️ LinkedIn Post + Image Generator
**File:** `LINKEDIN POST+IMAGE GENRATER.json`

Combines AI text generation with image generation to produce a complete LinkedIn post package — both caption and a matching visual — ready to publish.

**Integrations:** Groq API · Image generation API  
**Trigger:** Manual / form

---

### 6. 📊 AI-Powered Review Analysis System
**File:** `Powered Review Analysis System.json`

The most advanced workflow in the collection. A full end-to-end product review pipeline with three trigger modes, NVIDIA AI analysis, business scoring, MySQL persistence, and a complete analytics report.

#### Trigger Modes
| Mode | Description |
|------|-------------|
| 📝 Form Submission | Customer submits a review via n8n web form |
| ▶️ Manual Test | Loads 5 built-in sample reviews for testing |
| ⏰ Daily Schedule | Automatically fetches reviews from the database each day |

#### Pipeline Steps
| Step | Node | Description |
|------|------|-------------|
| 1 | Normalize / Load Data | Standardizes data from any trigger source |
| 2 | Validate & Sanitize | Rejects reviews with missing fields or short text |
| 3 | 🤖 NVIDIA AI Analysis | Sends review to `meta/llama3-70b-instruct` via NVIDIA API |
| 4 | Parse AI Response | Extracts structured JSON from LLM output |
| 5 | Enrich & Score | Adds NPS category, urgency level, action items |
| 6 | Save to MySQL | Upserts full analysis into `product_reviews` table |
| 7 | Generate Summary Report | Aggregates all reviews into a business analytics report |
| 8 | Final Output & Log | Logs KPIs and marks pipeline as complete |

#### AI Output Fields per Review
| Field | Description |
|-------|-------------|
| `sentiment` | positive / neutral / negative |
| `sentiment_score` | 0–10 scale |
| `confidence` | 0–100% |
| `key_topics` | Up to 5 specific topics detected |
| `main_praise` | Top positive point extracted |
| `main_issue` | Top complaint extracted |
| `priority` | high / medium / low |
| `suggested_response` | Ready-to-use customer reply |
| `nps_category` | promoter / passive / detractor |
| `urgency_level` | critical / urgent / monitor / positive |
| `tags` | warranty, shipping, durability, performance, etc. |

**Integrations:** NVIDIA NIM API · MySQL  
**Model:** `meta/llama3-70b-instruct`  
**Database Table:** `product_reviews`

---

### 7. 🐙 GitHub Workflow
**File:** `github akash.json`

A GitHub automation workflow for triggering actions based on repository events such as pushes, pull requests, or issue updates.

**Integrations:** GitHub API  
**Trigger:** GitHub webhook

---

## 🔑 CREDENTIALS REQUIRED

| Credential | Used By |
|------------|---------|
| `Groq API Key` | Blog Generator, WhatsApp Agent, LinkedIn workflows |
| `Gmail OAuth2` | AI Blog Generator (email delivery) |
| `WhatsApp Business API` | AI WhatsApp Appointment |
| `NVIDIA NIM API Key` | Review Analysis System |
| `MySQL Connection` | Review Analysis System (database storage) |
| `GitHub OAuth` | GitHub workflow |

> Get your free Groq API key at: https://console.groq.com  
> Get your NVIDIA NIM API key at: https://build.nvidia.com

---

## 🛠️ Tech Stack

- **Automation Engine**: n8n (self-hosted or cloud)
- **LLMs**: Groq (LLaMA 3.3 70B) · NVIDIA NIM (LLaMA 3 70B Instruct)
- **Messaging**: WhatsApp Business API
- **Email**: Gmail OAuth2
- **Database**: MySQL
- **Social**: LinkedIn
- **Scheduling**: n8n built-in cron scheduler
- **Memory**: LangChain Buffer Window Memory

No Python or backend code required — everything runs inside n8n!

---

## 📊 WORKFLOW SUMMARY

| Workflow | Trigger | AI Model | Integrations | Complexity |
|----------|---------|----------|--------------|------------|
| AI Blog Generator | Form | Groq LLaMA 3.3 70B | Gmail | ⭐⭐⭐ |
| WhatsApp Appointment | WhatsApp | Groq LLaMA 3.3 70B | WhatsApp | ⭐⭐⭐ |
| LinkedIn Post + Humanizer | Manual | Groq LLaMA 3.3 70B | LinkedIn | ⭐⭐ |
| Appointment Booking Agent | Webhook | Groq LLaMA 3.3 70B | Calendar | ⭐⭐ |
| LinkedIn Post + Image | Manual | Groq + Image API | LinkedIn | ⭐⭐ |
| Review Analysis System | Form / Cron / Manual | NVIDIA LLaMA 3 70B | MySQL | ⭐⭐⭐⭐⭐ |
| GitHub Workflow | GitHub Event | — | GitHub | ⭐⭐ |

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
