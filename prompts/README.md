# Biblioteca de Prompts

Esta pasta funciona como índice da biblioteca de prompts do **AI-Assisted Data Analysis Playbook**.

A documentação completa, incluindo V1, testes, framework final e versões refinadas, está em:

**[Engenharia de Prompts](../docs/03-engenharia-de-prompts.md)**

---

## Como usar

1. escolha o módulo correspondente à etapa do projeto;
2. utilize a **versão recomendada** indicada neste índice;
3. defina o **Modo Orientador** ou **Modo Revisor**, quando aplicável;
4. substitua os campos entre colchetes pelas informações reais do projeto;
5. forneça apenas evidências e regras de negócio conhecidas;
6. aplique o **Bloco Transversal de Confiabilidade**;
7. valide a resposta antes de utilizá-la em uma entrega.

### Modos

**Orientador**  
Use quando precisar descobrir o que fazer, em qual ordem e como validar uma etapa.

**Revisor**  
Use quando já existir uma análise, metodologia, visual, dashboard ou documentação para ser avaliada.

---

## Framework final

> **Modo → Escopo → Contexto → Evidências → Lacunas → Tarefa → Restrições epistemológicas → Fontes relevantes → Validação → Entrega**

O framework surgiu a partir dos testes e cicatrizes documentados no projeto.

---

## Versões recomendadas

| ID | Prompt | Versão recomendada | Status |
|---|---|---|---|
| P01 | Entendimento do problema de negócio | **P01-V2** | Refinado após T01 |
| P02 | Entendimento dos dados | P02-V1 | Não testado comparativamente |
| P03 | Qualidade dos dados | **P03-V2** | Refinado após T02 |
| P04 | Preparação e transformação | P04-V1 | Não testado comparativamente |
| P05 | Análise exploratória | P05-V1 | Não testado comparativamente |
| P06 | Métricas e KPIs | P06-V1 | Não testado comparativamente |
| P07 | Análise estatística e relações | P07-V1 | Não testado comparativamente |
| P08 | Visualização de dados | **P08-V2** | Refinado após T03 |
| P09 | Dashboard | P09-V1 | Não testado comparativamente |
| P10 | Insights e recomendações | P10-V1 | Não testado comparativamente |
| P11 | Storytelling e comunicação | P11-V1 | Não testado comparativamente |
| P12 | Documentação e QA | P12-V1 | Não testado comparativamente |

---

## Convenção de versionamento

As revisões são identificadas como:

```text
P01-V1
P01-V2
P01-V3
```

Uma nova versão só deve ser criada quando houver um motivo documentado.

Histórico esperado:

> **Prompt inicial → problema encontrado → evidência → alteração → nova versão**

---

## Bloco Transversal de Confiabilidade

As versões finais devem seguir regras que impeçam a IA de preencher silenciosamente lacunas, inventar regras, criar thresholds arbitrários, tratar hipótese como fato ou usar linguagem mais categórica do que a evidência permite.

O bloco completo está documentado em **[Engenharia de Prompts](../docs/03-engenharia-de-prompts.md#bloco-transversal-de-confiabilidade)**.

---

## O que esta biblioteca não faz

Os prompts não substituem:

- validação humana;
- regras de negócio;
- execução de SQL ou Python em ambiente apropriado;
- revisão estatística especializada quando necessária;
- verificação dos números e resultados finais.

> **A IA pode propor, estruturar, explicar, revisar e questionar. O analista continua responsável por validar.**
