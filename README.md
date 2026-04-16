# 🚀 NovaMind AI Content Pipeline

An end-to-end AI-powered marketing analytics pipeline that automates content generation, audience segmentation, A/B testing, CRM logging, and performance analysis in a single Streamlit application.

---

## 🎯 Business Problem

Early-stage B2B teams struggle to scale content marketing effectively:

- Content creation is manual and slow  
- Messaging is not tailored to different audience segments  
- A/B testing is inconsistent or missing  
- Performance insights are fragmented and delayed  

---

## 💡 Solution

This project simulates a fully automated growth analytics pipeline that:

- Generates blog content and persona-specific newsletters using AI  
- Segments users into personas (Founder, Operations, Marketing)  
- Assigns A/B variants with different messaging strategies  
- Tracks engagement metrics (open, click, conversion)  
- Analyzes results to identify the best-performing strategy  

---

## 📈 What This Pipeline Produces

Each run generates:

- Campaign-level metrics (open rate, CTR, conversion rate)
- Funnel analysis (sent → opened → clicked → converted)
- A/B comparison across personas and variants
- Automated performance summary and next-step recommendation

---

## 🏗️ Architecture Overview

The repository is organized as a modular pipeline.

- app.py orchestrates the full workflow and renders the Streamlit dashboard  
- content_generator.py generates blog content and persona-specific newsletter variants  
- campaign_manager.py segments users and assigns A/B variants  
- crm_hubspot.py handles HubSpot integration (live or simulated)  
- metrics_simulator.py simulates engagement and aggregates metrics  
- performance_analyzer.py generates A/B insights and summaries  
- utils.py provides shared helpers  

---

## 🔄 Flow Diagram

Topic Input → Content Generation → Persona Segmentation → A/B Assignment → CRM Logging → Metrics Simulation → Aggregation & Analysis → Dashboard & Report

---

## 📊 System Design & Analytics Logic

This project implements an end-to-end AI-powered marketing pipeline that simulates a real-world content growth loop: from content generation → audience targeting → campaign delivery → performance measurement → optimization.

### 1. User Segmentation (Persona Design)

Users are segmented into distinct personas based on assumed behavioral and business characteristics. In this project, three primary personas are defined:

- Startup Founders → focus on growth, efficiency, automation ROI  
- Creative Agency Owners → focus on workflow optimization and client scalability  
- Freelancers → focus on productivity and ease of use  

Segmentation is applied at the contact level (via `persona_segment`) and drives downstream personalization in both messaging and distribution.

---

### 2. A/B Testing Design (Content Framing Experiment)

The system simulates an A/B test by varying **message framing strategies** rather than core content topics.

Each campaign generates:
- A shared blog base (same topic)
- Multiple newsletter variants per persona with different:
  - Tone (analytical vs inspirational)
  - Value proposition framing (efficiency vs creativity vs growth)
  - Emphasis (features vs outcomes vs use cases)

Although multiple elements vary in implementation, the conceptual experimental variable is:
> **Message framing strategy**

This approximates real-world marketing experiments where copy positioning affects engagement.

---

### 3. CRM Integration & Campaign Logging

The pipeline integrates with HubSpot (or runs in mock mode) to simulate:

- Contact creation/update  
- Persona tagging  
- Campaign assignment  
- Campaign logging (blog title, newsletter version, timestamp)  

All campaign events are stored in structured outputs for traceability and reproducibility.

---

### 4. Funnel Analysis Framework

After distribution, the system simulates a standard marketing funnel:

- Sent → Opened → Clicked → Converted / Unsubscribed  

Key metrics include:
- Open Rate  
- Click-Through Rate (CTR)  
- Unsubscribe Rate  

These metrics are generated probabilistically to mimic realistic variation across personas and content variants.

The funnel enables comparison across:
- Personas  
- Content framing strategies  
- Campaign iterations  

---

### 5. Performance Analysis & Insight Generation

The system aggregates performance across segments and produces:

- Persona-level performance comparison  
- Best-performing content variant identification  
- AI-generated performance summary  

Example insight:
> “Creative Agency Owners showed higher CTR under case-study-driven messaging, suggesting stronger response to applied examples.”

---

### 6. Feedback Loop & Optimization Logic

The pipeline closes the loop by:

- Using performance data to inform future content direction  
- Highlighting which persona–message combinations perform best  
- Simulating iterative campaign optimization  

This reflects real-world growth analytics workflows where:
> Data → Insight → Content Strategy Adjustment

---

### 7. Runtime & Execution

- Typical runtime: **15 seconds** in mock mode  
- Real API mode runtime: **5 minutes** for mock_contacts data (600 data)
- All outputs are generated in a single pipeline execution triggered via Streamlit UI  

---

### 8. System Output Artifacts

Each run generates structured outputs:

- Generated content (JSON)  
- Campaign logs (CSV)  
- Performance history (CSV)  
- AI performance summary (Markdown)  

These outputs support:
- Reproducibility  
- Historical comparison  
- Analytical extension  

---

### Summary

This system is not just a content generator, but a simplified simulation of a **data-driven marketing analytics pipeline**, integrating:

- AI content generation  
- CRM-based segmentation  
- Experimental design (A/B testing)  
- Funnel-based performance tracking  
- Insight-driven iteration  

It demonstrates how modern analytics workflows combine **generation, experimentation, and decision-making** into a continuous optimization loop.

---

## 🛠️ Tools, APIs, and Models Used

- Python, Streamlit, Pandas  
- OpenAI API (gpt-4.1-mini)  
- HubSpot CRM API  

---

## ⚠️ Assumptions Made

- Contacts are simulated  
- Email delivery is simulated  
- Metrics are probabilistic  
- No statistical significance testing  
- Designed for demonstration  

---

## ▶️ Instructions to Run Locally

> The app can run fully in mock mode without API keys.

```bash
# 1. Clone the repository
git clone https://github.com/elinxxy1307-cloud/novamind-ai-marketing-content-pipeline.git
cd novamind-ai-marketing-content-pipeline

# 2. (Optional but recommended) Create a virtual environment
python3 -m venv venv
source venv/bin/activate   # On Windows: venv\Scripts\activate

# 3. Install dependencies
pip install -r requirements.txt

# 4. Set up environment variables
cp .env.example .env

# 5. Run the app
streamlit run app.py
```

Open your browser and go to: http://localhost:8501

If you want to use real APIs, add the following to your .env file:

OPENAI_API_KEY=your_key_here

HUBSPOT_ACCESS_TOKEN=your_token_here
