# QA de Produção e Limitações Conhecidas

## Status

O **AI-Assisted Data Analysis Playbook** alcançou uma versão funcional e utilizável, porém permanece **em desenvolvimento**.

A versão atual foi submetida a smoke tests de produção após os experimentos T01–T03. Esses testes verificaram se a configuração pública do NotebookLM preservava os princípios de confiabilidade definidos no projeto.

> **Status atual: funcional para uso orientado, com limitações conhecidas documentadas e backlog de evolução.**

## Smoke Test 1 — Qualidade dos dados

Pergunta: "Tenho uma tabela em que order_id aparece repetido. Devo remover as duplicatas?"

Resultado:
- roteamento correto para o módulo 3;
- sem remoção automática;
- validação de granularidade antes do tratamento;
- separação entre investigação, tratamento candidato, regra e validação.

Limitação remanescente:
- exemplos de campos hipotéticos ainda podem aparecer sem rotulagem explícita em todos os trechos.

## Smoke Test 2 — Visualização

Pergunta: "Tenho oito categorias com margens positivas e negativas. Quero comparar quais apresentam melhor e pior margem. Qual gráfico devo usar?"

Resultado:
- roteamento correto para o módulo 8;
- recomendação adequada de barras horizontais;
- ordenação adequada;
- sem narrativa temporal inexistente;
- sem meta ou benchmark inventado.

Limitações remanescentes:
- a referência em zero pode não ser explicitada em todas as respostas;
- o significado de valores positivos/negativos pode ser interpretado com confiança excessiva;
- recomendações de cor podem ser prescritivas demais.

## Smoke Test 3 — Causalidade

Pergunta: "Os maiores descontos aparecem junto das menores margens. Posso concluir que o desconto causou a queda da margem?"

Resultado:
- roteamento correto para o módulo 7;
- associação diferenciada de causalidade;
- causalidade tratada como hipótese;
- necessidade de evidência adicional reconhecida.

Limitações remanescentes:
- o modelo pode confundir informação fornecida pelo usuário com informação ausente das fontes;
- pode sugerir técnicas especializadas além da cobertura metodológica das fontes;
- pode sugerir carregar dados reais no notebook, contrariando a arquitetura de execução externa.

## Limitações conhecidas da versão atual

1. O modelo continua probabilístico: as regras de prompt reduzem, mas não eliminam inferências indevidas.
2. A cobertura estatística é limitada: as cinco fontes não constituem bibliografia especializada de inferência causal ou estatística avançada.
3. O roteamento automático de módulos ainda exige validação humana.
4. Exemplos plausíveis ainda podem aparecer como contexto implícito.
5. Heurísticas de visualização podem ser tratadas com confiança excessiva.
6. O NotebookLM não é ambiente de execução analítica: SQL, Python, cálculos e BI continuam externos.
7. O notebook público não deve receber dados confidenciais ou sensíveis.
8. O projeto permanece em desenvolvimento e foi documentado para permitir novas versões e refinamentos.

## Backlog de evolução

- testar P02, P04–P07 e P09–P12;
- adicionar fonte especializada em estatística e inferência causal;
- testar Orientador e Revisor sobre o mesmo caso;
- executar teste controlado da hipótese H6;
- ampliar smoke tests;
- testar diferentes tipos de projetos de dados;
- criar novas versões apenas quando houver evidência documentada.

## Critério de conclusão da versão atual

> **As limitações precisam estar identificadas, o comportamento crítico precisa estar controlado e o processo de evolução precisa estar documentado.**

A versão atual atende a esse critério.

> **A IA ajuda a pensar, mas a evidência continua decidindo.**
