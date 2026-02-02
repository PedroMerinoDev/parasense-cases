# Estudo de Caso: CRM Cognitivo & Classificação de Leads 📈

> **Aplicação do Motor Neuro-Simbólico em Vendas Complexas (Seguros)**

Baseado na adaptação do motor MPD (ParaSense) para um cenário de **Vendas Consultivas**, mapeamos interações humanas e digitais para um reticulado de decisão capaz de identificar nuances que CRMs tradicionais ignoram.

## 1. O Problema: Lead Scoring Linear vs. Realidade

Sistemas de pontuação tradicionais (Linear Scoring) somam pontos de forma cega:
- Abriu email? +10 pontos.
- Visitou site? +5 pontos.
- **Resultado:** Um lead com muito engajamento mas **zero capacidade financeira** recebe uma pontuação alta ("Lead Quente"), fazendo a equipe de vendas desperdiçar tempo.

**O Desafio:** Identificar a **contradição** entre *Vontade de Comprar* e *Capacidade de Comprar*.

## 2. A Solução ParaSense (Modelagem Lógica)

Em vez de uma régua única (0 a 100), modelamos a decisão como uma **Proposição Lógica (PROPOSITION_01)**: *"Este lead irá converter em uma apólice?"*

### Configuração dos Fatores (FACTOR_04)
Substituímos métricas de risco por um framework de vendas (BANT Adaptado):

| ID | Fator | Descrição | Peso |
|:---|:------|:----------|:-----|
| **F1** | **Perfil (Fit)** | Dados demográficos (Idade, CEP, Bens) vs. Perfil Ideal. | 1.0 |
| **F2** | **Engajamento** | Interações digitais (Cliques, Tempo de página). | 1.0 |
| **F3** | **Capacidade** | Renda presumida vs. Valor do Prêmio. | 1.2 |
| **F4** | **Intenção** | Declaração explícita ("Quero cotar"). | 1.5 |

---

## 3. Dinâmica de Evidências (EVIDENCE_06)

O sistema trata cada interação como um vetor de crença `(μ)` e descrença `(λ)`, permitindo inputs de Agentes Digitais e Humanos.

### Cenário A: O Agente Digital (Sensor)
*   **Evento:** Lead clica no e-mail "Oferta Exclusiva Black Friday".
*   **Ação do Motor:** Insere evidência no Fator **Engajamento**.
    *   `μ = 0.8` (Forte interesse demonstrado)
    *   `λ = 0.0`

### Cenário B: O Agente Humano (Expert)
*   **Evento:** Corretor liga, lead atende mas diz: *"Adorei a proposta, mas estou desempregado agora."*
*   **Ação do Motor:** Corretor tabula a objeção, que vira evidência no Fator **Capacidade**.
    *   `μ = 0.0`
    *   `λ = 0.9` (Forte descrença na capacidade de pagamento)

---

## 4. O Diferencial: Detecção de Contradição ($G_{in}$)

Ao recalcular o estado do lead no Reticulado de Hasse, o ParaSense não apenas "baixa a nota". Ele identifica a **natureza topológica** do lead.

### Perfil 1: O "Curioso Falido" (Estado Inconsistente)
*   **Sinais:** Alto Engajamento (`μ→1.0` em F2) MAS Baixa Capacidade (`λ→1.0` em F3).
*   **Cálculo MPD:**
    *   O Grau de Certeza ($G_{ce}$) fica próximo de zero (as forças se anulam).
    *   **O Grau de Contradição ($G_{in}$) explode.**
*   **Decisão do Sistema:** Em vez de mandar para o vendedor (falso positivo de score alto), o sistema classifica como **"Inconsistente"** e move para uma trilha de nutrição de longo prazo (ou oferta de produto mais barato).

### Perfil 2: O "Lead Tímido" (Estado Paracompleto)
*   **Sinais:** Perfil Ideal (`μ→1.0` em F1) MAS Engajamento Zero (`μ=0, λ=0` em F2).
*   **Cálculo MPD:**
    *   Baixa energia global.
*   **Decisão do Sistema:** Identifica falta de informação (Ignorância). Sugere uma **"Ação de Ruptura"** (ex: envio de WhatsApp ativo) para forçar a geração de uma evidência, seja positiva ou negativa.

---

## Conclusão Técnica

Essa aplicação transformou o ParaSense de um motor de risco puramente matemático em um **Orquestrador de Vendas Inteligente**.

Utilizando a mesma estrutura de tabelas (`InMemoryDecisionEngine`) validada em cenários de apostas de alta frequência, provamos que a **Lógica Paraconsistente** é agnóstica ao domínio: ela resolve conflitos, seja em *odds* de futebol ou na venda de seguros de vida.
