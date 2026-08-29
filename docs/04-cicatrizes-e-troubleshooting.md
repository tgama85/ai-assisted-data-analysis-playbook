# Cicatrizes e Troubleshooting

## Objetivo

Esta seção registra os erros, limitações, desvios de escopo e aprendizados identificados durante os testes do **AI-Assisted Data Analysis Playbook**.

O objetivo não é apenas mostrar respostas que funcionaram, mas documentar o raciocínio de melhoria:

> **Sintoma → causa provável → impacto → tentativa de controle → resultado → aprendizado → melhoria futura**

Os testes efetivamente realizados foram:

| Teste | Tema | Baseline | Estruturado | Resultado |
|---|---|---:|---:|---|
| T01 | Problema de negócio | 16/18 | 16/18 | teste piloto; revelou variável de confusão |
| T02 | Qualidade dos dados | 11/18 | 16/18 | ganho claro com prompting estruturado |
| T03 | Visualização de dados | 16/18 | 17/18 | ganho menor, focado em justificativa e auditabilidade |

Não foram executados T04 ou T05.

---

## Cicatriz 1 — A instrução global contaminou o baseline

### Sintoma

No T01, o prompt baseline era propositalmente simples, mas a resposta já veio fortemente estruturada.

### Causa provável

O NotebookLM ainda estava com a instrução personalizada do projeto ativa. Essa configuração já determinava comportamentos como:

- identificar lacunas;
- não inventar;
- separar hipótese de conclusão;
- atuar como Orientador/Revisor;
- organizar respostas em uma estrutura analítica.

### Impacto

O experimento não isolava apenas o efeito do prompt. Na prática, comparava:

**prompt simples + instrução estruturada**

versus

**prompt estruturado + instrução estruturada**.

### Troubleshooting

A partir do T02, os testes foram realizados em configuração **Padrão**, mantendo:

- mesmas fontes;
- mesmo caso;
- conversas independentes;
- apenas o prompt variando.

### Aprendizado

> **Ao testar engenharia de prompts, instruções permanentes, histórico da conversa e configurações do sistema são variáveis experimentais e precisam ser controladas.**

---

## Cicatriz 2 — A IA preenche lacunas com detalhes plausíveis

### Sintoma

No T02, a IA sugeriu colunas como `product_id`, `quantity` e `price`, embora nenhuma delas tivesse sido fornecida no cenário.

Também sugeriu chaves compostas usando campos não disponíveis ou insuficientes.

### Impacto

Informações plausíveis podem ser confundidas com informações realmente existentes no schema.

### Troubleshooting

A resposta adequada deve declarar primeiro a lacuna:

> “Não é possível determinar a chave de item com as colunas fornecidas.”

Se um exemplo hipotético for útil, ele deve ser explicitamente rotulado como hipótese ou exemplo.

### Aprendizado

> **Não basta proibir a invenção de regras de negócio. É necessário impedir que a IA complete o schema, os stakeholders ou o contexto com estruturas apenas plausíveis.**

---

## Cicatriz 3 — Restrição de decisão não elimina inferência

### Sintoma

O P03-V1 impediu decisões arbitrárias sobre “desconto excessivo”, mas a IA ainda sugeriu causas como liquidação, erros de integração, cupons acumulados, estornos ou problemas logísticos.

### Impacto

A IA pode respeitar a proibição de tomar uma decisão e ainda assim preencher a falta de contexto com explicações não comprovadas.

### Aprendizado

> **Restrição de decisão ≠ restrição de inferência.**

### Melhoria futura

As próximas versões deverão classificar afirmações como:

- fornecido pelo usuário;
- evidência calculada;
- inferência;
- hipótese a testar;
- exemplo hipotético;
- informação ausente.

---

## Cicatriz 4 — A IA cria thresholds arbitrários

### Sintoma

No baseline do T02, a IA sugeriu:

- que menos de 1% de nulos teria impacto marginal;
- faixas como “desconto baixo < 20%”, “moderado 20–50%” e “agressivo > 50%”.

Nenhum desses limites havia sido fornecido.

### Impacto

Números arbitrários podem parecer objetivos e ser incorporados indevidamente como regra de negócio.

### Aprendizado

> **Thresholds, faixas, metas, benchmarks e pontos de corte precisam de fonte, regra de negócio ou justificativa analítica documentada.**

---

## Cicatriz 5 — Gráfico correto não significa conclusão correta

### Sintoma

No T03, tanto baseline quanto P08-V1 escolheram corretamente um gráfico de barras horizontais ordenado e com referência em zero.

Mesmo assim, as respostas evoluíram de descrições válidas para afirmações como:

- “estão destruindo a margem”;
- “prejuízo crônico”;
- “política agressiva de descontos”;
- “custos logísticos”.

### Impacto

O visual pode estar tecnicamente correto e o storytelling ainda extrapolar as evidências.

### Aprendizado

> **Gráfico correto ≠ conclusão correta.**

A narrativa executiva também precisa ser rastreável até os dados.

---

## Cicatriz 6 — Heurística virou regra universal

### Sintoma

A IA tratou recomendações de visualização, como limitar dashboards a três gráficos, como se fossem regras gerais.

### Impacto

Uma orientação contextual pode ser aplicada mecanicamente fora do cenário em que faz sentido.

### Aprendizado

> **A IA precisa distinguir princípio, recomendação, heurística e regra obrigatória.**

### Melhoria futura

Quando usar uma orientação das fontes, a resposta deverá indicar se ela é:

- princípio;
- heurística;
- recomendação;
- regra formal.

---

## Cicatriz 7 — Fonte correta pode gerar conteúdo irrelevante

### Sintoma

No teste de sanidade da Etapa 6, o NIST foi corretamente utilizado, mas trouxe temas como:

- model collapse;
- red-teaming;
- desligamento de sistemas;
- ataques adversariais.

Os assuntos eram válidos, porém pouco relevantes para o cotidiano de um analista usando IA como apoio.

### Impacto

Grounding melhora factualidade, mas não garante relevância.

### Aprendizado

> **Fonte confiável ≠ trecho relevante para qualquer pergunta.**

### Melhoria futura

Selecionar apenas as fontes necessárias para a tarefa e pedir explicitamente relevância ao contexto analítico.

---

## Cicatriz 8 — Linguagem forte demais aumenta o grau de certeza

### Sintoma

Foram observadas expressões como:

- “universalmente”;
- “drasticamente”;
- “forte correlação negativa” antes de calculá-la;
- “margens saudáveis” sem benchmark;
- “prejuízo crônico” com base apenas em média agregada.

### Impacto

O grau de certeza da linguagem pode ultrapassar a força da evidência.

### Troubleshooting

As respostas futuras deverão usar linguagem proporcional à evidência:

- **Fato:** “Os dados mostram...”
- **Interpretação:** “Os resultados sugerem...”
- **Hipótese:** “Uma possibilidade a investigar é...”
- **Ausência de evidência:** “Não é possível determinar com as informações fornecidas.”

### Aprendizado

> **A intensidade da linguagem também precisa ser validada, não apenas o conteúdo factual.**

---

# Avaliação das hipóteses iniciais

| Hipótese | Status | Evidência |
|---|---|---|
| H1 — Mais contexto reduz respostas genéricas | Parcialmente suportada | respostas estruturadas foram mais específicas, mas contexto e outros elementos variaram juntos |
| H2 — Restrições reduzem conclusões inadequadas | Suportada | P03 reduziu decisões arbitrárias, embora não tenha eliminado inferências |
| H3 — Solicitar lacunas reduz preenchimento automático | Fortemente suportada | P03 explicitou a ausência de regra para desconto excessivo |
| H4 — Formato definido melhora reutilização | Fortemente suportada | respostas estruturadas ficaram mais auditáveis |
| H5 — Orientador/Revisor melhora aderência | Parcialmente suportada | comportamento foi adequado, mas o mesmo caso não foi comparado formalmente nos dois modos |
| H6 — Seleção de fontes reduz irrelevância | Evidência preliminar | o teste de sanidade mostrou excesso vindo de fonte ampla, sem comparação controlada |

---

# Troubleshooting consolidado

| Sintoma | Correção de prompting |
|---|---|
| IA inventa coluna ou stakeholder | exigir declaração de lacuna e rotular exemplos hipotéticos |
| IA cria threshold arbitrário | proibir ponto de corte sem regra, fonte ou justificativa |
| IA transforma hipótese em fato | exigir classificação de evidência, hipótese e interpretação |
| IA avança etapas prematuramente | delimitar o escopo do módulo atual |
| IA cria causalidade | pedir evidência necessária antes de afirmação causal |
| IA usa conteúdo irrelevante de fonte ampla | restringir fontes e exigir relevância para a pergunta |
| IA transforma heurística em regra | pedir classificação da recomendação |
| IA usa linguagem categórica demais | exigir nível de certeza proporcional à evidência |
| IA cria storytelling não sustentado | rastrear cada mensagem executiva até uma evidência |

---

# Conclusão

Os testes não demonstraram simplesmente que “prompts maiores são melhores”.

O principal resultado foi:

> **Prompts estruturados tornam o trabalho da IA mais controlável e auditável, mas não eliminam a necessidade de pensamento crítico.**

O ganho variou conforme a tarefa:

- em qualidade de dados, a melhoria foi expressiva;
- em visualização, o baseline já era forte e o ganho foi menor;
- no piloto de problema de negócio, a instrução global mascarou o efeito do prompt.

O objetivo do prompting estruturado, portanto, não é adicionar detalhes indiscriminadamente, mas fornecer o contexto, as restrições e os critérios de validação necessários para reduzir ambiguidades e tornar a resposta verificável.
