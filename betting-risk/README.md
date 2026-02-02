# Estudo de Caso: Risk Shield em Apostas de Tempo Real 🛡️

## O Desafio de Engenharia

Plataformas de apostas online processam milhares de transações por segundo. A detecção de fraude age como um gargalo crítico.

**O Dilema (Double-Bind):**
- **Muito Rígido:** Você bloqueia apostadores legítimos de alto valor (Falsos Positivos) → Perda de receita.
- **Muito Leniente:** Você permite abuso de bônus ou lavagem de dinheiro (Falsos Negativos) → Risco jurídico/licença.

A maioria dos "Motores de Risco" são apenas pilhas de `IF`s (`if aposta > 1000 and idade < 18...`). Isso se torna um código espaguete inmanutenível.

## A Solução ParaSense

Modelamos o Risco não como um booleano (`ÉFraude? Sim/Não`), mas como um campo contínuo de **Evidências**.

### Modelagem de Evidências

| Sinal | μ (Suspeita) | λ (Confiança) | Nota |
|:-------|:--------------|:----------|:-----|
| **Fingerprint do Dispositivo** | 0.1 | 0.9 | Dispositivo Conhecido (Alta Confiança) |
| **Geolocalização IP** | 0.8 | 0.0 | IP de VPN conhecida (Alta Suspeita) |
| **Padrão de Aposta** | 0.6 | 0.2 | Valor 5x maior que a média (Suspeita Média) |

### O "Choque" (Contradição)

Em um sistema binário, `Dispositivo Conhecido` (Confiável) cancelaria `IP Suspeito` (Não confiável) dependendo de qual regra rodasse primeiro. Isso é frágil.

Na Lógica ParaSense Eτ, esses sinais se acumulam no reticulado:
- **Gce (Certeza Global):** Baixo (Confiança e Suspeita se anulam matematicamente).
- **Gin (Contradição Global):** **EXTREMAMENTE ALTO**.

### Estratégia de Decisão

O motor não "chuta". Ele enxerga o estado de **Alta Contradição** (`T`).
Estratégia Acionada: **Intervenção**.

Em vez de autobloquear (perder o usuário) ou permitir (arriscar fraude), o sistema aciona **Atrito Dinâmico**:
- Solicitar um 2FA específico.
- Limitar o valor da aposta temporariamente.
- Sinalizar para fila de revisão humana com alta prioridade.

## Resultado

- **Redução de 30%** em Falsos Positivos (usuários VIP não bloqueados).
- **Auditabilidade:** Toda decisão acompanha um rastro de "Porquê", explicando exatamente quais fatores causaram a contradição.
