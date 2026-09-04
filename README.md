# Pressão assistencial nas urgências do SNS em Portugal

Este repositório reúne um conjunto de projetos de análise de dados sobre a pressão assistencial nos serviços de urgência hospitalar do Serviço Nacional de Saúde em Portugal Continental.

O trabalho parte de dados públicos agregados e tem como objetivo demonstrar um fluxo de análise em Health Data Science, desde a preparação dos dados até à monitorização de indicadores e construção de modelos preditivos simples.

Este projeto não utiliza dados individuais de utentes, profissionais ou episódios clínicos.

---

## Objetivo geral

Analisar a evolução da pressão assistencial nas urgências hospitalares do SNS em Portugal Continental e explorar indicadores públicos que permitam monitorizar padrões de congestionamento ao longo do tempo.

O projeto tem também uma componente preditiva inicial, procurando estimar o tempo médio diário de espera entre a triagem e a primeira observação médica.

---

## Fonte dos dados

Os dados utilizados têm origem no Portal da Transparência do SNS, no conjunto de dados:

**Atividade nos Cuidados Saúde Hospitalares — Monitorização Sazonal**

Os dados encontram-se em formato agregado e incluem indicadores diários por região/ARS e para Portugal Continental.

Indicadores utilizados:

- número estimado de episódios de urgência;
- taxa diária de atendimentos urgentes com prioridade verde ou azul;
- taxa diária de atendimentos urgentes com internamento;
- tempo médio de espera entre a triagem e a primeira observação médica.

---

## Estrutura do repositório

```text
ed-crowding-sns-portugal/
│
├── data/
│   ├── raw/
│   │   └── monitorizacao_sazonal_csh_raw.csv
│   │
│   └── processed/
│       ├── monitorizacao_sazonal_csh_wide.csv
│       ├── monitorizacao_sazonal_csh_nacional.csv
│       └── monitorizacao_sazonal_csh_regional.csv
│
├── notebooks/
│   ├── 01_eda_monitorizacao_urgencias_sns.ipynb
│   └── 02_previsao_tempo_medio_espera_sns.ipynb
│
├── reports/
│   ├── figures/
│   └── tables/
│       ├── projeto2_comparacao_modelos.csv
│       ├── projeto2_previsoes_modelo_final.csv
│       ├── projeto2_coeficientes_regressao_linear.csv
│       └── projeto2_metricas_dias_pico.csv
│
├── requirements.txt
└── README.md
```

---

# Projeto 1 — Análise exploratória e monitorização das urgências

## Pergunta orientadora

Como evolui a pressão assistencial nos serviços de urgência hospitalar do SNS em Portugal Continental e que indicadores públicos permitem monitorizar padrões de congestionamento ao longo do tempo e entre regiões?

---

## Objetivos do Projeto 1

O primeiro projeto teve como objetivo preparar e explorar os dados públicos de monitorização sazonal das urgências hospitalares.

Foram definidos os seguintes objetivos:

- carregar e validar os dados originais;
- normalizar nomes de colunas e indicadores;
- transformar os dados de formato longo para formato analítico;
- criar tabelas nacionais e regionais;
- avaliar a cobertura temporal dos dados;
- identificar valores em falta;
- analisar a evolução dos principais indicadores ao longo do tempo;
- comparar padrões nacionais e regionais.

---

## Preparação dos dados

O ficheiro original foi carregado a partir da pasta `data/raw/`.

A estrutura original dos dados encontrava-se em formato longo, com as seguintes colunas principais:

- `Período`;
- `Região/ARS`;
- `Indicador`;
- `Valor`;
- `Unidade`;
- `ID`.

Após a preparação, os indicadores foram reorganizados em formato largo, permitindo uma leitura analítica mais direta.

Foram criadas três tabelas principais:

- `monitorizacao_sazonal_csh_wide.csv`;
- `monitorizacao_sazonal_csh_nacional.csv`;
- `monitorizacao_sazonal_csh_regional.csv`.

---

## Indicadores analisados

Foram analisados quatro indicadores principais:

| Indicador tratado | Descrição |
|---|---|
| `episodios_urgencia` | Número estimado de episódios de urgência |
| `prioridade_verde_azul` | Atendimentos urgentes com prioridade verde ou azul por 100.000 residentes |
| `taxa_internamento` | Percentagem de atendimentos urgentes com internamento |
| `tempo_medio_espera` | Tempo médio de espera entre triagem e primeira observação médica |

---

## Cobertura temporal

O período global analisado vai de:

```text
2016-11-01 a 2026-05-09
```

A série nacional apresenta quatro datas em falta:

```text
2025-02-04
2025-02-05
2025-02-06
2025-02-07
```

No Projeto 1, estes valores em falta foram identificados e documentados, mas não foram imputados.

---

## Principais resultados do Projeto 1

### Evolução dos episódios de urgência

Nos anos completos, o maior valor médio diário de episódios de urgência ocorreu em 2019.

Em 2020 observou-se uma quebra acentuada face a 2019, compatível com uma alteração estrutural do padrão de utilização dos serviços de urgência durante esse período.

---

### Tempo médio de espera

O tempo médio de espera apresentou variação relevante ao longo do período analisado.

Entre os anos completos, 2024 apresentou o maior valor médio anual de tempo de espera, enquanto 2020 apresentou o menor valor médio anual.

A análise mensal mostrou também picos importantes, nomeadamente em períodos de maior pressão assistencial.

---

### Taxa de internamento

A taxa diária de atendimentos urgentes com internamento também apresentou variações relevantes ao longo do tempo.

Entre os anos completos, 2020 destacou-se com a maior média anual da taxa de internamento.

---

### Prioridade verde ou azul

O indicador de atendimentos urgentes com prioridade verde ou azul foi analisado como episódios por 100.000 residentes.

Este indicador não deve ser interpretado como percentagem.

---

### Comparação regional

A análise regional mostrou diferenças relevantes entre regiões.

Entre os anos completos:

- a ARS Norte apresentou a maior média diária de episódios de urgência;
- a ARS Lisboa e Vale do Tejo apresentou o maior tempo médio de espera;
- a ARS Algarve apresentou a maior taxa de internamento;
- a ARS Lisboa e Vale do Tejo apresentou o maior valor do indicador de prioridade verde ou azul.

Estas diferenças sugerem que a pressão assistencial não se distribui de forma homogénea no território.

---

## Conclusão do Projeto 1

O Projeto 1 demonstrou que os dados públicos do SNS permitem monitorizar a pressão assistencial nas urgências hospitalares através de indicadores agregados.

A análise permitiu identificar padrões temporais, diferenças regionais, períodos de maior pressão e limitações relacionadas com cobertura temporal e valores em falta.

Este projeto serviu como base para os projetos seguintes, nomeadamente para a modelação preditiva do tempo médio de espera.

---

# Projeto 2 — Previsão do tempo médio de espera

## Pergunta orientadora

É possível prever o tempo médio diário de espera entre a triagem e a primeira observação médica nas urgências hospitalares do SNS em Portugal Continental usando apenas informação histórica e variáveis de calendário?

---

## Objetivos do Projeto 2

O segundo projeto teve como objetivo desenvolver uma primeira abordagem preditiva para estimar o tempo médio diário de espera.

O objetivo não foi criar uma ferramenta clínica final, mas sim demonstrar um fluxo técnico rigoroso de modelação preditiva aplicado a dados públicos agregados.

Foram definidos os seguintes objetivos:

- preparar a série temporal nacional;
- criar uma estrutura diária contínua;
- criar variáveis explicativas sem fuga de informação temporal;
- definir baselines simples;
- treinar modelos supervisionados de regressão;
- avaliar os modelos com métricas apropriadas;
- analisar os erros globais e os erros em dias de maior pressão;
- selecionar o melhor modelo candidato.

---

## Variável-alvo

A variável-alvo do Projeto 2 foi:

```text
tempo_medio_espera
```

Esta variável representa o tempo médio de espera, em minutos, entre a triagem e a primeira observação médica.

A unidade de análise foi o dia, considerando apenas o agregado nacional de Portugal Continental.

---

## Preparação da série temporal

A série nacional foi ordenada cronologicamente e reindexada para uma frequência diária contínua.

As quatro datas em falta em fevereiro de 2025 foram mantidas como valores nulos numa fase inicial. Posteriormente, as linhas sem informação suficiente para modelação foram removidas após a criação de lags e médias móveis.

A tabela final de modelação ficou com:

```text
3417 observações
22 variáveis explicativas
```

---

## Variáveis explicativas

Foram criadas variáveis de calendário e variáveis históricas.

Variáveis de calendário:

- ano;
- mês;
- dia da semana;
- dia do mês;
- dia do ano;
- semana do ano;
- indicador de fim de semana.

Variáveis históricas:

- lags de 1, 7 e 14 dias do tempo médio de espera;
- lags de 1, 7 e 14 dias dos episódios de urgência;
- lags de 1, 7 e 14 dias da prioridade verde ou azul;
- lags de 1, 7 e 14 dias da taxa de internamento;
- médias móveis de 7, 14 e 28 dias do tempo médio de espera.

Para evitar fuga de informação, não foram usados valores do próprio dia para prever o tempo médio de espera desse mesmo dia.

---

## Divisão temporal treino/teste

A divisão entre treino e teste respeitou a ordem temporal dos dados.

```text
Treino: 2016-11-29 a 2024-12-31
Teste: 2025-01-01 a 2026-05-09
```

Dimensões:

```text
Linhas de treino: 2955
Linhas de teste: 462
```

Esta abordagem simula um cenário mais realista, em que o modelo é treinado com dados históricos e avaliado em períodos futuros.

---

## Modelos avaliados

Foram avaliados modelos baseline e modelos supervisionados de regressão.

Modelos baseline:

- previsão pelo valor do dia anterior;
- previsão pelo valor da semana anterior;
- previsão pela média móvel dos 7 dias anteriores.

Modelos supervisionados:

- regressão linear;
- Random Forest Regressor;
- Ridge Regression.

---

## Métricas utilizadas

Foram utilizadas duas métricas principais:

| Métrica | Interpretação |
|---|---|
| MAE | Erro médio absoluto, em minutos |
| RMSE | Erro quadrático médio, penaliza mais erros elevados |

O MAE foi usado como principal critério de seleção, por ser diretamente interpretável no contexto do tempo médio de espera.

---

## Resultados dos modelos

A comparação final dos modelos foi a seguinte:

| Modelo | MAE | RMSE |
|---|---:|---:|
| Regressão linear | 4,43 | 6,05 |
| Ridge Regression | 4,59 | 6,25 |
| Random Forest | 4,65 | 6,33 |
| Baseline média 7 dias | 6,01 | 7,86 |
| Baseline dia anterior | 6,23 | 7,94 |
| Baseline semana anterior | 6,47 | 9,03 |

O melhor baseline foi a média móvel dos 7 dias anteriores.

O melhor modelo supervisionado foi a regressão linear.

---

## Modelo final selecionado

O modelo final selecionado foi:

```text
Regressão linear
```

Resultados no conjunto de teste:

```text
MAE: 4,431 minutos
RMSE: 6,050 minutos
```

Melhoria face ao melhor baseline:

```text
Melhoria no MAE: 26,3%
Melhoria no RMSE: 23,0%
```

Estes resultados indicam que a utilização de variáveis históricas e de calendário acrescentou valor face a uma regra simples baseada apenas na média dos 7 dias anteriores.

---

## Análise dos erros

A análise dos erros mostrou que a regressão linear apresentou bom desempenho global, mas manteve dificuldade em prever picos abruptos do tempo médio de espera.

Os maiores erros ocorreram em períodos específicos, nomeadamente no início de janeiro de 2025 e no final de dezembro de 2025/início de janeiro de 2026.

Esta limitação é relevante porque os dias com maior pressão assistencial são precisamente os mais importantes do ponto de vista operacional.

---

## Avaliação em dias de maior pressão

Foi realizada uma análise específica dos dias de maior pressão.

Foram considerados dias de pico os dias do conjunto de teste em que o tempo médio de espera foi igual ou superior ao percentil 90 observado no conjunto de treino.

Resultados nos dias de pico:

| Modelo | MAE global | RMSE global | MAE picos | RMSE picos |
|---|---:|---:|---:|---:|
| Regressão linear | 4,43 | 6,05 | 9,82 | 12,77 |
| Random Forest | 4,65 | 6,33 | 10,59 | 13,93 |

Nos dias de pico:

```text
Regressão linear com menor erro: 18 dias
Random Forest com menor erro: 13 dias
```

A Random Forest teve melhor desempenho em alguns dias de pico específicos, mas não melhorou o desempenho global nem o desempenho agregado nos dias de maior pressão.

---

## Interpretação do modelo final

A análise dos coeficientes da regressão linear mostrou que as variáveis mais relevantes estão sobretudo relacionadas com o histórico recente do próprio tempo médio de espera.

As variáveis com maior peso relativo foram:

- média móvel dos 7 dias anteriores do tempo médio de espera;
- média móvel dos 14 dias anteriores;
- valor do tempo médio de espera no dia anterior;
- variáveis de calendário, como mês, dia do ano e dia da semana.

Este resultado reforça que o principal sinal preditivo está na memória recente da série temporal.

A interpretação dos coeficientes deve ser feita com cautela, porque várias variáveis estão correlacionadas entre si, especialmente os lags e as médias móveis.

---

## Conclusão do Projeto 2

O Projeto 2 demonstrou que é possível construir uma primeira abordagem preditiva para o tempo médio diário de espera nas urgências hospitalares do SNS em Portugal Continental usando dados públicos agregados.

A regressão linear foi o melhor modelo candidato, superando os baselines, o Random Forest e a Ridge Regression.

O modelo final obteve um erro médio absoluto de aproximadamente 4,4 minutos no conjunto de teste, representando uma melhoria de 26,3% face ao melhor baseline.

Apesar do desempenho global positivo, o modelo apresenta limitações relevantes, sobretudo na previsão de picos abruptos de tempo médio de espera.

Assim, este projeto deve ser interpretado como uma prova de conceito preditiva e não como uma ferramenta final de apoio à decisão.

---

# Limitações gerais

Este repositório utiliza dados públicos agregados, o que impõe limitações importantes:

- não existem dados ao nível individual do utente;
- não existem dados clínicos detalhados;
- não existem variáveis sobre recursos disponíveis, como equipas, camas, lotação ou tempos por etapa do circuito;
- não é possível avaliar causas diretas dos aumentos do tempo de espera;
- a análise é limitada aos indicadores públicos disponíveis;
- alguns períodos apresentam falhas de dados;
- os modelos preditivos não devem ser interpretados como ferramentas clínicas validadas.

Estas limitações não invalidam o projeto, mas definem claramente o seu âmbito.

---

# Próximos desenvolvimentos

Os próximos passos previstos incluem:

1. desenvolver um modelo de classificação para identificar dias de urgência congestionada;
2. construir um dashboard interativo com os principais indicadores;
3. explorar modelos específicos para deteção de picos;
4. aprofundar a análise regional;
5. avaliar novas variáveis explicativas, caso estejam disponíveis;
6. preparar uma camada futura com dados internacionais mais detalhados, como bases clínicas abertas.

---

# Tecnologias utilizadas

O projeto foi desenvolvido em Python, com recurso a bibliotecas comuns em análise de dados e Machine Learning:

- pandas;
- matplotlib;
- scikit-learn;
- pathlib.

Ambiente de desenvolvimento:

- Python;
- Jupyter Notebook;
- Visual Studio Code;
- GitHub.

---

# Como reproduzir

1. Clonar o repositório.

2. Entrar na pasta do projeto:

```bash
cd ed-crowding-sns-portugal
```

3. Criar e ativar ambiente virtual:

```bash
python -m venv .venv
```

No Windows:

```bash
.venv\Scripts\activate
```

4. Instalar dependências:

```bash
pip install -r requirements.txt
```

5. Executar os notebooks pela ordem:

```text
01_eda_monitorizacao_urgencias_sns.ipynb
02_previsao_tempo_medio_espera_sns.ipynb
```

---

# Nota ética

Este projeto utiliza apenas dados públicos agregados.

Não são utilizados dados individuais de utentes, profissionais de saúde ou episódios clínicos identificáveis.

Os resultados devem ser interpretados como análise exploratória e prova de conceito em Health Data Science, não como instrumento final de avaliação clínica, institucional ou profissional.

---

# Autor

Projeto desenvolvido por Ivo Margarido.

Enfermeiro em transição para a área de Health Data Science, com interesse na utilização de dados para melhorar a visibilidade, a qualidade e a segurança dos cuidados de saúde.