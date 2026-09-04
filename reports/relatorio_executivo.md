# Relatório executivo — Pressão assistencial nas urgências do SNS em Portugal

## Enquadramento

Este projeto analisa dados públicos agregados sobre a atividade dos serviços de urgência hospitalar do Serviço Nacional de Saúde em Portugal Continental.

O objetivo é monitorizar indicadores de pressão assistencial nas urgências e testar uma primeira abordagem preditiva para o tempo médio diário de espera entre a triagem e a primeira observação médica.

O projeto não utiliza dados individuais de utentes, profissionais ou episódios clínicos identificáveis.

---

## Fonte dos dados

Os dados têm origem no Portal da Transparência do SNS, no conjunto:

**Atividade nos Cuidados Saúde Hospitalares — Monitorização Sazonal**

Foram analisados indicadores diários por região/ARS e para Portugal Continental:

- número estimado de episódios de urgência;
- atendimentos urgentes com prioridade verde ou azul por 100.000 residentes;
- taxa diária de atendimentos urgentes com internamento;
- tempo médio de espera entre a triagem e a primeira observação médica.

O período analisado decorre entre **2016-11-01 e 2026-05-09**.

---

## Projeto 1 — Monitorização da pressão assistencial

A primeira fase consistiu na preparação, validação e análise exploratória dos dados.

Foram criadas tabelas analíticas nacionais e regionais a partir do ficheiro original em formato longo. Foram também identificadas falhas de cobertura temporal, incluindo quatro datas em falta na série nacional em fevereiro de 2025.

### Principais achados

A análise mostrou variações relevantes na atividade das urgências ao longo do tempo.

Entre os anos completos, **2019 apresentou a maior média diária de episódios de urgência**, enquanto **2020 apresentou uma quebra acentuada** face ao ano anterior.

O **tempo médio de espera aumentou nos anos mais recentes**, com **2024 a apresentar o maior valor médio anual entre os anos completos**.

A comparação regional mostrou diferenças importantes entre regiões:

- a **ARS Norte** apresentou a maior média diária de episódios de urgência;
- a **ARS Lisboa e Vale do Tejo** apresentou o maior tempo médio de espera;
- a **ARS Algarve** apresentou a maior taxa de internamento;
- a **ARS Lisboa e Vale do Tejo** apresentou o maior valor do indicador de prioridade verde ou azul.

Estes resultados sugerem que a pressão assistencial não se distribui de forma homogénea no território.

---

## Projeto 2 — Previsão do tempo médio de espera

A segunda fase desenvolveu uma primeira prova de conceito preditiva para estimar o tempo médio diário de espera em Portugal Continental.

Foram criadas variáveis explicativas de calendário, lags e médias móveis, utilizando apenas informação histórica para evitar fuga de informação temporal.

A divisão treino/teste respeitou a ordem cronológica:

| Conjunto | Período | Observações |
|---|---|---:|
| Treino | 2016-11-29 a 2024-12-31 | 2955 |
| Teste | 2025-01-01 a 2026-05-09 | 462 |

Foram avaliados modelos baseline e modelos supervisionados de regressão.

### Resultados dos modelos

| Modelo | MAE | RMSE |
|---|---:|---:|
| Regressão linear | 4,43 | 6,05 |
| Ridge Regression | 4,59 | 6,25 |
| Random Forest | 4,65 | 6,33 |
| Baseline média 7 dias | 6,01 | 7,86 |
| Baseline dia anterior | 6,23 | 7,94 |
| Baseline semana anterior | 6,47 | 9,03 |

O melhor modelo foi a **regressão linear**, com:

- **MAE:** 4,431 minutos;
- **RMSE:** 6,050 minutos;
- **melhoria de 26,3% no MAE** face ao melhor baseline;
- **melhoria de 23,0% no RMSE** face ao melhor baseline.

A análise dos coeficientes mostrou que o principal sinal preditivo está no histórico recente do próprio tempo médio de espera, sobretudo nas médias móveis e nos valores observados em dias anteriores.

---

## Dias de maior pressão

Foi feita uma análise específica dos dias de maior pressão, definidos como dias do conjunto de teste com tempo médio de espera igual ou superior ao percentil 90 observado no treino.

| Modelo | MAE picos | RMSE picos |
|---|---:|---:|
| Regressão linear | 9,82 | 12,77 |
| Random Forest | 10,59 | 13,93 |

A regressão linear manteve melhor desempenho também nos dias de pico.

Ainda assim, os erros aumentaram nestes períodos, mostrando que a previsão de valores extremos continua a ser uma limitação relevante.

---

## Conclusões principais

Os dados públicos agregados do SNS permitem monitorizar padrões de pressão assistencial nas urgências hospitalares e identificar diferenças temporais e regionais relevantes.

A análise exploratória confirmou variações importantes no volume de episódios, tempo médio de espera, taxa de internamento e prioridade verde ou azul.

A prova de conceito preditiva mostrou que é possível estimar o tempo médio diário de espera com erro médio absoluto de aproximadamente **4,4 minutos**, melhorando claramente face a baselines simples.

Apesar do bom desempenho global, o modelo ainda tem dificuldade em prever picos abruptos de tempo de espera, que são precisamente os períodos de maior relevância operacional.

---

## Limitações

Este projeto utiliza dados públicos agregados, o que limita a profundidade da análise.

As principais limitações são:

- ausência de dados individuais de utentes;
- ausência de variáveis clínicas detalhadas;
- ausência de informação operacional sobre equipas, camas, lotação ou recursos disponíveis;
- impossibilidade de inferir causalidade;
- existência de algumas falhas temporais nos dados;
- modelos ainda não validados para utilização operacional.

---

## Valor do projeto

Este projeto demonstra um fluxo aplicado de Health Data Science com dados públicos:

- preparação e validação de dados;
- análise exploratória;
- criação de indicadores;
- comparação temporal e regional;
- engenharia de variáveis temporais;
- construção de modelos baseline;
- modelação supervisionada;
- avaliação de desempenho;
- análise de erros;
- seleção fundamentada de modelo.

---

## Próximos passos

Os próximos desenvolvimentos previstos são:

1. desenvolver um modelo de classificação para identificar dias de urgência congestionada;
2. construir um dashboard interativo com os principais indicadores;
3. explorar abordagens específicas para previsão ou deteção de picos;
4. aprofundar a análise regional;
5. avaliar novas variáveis explicativas, caso estejam disponíveis.

---

## Nota ética

Este projeto utiliza apenas dados públicos agregados.

Não são utilizados dados individuais de utentes, profissionais de saúde ou episódios clínicos identificáveis.

Os resultados devem ser interpretados como análise exploratória e prova de conceito em Health Data Science, não como ferramenta clínica ou institucional validada.