# AI-Driven AIOps RCA System

An end-to-end AIOps system for **root cause analysis (RCA)** built on unified observability data
(traces, metrics, logs, HAR, JFR), designed to reduce signal noise, improve explainability,
and accelerate incident resolution.

## Table of Contents
- [Overview](#overview)
- [Key Outcomes](#key-outcomes)
- [System Architecture](#system-architecture)
- [Pipeline](#pipeline)
- [Data Model](#data-model)
- [Machine Learning Techniques](#machine-learning-techniques)
- [Agentic / LLM Integration](#agentic--llm-integration)
- [SRE Agent Blueprint](#sre-agent-blueprint)
- [Repository Structure](#repository-structure)
- [Sample Outputs](#sample-outputs)
- [Why This Matters](#why-this-matters)

## Overview

This project implements an **AI-driven AIOps pipeline** for analyzing observability data and
performing explainable root cause analysis.

It unifies multiple telemetry sources into a structured, evidence-based representation and applies:
- signal reduction through clustering and normalization
- deterministic evidence scoring
- optional LLM-assisted reasoning
- agentic refinement for targeted evidence gathering

The goal is to move from:

**noisy telemetry → structured evidence → explainable RCA**

## Key Outcomes

- **200–500× signal reduction** via log clustering and trace pattern normalization
- **Isomorphic trace grouping** using structural hashing
- **Explainable RCA** with explicit evidence mapping across signals
- **Agentic workflows** for iterative evidence gathering under ambiguity
- Recognized as an **Exemplary Assignment**

## System Architecture

The diagram below shows the deterministic RCA core, bounded agentic refinement loop, LLM policy/synthesis roles, MCP tool layer, and post-incident learning feedback path.

![Architecture Diagram](./aiops-rca-agentic-architecture.png)


## Pipeline

1. **Ingestion**
   - Logs, traces, metrics, HAR, JFR

2. **Feature Engineering**
   - Log templates
   - Trace structure encoding
   - Metric aggregation
   - Cross-signal correlation features

3. **Signal Reduction**
   - Log clustering and template reduction
   - Trace normalization via structural hashing

4. **Evidence Construction**
   - Unified record per trace / incident
   - Cross-signal evidence mapping
   - Context for RCA and guided reasoning

5. **RCA Analysis**
   - Deterministic scoring
   - ML-based clustering / anomaly detection
   - Optional LLM-assisted reasoning

6. **Output**
   - Root cause hypothesis
   - Confidence score
   - Evidence attribution
   - Suggested next investigation steps

## Data Model

Each trace / incident is represented as a **single structured record** to support ML analysis and
explainable RCA.

Example fields:
- Trace ID
- Service graph / structure hash
- Latency metrics (p50, p95, p99)
- Error indicators / exceptions
- Log template IDs
- Deployment / config change indicators
- Resource metrics (CPU, memory)

This unified representation supports:
- clustering
- anomaly detection
- supervised / unsupervised RCA
- evidence-driven reasoning

## Machine Learning Techniques

- **Clustering**
  - Log template clustering
  - Trace pattern grouping using structural hashing

- **Anomaly Detection**
  - Latency outliers
  - Error pattern detection
  - Cross-signal abnormality detection

- **Forecasting**
  - Time-series trend analysis in `Forecasting.ipynb`

- **RCA Modeling**
  - Deterministic evidence scoring
  - Candidate ranking and confidence estimation
  - Optional classification / ensemble extensions

## Agentic / LLM Integration

The system supports **agentic workflows** for guided RCA:
- evidence-driven prompting rather than raw telemetry dumps
- iterative hypothesis refinement
- targeted evidence retrieval
- bounded, cost-aware reasoning

Key design principles:
- deterministic + LLM hybrid
- explicit evidence grounding
- controlled cost and safety guardrails
- production-oriented extensibility

## SRE Agent Blueprint

The repository also includes **`SRE-Agent-Blueprint.ipynb`**, which complements the RCA notebook.

The separation is intentional:

- **`RCA.ipynb`** focuses on the **analytics and reasoning workflow**:
  multi-signal RCA, evidence correlation, causal hypotheses, and explainable outputs.

- **`SRE-Agent-Blueprint.ipynb`** focuses on the **system design and orchestration layer**:
  ambiguity detection, constrained agentic refinement, tool use, confidence-aware routing,
  guided evidence collection, and the learning loop.

Together, they show both:
- the **RCA engine**
- the **production-oriented AI-native operating model** built around it

This makes the project stronger than a single oversized notebook because it separates
**analysis logic** from **agent architecture and operationalization**.

## Repository Structure
- [SRE-Agent-Blueprint.ipynb](./SRE-Agent-Blueprint.ipynb) — AI-native SRE / AIOps blueprint, orchestration, guardrails, and learning loop
- [RCA.ipynb](./RCA.ipynb) — root cause analysis workflow and evidence correlation
- [Logs.ipynb](./Logs.ipynb) — log clustering, template reduction, anomaly analysis
- [Forecasting.ipynb](./Forecasting.ipynb) — forecasting and trend analysis

## Sample Outputs

Examples produced by the system include:
- clustered log templates for major noise reduction
- grouped traces with identical structural patterns
- RCA outputs with:
  - root cause hypothesis
  - confidence score
  - supporting evidence across logs, metrics, and traces
- blueprint artifacts showing:
  - deterministic scoring
  - ambiguity-aware escalation
  - constrained evidence-gathering loops

## Why This Matters

Modern observability systems generate **massive telemetry volumes**, making manual RCA slow,
inconsistent, and expensive.

This project demonstrates how to:
- reduce signal volume by orders of magnitude
- unify heterogeneous telemetry into structured evidence
- produce **explainable, reproducible RCA**
- extend RCA into an **AI-native SRE operating model**
- integrate AI/ML and LLMs in a **controlled, production-oriented way**
