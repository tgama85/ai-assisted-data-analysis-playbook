# Guia de Uso Público do AI-Assisted Data Analysis Playbook

Este documento descreve como preparar e utilizar publicamente o notebook **AI-Assisted Data Analysis Playbook** no NotebookLM.

O objetivo é oferecer uma experiência de uso clara e segura sem transformar a IA em autoridade final sobre a análise.

> **A IA ajuda a pensar, mas a evidência continua decidindo.**

---

## 1. Finalidade

O notebook foi criado para apoiar analistas ao longo do ciclo de projetos de Análise de Dados.

Ele pode atuar como:

- **Orientador:** ajuda a planejar, investigar e estruturar uma etapa;
- **Revisor:** avalia algo já produzido e procura lacunas, riscos, inferências e problemas de rastreabilidade.

O notebook não substitui:

- validação humana;
- regras de negócio;
- execução real de SQL, Python ou BI;
- revisão estatística especializada;
- responsabilidade profissional pela entrega.

---

## 2. Configuração recomendada da conversa

Antes de publicar o notebook, configure o chat como **Personalizado** e utilize a instrução abaixo.

~~~text
Você é o AI-Assisted Data Analysis Playbook, um assistente de apoio a analistas de dados.

Seu objetivo é ORIENTAR ou REVISAR projetos de Análise de Dados com base nas fontes selecionadas e no contexto informado pelo usuário. Não substitua validação humana.

MODO:
- Se o usuário estiver iniciando, planejando ou perguntando como fazer algo, atue como ORIENTADOR.
- Se o usuário fornecer uma análise, visual, dashboard, documentação ou conclusão para avaliação, atue como REVISOR.
- Quando útil, informe qual modo está adotando.

ESCOPO:
Identifique a etapa atual do ciclo analítico e permaneça nela:
1. problema de negócio
2. entendimento dos dados
3. qualidade dos dados
4. preparação e transformação
5. análise exploratória
6. métricas e KPIs
7. estatística e relações
8. visualização
9. dashboard
10. insights e recomendações
11. storytelling e comunicação
12. documentação e QA

CONFIABILIDADE:
- Diferencie fato fornecido, evidência calculada, inferência, hipótese a testar, exemplo hipotético e informação ausente.
- Não complete silenciosamente informações ausentes.
- Não invente colunas, tabelas, stakeholders, regras de negócio, metas, benchmarks, thresholds, fórmulas ou resultados.
- Não considere nulos, repetições, outliers ou valores negativos automaticamente como erro.
- Não transforme correlação ou associação em causalidade.
- Não transforme heurísticas ou recomendações das fontes em regras universais.
- Use linguagem proporcional à força da evidência.
- Quando faltar informação essencial, declare: "Informação ausente — necessita validação."
- Se as fontes não sustentarem uma afirmação, declare a limitação.
- Se a tarefa depender de cálculo, SQL, Python, planilha ou BI, explique o procedimento e indique que a execução deve ocorrer externamente.

FONTES:
Use somente as fontes selecionadas no notebook e o contexto fornecido pelo usuário.
Utilize citações quando uma recomendação ou conceito depender das fontes.
Não inclua conteúdo apenas porque é tecnicamente correto; priorize o que é relevante para a etapa atual.

RESPOSTA:
Quando adequado, organize a resposta em:
Contexto → Objetivo → Evidências → Lacunas → Ação → Validação → Entrega.

Antes de concluir, verifique se cada afirmação relevante pode ser rastreada até:
- informação fornecida;
- resultado calculado;
- regra de negócio documentada;
- ou fonte citada.

Sempre termine informando o próximo passo recomendado.
~~~

---

## 3. Como começar uma conversa

O usuário não precisa conhecer os IDs P01–P12 para utilizar o notebook.

Um bom início é fornecer:

- contexto do negócio;
- problema ou dúvida;
- dados disponíveis;
- etapa atual, se conhecida;
- resultado ou entrega esperada.

### Exemplo

~~~text
Estou iniciando uma análise de vendas.
A diretoria informou que o faturamento cresceu, mas a margem caiu.
Tenho uma tabela de pedidos com vendas, desconto, lucro, categoria e região.

Ajude-me a estruturar o problema analítico e diga quais informações ainda preciso obter antes de analisar os dados.
~~~

---

## 4. Prompts rápidos

### Descobrir a etapa

~~~text
Analise minha demanda e identifique em qual etapa do ciclo de Análise de Dados estou.
Não avance para etapas posteriores.
Indique quais informações preciso fornecer para continuar.
~~~

### Revisar uma decisão

~~~text
Atue como REVISOR.
Avalie a decisão abaixo e separe:
fato fornecido, evidência, inferência, hipótese e informação ausente.

Aponte qualquer conclusão que não possa ser rastreada até os dados ou a uma regra de negócio documentada.
~~~

### Validar uma conclusão

~~~text
Revise esta conclusão.
Diga:
1. o que os dados realmente permitem afirmar;
2. o que é interpretação;
3. o que ainda é hipótese;
4. que evidência seria necessária para avançar.
~~~

---

## 5. Condições de uso

### Validação humana obrigatória

Respostas geradas por IA podem conter erros, inferências excessivas ou interpretações inadequadas. Nenhuma recomendação deve ser incorporada automaticamente a uma entrega analítica.

### Execução externa

O notebook pode propor código, cálculos ou métodos, mas processamento e validação devem ocorrer em ambientes adequados, como SQL, BigQuery, Python, Pandas, planilhas ou ferramentas de BI.

### Dados confidenciais

Não utilize o notebook público para inserir informações confidenciais, dados pessoais, segredos comerciais ou qualquer conteúdo que não deva ser exposto ou processado em um ambiente compartilhado.

### Regras de negócio

Metas, thresholds, classificações e regras operacionais precisam ser fornecidos ou validados por quem conhece o negócio.

### Fontes

As respostas são ancoradas nas fontes selecionadas, mas uma fonte confiável pode conter conteúdo irrelevante para uma pergunta específica. O usuário deve conferir as citações e o contexto original.

### Direitos autorais

O notebook público deve conter apenas fontes que possam ser utilizadas e compartilhadas legitimamente. O projeto não redistribui livros comerciais ou materiais obtidos de origem não verificável.

---

## 6. Preparação visual para publicação

Antes de compartilhar o notebook:

1. mantenha apenas as cinco fontes oficiais selecionadas;
2. renomeie fontes com nomes claros e profissionais;
3. remova ou renomeie artefatos de testes para que não pareçam entregas oficiais;
4. crie uma nota chamada **LEIA PRIMEIRO — Como usar este Playbook**;
5. inclua nessa nota o objetivo, as condições de uso e três prompts de início;
6. confirme que o chat está configurado como **Personalizado**;
7. faça um teste final em conversa nova;
8. somente depois habilite o compartilhamento público.

### Nomes recomendados para as fontes

| Fonte atual | Nome público recomendado |
|---|---|
| goodenoughtogreat_0.pdf | Tableau — Good Enough to Great: A Quick Guide for Better Data Visualizations |
| NIST.AI.600-1.pdf.pdf | NIST — AI RMF Generative AI Profile (AI 600-1) |
| Prompt design strategies... | Google AI — Prompt Design Strategies |
| Understanding and preparing data... | IBM — Understanding and Preparing Data |
| What Are Data Quality Dimensions? | IBM — Data Quality Dimensions |

---

## 7. Checklist de teste antes da publicação

Use três consultas de sanidade:

### Teste A — Qualidade

~~~text
Tenho uma tabela em que order_id aparece repetido.
Devo remover as duplicatas?
~~~

**Comportamento esperado:** não recomendar remoção automática; pedir confirmação da granularidade.

### Teste B — Visualização

~~~text
Tenho oito categorias com margens positivas e negativas.
Quero comparar melhor e pior desempenho.
Qual gráfico devo usar?
~~~

**Comportamento esperado:** recomendar visual comparativo adequado, tratar o zero corretamente e não inventar metas.

### Teste C — Causalidade

~~~text
Os maiores descontos aparecem junto das menores margens.
Posso concluir que o desconto causou a queda da margem?
~~~

**Comportamento esperado:** negar conclusão causal sem evidência adicional e indicar o que seria necessário investigar.

---

## 8. Compartilhamento

Para a experiência pública, prefira o link de **visualização da conversa** quando quiser uma interface mais focada no chat.

Mesmo em uma visualização focada, trate fontes e artefatos do notebook como conteúdo potencialmente acessível a leitores. Não use a interface como mecanismo de ocultação de material sensível.

A opção de permitir cópia deve ser habilitada somente se o objetivo for permitir que outras pessoas reutilizem o notebook como template.

---

## 9. Princípio final

> **O Playbook não responde no lugar do analista. Ele ajuda o analista a construir uma resposta que possa ser explicada, rastreada e validada.**
