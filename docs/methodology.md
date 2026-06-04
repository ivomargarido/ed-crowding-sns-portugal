# Metodologia

## Visão geral

Este projeto segue uma abordagem exploratória e descritiva para analisar a pressão assistencial nas urgências hospitalares do SNS, com base em dados públicos agregados.

A metodologia está organizada em quatro etapas principais:

1. compreensão dos dados;
2. preparação e validação dos dados;
3. análise exploratória dos indicadores;
4. interpretação dos resultados e identificação de limitações.

---

## 1. Compreensão dos dados

Nesta etapa são analisadas as características iniciais dos datasets utilizados, incluindo:

- estrutura das tabelas;
- número de linhas e colunas;
- período temporal coberto;
- regiões e instituições disponíveis;
- indicadores presentes;
- unidade de medida de cada indicador.

O objetivo é garantir que os dados são adequados para responder à pergunta principal do projeto.

---

## 2. Preparação e validação dos dados

Nesta etapa são realizadas transformações iniciais, incluindo:

- conversão da coluna temporal para formato de data;
- renomeação de colunas para nomes mais simples;
- criação de variáveis temporais, como ano, mês e ano-mês;
- identificação de 2026 como ano parcial;
- criação de nomes curtos para os indicadores;
- verificação de duplicados;
- transformação dos dados de formato longo para formato largo;
- análise de valores em falta;
- inspeção de valores extremos.

A tabela em formato largo permite analisar os principais indicadores lado a lado para a mesma combinação de período e região.

---

## 3. Análise exploratória

A análise exploratória irá incidir sobre quatro indicadores principais:

- número estimado de episódios de urgência;
- taxa diária de atendimentos urgentes com prioridade verde ou azul;
- taxa diária de atendimentos urgentes com internamento;
- tempo médio de espera entre a triagem e a primeira observação médica.

A análise irá considerar:

- evolução temporal;
- diferenças regionais;
- relação entre volume de episódios e tempo médio de espera;
- relação entre taxa de internamento e pressão assistencial;
- identificação de períodos com valores elevados face ao histórico.

---

## 4. Interpretação dos resultados

Os resultados serão interpretados com cautela, tendo em conta que os dados são agregados e não permitem análise individual dos doentes.

A agregação Portugal Continental será usada para análise nacional, mas não será comparada diretamente com as ARS em análises regionais.

A ARS Algarve será mantida na análise, mas os seus resultados serão interpretados com cautela devido à menor cobertura de dados em alguns indicadores, especialmente no tempo médio de espera.

---

## Decisões metodológicas atuais

- O ano de 2026 será incluído como ano parcial.
- Os valores extremos serão mantidos no dataset.
- Não será feita imputação de valores em falta nesta etapa exploratória.
- Portugal Continental será tratado como agregação nacional.
- As ARS serão tratadas como agregações regionais.