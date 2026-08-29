# Exemplos Práticos

Esta pasta documenta os testes realizados na Etapa 8 do **AI-Assisted Data Analysis Playbook**.

O objetivo foi comparar prompts simples com prompts estruturados da biblioteca V1.

---

## Caso fictício

Os experimentos utilizaram a **VarejoX**, um e-commerce fictício de produtos para casa, evitando dados corporativos ou sensíveis.

O cenário continha ambiguidades típicas:

- nulos;
- identificadores repetidos;
- descontos elevados sem regra definida;
- lucro negativo;
- escolha de visualização;
- risco de confundir associação com causa.

---

# T01 — Entendimento do problema de negócio

**Prompt testado:** P01-V1

| Condição | Pontuação |
|---|---:|
| Baseline | 16/18 |
| P01-V1 | 16/18 |

A instrução personalizada do NotebookLM já estruturava o baseline, criando uma variável de confusão.

> **Aprendizado:** configurações globais, histórico e instruções permanentes também precisam ser controlados.

---

# T02 — Qualidade dos dados

**Prompt testado:** P03-V1

| Condição | Pontuação |
|---|---:|
| Baseline | 11/18 |
| P03-V1 | 16/18 |

O prompt estruturado melhorou a separação entre problema confirmado, possível problema, comportamento legítimo e informação dependente de regra de negócio.

O baseline criou thresholds e campos não fornecidos.

> **Aprendizado:** restrições explícitas e lacunas aumentam a auditabilidade, mas não eliminam inferências plausíveis.

---

# T03 — Visualização de dados

**Prompt testado:** P08-V1

| Condição | Pontuação |
|---|---:|
| Baseline | 16/18 |
| P08-V1 | 17/18 |

O baseline já escolheu corretamente o gráfico. O ganho esteve principalmente na justificativa, na explicação de visuais inadequados e na separação entre observação e conclusão.

> **Aprendizado: Gráfico correto ≠ conclusão correta.**

---

# Resumo

| Teste | Tema | Baseline | Estruturado |
|---|---|---:|---:|
| T01 | Problema de negócio | 16/18 | 16/18 |
| T02 | Qualidade dos dados | 11/18 | 16/18 |
| T03 | Visualização | 16/18 | 17/18 |

Os testes T04 e T05 não foram executados.

A amostra final foi considerada suficiente para gerar as cicatrizes que fundamentaram P01-V2, P03-V2 e P08-V2.

Mais detalhes:

- [Engenharia de Prompts](../docs/03-engenharia-de-prompts.md)
- [Cicatrizes e Troubleshooting](../docs/04-cicatrizes-e-troubleshooting.md)
