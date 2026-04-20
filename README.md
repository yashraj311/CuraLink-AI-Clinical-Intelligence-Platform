# CuraLink AI — Clinical Intelligence Platform

> A full-stack AI-powered medical research assistant that 
> understands clinical context, retrieves deep research, 
> reasons over it, and delivers structured answers.

## 📸 Screenshots
![Demo]()

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
