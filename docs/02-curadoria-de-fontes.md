# Curadoria de Fontes

## Objetivo

A curadoria do **AI-Assisted Data Analysis Playbook** foi definida para fornecer ao NotebookLM uma base de conhecimento confiável, complementar e suficientemente ampla para apoiar o ciclo completo de um projeto de Análise de Dados.

Foram selecionadas **cinco fontes principais**, respeitando a recomendação do desafio da DIO de trabalhar com 3 a 5 fontes e priorizando qualidade em vez de quantidade.

A estratégia adotada foi:

> **Poucas fontes, alta autoridade, funções complementares e cobertura explícita dos módulos do projeto.**

As fontes foram escolhidas para formar cinco pilares:

1. metodologia de projetos analíticos;
2. qualidade e preparação de dados;
3. visualização, dashboards e comunicação;
4. engenharia de prompts;
5. governança, confiabilidade e validação da IA.

---

## Critérios de seleção

As fontes candidatas foram avaliadas segundo os seguintes critérios:

| Critério | Peso |
|---|---:|
| Autoridade da instituição ou autoria | 25% |
| Cobertura dos módulos necessários | 25% |
| Aplicabilidade prática | 20% |
| Clareza e qualidade do conteúdo | 10% |
| Acesso aberto | 10% |
| Compatibilidade com o NotebookLM | 5% |
| Atualidade ou estabilidade conceitual | 5% |
| **Total** | **100%** |

Além da qualidade técnica, foram priorizadas fontes:

- disponibilizadas oficialmente por seus autores ou instituições;
- com acesso público legítimo;
- que pudessem ser consultadas por outras pessoas que desejassem reproduzir o projeto;
- com baixa redundância entre si;
- adequadas aos modos **Orientador** e **Revisor** definidos na arquitetura do projeto.

Materiais comerciais protegidos por direitos autorais, quando não disponibilizados oficialmente em acesso aberto, não foram utilizados como fontes do NotebookLM.

---

# Fontes selecionadas

## 1. IBM — Compreensão e preparação de dados / CRISP-DM

**Instituição:** IBM  
**Tema principal:** ciclo de vida e metodologia de projetos analíticos  
**Formato:** página web  
**Idioma:** português  
**Acesso:** aberto  
**Data de acesso:** 28/08/2026

**URL:**  
https://www.ibm.com/docs/pt-br/ws-and-kc?topic=modeler-understanding-preparing-data

### Papel no projeto

Esta fonte funciona como a principal base metodológica do playbook.

O CRISP-DM organiza o trabalho analítico em etapas que incluem:

- entendimento do negócio;
- entendimento dos dados;
- preparação dos dados;
- modelagem;
- avaliação;
- implantação.

Para este projeto, sua principal contribuição está na ideia de que o trabalho técnico não deve começar antes que o problema de negócio e os dados disponíveis sejam compreendidos.

### Módulos atendidos

**Cobertura principal:**

- Módulo 1 — Entendimento do problema de negócio;
- Módulo 2 — Entendimento dos dados;
- Módulo 4 — Preparação e transformação;
- Módulo 5 — Análise exploratória.

**Cobertura complementar:**

- Módulo 3 — Qualidade dos dados;
- Módulo 6 — Métricas e KPIs;
- Módulo 7 — Análise estatística e relações;
- Módulo 12 — Documentação e QA.

### Justificativa da escolha

Foi escolhida em vez de uma metodologia vinculada a uma ferramenta específica porque oferece uma estrutura de raciocínio aplicável a diferentes tecnologias, como SQL, Python, BigQuery, planilhas e ferramentas de BI.

### Limitação

O CRISP-DM não aprofunda todas as técnicas estatísticas ou de visualização. Essas lacunas são complementadas pelas demais fontes.

---

## 2. IBM — Dimensões da qualidade de dados

**Instituição:** IBM  
**Tema principal:** qualidade de dados  
**Formato:** página web  
**Idioma:** português  
**Acesso:** aberto  
**Data de acesso:** 28/08/2026

**URL:**  
https://www.ibm.com/br-pt/think/topics/data-quality-dimensions

### Papel no projeto

Esta fonte fundamenta a avaliação da confiabilidade dos dados antes da análise.

Entre as dimensões abordadas estão:

- precisão;
- completude;
- consistência;
- atualidade;
- validade;
- unicidade.

Esses conceitos serão utilizados para estruturar checklists, identificar riscos e justificar decisões de tratamento.

### Módulos atendidos

**Cobertura principal:**

- Módulo 3 — Qualidade dos dados.

**Cobertura complementar:**

- Módulo 2 — Entendimento dos dados;
- Módulo 4 — Preparação e transformação;
- Módulo 6 — Métricas e KPIs;
- Módulo 12 — Documentação e QA.

### Justificativa da escolha

A fonte apresenta conceitos de qualidade de forma independente de uma ferramenta específica, permitindo que sejam aplicados a diferentes bases e ambientes analíticos.

### Limitação

A fonte fornece princípios e dimensões de qualidade, mas não substitui regras de negócio específicas de cada projeto. Valores suspeitos ou incomuns deverão ser validados dentro do contexto dos dados.

---

## 3. Tableau — Good Enough to Great: A Quick Guide for Better Data Visualizations

**Instituição:** Tableau  
**Tema principal:** visualização de dados, dashboards e comunicação visual  
**Formato:** PDF oficial  
**Idioma:** inglês  
**Acesso:** aberto  
**Data de acesso:** 28/08/2026

**URL:**  
https://www.tableau.com/sites/default/files/whitepapers/goodenoughtogreat_0.pdf

### Papel no projeto

Esta fonte fundamenta a escolha e construção de visualizações, além da organização visual de dashboards.

O material aborda tópicos como:

- escolha do tipo de gráfico;
- comparação;
- distribuição;
- mapas;
- uso de cor;
- tamanho;
- texto;
- hierarquia visual;
- composição de dashboards;
- direcionamento da atenção;
- narrativa visual.

### Módulos atendidos

**Cobertura principal:**

- Módulo 8 — Visualização de dados;
- Módulo 9 — Dashboard.

**Cobertura complementar:**

- Módulo 5 — Análise exploratória;
- Módulo 10 — Insights e recomendações;
- Módulo 11 — Storytelling e comunicação.

### Justificativa da escolha

O material reúne em uma única fonte princípios de construção de gráficos e organização de dashboards, permitindo cobrir dois módulos centrais sem utilizar materiais redundantes.

Também fornece uma alternativa aberta e legítima para estudar conceitos de comunicação visual sem redistribuir livros comerciais protegidos por direitos autorais.

### Limitação

Exemplos ligados a interfaces de produtos podem envelhecer com o tempo. Os princípios de percepção visual, escolha de gráficos, legibilidade e hierarquia são mais estáveis e serão priorizados.

---

## 4. Google AI for Developers — Prompt design strategies

**Instituição:** Google  
**Tema principal:** engenharia de prompts  
**Formato:** página web  
**Idioma:** inglês  
**Acesso:** aberto  
**Data de acesso:** 28/08/2026

**URL:**  
https://ai.google.dev/gemini-api/docs/prompting-strategies

### Papel no projeto

Esta é uma fonte transversal aos 12 módulos.

Ela fundamenta como transformar tarefas analíticas em instruções claras para uma IA generativa, trabalhando elementos como:

- contexto;
- definição clara da tarefa;
- restrições;
- formato esperado da resposta;
- exemplos;
- decomposição de tarefas complexas;
- refinamento iterativo;
- avaliação das respostas.

### Aplicação no projeto

A fonte servirá de base para a futura estrutura de prompts do playbook:

> **Contexto → Objetivo → Evidências → Lacunas → Ação → Validação → Entrega**

Também será utilizada para documentar versões de prompts, falhas, refinamentos e troubleshooting.

### Módulos atendidos

Aplicação **transversal aos 12 módulos**.

### Justificativa da escolha

Foi priorizada por ser documentação oficial, atualizada e diretamente relacionada ao comportamento de modelos generativos.

### Limitação

As recomendações são gerais para interação com modelos de IA. Sua aplicação específica ao trabalho de Análise de Dados será desenvolvida e testada ao longo deste projeto.

---

## 5. NIST — Artificial Intelligence Risk Management Framework: Generative Artificial Intelligence Profile (NIST AI 600-1)

**Instituição:** National Institute of Standards and Technology — NIST  
**Tema principal:** riscos, confiabilidade, governança e validação da IA generativa  
**Formato:** publicação técnica / PDF oficial  
**Idioma:** inglês  
**Acesso:** aberto  
**Publicação:** 2024  
**Data de acesso:** 28/08/2026

**Página oficial:**  
https://www.nist.gov/publications/artificial-intelligence-risk-management-framework-generative-artificial-intelligence

### Papel no projeto

Esta fonte sustenta a camada transversal de governança do uso da IA.

É utilizada para fundamentar práticas relacionadas a:

- confiabilidade;
- confabulações e respostas não fundamentadas;
- integridade da informação;
- interação humano–IA;
- identificação de riscos;
- avaliação;
- supervisão humana;
- validação.

### Módulos atendidos

**Cobertura principal:**

- camada transversal de governança da IA;
- Módulo 12 — Documentação e QA.

**Cobertura complementar:**

- Módulo 1 — Entendimento do problema de negócio;
- Módulo 7 — Análise estatística e relações;
- Módulo 10 — Insights e recomendações;
- Módulo 11 — Storytelling e comunicação.

### Justificativa da escolha

O documento oferece uma referência institucional independente para evitar que respostas de IA sejam tratadas como evidência ou verdade sem validação.

### Limitação

É um framework amplo de gestão de riscos de IA generativa e não foi escrito especificamente para projetos de Análise de Dados. O playbook fará a adaptação desses princípios ao contexto analítico.

---

# Matriz de cobertura das fontes

| Módulo | IBM CRISP-DM | IBM Qualidade | Tableau | Google Prompts | NIST |
|---|:---:|:---:|:---:|:---:|:---:|
| 1. Problema de negócio | ● |  |  | ◐ | ◐ |
| 2. Entendimento dos dados | ● | ● |  | ◐ |  |
| 3. Qualidade dos dados | ◐ | ● |  | ◐ | ◐ |
| 4. Preparação e transformação | ● | ● |  | ◐ |  |
| 5. Análise exploratória | ● | ◐ | ◐ | ◐ |  |
| 6. Métricas e KPIs | ◐ | ◐ | ◐ | ◐ |  |
| 7. Estatística e relações | ◐ |  |  | ◐ | ● |
| 8. Visualização |  |  | ● | ◐ |  |
| 9. Dashboard |  |  | ● | ◐ |  |
| 10. Insights e recomendações | ◐ |  | ● | ◐ | ● |
| 11. Storytelling e comunicação | ◐ |  | ● | ◐ | ◐ |
| 12. Documentação e QA | ● | ● | ◐ | ◐ | ● |
| Engenharia de prompts |  |  |  | ● | ◐ |
| Governança da IA |  |  |  | ◐ | ● |

**Legenda**

- ● cobertura principal;
- ◐ cobertura complementar.

---

# Limitação identificada na cobertura

O **Módulo 7 — Análise estatística e relações** possui cobertura suficiente para o escopo deste playbook, mas não será tratado como um curso completo de estatística.

O NotebookLM poderá:

- orientar análises exploratórias;
- sugerir investigações;
- explicar conceitos;
- alertar sobre interpretações inadequadas;
- apoiar a leitura dos resultados.

Entretanto, análises estatísticas especializadas deverão utilizar referências específicas quando necessário.

Um princípio importante será mantido:

> **Correlação não implica causalidade.**

---

# Política de direitos autorais

Para preservar a legalidade e a reprodutibilidade do projeto:

- somente materiais disponibilizados legitimamente pelos autores ou instituições serão utilizados como fontes oficiais;
- PDFs comerciais obtidos de fontes de distribuição não verificadas não serão carregados no NotebookLM;
- materiais protegidos por direitos autorais não serão redistribuídos pelo GitHub;
- o repositório disponibilizará links para as fontes oficiais, e não cópias dos documentos;
- livros e outras obras comerciais poderão ser citados como referências complementares, quando pertinente, sem reprodução integral de seu conteúdo.

---

# Estratégia final

As cinco fontes selecionadas formam os seguintes pilares:

**Metodologia analítica**

+

**Qualidade e preparação dos dados**

+

**Visualização e comunicação**

+

**Engenharia de prompts**

+

**Governança e validação da IA**

Em conjunto, elas fornecem a base necessária para que o NotebookLM atue nos dois comportamentos definidos para o projeto:

- **Modo Orientador:** apoiar o analista na definição do que fazer e como estruturar uma etapa do projeto;
- **Modo Revisor:** avaliar entregas já produzidas, identificar inconsistências, lacunas e riscos e sugerir validações adicionais.

As fontes não serão tratadas como autoridades infalíveis. Sempre que houver divergência, falta de contexto ou ausência de evidência, a decisão final continuará sob responsabilidade do analista.

> **A IA pode propor, estruturar, explicar, revisar e questionar. O analista continua responsável por validar.**
