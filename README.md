<h1 align="center">Shreyash Yadav</h1>

<p align="center">
  <strong>Software Engineer &nbsp;·&nbsp; AI Engineer</strong>
</p>

<p align="center">
  MS Information Systems, Northeastern University, graduating <strong>December 2026</strong><br/>
  Looking for full-time <strong>Software Engineer</strong> and <strong>AI Engineer</strong> roles
</p>

<p align="center">
  <a href="https://www.linkedin.com/in/shreyashyadavai">LinkedIn</a>
  &nbsp;·&nbsp;
  <a href="https://shreyashyadav.vercel.app">Portfolio</a>
  &nbsp;·&nbsp;
  <a href="mailto:shreyashyadav.work@gmail.com">shreyashyadav.work@gmail.com</a>
</p>

---

## About Me

I'm a software engineer with three years of full-time production work at NodeOps and WHP Jewellers. I build LLM applications and agents, and most of that work is the engineering around the model: validating what it returns, deciding when a person has to approve an action, and measuring the result with evaluations, benchmarks and load tests.

## Experience

- **NodeOps**, Software Engineer, 2023 to 2024: Go and TypeScript APIs that automated blockchain node deployments across 20+ protocols, and Next.js dashboards for NodeOps Console.
- **WHP Jewellers**, Full Stack Developer, 2021 to 2023: e-commerce modules in React, Node.js and Spring Boot for a $10M-funded omnichannel platform, with JWT login and role-based access.

---

## Projects

Every figure below comes from the project's own repository, which documents how it was measured and its limits.

### OpsPilot: incident-response agent

[Repository](https://github.com/shreyashyadav1/opspilot)

When an alert fires in a small microservice system, a LangGraph agent investigates it through an MCP server (service health, Prometheus metrics, logs, deploy history), names the root-cause service and fault category in a Pydantic-validated diagnosis, and can roll back a deploy only after a person approves it.

- The system under investigation is a Docker Compose stack of FastAPI and Spring Boot services, Postgres and Prometheus, with a control plane that injects six kinds of fault and records the ground truth.
- Operator dashboard in Next.js and TypeScript on a FastAPI agent API: a live timeline of every model turn and tool call, approve and reject, optional role-based API keys, and pending approvals that survive restarts.
- A 28-scenario fault-injection benchmark with known root causes and distractor deploys, scored on root-cause accuracy, tool-call precision, steps, time to diagnosis and token cost. GitHub Actions runs all 28 deterministically, on simulated telemetry with a rule-based playbook model, to test the harness end to end. Results with a hosted LLM are not published yet.
- An OpenTelemetry trace per investigation and a cost estimate per incident. The Kustomize manifests (with Loki and Grafana Alloy for logs) are rendered and validated with kubeconform in CI but have not been run on a real cluster.

LangGraph · MCP · FastAPI · Spring Boot · Next.js · TypeScript · PostgreSQL · Prometheus · OpenTelemetry · Docker

### Switchyard: LLM gateway in Go

[Repository](https://github.com/shreyashyadav1/switchyard)

An OpenAI-compatible gateway in front of Groq, OpenRouter, OpenAI and self-hosted vLLM. Clients keep their OpenAI SDK and change only the base URL; OpsPilot can send its model calls through it.

- Per-key token-bucket rate limits and daily dollar budgets, retries with backoff and jitter, fallback to the next provider, and a circuit breaker per provider and model that skips a failing target for a cooldown.
- Token and cost accounting on every response, an exact-match response cache, Prometheus metrics, and OpenTelemetry spans that join the caller's trace.
- Adds about 44 µs per non-streaming request over a direct call to a local fake upstream (median of 10 runs on an Apple M3: 78.9 µs against 34.7 µs). Streaming, the cache, retries, failover and a deployed instance are not measured ([docs/BENCHMARKS.md](https://github.com/shreyashyadav1/switchyard/blob/main/docs/BENCHMARKS.md)).
- A Terraform module for Google Cloud Run sized for the free tier, and Kustomize manifests for Kubernetes; CI runs `terraform validate` and kubeconform on them.

Go · OpenTelemetry · Prometheus · Terraform · Cloud Run · Kustomize

### IntelliClaim AI: insurance document intelligence

[Repository](https://github.com/shreyashyadav1/intelliclaim-ai) · [Frontend](https://intelliclaim-ai.vercel.app) (backend hosting is paused, so the site shows a "demo server offline" notice)

Reads claim PDFs and scans (PyMuPDF for text layers, Tesseract OCR for scanned pages), extracts eleven claim fields with an LLM into Pydantic-validated, allow-listed output, answers questions over the documents with page citations, and scores each claim's risk with rules plus an optional LLM review.

Measured on a synthetic, labelled dataset of 60 fictional documents, 216 answerable questions and 206 claims ([method and caveats](https://github.com/shreyashyadav1/intelliclaim-ai/blob/master/backend/evals/README.md)):

- Retrieval: top-5 recall went from 0.653 with vector search to 0.907 with hybrid BM25 + vector search, and to 1.000 once chunks containing the exact document number named in the question go first. That last step was designed on this dataset's misses, so the 1.000 is in-sample.
- RAG answers through the API with Groq `gpt-oss-120b`: 216 of 216 correct after the retrieval fixes, up from 189 of 215 before them, with citation precision 1.000. Also in-sample.
- Extraction: micro-F1 0.986 on the 60 synthetic documents (text-layer PDFs). In-sample as well, because the prompt was fixed after looking at failures on the same documents.
- Risk scoring: PR-AUC 0.805 for the rules alone and 0.883 with the LLM review, on the 206 synthetic claims.

It also has an MCP server with four read-only tools for agents, OpenTelemetry tracing that records the tokens and cost of every model call and adds the spend to the document or claim, and 531 backend tests (91% line coverage) that run in CI next to an evaluation job that fails when a metric drops below its threshold.

FastAPI · Groq · LangChain · LlamaIndex · ChromaDB · fastembed · MongoDB · React · MCP · OpenTelemetry · Docker

### MeetSense: real-time meeting transcription

[Repository](https://github.com/shreyashyadav1/MeetSense) · [Frontend](https://meet-sense.vercel.app) (backend hosting is paused, so the site shows a "demo server offline" notice)

The browser streams microphone audio over a WebSocket to FastAPI, which forwards it to Deepgram (nova-2 with speaker diarization). Final transcript segments get a per-meeting sequence number and fan out to every viewer, relayed through Redis when it is available. From the transcript, Groq (`gpt-oss-120b`) writes a summary, action items, decisions, open questions and a follow-up email as validated JSON.

- Load test: 200 concurrent streaming meetings with transcript delivery (server emit to client receive) at p95 2.2 ms, and no errors, sequence gaps or duplicates. It ran in mock transcription mode with the server and the load generator on one 8 GB laptop, so it measures the server's WebSocket path, not Deepgram ([loadtest/RESULTS.md](https://github.com/shreyashyadav1/MeetSense/blob/master/loadtest/RESULTS.md)).
- Exports approved action items to GitHub Issues idempotently: each issue carries a hidden marker with a hash of its action item, so a retry or a double click reuses the existing issue instead of filing a duplicate.

React 19 · TypeScript · FastAPI · WebSockets · Deepgram · Groq · Redis · PostgreSQL

### Emergency Response MAS: multi-agent coordination (course project)

[Repository](https://github.com/shreyashyadav1/emergency-response-mas)

Four kinds of agents coordinate ambulances, hospitals and staff in a seeded mass-casualty simulator and negotiate when their goals conflict. Across 600 runs on synthetic scenarios, paired by seed, the agents with negotiation beat the best baseline at every stress level by +0.056 to +0.067 weighted survival (p < 0.001). A version built on the OpenAI Agents SDK (`gpt-4o-mini`) also beats both baselines but trails the rule-based agents slightly. A Streamlit dashboard replays each run minute by minute.

Python · OpenAI Agents SDK · Streamlit · Plotly · pytest

---

## Tech Stack

- **Languages:** Python, TypeScript, Go, Java
- **AI and LLMs:** LangGraph, LangChain, LlamaIndex, MCP, OpenAI, Groq, ChromaDB
- **Backend:** FastAPI, Node.js, Spring Boot
- **Frontend:** React, Next.js
- **Databases:** PostgreSQL, MongoDB, Redis
- **Infrastructure and observability:** Docker, GitHub Actions, AWS, Terraform, Kustomize, Prometheus, OpenTelemetry
