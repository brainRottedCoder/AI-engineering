# AI Engineering: Learning Roadmap & Notes

A structured, in-depth path to becoming an **AI Engineer** (also leading to **LLM Ops Engineer**, **AI Forward Deployed Engineer (AI FDE)**, **Agentic AI Engineer**, **AI Platform Engineer**).

The core structure follows Krish Naik's *Complete AI Engineering Roadmap* video. Topics I added because they matter in real AI engineering work are tagged with **➕**.

> **How to use this repo**
> 1. Work through the modules in order. Skip ahead only if you can already do the "Checkpoint" for a module.
> 2. For every topic: learn the concept, write notes in `notes/`, then build something small in `projects/`.
> 3. Tick the checkboxes as you go. Commit often.
> 4. A topic is only ticked when it passes the **four gates** in [`.cursor/rules/learning-completion.mdc`](.cursor/rules/learning-completion.mdc): **project + evals**, **detailed notes**, **published teach-back (public link)**, and **OA-format quiz (80%+)**.

## Learning Protocol

| Practice | What | When |
|---|---|---|
| **Eval-first projects** | Every LLM project has `evals/` (golden set + `run_evals.py`) and a baseline-vs-current metrics table | From Module 3/4 onward |
| **Mock take-homes** | Timed, fresh-spec builds graded on a rubric (pass 70) | After Phase A, Module 5, Module 7, Phase C, and a final FDE-style one |
| **Failure journal** | Real bugs and breakages, with root cause and prevention, in `notes/failure.md` | Whenever something breaks (or on purpose, via fault injection) |
| **Public teach-back** | A short video, thread, or post explaining what you built, with the link logged in `teachbacks/log.md` | Once per project milestone or module |
| **Spaced review** | 10-question mixed quiz across earlier modules (pass 70) | Every 2 weeks |

---

## Table of Contents

- [Learning Protocol](#learning-protocol)
- [Suggested Repo Structure](#suggested-repo-structure)
- [Roadmap at a Glance](#roadmap-at-a-glance)
- [Module 0 ➕ Math & Prerequisites](#module-0--math--prerequisites)
- [Module 1: Programming & Software Engineering](#module-1-programming--software-engineering)
- [Module 2: AI/ML Foundations](#module-2-aiml-foundations)
- [Module 3: Generative AI & Foundation Models](#module-3-generative-ai--foundation-models)
- [Module 4: LLM Application Engineering](#module-4-llm-application-engineering)
- [Module 5: RAG Engineering](#module-5-rag-engineering)
- [Module 6: AI Agents](#module-6-ai-agents)
- [Module 7: Agent Orchestration](#module-7-agent-orchestration)
- [Module 8: Evaluation](#module-8-evaluation)
- [Module 9: AI Observability](#module-9-ai-observability)
- [Module 10: Guardrails & AI Security](#module-10-guardrails--ai-security)
- [Module 11: Deployment (GenAI Ops / Agent Ops)](#module-11-deployment-genai-ops--agent-ops)
- [Module 12: Cloud Engineering](#module-12-cloud-engineering)
- [Module 13: AI System Design](#module-13-ai-system-design)
- [Module 14 ➕ Fine-Tuning & Model Customization](#module-14--fine-tuning--model-customization)
- [Module 15 ➕ Inference & Model Serving](#module-15--inference--model-serving)
- [Module 16 ➕ Multimodal & Voice AI](#module-16--multimodal--voice-ai)
- [Module 17 ➕ AI-Assisted Development](#module-17--ai-assisted-development)
- [Module 18 ➕ Responsible AI, Governance & Cost](#module-18--responsible-ai-governance--cost)
- [Module 19 ➕ Interview Prep & Portfolio](#module-19--interview-prep--portfolio)
- [Capstone Projects](#capstone-projects)
- [Core Reading & Resources](#core-reading--resources)
- [Progress Tracker](#progress-tracker)

---

## Suggested Repo Structure

```
ai-engineering/
├── README.md
├── notes/
│   ├── 00-math/
│   ├── 01-programming/
│   ├── 02-ml-foundations/
│   ├── ... one folder per module
├── projects/
│   ├── 01-fastapi-service/
│   ├── 05-rag-chatbot/
│   ├── 06-tool-using-agent/
│   └── ...
├── cheatsheets/
└── interview-questions/
```

---

## Roadmap at a Glance

| Phase | Modules | Goal |
|---|---|---|
| **A. Foundations** | 0, 1, 2 | Code, backend, data, and ML/DL/transformer fundamentals |
| **B. Building with LLMs** | 3, 4, 5, 6, 7 | Build LLM apps, RAG systems, agents, and multi-agent workflows |
| **C. Production readiness** | 8, 9, 10, 11, 12, 13 | Evaluate, observe, secure, deploy, and design at scale |
| **D. Depth & career** | 14 to 19 | Fine-tuning, serving, multimodal, tooling, governance, interviews |

---

## Module 0 ➕ Math & Prerequisites

You do not need a math degree, but you need intuition for how models learn.

- [ ] **Linear algebra:** vectors, matrices, dot product, matrix multiplication, norms, eigenvalues/eigenvectors, SVD (intuition)
- [ ] **Calculus:** derivatives, partial derivatives, chain rule, gradients (the basis of backpropagation)
- [ ] **Probability:** random variables, distributions (Gaussian, Bernoulli, categorical), conditional probability, Bayes' theorem, expectation and variance
- [ ] **Statistics:** mean/median/variance, sampling, hypothesis testing, confidence intervals, correlation vs causation, bias-variance
- [ ] **Information theory:** entropy, cross-entropy, KL divergence (used in loss functions and RLHF)
- [ ] **Optimization basics:** loss functions, gradient descent, learning rate, convexity (intuition)

**Checkpoint:** explain why gradient descent works and compute a gradient by hand for a tiny network.

---

## Module 1: Programming & Software Engineering

> Even if coding agents write most of your code, you must understand code to give good instructions, review output, and debug. Three pillars: **Python, Backend, Data**, plus DevOps basics.

### 1.1 Python
- [ ] Core syntax, data structures, comprehensions, generators, iterators
- [ ] Object-oriented programming (classes, inheritance, composition, dataclasses)
- [ ] Functions, decorators, context managers
- [ ] **Async Python** (`asyncio`, `async/await`, concurrency vs parallelism, `httpx`/`aiohttp`)
- [ ] **Type hints** (`typing`, generics, Protocols), static checking with `mypy`/`pyright`
- [ ] **Error handling** (exceptions, custom errors, retries, timeouts)
- [ ] **Testing** (`pytest`, fixtures, mocking, parametrized tests, coverage)
- [ ] ➕ Packaging and environments (`venv`, `uv`/`pip`, `pyproject.toml`)
- [ ] ➕ Scientific stack: NumPy, Pandas, Matplotlib
- [ ] ➕ Code quality: `ruff`/`black`, pre-commit hooks, docstrings

### 1.2 Backend Engineering
- [ ] REST API fundamentals (HTTP methods, status codes, idempotency)
- [ ] **FastAPI** (routing, dependency injection, background tasks)
- [ ] **Pydantic** (validation, settings, serialization), which you will also use for LLM structured output
- [ ] **Authentication & authorization** (API keys, JWT, OAuth2, RBAC)
- [ ] **WebSockets** and Server-Sent Events (for streaming LLM output)
- [ ] API design (versioning, pagination, error contracts, OpenAPI docs)
- [ ] ➕ Task queues & background workers (Celery, RQ, Arq), message brokers (Redis, RabbitMQ, Kafka basics)
- [ ] ➕ Data structures & algorithms basics (arrays, hash maps, trees, graphs, complexity)

### 1.3 Data
- [ ] **SQL** (joins, aggregations, window functions, indexes, transactions)
- [ ] **PostgreSQL** (and `pgvector` later for RAG)
- [ ] **Redis** (caching, rate limiting, pub/sub)
- [ ] **JSON** and data modeling (structured vs unstructured data)
- [ ] ➕ NoSQL (MongoDB, document stores), ORMs (SQLAlchemy), migrations (Alembic)
- [ ] ➕ Data formats: CSV, Parquet, JSONL

### 1.4 DevOps Basics
- [ ] **Git & GitHub** (branching, PRs, rebasing, resolving conflicts)
- [ ] **Linux** (shell, permissions, processes, networking basics)
- [ ] **Docker** (images, containers, Compose)
- [ ] Environment management and config (`.env`, secrets)
- [ ] **Logging** (structured logs, log levels)
- [ ] Cloud fundamentals (compute, storage, networking, IAM)

**Projects:** FastAPI + PostgreSQL + Redis CRUD service with auth, tests, and a Dockerfile.

**Checkpoint:** ship a containerized, tested API with streaming endpoint and CI on GitHub Actions.

---

## Module 2: AI/ML Foundations

> Don't skip this. LLMs are built on these ideas, and you will debug and reason far better with them.

### 2.1 Machine Learning
- [ ] Supervised learning: linear/logistic regression, decision trees, random forests, gradient boosting (XGBoost/LightGBM), SVM, k-NN
- [ ] Unsupervised learning: k-means, hierarchical clustering, PCA, t-SNE/UMAP
- [ ] **Feature engineering** (scaling, encoding, missing values, feature selection)
- [ ] **Model evaluation:** train/val/test split, cross-validation, accuracy/precision/recall/F1, ROC-AUC, confusion matrix, regression metrics
- [ ] Overfitting, underfitting, regularization (L1/L2), bias-variance trade-off
- [ ] Hyperparameter tuning
- [ ] **Model serving** basics (pickling/ONNX, REST inference endpoints)
- [ ] ➕ Exploratory Data Analysis (EDA), data leakage, class imbalance
- [ ] ➕ scikit-learn workflows and pipelines

### 2.2 Deep Learning
- [ ] Neural networks: perceptron, MLP, activation functions
- [ ] **Backpropagation** (implement it from scratch once)
- [ ] **Optimizers:** SGD, momentum, Adam/AdamW, learning-rate schedules
- [ ] **PyTorch:** tensors, autograd, `nn.Module`, DataLoader, training loops
- [ ] **GPU basics:** CUDA concepts, memory, mixed precision (fp16/bf16)
- [ ] TensorFlow/Keras (awareness)
- [ ] Regularization: dropout, batch/layer norm, early stopping
- [ ] CNNs (vision basics), RNN/LSTM/GRU (history and why transformers replaced them)
- [ ] ➕ Loss functions deep-dive (cross-entropy, MSE, contrastive, triplet)
- [ ] ➕ Transfer learning and pretrained models

### 2.3 NLP
- [ ] Text preprocessing, **tokenization** (BPE, WordPiece, SentencePiece)
- [ ] **Embeddings:** word2vec/GloVe, then contextual embeddings; cosine similarity
- [ ] **Attention** mechanism and sequence-to-sequence models
- [ ] NLP tasks: classification, NER, summarization, translation, QA

### 2.4 Transformers (the backbone of LLMs)
- [ ] **Self-attention** (Q, K, V, scaled dot-product)
- [ ] **Multi-head attention**
- [ ] **Positional encoding** (sinusoidal, learned, RoPE, ALiBi)
- [ ] **Encoder vs decoder vs encoder-decoder** architectures (BERT vs GPT vs T5)
- [ ] **Pre-training, fine-tuning, inference**
- [ ] ➕ KV cache, causal masking, autoregressive decoding
- [ ] ➕ Sampling: temperature, top-k, top-p, beam search
- [ ] ➕ Scaling laws, Mixture-of-Experts (MoE), efficient attention (FlashAttention, GQA/MQA)
- [ ] ➕ Build a small GPT from scratch (nanoGPT-style)

**Projects:** train a classifier with scikit-learn and PyTorch; implement a mini-transformer; fine-tune a small BERT for text classification.

**Checkpoint:** explain the full forward pass of a decoder-only transformer on a whiteboard.

---

## Module 3: Generative AI & Foundation Models

### 3.1 LLM Model Engineering
- [ ] Integrating with LLM **APIs** (OpenAI, Anthropic, Google, open-source via Hugging Face/Ollama)
- [ ] **Tokens** and tokenizers, counting tokens, cost per token
- [ ] **Context window** (what it is, limits, "lost in the middle")
- [ ] **API usage patterns** (system/user/assistant roles, parameters, rate limits)
- [ ] **Model selection** (capability vs cost vs latency vs privacy; open vs closed)
- [ ] **Quantization** (int8/int4, GGUF, GPTQ, AWQ) and its quality trade-offs
- [ ] **Multimodal models:** audio, vision, speech, documents
- [ ] ➕ Reasoning models and "thinking" budgets, when to use them
- [ ] ➕ Open-weight model ecosystem (Llama, Mistral, Qwen, Gemma, DeepSeek), Hugging Face Hub, `transformers`, Ollama, LM Studio

### 3.2 Context Engineering
- [ ] **Prompt engineering** (clear instructions, roles, delimiters, examples)
- [ ] **System prompts** design
- [ ] **Few-shot prompting**
- [ ] **Dynamic context** (assembling context at runtime)
- [ ] **Context compression** (summarization, pruning, token budgeting)
- [ ] **Context selection** (what to include and exclude)
- [ ] **Structured context** (XML/JSON sections, schemas)
- [ ] **Long-term context** (memory stores, summaries, retrieval)
- [ ] ➕ Prompting techniques: chain-of-thought, self-consistency, ReAct, prompt chaining, role prompting
- [ ] ➕ Prompt versioning and prompt testing
- [ ] ➕ Prompt caching (provider-side) to reduce cost and latency

**Projects:** a CLI chatbot with conversation memory, token counting, and swappable model providers.

**Checkpoint:** given a task, design a prompt + context strategy and justify every token you include.

---

## Module 4: LLM Application Engineering

- [ ] **Structured output** (JSON mode, JSON Schema, Pydantic models, constrained decoding)
- [ ] **Tool / function calling:** how the LLM requests a tool, how you execute and return results
- [ ] **Creating custom tools** (schemas, descriptions, validation, error messages the model can act on)
- [ ] **Streaming** responses (SSE/WebSocket) and partial-output handling
- [ ] **Async execution** and concurrency for parallel LLM calls
- [ ] **Retries & fallbacks** (exponential backoff, provider fallback, timeouts)
- [ ] **Model routing** (cheap model for easy tasks, strong model for hard ones)
- [ ] **LLM gateways** (LiteLLM, Portkey, OpenRouter, custom proxy)
- [ ] **Semantic caching** (embedding-based cache hits)
- [ ] **Rate limiting** (per-user, per-key, token-based)
- [ ] **Cost optimization** (prompt trimming, caching, batching, smaller models)
- [ ] ➕ Batch APIs for offline workloads
- [ ] ➕ Frameworks: LangChain, LlamaIndex, plus the discipline of using raw SDKs without a framework
- [ ] ➕ Idempotency and request deduplication for LLM calls

**Projects:** an "LLM gateway" service in FastAPI with routing, fallback, caching, rate limiting, and a cost dashboard.

**Checkpoint:** a request fails mid-stream; describe exactly how your system recovers.

---

## Module 5: RAG Engineering

> RAG gives an LLM access to your data (beyond its training cutoff) and your brand/context.

### 5.1 Core RAG: Ingestion, Retrieval, Generation
- [ ] **Ingestion:** loading documents (PDF, HTML, Docs, DBs), parsing and cleaning, OCR
- [ ] **Chunking strategies:** fixed, recursive, semantic, structure-aware, chunk size/overlap trade-offs
- [ ] **Embeddings:** choosing embedding models, dimensions, multilingual, fine-tuning embeddings
- [ ] **Vector databases:** FAISS, Chroma, Qdrant, Weaviate, Pinecone, Milvus, `pgvector`
- [ ] Indexing: HNSW, IVF, product quantization, ANN trade-offs
- [ ] **Retrieval:** similarity search, top-k, metadata filtering
- [ ] **Generation:** prompt assembly, citations, grounding, "I don't know" behavior

### 5.2 Advanced RAG
- [ ] **Hybrid search** (BM25 + vector)
- [ ] **Reranking** (cross-encoders, Cohere/BGE rerankers)
- [ ] **Query expansion** and **query rewriting**
- [ ] **Multi-query RAG**
- [ ] **Parent-child retrieval**
- [ ] **Graph RAG** (knowledge graphs, Neo4j)
- [ ] **Multimodal RAG** (images, tables, PDFs with figures)
- [ ] **Corrective RAG**
- [ ] **Self-RAG**
- [ ] **Agentic RAG** (agent decides when and what to retrieve)
- [ ] ➕ Vectorless / reasoning-based RAG (tree/index-based retrieval without embeddings)
- [ ] ➕ Contextual retrieval, late chunking, HyDE
- [ ] ➕ Handling tables, code, and structured data (text-to-SQL)
- [ ] ➕ Freshness and incremental indexing, deletion, access control (per-user document permissions)
- [ ] ➕ Common failure modes: bad chunks, retrieval misses, context stuffing, stale data

### 5.3 RAG Interview Prep
- [ ] Scenario-based questions (design a support bot over 1M documents, reduce hallucinations, handle PDFs with tables)

**Projects:** (1) naive RAG over your own notes; (2) upgrade it with hybrid search + reranking; (3) add evaluation (see Module 8).

**Checkpoint:** show measurable retrieval-quality improvement from each upgrade.

---

## Module 6: AI Agents

### 6.1 Agent Fundamentals
- [ ] What an agent is vs a workflow vs a plain LLM call
- [ ] The agent loop: observe, think, act, repeat; stopping conditions and max-step guards

### 6.2 Tools
- [ ] **External APIs**
- [ ] **Databases** (SQL, vector stores)
- [ ] **Browser** tools (web search, page fetch, automation)
- [ ] **Code execution / coding agents** (sandboxed interpreters)
- [ ] ➕ File system and shell tools, with permissioning

### 6.3 Memory
- [ ] Short-term (conversation/scratchpad) vs long-term (vector/DB) memory
- [ ] Episodic, semantic, procedural memory
- [ ] Memory write/read policies, summarization, forgetting

### 6.4 Reasoning & Planning
- [ ] **Reasoning** (chain-of-thought, reasoning models)
- [ ] **Planning** and **task decomposition**
- [ ] **Reflection** and self-critique
- [ ] **ReAct** pattern
- [ ] ➕ Plan-and-execute, tree search, verifier/critic loops

### 6.5 MCP (Model Context Protocol)
- [ ] MCP architecture: **client**, **server**
- [ ] MCP **tools**, **resources**, **prompts**
- [ ] Building your own MCP server; consuming existing ones
- [ ] **MCP security** (auth, permissions, trust boundaries, tool poisoning)

### 6.6 ➕ Additional Agent Topics
- [ ] Agent-to-agent protocols (A2A) and interoperability
- [ ] Computer-use / browser-use agents
- [ ] Agent skills and reusable instruction packages
- [ ] Failure modes: looping, tool misuse, hallucinated tool calls, runaway cost

**Projects:** a research agent (search, read, summarize, cite); a coding agent in a sandbox; a custom MCP server wrapping an API you use.

**Checkpoint:** your agent completes a 5+ step task reliably and stops safely when it can't.

---

## Module 7: Agent Orchestration

> Agents are workers. Orchestration is the environment that lets them work efficiently and reliably.

- [ ] **Agent state management** (typed state, checkpoints, persistence, resume)
- [ ] **Workflows** (sequential, parallel, conditional, loops)
- [ ] **Routing** (intent routing, supervisor pattern)
- [ ] **Multi-agent systems** (supervisor/worker, handoffs, debate, swarm, hierarchical)
- [ ] **Human-in-the-loop** (approvals, interrupts, edits before action)
- [ ] **Frameworks:** LangGraph, Google ADK, OpenAI Agents SDK, ➕ CrewAI, AutoGen, LlamaIndex workflows, Pydantic AI
- [ ] ➕ Durable execution for long-running agents (Temporal, queues, retries)
- [ ] ➕ Parallel tool execution and sub-agents for context isolation
- [ ] ➕ Choosing "workflow vs agent": use the simplest design that works
- [ ] ➕ Efficiency: token/latency/cost budgets per run

**Projects:** a LangGraph multi-agent system (planner, researcher, writer, reviewer) with human approval and persistent state.

**Checkpoint:** kill the process mid-run and resume from the last checkpoint.

---

## Module 8: Evaluation

> You cannot improve what you cannot measure.

### 8.0 Eval Lite (start in Module 3/4, not here)
- [ ] A golden set of 20+ examples in `evals/golden.jsonl` for every LLM project
- [ ] A `run_evals.py` that prints metrics and saves results per run
- [ ] A baseline-vs-current metrics table in the project README, updated on every prompt, model, or retrieval change
- [ ] Simple metrics first: exact match, regex, hit@k for retrieval, tool-selection accuracy

The sections below deepen this: judges, RAG and agent metrics, A/B tests, and CI.

### 8.1 Types of Evals
- [ ] **LLM evals:** accuracy, relevance, **hallucination**, toxicity, **LLM-as-a-judge**
- [ ] **RAG evals:** retrieval recall, precision, **groundedness**, **faithfulness**, answer relevance (frameworks: RAGAS, DeepEval, TruLens)
- [ ] **Agent evals:** task success, **tool selection**, **tool arguments**, **goal completion**, trajectory quality

### 8.2 Evaluation Pipeline
- [ ] **Golden datasets** (high-quality annotated sets)
- [ ] **Offline evals** (pre-release) and **online evals** (production monitoring)
- [ ] **A/B testing**
- [ ] **Regression testing** (every prompt/model change runs the suite)
- [ ] **Human evaluation** and review queues
- [ ] ➕ Building synthetic test sets, and their limits
- [ ] ➕ Judging the judge: calibrating LLM-as-a-judge against human labels, bias (position, verbosity, self-preference)
- [ ] ➕ Benchmarks awareness (MMLU, GPQA, SWE-bench, etc.) and why they don't replace your own evals
- [ ] ➕ Eval-driven development and CI integration

**Projects:** build an eval harness with a 100-example golden set for your RAG project; fail CI on regression.

**Checkpoint:** every change you make is justified by an eval delta.

---

## Module 9: AI Observability

- [ ] **Traces, metrics, logs** for LLM systems
- [ ] Tracing every **LLM call** and **tool call**, with inputs, outputs, latency, tokens, cost
- [ ] **LangSmith**
- [ ] **OpenTelemetry** (and GenAI semantic conventions)
- [ ] **Langfuse**, ➕ Arize Phoenix, Helicone, W&B Weave
- [ ] Cloud-native monitoring: AWS CloudWatch, Google Cloud Operations, Azure Monitor
- [ ] ➕ Dashboards and alerts (latency, error rate, cost per user, quality scores)
- [ ] ➕ User feedback capture (thumbs, edits) feeding back into evals
- [ ] ➕ Debugging workflow: from a bad answer, find the trace, find the failing step
- [ ] ➕ PII handling in traces

**Projects:** instrument your agent with traces and a dashboard showing cost, latency, and failure points.

**Checkpoint:** diagnose a production-style failure using only traces.

---

## Module 10: Guardrails & AI Security

### 10.1 Guardrails
- [ ] **Input guardrails** (topic restriction, PII, injection detection)
- [ ] **Output guardrails** (schema validation, safety, factuality checks)
- [ ] Tools: Guardrails AI, NeMo Guardrails, Llama Guard, provider moderation APIs

### 10.2 AI Security
- [ ] **Prompt injection** (direct) and **indirect injection** (via documents, web pages, tool outputs)
- [ ] **Jailbreaking**
- [ ] **Data leakage** and **PII detection**
- [ ] **Tool permissions** and **least privilege**
- [ ] **Secret management** (never put secrets in prompts or context)
- [ ] **Agent sandboxing** (containers, network egress control, filesystem limits)
- [ ] **MCP security**
- [ ] **Rate limiting** and abuse prevention
- [ ] ➕ OWASP Top 10 for LLM Applications
- [ ] ➕ The "lethal trifecta" (private data + untrusted content + external communication) and how to break it
- [ ] ➕ Red teaming, adversarial testing, model/supply-chain risks
- [ ] ➕ Audit logging and incident response

**Projects:** red-team your own agent: attempt injection via a poisoned document, then harden it.

**Checkpoint:** a malicious document cannot make your agent exfiltrate data.

---

## Module 11: Deployment (GenAI Ops / Agent Ops)

- [ ] **CI/CD** with **GitHub Actions**
- [ ] **Docker** and **Kubernetes** (deployments, services, autoscaling, secrets)
- [ ] **Model versioning**
- [ ] **Prompt versioning**
- [ ] **Data versioning** (DVC, lakeFS)
- [ ] **Experiment tracking** (MLflow, Weights & Biases)
- [ ] **Rollback** strategies
- [ ] **Canary deployments** (and blue/green, shadow traffic)
- [ ] The trio: **MLOps + LLMOps + DevOps**
- [ ] ➕ Infrastructure as code (Terraform), config management
- [ ] ➕ Feature flags for model/prompt rollouts
- [ ] ➕ Scaling, load testing, queueing, and backpressure
- [ ] ➕ SLOs/SLAs for AI systems (latency, quality, availability)

**Projects:** deploy your RAG/agent app to Kubernetes (or a managed container service) with CI/CD, canary rollout, and one-command rollback.

**Checkpoint:** roll out a prompt change to 5% of traffic and roll it back automatically on eval regression.

---

## Module 12: Cloud Engineering

### AWS
- [ ] **Amazon Bedrock**, **SageMaker**, **ECS / EKS**, **Lambda**, **CloudWatch**
- [ ] ➕ S3, IAM, API Gateway, OpenSearch, RDS, VPC basics

### GCP
- [ ] **Vertex AI**, **Gemini**, **Cloud Run**, **GKE**, **BigQuery**
- [ ] ➕ Cloud Storage, IAM, Pub/Sub

### Azure
- [ ] **Azure AI**, **Azure OpenAI**, **AKS**, **Azure Functions**, **Monitoring**
- [ ] ➕ Blob Storage, Entra ID, Azure AI Search

- [ ] ➕ Cloud cost management, networking and private endpoints, region/data-residency choices

**Checkpoint:** deploy the same app on two clouds and compare cost, latency, and operational effort.

---

## Module 13: AI System Design

- [ ] **Architecture design** for AI products (components, data flow, failure domains)
- [ ] **Model selection**
- [ ] **RAG vs fine-tuning** (and when to combine)
- [ ] **Agent vs workflow**
- [ ] **Database selection** (relational, vector, graph, cache)
- [ ] **Queues** and async pipelines
- [ ] **Caching** layers (prompt, semantic, result)
- [ ] **Reliability** (retries, fallbacks, circuit breakers, graceful degradation)
- [ ] ➕ Latency budgets and capacity planning
- [ ] ➕ Multi-tenancy, data isolation, per-tenant customization
- [ ] ➕ Privacy/compliance architecture (on-prem, VPC, data retention)
- [ ] ➕ Build vs buy decisions
- [ ] ➕ Practice designs: customer-support copilot, enterprise search, document-processing pipeline, coding assistant, voice agent, AI analytics assistant

**Deliverable:** write 5 design docs with diagrams, trade-offs, and failure analysis in `notes/13-system-design/`.

---

## Module 14 ➕ Fine-Tuning & Model Customization

- [ ] When to fine-tune vs prompt vs RAG
- [ ] Dataset creation, cleaning, formatting (instruction/chat formats), data quality over quantity
- [ ] **Supervised fine-tuning (SFT)**
- [ ] **Parameter-efficient fine-tuning:** LoRA, QLoRA, adapters
- [ ] **Preference optimization:** RLHF, DPO, RLAIF; reward models
- [ ] ➕ Reinforcement learning with verifiable rewards (GRPO) at a conceptual level
- [ ] **Distillation** (teacher to smaller student)
- [ ] Tooling: Hugging Face `transformers`/`peft`/`trl`, Unsloth, Axolotl, torchtune
- [ ] Evaluating fine-tuned models, catastrophic forgetting, overfitting
- [ ] Fine-tuning **embedding** and **reranker** models

**Project:** QLoRA fine-tune a small open model on a narrow task and beat the base model on your eval set.

---

## Module 15 ➕ Inference & Model Serving

- [ ] How inference works: prefill vs decode, KV cache, batching
- [ ] **Serving engines:** vLLM, TGI, SGLang, TensorRT-LLM, llama.cpp, Ollama
- [ ] Continuous batching, speculative decoding, paged attention
- [ ] Quantization for serving (AWQ, GPTQ, FP8), GGUF for local use
- [ ] GPU selection and sizing (VRAM math), multi-GPU (tensor/pipeline parallelism)
- [ ] Throughput vs latency, time-to-first-token, tokens/second
- [ ] Self-hosting vs API: cost break-even analysis
- [ ] Serverless GPU options and autoscaling

**Project:** self-host an open model with vLLM behind your gateway and benchmark it against an API model.

---

## Module 16 ➕ Multimodal & Voice AI

- [ ] Vision-language models, document understanding, OCR pipelines
- [ ] Image generation and diffusion models (concepts and APIs)
- [ ] Speech-to-text (Whisper-style) and text-to-speech
- [ ] **Realtime voice agents** (streaming audio, turn-taking, interruption handling, latency budgets)
- [ ] Video understanding basics
- [ ] Multimodal RAG pipelines (see Module 5)

**Project:** a voice assistant with sub-second response and tool calling.

---

## Module 17 ➕ AI-Assisted Development

- [ ] Using coding agents effectively (Claude Code, Codex, Cursor, Copilot): writing clear specs, supplying context, reviewing diffs
- [ ] Project instruction files (`CLAUDE.md`, `AGENTS.md`), reusable skills and commands
- [ ] Test-driven workflow with agents; reviewing and verifying generated code
- [ ] Spec-driven development, task decomposition for agents
- [ ] Limits: when AI-generated code is risky (security, subtle bugs, licensing)

**Practice:** build one project of your own where an agent writes the first draft and you own the review, tests, and architecture.

---

## Module 18 ➕ Responsible AI, Governance & Cost

- [ ] Bias, fairness, and explainability basics
- [ ] Privacy and data protection (GDPR, India's DPDP Act), data retention
- [ ] Regulation awareness (EU AI Act, sector rules)
- [ ] Model cards, system cards, documentation practices
- [ ] Copyright and licensing for models and training data
- [ ] Human oversight design, transparency to users
- [ ] **FinOps for AI:** tracking and forecasting token spend, budgets per feature and per tenant
- [ ] Environmental cost awareness

---

## Module 19 ➕ Interview Prep & Portfolio

- [ ] Python and backend questions; SQL; system design
- [ ] ML/DL fundamentals and transformer internals
- [ ] RAG scenario questions (chunking, retrieval failures, evaluation)
- [ ] Agent design questions (tools, memory, failure handling)
- [ ] AI system design rounds
- [ ] Take-home and live coding with LLM APIs
- [ ] **FDE-specific skills:** requirements discovery with customers, rapid prototyping, integration with messy enterprise systems, communicating trade-offs to non-technical stakeholders
- [ ] Portfolio: 3 to 5 deployed projects with READMEs, architecture diagrams, eval results, and demo links
- [ ] Writing: blog posts or notes explaining what you built and learned
- [ ] Open source contributions

---

## Capstone Projects

| # | Project | Modules used |
|---|---|---|
| 1 | **Production RAG assistant** over a real document set, with hybrid search, reranking, eval suite, tracing, and guardrails | 1, 3, 4, 5, 8, 9, 10, 11 |
| 2 | **Multi-agent research and report system** with LangGraph, MCP tools, human approval, persistent state | 6, 7, 8, 9, 10 |
| 3 | **LLM gateway + cost dashboard** with routing, caching, rate limits, fallbacks | 4, 9, 11, 18 |
| 4 | **Fine-tuned small model** served with vLLM and evaluated against an API baseline | 2, 14, 15, 8 |
| 5 | **Voice agent** with tool calling, deployed on cloud with CI/CD | 16, 6, 11, 12 |
| 6 | **Enterprise-grade agent**: auth, sandboxing, injection defenses, audit logs, canary deploys | 10, 11, 13 |

---

## Core Reading & Resources

> Verify links and editions yourself; resources change often. Search the titles below.

**Courses & videos**
- Andrej Karpathy: *Neural Networks: Zero to Hero*, and his "Let's build GPT" and tokenizer videos
- 3Blue1Brown: *Essence of Linear Algebra*, *Neural Networks* series
- fast.ai: *Practical Deep Learning for Coders*
- Stanford: CS229 (ML), CS224N (NLP), CS336 (LLMs from scratch)
- DeepLearning.AI short courses (prompting, RAG, agents, evals)
- Hugging Face courses (LLM, Agents, Diffusion)
- Krish Naik's channel: roadmaps, LangChain/LangGraph, RAG, and agentic AI playlists

**Books**
- *AI Engineering* by Chip Huyen
- *Designing Machine Learning Systems* by Chip Huyen
- *Hands-On Large Language Models* by Jay Alammar and Maarten Grootendorst
- *Build a Large Language Model (From Scratch)* by Sebastian Raschka
- *Designing Data-Intensive Applications* by Martin Kleppmann

**Papers to read (in order)**
1. *Attention Is All You Need*
2. BERT; GPT-2/GPT-3 ("Language Models are Few-Shot Learners")
3. *Chain-of-Thought Prompting*; *ReAct*
4. *Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks*
5. LoRA and QLoRA
6. InstructGPT (RLHF); DPO
7. *Lost in the Middle*
8. FlashAttention; PagedAttention (vLLM)
9. Self-RAG; Corrective RAG

**Documentation to bookmark**
- Official docs for the LLM providers you use (OpenAI, Anthropic, Google)
- LangChain, LangGraph, LlamaIndex, Google ADK, OpenAI Agents SDK
- Model Context Protocol specification
- Hugging Face `transformers`, `peft`, `trl`
- vLLM, OpenTelemetry, Langfuse, LangSmith
- OWASP Top 10 for LLM Applications

**Communities & news**
- Hugging Face papers feed, arXiv (cs.CL, cs.LG, cs.AI), Latent Space, The Batch, Simon Willison's blog

---

## Progress Tracker

Status: ☐ not started · 🔨 in progress · 📝 gates 1 to 3 done, quiz pending · ✅ all four gates met

| Module | Status | Notes link | Project link |
|---|---|---|---|
| 0. Math & prerequisites | ☐ | | |
| 1. Programming & software eng. | ☐ | | |
| 2. AI/ML foundations | ☐ | | |
| 3. GenAI & foundation models | ☐ | | |
| 4. LLM application engineering | ☐ | | |
| 5. RAG engineering | ☐ | | |
| 6. AI agents | ☐ | | |
| 7. Agent orchestration | ☐ | | |
| 8. Evaluation | ☐ | | |
| 9. Observability | ☐ | | |
| 10. Guardrails & security | ☐ | | |
| 11. Deployment / Ops | ☐ | | |
| 12. Cloud | ☐ | | |
| 13. AI system design | ☐ | | |
| 14. Fine-tuning | ☐ | | |
| 15. Inference & serving | ☐ | | |
| 16. Multimodal & voice | ☐ | | |
| 17. AI-assisted development | ☐ | | |
| 18. Responsible AI & cost | ☐ | | |
| 19. Interview prep & portfolio | ☐ | | |

---

## Suggested Pacing

| Months | Focus |
|---|---|
| 1 to 2 | Modules 0, 1 |
| 3 to 4 | Module 2 |
| 5 to 6 | Modules 3, 4, 5, plus **Eval Lite (8.0)** and take-home #2 |
| 7 to 8 | Modules 6, 7, plus take-home #3 |
| 9 to 10 | Modules 8 (full depth), 9, 10 |
| 11 to 12 | Modules 11, 12, 13, plus take-home #4 |
| 13 to 15 | Modules 14 to 19, capstones, interview prep, final take-home #5 |

Take-home #1 comes after Modules 0 to 2 (end of month 4). A spaced review runs every 2 weeks throughout.

Adjust freely. If you already know Python and backend basics, start at Module 2 or 3 and fill gaps as you meet them.

---

## License

Notes and code in this repo are for personal learning. Add a license of your choice if you plan to make it public.