# CuraLink AI — Clinical Intelligence Platform

> A full-stack AI-powered medical research assistant that 
> understands clinical context, retrieves deep research, 
> reasons over it, and delivers structured answers.

## 📸 Screenshots
<img width="1600" height="803" alt="WhatsApp Image 2026-04-20 at 8 08 34 AM" src="https://github.com/user-attachments/assets/88c0eee7-3a8f-4b61-95a9-7081436a6061" />
.
<img width="1370" height="873" alt="WhatsApp Image 2026-04-20 at 8 17 16 AM" src="https://github.com/user-attachments/assets/9fdda48c-02f7-46d5-8e33-8dedca7cb80f" />
.
<img width="1284" height="905" alt="WhatsApp Image 2026-04-20 at 8 17 51 AM" src="https://github.com/user-attachments/assets/52d52178-1d6e-4ca3-a2d7-11f2c3828e26" />
.
<img width="1161" height="911" alt="WhatsApp Image 2026-04-20 at 8 18 22 AM" src="https://github.com/user-attachments/assets/0eaf7221-b2e3-4c55-88a0-8361b78acf3c" />

## Live Demo
🌐 [curalink-ai.vercel.app](https://curalink-ai-mu.vercel.app/)
🎥 [Watch Demo](https://www.loom.com/share/543c1d7db0204c27a8cb65a87180f601)

## Architecture

User → Vercel (React) → Railway (Express)
                      → Groq (llama-3.1-8b) 
                      → MongoDB Atlas
                      → PubMed API
                      → ClinicalTrials.gov API
                      → OpenAlex API

<img width="953" height="705" alt="image" src="https://github.com/user-attachments/assets/1f5fe440-e593-4a1c-a4c3-62b3198dca30" />


## Pipeline
1. **Query Expansion** — LLM combines disease + intent 
   into precision search string
2. **Deep Retrieval** — 80 PubMed (with abstracts via 
   efetch) + 50 ClinicalTrials + 80 OpenAlex = 210+ candidates
3. **Ranking** — Weighted score: relevance (50%) + 
   recency (30%) + credibility (20%)
4. **Synthesis** — Top 8 results passed to llama-3.1-8b 
   for structured 4-section clinical response
5. **Memory** — Sessions stored in MongoDB, 
   last 3 exchanges injected into every LLM call

## Tech Stack
- **Frontend** — React · Vercel
- **Backend** — Node.js · Express · Railway
- **Database** — MongoDB Atlas
- **LLM** — llama-3.1-8b-instant (Groq) — open-source
- **APIs** — PubMed · ClinicalTrials.gov · OpenAlex

## Local Setup
```bash
# Backend
cd backend
npm install
# Add .env with GROQ_API_KEY, MONGO_URI
node server.js

# Frontend
cd frontend
npm install
npm start
