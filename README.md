# Scott Severance

**I build autonomous AI systems — agents that plan, act, review their own work, and mostly run where the data already lives.**

Two properties show up in most of what I ship: it makes decisions without a human in the loop, and it doesn't need to phone home to do it. A coding assistant with no API key. A statistics toolkit with no telemetry. A vulnerability scanner with two runtime dependencies. Local-first isn't a marketing angle here — it's a constraint I design against, because the interesting problems start when you can't just call a hosted model for every decision.

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![LangGraph](https://img.shields.io/badge/LangGraph-1C3C3C?style=flat-square)
![Neo4j](https://img.shields.io/badge/Neo4j-4581C3?style=flat-square&logo=neo4j&logoColor=white)
![ONNX](https://img.shields.io/badge/ONNX-005CED?style=flat-square&logo=onnx&logoColor=white)
![Ollama](https://img.shields.io/badge/Ollama-000000?style=flat-square&logo=ollama&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white)

**Focus:** agentic architectures · applied security · MLOps & drift · edge/on-device inference · retrieval over knowledge graphs

---

## Background

Principal engineer in applied AI and ML systems — two decades in statistics and analytics, production ML and NLP since 2017. That work spans agentic infrastructure (Model Context Protocol servers, multi-provider LLM abstractions with OAuth 2.1), production NLP across the full lineage from lexicon scoring through LSTM/GRU to transformer fine-tuning, and applied causal inference rigorous enough to survive a CFO — synthetic control, difference-in-differences, ANOVA with post-hoc correction.

Independently, I've fine-tuned GPT-J and LLaMA-class models using both LoRA and full-parameter approaches on an 8×A100 DeepSpeed cluster — including debugging the training divergence and tokenization failures that don't appear in the tutorials.

- **Recognition** — Brandon Hall Gold Award, Best Advance in AI for Learning
- **Teaching** — Guest lecturer on applied AI/ML, George Mason University CLO Certification Program (2020–2024, four cohorts)
- **Education** — M.S. Data Science, Southern Methodist University · B.B.A. Management Information Systems, Dallas Baptist University

---

## Featured work

| Project | What it does | Why it's not trivial |
|---|---|---|
| **[Agent-Builder](https://github.com/ssevera1/Agent-Builder)** | Design, test, and deploy AI agents against any LLM provider. CLI-first TypeScript monorepo. | 6 providers behind one interface, 5 agent patterns, DAG workflows, and an evaluation framework — the hard part isn't calling a model, it's making runs comparable across providers. MCP compatible. |
| **[CodingAgent](https://github.com/ssevera1/CodingAgent)** | A coding assistant that runs fully offline via Ollama. No API keys, no subscription, no data leaving the machine. | Every affordance you'd get from a hosted model has to be rebuilt against a local one — tool use, context management, and recovery when a smaller model returns something malformed. |
| **[Vulnerability-Scanner](https://github.com/ssevera1/Vulnerability-Scanner)** | Cross-platform scanner, pen tester, zero-day detector, and OS hardener for Linux, Windows, and macOS. | A five-phase pipeline with 14 CIS-aligned scanners and backup-first hardening — it changes system state, so every hardening step has to be reversible before it's applied. Two runtime dependencies. |
| **[Self-Healing-MLOps-Pipeline](https://github.com/ssevera1/Self-Healing-MLOps-Pipeline)** | Fraud-detection pipeline that detects data drift with Evidently AI and retrains itself. | Drift detection is the easy half. Deciding *when* retraining is justified — versus reacting to noise and quietly degrading the model — is the part that needs judgment. |

---

## These repositories maintain themselves

Eleven of my repos run an autonomous improvement loop I built on GitHub Actions. It isn't a bot that bumps dependencies:

- A scheduled agent reads the repo, picks **one** focused improvement, and opens a pull request.
- A **second, stronger model reviews that PR** — approves and auto-merges it, or requests changes with specific feedback.
- If changes are requested, a third workflow dispatches an agent to address the review. It's explicitly instructed to **verify each claim before implementing it, and to push back with file-and-line evidence when the reviewer is wrong** — two models agreeing to be wrong together is the failure mode worth designing against.
- A daily janitor closes proposals that stalled, and feeds those titles back into the prompt as "don't repeat these."

The guardrails are the interesting part, because an agent with commit access fails in expensive ways. Writes are confined to the repo root with path-traversal and dotfile rejection; workflow files and lock files are off-limits to the agent entirely; git hooks are disabled during its commits; a rewrite that returns less than 60% of the original file is treated as accidental deletion and discarded regardless of how plausible the commit message reads; and the fix loop is bounded to two rounds so a disagreement can't ping-pong into an unbounded API bill.

It works — the loop has proposed, reviewed, revised, and merged its own changes across all eleven repos unattended.

---

## Everything else

**Agents & autonomy**
- **[DeepResearchAgent](https://github.com/ssevera1/DeepResearchAgent)** — cyclic research agent in LangGraph (Planner → Worker → Reviewer)
- **[Autonomous-SOC-Security-Agent](https://github.com/ssevera1/Autonomous-SOC-Security-Agent)** — triages SIEM alerts and checks IP reputation, with human approval enforced before anything gets blocked
- **[PDA](https://github.com/ssevera1/PDA)** — answers real phone calls via Twilio, converses using Claude/Grok/Gemini, and sends call summaries to Telegram

**Data, retrieval & ML**
- **[GraphRAG-Compliance-Navigator](https://github.com/ssevera1/GraphRAG-Compliance-Navigator)** — extracts compliance entities from legal text into a Neo4j knowledge graph, retrieved via hybrid vector + graph search
- **[Data-Science-Toolkit](https://github.com/ssevera1/Data-Science-Toolkit)** — 32+ interactive statistics and modeling tools in Streamlit, running 100% offline with zero telemetry

**Edge & on-device**
- **[Edge-Native-Vision-Copilot](https://github.com/ssevera1/Edge-Native-Vision-Copilot)** — real-time PPE violation detection via ONNX inference and acoustic sensor fusion, tuned for constrained hardware
- **[ToneAnalyzer](https://github.com/ssevera1/ToneAnalyzer)** — voice stress analysis and facial emotion detection running entirely client-side, shipped to web, desktop (Electron), and mobile (Capacitor)

---

## Stack

**Languages** — Python, TypeScript
**AI/ML** — LangGraph, Ollama, ONNX Runtime, TensorFlow.js, scikit-learn, Evidently AI, Feast
**Data** — Neo4j, vector + graph hybrid retrieval, Streamlit
**Infra** — GitHub Actions, Docker, Twilio

---

## Elsewhere

- LinkedIn — [linkedin.com/in/scott-severance](https://www.linkedin.com/in/scott-severance)
- Website — [scottseverance.net](https://scottseverance.net)
