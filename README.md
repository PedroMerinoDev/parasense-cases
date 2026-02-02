# Casos de Uso: ParaSense em Produção 📂

> **Estudos de Caso Técnicos / Engenharia de Sistemas de Decisão**

Este repositório documenta cenários reais onde o **Motor Neuro-Simbólico ParaSense** foi aplicado para resolver problemas de alta incerteza, dados contraditórios e riscos críticos.

Diferente de abordagens tradicionais de Machine Learning (baseadas apenas em probabilidade estatística), estes casos demonstram o uso de **Lógica Paraconsistente (Eτ)** para lidar com "informação imperfeita" sem travar o sistema.

## Estudos de Caso

### 1. [LLM Guardrails & Controle de Alucinação](./llm-guardrails)
**Problema:** Grandes Modelos de Linguagem (LLMs) são estocásticos e propensos a "alucinações confiantes" ou violações sutis de política que filtros Regex falham em detectar.
**Solução:** Uma camada de arbitragem simbólica que avalia inputs/outputs contra múltiplas políticas de segurança contraditórias (ex: "seja prestativo" vs "seja seguro").

### 2. [Risk Shield: Apostas em Tempo Real](./betting-risk)
**Problema:** Detectar fraudes em mercados de apostas de alta frequência onde os sinais de comportamento do usuário são frequentemente contraditórios (ex: dispositivo confiável + tamanho de aposta anômalo).
**Solução:** Um reticulado de decisão que aceita sinais conflitantes e computa uma "Energia de Risco", bloqueando transações apenas quando a contradição excede um limiar de segurança.

### 3. [CRM Cognitivo & Lead Scoring](./lead-scoring)
**Problema:** CRMs tradicionais somam pontos linearmente, confundindo "Curiosos sem dinheiro" com "Compradores reais".
**Solução:** Uso do MPD para detectar a contradição entre *Interesse* (Engajamento) e *Capacidade* (Renda), filtrando leads inconsistentes e priorizando vendas reais.

---
*Engenharia de Sistemas de Decisão por [Pedro Merino](https://github.com/PedroMerinoDev)*
