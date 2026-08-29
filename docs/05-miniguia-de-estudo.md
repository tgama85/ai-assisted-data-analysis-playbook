# Miniguia de Estudo

## Análise de Dados Assistida por IA

Este miniguia consolida os principais aprendizados do **AI-Assisted Data Analysis Playbook** e serve como material de revisão rápida para uso de Inteligência Artificial ao longo de projetos de Análise de Dados.

> **A IA pode propor, estruturar, explicar, revisar e questionar. O analista continua responsável por validar.**

---

# 1. O papel da IA em um projeto de Análise de Dados

A Inteligência Artificial pode apoiar o analista em praticamente todo o ciclo analítico. Ela pode ajudar a estruturar problemas de negócio, levantar perguntas, revisar schemas e documentação, planejar qualidade, propor SQL ou Python, organizar EDA, revisar métricas, sugerir visualizações, avaliar dashboards, estruturar insights, documentar e revisar entregas.

Seu papel ideal é:

> **Orientar → Propor → Explicar → Revisar → Questionar**

Enquanto cabe ao analista:

> **Executar → Validar → Interpretar → Decidir → Assumir responsabilidade pela entrega**

---

# 2. Ciclo de Análise de Dados Assistida por IA

## 2.1 Entendimento do problema

Antes de abrir SQL, Python ou uma ferramenta de BI, é necessário compreender o problema, quem precisa da resposta, qual decisão será apoiada, quais perguntas podem ser respondidas com dados e quais hipóteses precisam ser testadas.

> **Pergunta-chave: Qual decisão de negócio esta análise pretende apoiar?**

## 2.2 Entendimento dos dados

Antes de transformar a base, o analista precisa conhecer tabelas, granularidade, chaves, relacionamentos, significado das colunas, período, origem e regras de negócio.

Um nome de coluna não é uma definição de negócio. Um campo chamado profit, por exemplo, não informa sozinho se representa lucro bruto, margem de contribuição, lucro líquido ou outro conceito.

> **Quando o significado de um campo não estiver documentado, a IA deve registrar uma lacuna, e não inventar a definição.**

## 2.3 Qualidade dos dados

A qualidade deve ser avaliada antes de decisões de tratamento.

Principais dimensões:

- **Precisão:** o valor representa corretamente a realidade?
- **Completude:** informações necessárias estão preenchidas?
- **Consistência:** os dados são coerentes entre registros ou sistemas?
- **Atualidade:** os dados representam o período necessário?
- **Validade:** valores seguem formato e domínio esperados?
- **Unicidade:** existem registros indevidamente duplicados?

Um valor incomum não é automaticamente erro.

- order_id repetido pode ser duplicidade ou múltiplos itens de um pedido;
- lucro negativo pode ser erro ou uma venda legítima com prejuízo;
- desconto de 80% pode ser anomalia, promoção autorizada ou erro.

> **Investigue antes de tratar.**

## 2.4 Preparação e transformação

Toda transformação deve responder:

> **O que foi alterado?**

> **Por que foi alterado?**

> **Como foi validado?**

A IA pode sugerir queries, transformações, regras de limpeza, agregações, joins e validações. A execução deve ocorrer em ambientes apropriados, como SQL, BigQuery, Python, Pandas, planilhas ou ferramentas de BI.

## 2.5 Análise exploratória

A análise exploratória investiga os dados; não deve confirmar uma conclusão antecipada.

> **Observação → Hipótese → Evidência → Conclusão**

## 2.6 Métricas e KPIs

Uma métrica deve responder a uma pergunta. Antes de utilizá-la, defina nome, objetivo, fórmula, numerador, denominador, granularidade, período, filtros, segmentações e limitações.

## 2.7 Estatística e relações

A IA pode ajudar a selecionar técnicas e interpretar resultados, mas deve reconhecer limites.

> **Correlação não implica causalidade.**

## 2.8 Visualização de dados

O gráfico deve partir da pergunta analítica:

- comparação entre categorias → barras;
- tendência temporal → linha;
- distribuição → histograma ou box plot;
- relação entre variáveis numéricas → dispersão;
- composição → visual parte-todo apenas quando houver um total real.

> **Gráfico correto ≠ conclusão correta.**

## 2.9 Dashboard

Um dashboard deve deixar claro quem vai utilizá-lo, para qual decisão, quais KPIs são prioritários, quais filtros agregam valor e qual hierarquia visual facilita a leitura.

Recomendações de design devem ser tratadas como heurísticas, e não automaticamente como regras universais.

## 2.10 Insights e recomendações

Um insight sólido precisa ser rastreável.

> **Dado → Evidência → Insight → Impacto → Recomendação**

## 2.11 Storytelling

Storytelling não significa dramatizar resultados.

> **Contexto → Problema → Evidências → Descobertas → Implicações → Recomendações**

A força da linguagem deve acompanhar a força da evidência.

## 2.12 Documentação e QA

Uma análise profissional deve permitir rastrear dados, regras, transformações, cálculos, decisões, limitações e validações.

> **Existe alguma afirmação nesta análise que não possa ser rastreada até os dados, uma regra de negócio documentada ou uma fonte confiável?**

---

# 3. Engenharia de prompts para analistas

O framework final desenvolvido neste projeto é:

> **Modo → Escopo → Contexto → Evidências → Lacunas → Tarefa → Restrições epistemológicas → Fontes relevantes → Validação → Entrega**

## Modo

- **Orientador:** ajuda a planejar.
- **Revisor:** avalia algo já produzido.

## Escopo

Delimite em qual etapa estamos para reduzir avanço prematuro.

## Evidências

Declare explicitamente o que sabemos.

## Lacunas

Declare também o que não sabemos.

## Restrições epistemológicas

Classifique quando relevante:

- **Fato fornecido**
- **Evidência calculada**
- **Inferência**
- **Hipótese a testar**
- **Exemplo hipotético**
- **Informação ausente**

---

# 4. Principais aprendizados dos testes

## T01 — Problema de negócio

**Baseline: 16/18**  
**P01-V1: 16/18**

A configuração personalizada do NotebookLM já influenciava o baseline.

**Aprendizado:** configurações globais também são variáveis experimentais.

## T02 — Qualidade dos dados

**Baseline: 11/18**  
**P03-V1: 16/18**

O prompt estruturado reduziu decisões arbitrárias e melhorou o reconhecimento de lacunas.

**Aprendizado:** restrições explícitas e classificação de problemas aumentam a auditabilidade.

## T03 — Visualização

**Baseline: 16/18**  
**P08-V1: 17/18**

A escolha do gráfico já era correta no baseline. A maior melhoria foi na justificativa.

**Aprendizado:** prompting estruturado pode melhorar raciocínio e verificabilidade mesmo quando a resposta principal não muda.

> **Prompts estruturados tornam o trabalho da IA mais controlável e auditável, mas não eliminam a necessidade de pensamento crítico.**

---

# 5. Glossário

| Termo | Definição |
|---|---|
| **Análise de Dados** | Processo de investigar dados para responder perguntas e apoiar decisões. |
| **CRISP-DM** | Metodologia estruturada para projetos analíticos, começando pelo entendimento do negócio e dos dados. |
| **Granularidade** | Nível de detalhe representado por cada linha ou registro. |
| **Regra de negócio** | Definição estabelecida pelo contexto operacional da organização. |
| **Qualidade de dados** | Avaliação da confiabilidade e adequação dos dados para determinado uso. |
| **Completude** | Grau em que informações necessárias estão presentes. |
| **Consistência** | Grau de coerência entre dados, registros ou sistemas. |
| **Validade** | Adequação de um valor aos formatos ou domínios esperados. |
| **Unicidade** | Ausência de duplicidades indevidas. |
| **Outlier** | Observação significativamente diferente das demais; não significa automaticamente erro. |
| **KPI** | Indicador-chave utilizado para acompanhar desempenho relacionado a um objetivo. |
| **EDA** | Exploratory Data Analysis; investigação inicial de padrões, distribuições e relações. |
| **Correlação** | Medida de associação entre variáveis; não demonstra causalidade. |
| **Insight** | Interpretação relevante e sustentada por evidências. |
| **Storytelling de dados** | Organização de evidências e descobertas em uma narrativa adequada ao público. |
| **Prompt** | Instrução fornecida a um modelo de IA. |
| **Engenharia de prompts** | Processo de estruturar, testar e refinar instruções para melhorar respostas de IA. |
| **Grounding** | Uso de fontes ou contexto fornecido para ancorar a resposta da IA. |
| **Alucinação / Confabulação** | Conteúdo gerado pela IA que parece plausível, mas não está devidamente fundamentado. |
| **Inferência** | Interpretação derivada de evidências, mas que não é um fato diretamente observado. |
| **Threshold** | Limite utilizado para classificar ou tomar decisões; deve possuir justificativa. |
| **Heurística** | Regra prática ou orientação útil, mas não necessariamente universal. |
| **QA** | Quality Assurance; processo de revisão e validação de uma entrega. |
| **Rastreabilidade** | Capacidade de conectar uma conclusão às evidências, regras ou fontes que a sustentam. |
| **Automation Bias** | Tendência humana de confiar excessivamente em recomendações automatizadas. |

---

# 6. Prompts reutilizáveis para revisão

A biblioteca completa está em [prompts/](../prompts/).

## Revisar uma análise

~~~text
Atue como REVISOR de uma análise de dados.

Identifique:
1. afirmações sustentadas por evidências;
2. hipóteses apresentadas como fatos;
3. regras de negócio não documentadas;
4. inferências sem validação;
5. possíveis relações causais indevidas;
6. métricas ou thresholds sem justificativa;
7. limitações não mencionadas.

Para cada problema:
Problema → Evidência → Risco → Correção → Como validar.

Se faltar informação, declare:
"Informação ausente — necessita validação."
~~~

## Revisar qualidade dos dados

~~~text
Classifique cada situação como:
- problema confirmado;
- possível problema;
- comportamento potencialmente legítimo;
- informação insuficiente.

Não recomende remover nulos, duplicados, outliers ou valores negativos
sem evidência e regra de negócio.

Evidência → Impacto → Investigação → Decisão → Validação.
~~~

## Revisar uma visualização

~~~text
Avalie esta visualização considerando pergunta e público.

Verifique:
- tipo de gráfico;
- escala;
- ordenação;
- rótulos;
- uso funcional da cor;
- legibilidade;
- valores negativos;
- risco de interpretação.

Separe:
O gráfico mostra
vs.
O gráfico NÃO permite concluir.

Não invente metas, benchmarks ou causas.
~~~

## Revisar uma conclusão

~~~text
Para cada conclusão, classifique como:
- fato observado;
- interpretação;
- hipótese;
- recomendação.

Pergunte:
"Qual evidência sustenta esta afirmação?"

Quando a evidência for insuficiente, reduza o nível de certeza.
~~~

## Revisão final de QA

~~~text
Revise:
- fontes;
- períodos;
- filtros;
- granularidade;
- métricas;
- cálculos;
- gráficos;
- conclusões;
- recomendações;
- limitações.

Ao final, responda:

"Existe alguma afirmação que não possa ser rastreada até os dados,
uma regra de negócio documentada ou uma fonte confiável?"
~~~

---

# 7. Regra final

> **A qualidade de uma resposta de IA não elimina a necessidade de validação. O objetivo do prompting estruturado é tornar o raciocínio mais explícito, rastreável e auditável.**
