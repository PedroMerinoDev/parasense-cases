# ParaSense Application Cases 📂

> **Technical Case Studies / Engineering Decision Systems**

This repository documents real-world scenarios where the **ParaSense Neuro-Symbolic Engine** was applied to solve problems involving high uncertainty, contradictory data streams, and critical risk management.

Unlike standard machine learning approaches (which rely on statistical probability), these cases demonstrate the use of **Paraconsistent Logic (Eτ)** to handle "imperfect" information without halting the system.

## Case Studies

### 1. [LLM Guardrails & Hallucination Control](./llm-guardrails)
**Problem:** Large Language Models (LLMs) are stochastic and prone to confident hallucinations or policy violations that standard Regex/Keyword filters miss.
**Solution:** A symbolic arbitration layer that evaluates inputs/outputs against multiple contradictory safety policies (e.g., "be helpful" vs "be safe").

### 2. [Real-Time Betting Risk Shield](./betting-risk)
**Problem:** Detecting fraud in high-frequency betting markets where user behavior signals are often contradictory (e.g., trusted device + anomalous bet size).
**Solution:** A decision lattice that accepts conflicting signals and computes a "Risk Energy" score, blocking transactions only when the contradiction exceeds a safety threshold.

### 3. [CRM Cognitivo & Lead Scoring](./lead-scoring) (PT-BR)
**Problema:** CRMs tradicionais somam pontos linearmente, confundindo "Curiosos sem dinheiro" com "Compradores reais".
**Solução:** Uso do MPD para detectar a contradição entre *Interesse* (Engajamento) e *Capacidade* (Renda), filtrando leads inconsistentes e priorizando vendas reais.

---
*Engineering Decision Systems by [Pedro Merino](https://github.com/pedromerino)*
