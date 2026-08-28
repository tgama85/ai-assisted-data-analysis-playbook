# Biblioteca de Prompts

Esta pasta funciona como índice da biblioteca de prompts do **AI-Assisted Data Analysis Playbook**.

A versão completa e documentada dos prompts está em:

**[Engenharia de Prompts — V1](../docs/03-engenharia-de-prompts.md)**

---

## Como usar

1. escolha o módulo correspondente à etapa do projeto;
2. defina o **Modo Orientador** ou **Modo Revisor**, quando aplicável;
3. substitua os campos entre colchetes pelas informações reais do projeto;
4. forneça apenas evidências e regras de negócio conhecidas;
5. mantenha as restrições e critérios de validação;
6. valide a resposta antes de utilizá-la em uma entrega.

### Modos

**Orientador**  
Use quando precisar descobrir o que fazer, em qual ordem e como validar uma etapa.

**Revisor**  
Use quando já existir uma análise, metodologia, visual, dashboard ou documentação para ser avaliada.

---

## Estrutura-base

> **Contexto → Objetivo → Evidências → Lacunas → Ação → Validação → Entrega**

Os prompts também podem incluir **Modo** e **Restrições**.

---

## Índice da V1

| ID | Prompt | Modo |
|---|---|---|
| P01-V1 | Entendimento do problema de negócio | Orientador / Revisor |
| P02-V1 | Entendimento dos dados | Orientador / Revisor |
| P03-V1 | Qualidade dos dados | Orientador / Revisor |
| P04-V1 | Preparação e transformação | Orientador / Revisor |
| P05-V1 | Análise exploratória | Orientador / Revisor |
| P06-V1 | Métricas e KPIs | Orientador / Revisor |
| P07-V1 | Análise estatística e relações | Orientador / Revisor |
| P08-V1 | Visualização de dados | Orientador / Revisor |
| P09-V1 | Dashboard | Orientador / Revisor |
| P10-V1 | Insights e recomendações | Orientador / Revisor |
| P11-V1 | Storytelling e comunicação | Orientador / Revisor |
| P12-V1 | Documentação e QA | Revisor |

---

## Convenção de versionamento

As revisões serão identificadas como:

```text
P01-V1
P01-V2
P01-V3
```

Cada alteração deverá ser justificada por evidências dos testes.

O histórico esperado é:

> **Prompt inicial → problema encontrado → alteração → novo resultado**

---

## O que esta biblioteca não faz

Os prompts não substituem:

- validação humana;
- regras de negócio;
- execução de SQL ou Python em ambiente apropriado;
- revisão estatística especializada quando necessária;
- verificação dos números e resultados finais.

> **A IA pode propor, estruturar, explicar, revisar e questionar. O analista continua responsável por validar.**
