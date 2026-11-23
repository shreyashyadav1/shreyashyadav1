<h1 align="center">Shreyash Yadav</h1>

<p align="center">
  <strong>Software Engineer &nbsp;·&nbsp; AI Engineer</strong>
</p>

<p align="center">
  <a href="https://www.linkedin.com/in/shreyashyadavai" target="_blank">
    <img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=flat&logo=linkedin&logoColor=white" alt="LinkedIn" />
  </a>
  &nbsp;
  <a href="https://shreyashyadav.vercel.app" target="_blank">
    <img src="https://img.shields.io/badge/Portfolio-000000?style=flat&logo=vercel&logoColor=white" alt="Portfolio" />
  </a>
  &nbsp;
  <a href="mailto:shreyashyadav.work@gmail.com">
    <img src="https://img.shields.io/badge/Email-EA4335?style=flat&logo=gmail&logoColor=white" alt="Email" />
  </a>
</p>

<p align="center">
  MS Information Systems, Northeastern University, graduating <strong>December 2026</strong><br/>
  Looking for full-time <strong>Software Engineer</strong> and <strong>AI Engineer</strong> roles
</p>

---

## About Me

I'm a software engineer with three years of full-time production work at NodeOps and WHP Jewellers, and I build AI agents for real business workflows along with the code that keeps them in check. My focus is the engineering around the model: validating what it returns, deciding when a person has to approve, and writing tests that catch it when something breaks.

## Experience

- **Cybersenz**, Software Engineering Intern (co-op), 2026: agentic workflows in Python and Playwright that worked through a health insurer's portals and cut manual data collection by 60%, plus LLM pipelines that pulled 75+ structured fields from insurance conversations.
- **NodeOps**, Software Engineer, 2023 to 2024: Go and TypeScript APIs that automated blockchain node deployments across 20+ protocols, and Next.js dashboards for NodeOps Console.
- **WHP Jewellers**, Full Stack Developer, 2021 to 2023: e-commerce modules in React, Node.js and Spring Boot for a $10M-funded omnichannel platform, with JWT login and role-based access.

---

## Featured Projects

### OpsPilot: AI On-Call Agent

**[Repo](https://github.com/shreyashyadav1/opspilot)**

An on-call agent that investigates incidents and can't roll anything back until a person approves.

- Digs through logs, Prometheus metrics, deploy history and service health with MCP tools, then returns a Pydantic-validated root-cause diagnosis
- Fault-injectable microservice system (FastAPI, Spring Boot, PostgreSQL, Prometheus on Docker Compose) with a chaos API
- 11-scenario fault-injection benchmark with known root causes, run in CI
- **LangGraph · MCP · FastAPI · Spring Boot · Next.js · TypeScript · PostgreSQL · Docker**

### IntelliClaim AI: Insurance Document Intelligence

**[Repo](https://github.com/shreyashyadav1/intelliclaim-ai)**

Pulls structured claim data out of medical reports, invoices and policy documents.

- Extracts 11 claim fields with Tesseract OCR for scanned pages and Pydantic-validated, allow-listed model output
- Hybrid BM25 + vector retrieval raised top-5 recall from 65% to 91% on a 216-question labeled benchmark, with cited answers
- 460+ pytest tests in CI
- **Groq (GPT-OSS 120B) · LangChain · LlamaIndex · ChromaDB · FastEmbed · FastAPI · React · MongoDB Atlas · Docker**

### Emergency Response MAS: Multi-Agent Coordination

**[Repo](https://github.com/shreyashyadav1/emergency-response-mas)**

Four agents that negotiate ambulances, ER beds and staff during simulated mass-casualty events.

- Built on the OpenAI Agents SDK with a reproducible, seeded emergency simulator
- Across a 600-run paired experiment, the negotiation protocol raised severity-weighted survival 5.6 to 6.7 points over the best baseline
- Streamlit and Plotly dashboard to replay every decision, plus 60 automated tests
- **OpenAI Agents SDK · GPT-4o-mini · Python · Streamlit · Plotly · pytest · Playwright**

### Switchyard: LLM Gateway in Go

**[Repo](https://github.com/shreyashyadav1/switchyard)**

An OpenAI-compatible gateway that gives every model request the same handling.

- Per-key rate limits and daily budgets, retries with backoff, and fallback across Groq, OpenRouter and vLLM
- Token and cost accounting, Prometheus metrics and OpenTelemetry traces
- **Go · OpenTelemetry · Prometheus · Terraform · Cloud Run**

### MeetSense AI: Real-Time Meeting Intelligence

**[Repo](https://github.com/shreyashyadav1/MeetSense)**

Turns live audio into a searchable, structured record of a meeting.

- Live transcription with speaker diarization streamed over WebSockets via Deepgram nova-2
- Versioned WebSocket protocol that keeps transcripts ordered across reconnects, load-tested to 200 concurrent streams
- Summaries, action items and decisions generated from finalized transcript segments
- **React 19 · TypeScript · FastAPI · Deepgram · WebSockets · Redis · PostgreSQL · Groq**

---

## Tech Stack

**AI / ML**

![LangChain](https://img.shields.io/badge/LangChain-000000?style=flat&logo=chainlink&logoColor=white)
![LangGraph](https://img.shields.io/badge/LangGraph-1C3C3C?style=flat&logoColor=white)
![LlamaIndex](https://img.shields.io/badge/LlamaIndex-6929C4?style=flat&logoColor=white)
![OpenAI](https://img.shields.io/badge/OpenAI-412991?style=flat&logo=openai&logoColor=white)
![Groq](https://img.shields.io/badge/Groq-F55036?style=flat&logoColor=white)
![ChromaDB](https://img.shields.io/badge/ChromaDB-1A1A2E?style=flat&logoColor=white)

**Languages**

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat&logo=typescript&logoColor=white)
![Go](https://img.shields.io/badge/Go-00ADD8?style=flat&logo=go&logoColor=white)
![Java](https://img.shields.io/badge/Java-ED8B00?style=flat&logo=openjdk&logoColor=white)

**Backend**

![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat&logo=fastapi&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat&logo=nodedotjs&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-6DB33F?style=flat&logo=springboot&logoColor=white)

**Frontend**

![React](https://img.shields.io/badge/React-61DAFB?style=flat&logo=react&logoColor=black)
![Next.js](https://img.shields.io/badge/Next.js-000000?style=flat&logo=nextdotjs&logoColor=white)

**Databases**

![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat&logo=postgresql&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=flat&logo=mongodb&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat&logo=redis&logoColor=white)

**Infrastructure**

![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat&logo=docker&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat&logo=amazonwebservices&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat&logo=githubactions&logoColor=white)
![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=flat&logo=prometheus&logoColor=white)

---

<p align="center">
  <a href="mailto:shreyashyadav.work@gmail.com">shreyashyadav.work@gmail.com</a>
  &nbsp;·&nbsp;
  <a href="https://www.linkedin.com/in/shreyashyadavai">LinkedIn</a>
  &nbsp;·&nbsp;
  <a href="https://shreyashyadav.vercel.app">Portfolio</a>
</p>
