# CuraLink AI — Clinical Intelligence Platform

> A full-stack AI-powered medical research assistant that 
> understands clinical context, retrieves deep research, 
> reasons over it, and delivers structured answers.

![Status](https://img.shields.io/badge/status-active-brightgreen)
![Stack](https://img.shields.io/badge/stack-React(Vercel)%20%7C%20Node.js+express.js(Railway)%20%7C%20MongoDB_Atlas%20%7C%20Groq(llama_3.1_8b_instant)%20%7C%20APIs(PubMed,ClinicalTrials.gov,OpenAlex)-purple)

## 📸 Screenshots
<img width="1600" height="803" alt="c1" src="https://github.com/user-attachments/assets/bf189928-013d-4e77-b8a3-383082cdc0a7" />
.
<img width="1370" height="873" alt="c2" src="https://github.com/user-attachments/assets/df75f04a-59fb-4fd9-8eb4-59e6b9f034f5" />
.
<img width="1284" height="905" alt="c3" src="https://github.com/user-attachments/assets/7b69521e-1a5c-4179-b3bb-190696c9efe0" />
.
<img width="1161" height="911" alt="c4" src="https://github.com/user-attachments/assets/c58d53d3-4e69-4bdd-a00d-6a2a3d732d6e" />

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

<img width="1265" height="827" alt="image" src="https://github.com/user-attachments/assets/5b0667be-f4ac-4466-b682-8a0ce0e9971e" />



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
