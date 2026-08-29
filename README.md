# AI-Assisted Data Analysis Playbook

> Um playbook para integrar Inteligência Artificial ao ciclo completo de projetos de Análise de Dados de forma crítica, estruturada e verificável.

Projeto desenvolvido no bootcamp **GenAI & Dados**, da DIO:

https://www.dio.me/bootcamp/bradesco-genai-dados

---

## Sobre o projeto

Pergunta norteadora:

> **Como estruturar o uso da IA para que ela se torne uma ferramenta confiável de apoio ao analista durante todo o ciclo de um projeto de Análise de Dados?**

A proposta não é substituir o analista.

A IA pode:

- orientar;
- propor;
- explicar;
- revisar;
- questionar.

O analista continua responsável por:

- executar;
- validar;
- interpretar;
- decidir;
- responder pela entrega.

> **A IA pode propor, estruturar, explicar, revisar e questionar. O analista continua responsável por validar.**

---

# Por que este projeto foi construído com IA

Este projeto foi propositalmente criado com **ChatGPT e NotebookLM**, porque o bootcamp trabalha o uso de IA Generativa e Prompt Engineering em cenários práticos.

A IA não foi apenas o tema: participou do processo de construção.

## ChatGPT — copiloto de construção

O ChatGPT foi utilizado para:

- decompor o desafio em etapas;
- estruturar escopo e arquitetura;
- apoiar a estratégia e curadoria de fontes;
- criar e refinar prompts;
- desenhar o experimento comparativo;
- avaliar respostas;
- identificar cicatrizes;
- consolidar aprendizados;
- redigir e revisar documentação;
- atualizar arquivos do GitHub por integração autorizada.

## NotebookLM — cérebro ancorado em fontes

O NotebookLM foi utilizado para:

- reunir cinco fontes confiáveis;
- responder com grounding e citações;
- atuar como Orientador e Revisor;
- executar testes de prompting;
- observar limites, falhas e padrões de resposta.

Foi utilizada a **versão gratuita do NotebookLM**.

## Responsabilidade humana

Nenhuma decisão foi delegada automaticamente às ferramentas.

A autora do projeto definiu objetivos, aprovou etapas, configurou o NotebookLM, executou testes, avaliou respostas, validou mudanças e manteve responsabilidade pela entrega.

### Arquitetura de colaboração

~~~text
ChatGPT
planejamento + co-criação + crítica + documentação
        │
        ▼
NotebookLM
fontes + grounding + experimentação
        │
        ▼
Analista
decisão + execução + validação + responsabilidade
~~~

---

# Arquitetura do cérebro de Análise de Dados

O playbook organiza o ciclo em 12 módulos:

1. Entendimento do problema de negócio
2. Entendimento dos dados
3. Qualidade dos dados
4. Preparação e transformação
5. Análise exploratória
6. Métricas e KPIs
7. Análise estatística e relações
8. Visualização de dados
9. Dashboard
10. Insights e recomendações
11. Storytelling e comunicação
12. Documentação e QA

Há uma camada transversal de governança e validação da IA.

**[Contexto e Objetivos](docs/01-contexto-e-objetivos.md)**

---

# Curadoria de fontes

Foram selecionadas cinco fontes abertas e complementares:

| Pilar | Fonte |
|---|---|
| Metodologia analítica | IBM — CRISP-DM / compreensão e preparação de dados |
| Qualidade de dados | IBM — Data Quality Dimensions |
| Visualização e dashboards | Tableau — Good Enough to Great |
| Engenharia de prompts | Google — Prompt Design Strategies |
| Governança de IA | NIST — Generative AI Profile |

A seleção priorizou autoridade, cobertura, aplicabilidade, acesso aberto, baixa redundância, compatibilidade com NotebookLM e origem legítima.

PDFs de livros comerciais obtidos de origem não verificável **não foram utilizados**.

**[Curadoria de Fontes](docs/02-curadoria-de-fontes.md)**

---

# Engenharia de prompts

A biblioteca inicial foi criada com 12 prompts.

O framework final é:

> **Modo → Escopo → Contexto → Evidências → Lacunas → Tarefa → Restrições epistemológicas → Fontes relevantes → Validação → Entrega**

O projeto também criou um **Bloco Transversal de Confiabilidade** para reduzir:

- invenção de colunas;
- stakeholders inexistentes;
- thresholds arbitrários;
- hipóteses apresentadas como fatos;
- causalidade indevida;
- heurísticas tratadas como regras;
- linguagem mais categórica do que a evidência permite.

**[Engenharia de Prompts](docs/03-engenharia-de-prompts.md)**  
**[Índice da Biblioteca](prompts/README.md)**

---

# Testes práticos

Foram realizados três testes comparativos com o cenário fictício **VarejoX**.

| Teste | Tema | Baseline | Prompt estruturado |
|---|---|---:|---:|
| T01 | Problema de negócio | 16/18 | 16/18 |
| T02 | Qualidade dos dados | 11/18 | 16/18 |
| T03 | Visualização | 16/18 | 17/18 |

Principais aprendizados:

- configurações globais afetam testes de prompting;
- restrições explícitas reduzem decisões arbitrárias;
- solicitar lacunas melhora o reconhecimento de informação ausente;
- formato de entrega melhora auditabilidade;
- grounding melhora factualidade, mas não garante relevância;
- gráfico correto pode ser acompanhado por conclusão incorreta;
- prompts estruturados ajudam, mas não substituem pensamento crítico.

Os testes T04 e T05 não foram executados.

**[Exemplos Práticos](examples/README.md)**  
**[Cicatrizes e Troubleshooting](docs/04-cicatrizes-e-troubleshooting.md)**

---

# Cicatrizes

Foram documentadas falhas reais observadas no uso da IA:

1. instrução global contaminando o baseline;
2. IA completando schemas com campos plausíveis;
3. restrição de decisão sem impedir inferências;
4. criação de thresholds arbitrários;
5. storytelling além da evidência;
6. heurística transformada em regra;
7. fonte correta gerando conteúdo irrelevante;
8. linguagem categórica demais.

> **Prompts estruturados tornam o trabalho da IA mais controlável e auditável, mas não eliminam a necessidade de pensamento crítico.**

---

# Uso público do NotebookLM

Para utilizar o notebook como ferramenta pública, o projeto inclui uma configuração de produção, condições de uso, prompts de início e checklist de publicação.

**[Guia de Uso Público](docs/06-guia-de-uso-publico.md)**  
**[Configuração de Produção do Chat](docs/08-configuracao-chat-producao.md)**

---

# Miniguia de estudo

A entrega consolidada contém:

- resumo do ciclo de análise assistida por IA;
- princípios de prompting;
- glossário;
- aprendizados experimentais;
- prompts reutilizáveis para revisão.

**[Abrir Miniguia de Estudo](docs/05-miniguia-de-estudo.md)**

---

# Estrutura do repositório

~~~text
ai-assisted-data-analysis-playbook/
│
├── README.md
├── LICENSE
│
├── docs/
│   ├── 01-contexto-e-objetivos.md
│   ├── 02-curadoria-de-fontes.md
│   ├── 03-engenharia-de-prompts.md
│   ├── 04-cicatrizes-e-troubleshooting.md
│   ├── 05-miniguia-de-estudo.md
│   ├── 06-guia-de-uso-publico.md
│   ├── 07-qa-producao-e-limitacoes.md
│   └── 08-configuracao-chat-producao.md
│
├── prompts/
│   └── README.md
│
├── examples/
│   └── README.md
│
└── assets/
    └── README.md
~~~

---

# Como reproduzir

1. Crie um notebook no NotebookLM.
2. Configure o idioma para Português (Brasil).
3. Adicione as cinco fontes descritas na curadoria.
4. Utilize o NotebookLM como base ancorada em fontes.
5. Escolha um prompt na biblioteca.
6. Preencha contexto, evidências e lacunas.
7. Execute análises técnicas em SQL, Python, BigQuery ou BI quando necessário.
8. Retorne resultados à IA para revisão.
9. Valide cada conclusão.
10. Documente decisões e limitações.

---

# Atendimento ao desafio da DIO

| Requisito | Onde encontrar |
|---|---|
| Contexto e objetivos | docs/01-contexto-e-objetivos.md |
| Curadoria de 3–5 fontes | docs/02-curadoria-de-fontes.md |
| Engenharia de prompts | docs/03-engenharia-de-prompts.md |
| Respostas, dificuldades e troubleshooting | docs/04-cicatrizes-e-troubleshooting.md e examples/README.md |
| Resumos estruturados | docs/05-miniguia-de-estudo.md |
| Glossário | docs/05-miniguia-de-estudo.md |
| Prompts reutilizáveis | prompts/README.md e docs/05-miniguia-de-estudo.md |
| Guia de uso público | docs/06-guia-de-uso-publico.md |

---

# Status de desenvolvimento

A versão atual é **funcional e utilizável**, mas permanece **em desenvolvimento**. O QA de produção identificou limitações conhecidas e um backlog explícito para evolução futura.

**[QA de Produção e Limitações](docs/07-qa-producao-e-limitacoes.md)**

---

# Limitações

- o NotebookLM não substitui ambientes de execução;
- somente três prompts foram avaliados comparativamente;
- o módulo estatístico não substitui bibliografia especializada;
- respostas de IA continuam sujeitas a erros, inferências e excesso de confiança;
- regras de negócio precisam de validação no contexto real;
- fontes abertas podem ser atualizadas.

---

# Tecnologias e ferramentas

- NotebookLM
- ChatGPT
- GitHub
- Prompt Engineering
- SQL, Python, BigQuery e BI como ambientes externos de execução

---

# Licença

O conteúdo original deste repositório é disponibilizado sob licença MIT.

Materiais de terceiros não são redistribuídos. O repositório mantém apenas referências e links para fontes oficiais.

---

## Conclusão

> **A IA ajuda a pensar, mas a evidência continua decidindo.**
