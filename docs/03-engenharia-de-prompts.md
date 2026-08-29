# Engenharia de Prompts

## Objetivo

Esta seção documenta a primeira versão da biblioteca de prompts do **AI-Assisted Data Analysis Playbook**.

A biblioteca foi criada para apoiar dois comportamentos do NotebookLM:

- **Modo Orientador:** ajuda o analista a descobrir o que fazer, em qual ordem, por quê e como validar cada etapa.
- **Modo Revisor:** avalia algo já produzido, identifica inconsistências, lacunas, riscos, pressupostos não comprovados e validações faltantes.

Os prompts abaixo representam a **versão inicial (V1)** da biblioteca. Na Etapa 8, três prompts foram avaliados comparativamente em testes controlados: **P01-V1 (problema de negócio)**, **P03-V1 (qualidade dos dados)** e **P08-V1 (visualização de dados)**. Os demais prompts permanecem como biblioteca inicial ainda não submetida a comparação experimental neste projeto.

Os testes não incluíram T04 ou T05. A amostra experimental final foi composta por **T01, T02 e T03**, considerada suficiente para identificar padrões, limitações e oportunidades de refinamento.

---

## Arquitetura-base dos prompts

Os prompts foram estruturados a partir do modelo:

> **Contexto → Objetivo → Evidências → Lacunas → Ação → Validação → Entrega**

Além desses elementos, cada prompt pode incluir:

- **Modo:** Orientador ou Revisor;
- **Restrições:** limites explícitos para reduzir inferências indevidas, respostas genéricas ou conclusões não fundamentadas.

Estrutura-padrão:

```text
MODO:
[ORIENTADOR ou REVISOR]

CONTEXTO:
O que já sabemos sobre o negócio, dados ou entrega.

OBJETIVO:
O que queremos alcançar nesta etapa.

EVIDÊNCIAS:
Dados, resultados, regras de negócio ou materiais disponíveis.

LACUNAS:
Informações que ainda podem estar faltando.

TAREFA:
O que a IA deve fazer.

RESTRIÇÕES:
O que ela não deve assumir ou fazer.

VALIDAÇÃO:
Como avaliar se a resposta é adequada.

ENTREGA:
Formato esperado da resposta.
```

---

## Convenção de nomenclatura e versionamento

Cada prompt recebe um identificador relacionado ao módulo correspondente do playbook:

| ID | Módulo |
|---|---|
| P01 | Entendimento do problema de negócio |
| P02 | Entendimento dos dados |
| P03 | Qualidade dos dados |
| P04 | Preparação e transformação |
| P05 | Análise exploratória |
| P06 | Métricas e KPIs |
| P07 | Análise estatística e relações |
| P08 | Visualização de dados |
| P09 | Dashboard |
| P10 | Insights e recomendações |
| P11 | Storytelling e comunicação |
| P12 | Documentação e QA |

As versões serão identificadas como:

```text
P01-V1
P01-V2
P01-V3
```

Esse padrão permitirá registrar posteriormente:

> **Prompt inicial → problema encontrado → alteração → novo resultado**

---

# Biblioteca de Prompts — V1

## P01-V1 — Entendimento do problema de negócio

```text
MODO: [ORIENTADOR ou REVISOR]

CONTEXTO:
Estou iniciando um projeto de Análise de Dados.

Contexto do negócio:
[descreva]

Demanda recebida:
[descreva]

Stakeholders conhecidos:
[descreva ou informe "não definido"]

OBJETIVO:
Transformar a demanda apresentada em um problema analítico claro e investigável.

TAREFA:
Com base nas fontes deste notebook e nas informações fornecidas:

1. identifique o problema central de negócio;
2. diferencie problema de negócio de tarefa técnica;
3. proponha perguntas analíticas;
4. identifique possíveis stakeholders;
5. proponha objetivos de análise;
6. levante hipóteses iniciais, deixando explícito que ainda precisam ser testadas;
7. indique quais critérios poderiam ser usados para avaliar o sucesso da análise;
8. identifique informações que ainda preciso obter antes de avançar.

RESTRIÇÕES:
Não invente regras de negócio, metas, stakeholders ou informações que não foram fornecidas.
Não trate hipóteses como conclusões.

VALIDAÇÃO:
Verifique se cada pergunta analítica está ligada ao problema de negócio e se pode, em princípio, ser respondida com dados.

ENTREGA:
Organize em:
Problema → Objetivos → Perguntas analíticas → Hipóteses → Lacunas → Próximos passos.
```

---

## P02-V1 — Entendimento dos dados

```text
MODO: [ORIENTADOR ou REVISOR]

CONTEXTO:
Problema de negócio:
[descreva]

Dados disponíveis:
[tabelas, schemas, colunas, descrições ou amostras]

OBJETIVO:
Compreender se os dados disponíveis são adequados para responder às perguntas do projeto.

TAREFA:
Analise as informações fornecidas e:

1. identifique a provável granularidade de cada tabela;
2. identifique possíveis chaves;
3. descreva relacionamentos candidatos entre tabelas;
4. destaque campos cujo significado precisa ser confirmado;
5. identifique dados potencialmente ausentes;
6. proponha um dicionário inicial dos campos;
7. avalie se os dados parecem suficientes para responder ao problema.

RESTRIÇÕES:
Não assuma o significado de uma coluna apenas pelo nome.
Quando uma definição depender de regra de negócio, marque-a como "necessita validação".

VALIDAÇÃO:
Diferencie claramente:
informação fornecida → inferência → informação ainda necessária.

ENTREGA:
Forneça:
Mapa das tabelas → Granularidade → Chaves → Relacionamentos → Dicionário inicial → Lacunas → Perguntas para o negócio.
```

---

## P03-V1 — Qualidade dos dados

```text
MODO: [ORIENTADOR ou REVISOR]

CONTEXTO:
Descrição dos dados:
[descreva]

Resultados já conhecidos sobre qualidade:
[insira nulos, duplicidades, valores, distribuições etc.]

OBJETIVO:
Planejar ou revisar uma avaliação de qualidade dos dados.

TAREFA:
Utilizando as dimensões de qualidade presentes nas fontes do notebook:

1. identifique verificações necessárias;
2. classifique-as, quando aplicável, em precisão, completude, consistência, atualidade, validade e unicidade;
3. indique quais problemas podem afetar as análises;
4. diferencie problema comprovado de possível problema;
5. proponha formas de investigação;
6. indique quais tratamentos exigem regra de negócio antes de serem aplicados.

RESTRIÇÕES:
Não recomende automaticamente remover nulos, duplicados ou outliers.
Não considere um valor incomum como erro sem evidência.

VALIDAÇÃO:
Para cada problema, informe:
Evidência → Impacto potencial → Investigação → Decisão necessária → Validação.

ENTREGA:
Produza um checklist priorizado de qualidade de dados.
```

---

## P04-V1 — Preparação e transformação

```text
MODO: [ORIENTADOR ou REVISOR]

CONTEXTO:
Problema de negócio:
[descreva]

Estrutura dos dados:
[descreva]

Problemas de qualidade identificados:
[descreva]

Ferramenta de execução:
[SQL / BigQuery / Python / Pandas / outra]

OBJETIVO:
Planejar ou revisar as transformações necessárias para construir a base analítica.

TAREFA:
Para cada transformação necessária:

1. explique o que deve ser alterado;
2. justifique por que a alteração é necessária;
3. indique possíveis riscos;
4. sugira a lógica ou código quando apropriado;
5. indique como validar o resultado após a transformação.

RESTRIÇÕES:
Não execute mentalmente cálculos que dependam de dados não fornecidos.
Não invente regras de negócio.
Não altere dados apenas para facilitar a análise.

VALIDAÇÃO:
Toda transformação deverá responder:
O que mudou?
Por que mudou?
Como saberemos que ficou correto?

ENTREGA:
Apresente um plano de transformação em ordem de execução.
```

---

## P05-V1 — Análise exploratória

```text
MODO: [ORIENTADOR ou REVISOR]

CONTEXTO:
Problema de negócio:
[descreva]

Dados disponíveis:
[descreva]

Perguntas de negócio:
[descreva]

OBJETIVO:
Criar ou revisar um plano de análise exploratória orientado ao problema.

TAREFA:
1. proponha perguntas exploratórias;
2. indique dimensões e métricas relevantes;
3. sugira comparações, distribuições ou tendências que devem ser investigadas;
4. identifique análises prioritárias;
5. indique possíveis anomalias a observar;
6. mostre como cada análise se conecta a uma pergunta de negócio.

RESTRIÇÕES:
Não transforme padrões hipotéticos em descobertas.
Não confunda exploração com confirmação de hipótese.

VALIDAÇÃO:
Classifique o que surgir como:
Observação → Hipótese → Evidência necessária → Possível conclusão.

ENTREGA:
Produza um roteiro de EDA priorizado.
```

---

## P06-V1 — Métricas e KPIs

```text
MODO: [ORIENTADOR ou REVISOR]

CONTEXTO:
Problema de negócio:
[descreva]

Objetivos:
[descreva]

Métricas atualmente consideradas:
[descreva]

OBJETIVO:
Definir ou revisar métricas e KPIs adequados ao problema.

TAREFA:
Para cada métrica:

1. explique qual pergunta ela responde;
2. defina fórmula;
3. identifique numerador e denominador, quando aplicável;
4. defina granularidade;
5. defina período;
6. indique segmentações relevantes;
7. explique sua interpretação;
8. aponte riscos de cálculo ou interpretação.

RESTRIÇÕES:
Não invente metas ou benchmarks.
Não use uma métrica apenas porque ela está disponível nos dados.

VALIDAÇÃO:
Verifique duplicidades, diferenças de granularidade, filtros, períodos e denominadores.

ENTREGA:
Crie uma ficha técnica para cada KPI.
```

---

## P07-V1 — Análise estatística e relações

```text
MODO: [ORIENTADOR ou REVISOR]

CONTEXTO:
Pergunta analítica:
[descreva]

Variáveis:
[descreva]

Resultados disponíveis:
[descreva]

OBJETIVO:
Identificar ou revisar análises quantitativas adequadas ao problema.

TAREFA:
1. indique quais técnicas descritivas ou relacionais podem ser úteis;
2. explique por que seriam adequadas;
3. informe os pressupostos ou cuidados necessários;
4. explique como interpretar os resultados;
5. destaque limitações.

RESTRIÇÕES:
Não conclua causalidade a partir de correlação.
Não invente significância estatística sem resultados de testes.
Se as fontes não forem suficientes para recomendar uma técnica especializada, declare a limitação.

ENTREGA:
Técnica → Finalidade → Requisitos → Interpretação → Limitações → Validação externa necessária.
```

---

## P08-V1 — Visualização de dados

```text
MODO: [ORIENTADOR ou REVISOR]

CONTEXTO:
Pergunta que o visual precisa responder:
[descreva]

Dados:
[descreva]

Público:
[descreva]

Visual atual, se houver:
[descreva]

OBJETIVO:
Escolher ou revisar a representação visual mais adequada.

TAREFA:
1. identifique o objetivo do visual;
2. recomende o tipo de gráfico;
3. explique a escolha;
4. proponha alternativas;
5. indique riscos de interpretação;
6. avalie legibilidade, hierarquia, rótulos, uso de cor e quantidade de categorias.

RESTRIÇÕES:
Não escolha gráficos apenas por estética.
Não recomende mapas quando localização não for relevante à pergunta.

ENTREGA:
Pergunta → Visual recomendado → Justificativa → Alternativas → Riscos → Melhorias.
```

---

## P09-V1 — Dashboard

```text
MODO: [ORIENTADOR ou REVISOR]

CONTEXTO:
Objetivo do dashboard:
[descreva]

Público:
[descreva]

KPIs:
[descreva]

Visuais ou estrutura atual:
[descreva]

OBJETIVO:
Projetar ou revisar a arquitetura de um dashboard.

TAREFA:
Avalie:

1. hierarquia das informações;
2. KPIs principais;
3. visuais necessários;
4. filtros;
5. redundância;
6. legibilidade;
7. organização da tela;
8. interatividade;
9. contexto fornecido ao usuário;
10. possíveis problemas de responsividade.

RESTRIÇÕES:
Não inclua visualizações sem uma pergunta ou função clara.
Evite redundância e excesso de filtros.

ENTREGA:
Arquitetura recomendada → Prioridade dos elementos → Melhorias → Itens que podem ser removidos → Checklist de QA.
```

---

## P10-V1 — Insights e recomendações

```text
MODO: [ORIENTADOR ou REVISOR]

CONTEXTO:
Resultados da análise:
[forneça números, tabelas ou conclusões preliminares]

Problema de negócio:
[descreva]

OBJETIVO:
Transformar resultados analíticos em insights rastreáveis.

TAREFA:
Para cada possível insight, construa:

Dado → Evidência → Insight → Impacto → Recomendação.

Diferencie claramente:
- resultado observado;
- interpretação;
- hipótese;
- recomendação.

RESTRIÇÕES:
Não invente causas.
Não transforme associação em causalidade.
Não forneça recomendações sem conexão com evidências.

VALIDAÇÃO:
Para cada afirmação, pergunte:
"Qual evidência sustenta isso?"

ENTREGA:
Apresente apenas insights que possam ser rastreados até os dados fornecidos.
```

---

## P11-V1 — Storytelling e comunicação

```text
MODO: [ORIENTADOR ou REVISOR]

CONTEXTO:
Público:
[descreva]

Objetivo da comunicação:
[descreva]

Principais resultados:
[descreva]

Formato:
[relatório / apresentação / resumo executivo / outro]

OBJETIVO:
Construir ou revisar uma narrativa clara e adequada ao público.

TAREFA:
Organize a comunicação segundo:

Contexto → Problema → Evidências → Descobertas → Implicações → Recomendações.

Avalie também:

- clareza;
- prioridade das mensagens;
- excesso de detalhes;
- linguagem técnica;
- consistência numérica;
- relação entre gráficos e narrativa.

RESTRIÇÕES:
Não dramatize resultados.
Não omita limitações relevantes.
Não acrescente conclusões não sustentadas pelos dados.

ENTREGA:
Produza uma estrutura narrativa e indique a mensagem principal de cada seção.
```

---

## P12-V1 — Documentação e QA

```text
MODO: REVISOR

CONTEXTO:
Esta é a documentação ou entrega que desejo revisar:
[cole ou descreva]

OBJETIVO:
Avaliar rastreabilidade, reprodutibilidade e consistência do projeto.

TAREFA:
Verifique:

1. fontes de dados;
2. regras de negócio;
3. metodologia;
4. transformações;
5. métricas;
6. cálculos;
7. filtros;
8. períodos;
9. decisões analíticas;
10. limitações;
11. coerência entre resultados e conclusões;
12. consistência entre dashboard, documentação e apresentação.

Classifique os problemas encontrados como:
- crítico;
- importante;
- melhoria recomendada.

RESTRIÇÕES:
Não assuma que uma decisão está correta apenas porque foi documentada.
Não invente regras para preencher lacunas.

VALIDAÇÃO FINAL:
Responda explicitamente:

"Existe alguma afirmação nesta análise que não possa ser rastreada até os dados ou até uma regra de negócio documentada?"

ENTREGA:
Problema → Evidência → Risco → Correção sugerida → Forma de validar.
```

---

# Hipóteses iniciais de engenharia de prompts

Antes dos testes, foram registradas seis hipóteses:

**H1 — Contexto**  
Prompts com mais contexto relevante deverão reduzir respostas genéricas.

**H2 — Restrições**  
Restrições explícitas deverão reduzir conclusões não fundamentadas.

**H3 — Lacunas**  
Solicitar explicitamente a identificação de lacunas deverá incentivar a IA a reconhecer falta de informação em vez de completá-la por inferência.

**H4 — Formato da entrega**  
Definir o formato esperado deverá produzir respostas mais consistentes e reutilizáveis.

**H5 — Modos Orientador e Revisor**  
Separar os dois comportamentos deverá melhorar a aderência da resposta à fase do trabalho analítico.

**H6 — Seleção de fontes**  
Selecionar apenas as fontes mais relevantes para cada consulta deverá reduzir conteúdo tecnicamente correto, porém fora do escopo da tarefa.

A hipótese H6 surgiu durante o primeiro teste de sanidade do NotebookLM: uma fonte ampla de governança de IA gerou tópicos válidos, mas além do contexto cotidiano de um projeto de Análise de Dados.

---

# Resultados dos testes da V1

| Teste | Prompt | Baseline | Estruturado | Síntese |
|---|---|---:|---:|---|
| T01 | P01-V1 — Problema de negócio | 16/18 | 16/18 | Piloto revelou interferência da instrução personalizada do NotebookLM |
| T02 | P03-V1 — Qualidade dos dados | 11/18 | 16/18 | Ganho claro com restrições, lacunas e estrutura de validação |
| T03 | P08-V1 — Visualização | 16/18 | 17/18 | Ganho menor, concentrado em justificativa e auditabilidade |

Os resultados completos e as falhas observadas estão documentados em **[Cicatrizes e Troubleshooting](04-cicatrizes-e-troubleshooting.md)**.

---

# Critérios de avaliação das próximas versões

Os testes futuros deverão observar, pelo menos:

- aderência ao problema apresentado;
- uso correto das fontes;
- reconhecimento de lacunas;
- separação entre fato, hipótese, interpretação e recomendação;
- ausência de regras de negócio inventadas;
- adequação ao modo solicitado;
- utilidade prática da resposta;
- clareza e organização;
- rastreabilidade das afirmações;
- excesso de conteúdo irrelevante.

Os resultados dos testes e as alterações feitas nos prompts serão registrados no arquivo de **Cicatrizes e Troubleshooting**.

---

# Princípio central

> **A IA pode propor, estruturar, explicar, revisar e questionar. O analista continua responsável por validar.**
