# Dicionário de dados

## Projeto

Monitorização da pressão assistencial nas urgências hospitalares do SNS com dados públicos.

---

## Dataset principal

### Nome original

Atividade nos Cuidados Saúde Hospitalares — Monitorização Sazonal

### Ficheiro local

`data/raw/monitorizacao_sazonal_csh_raw.csv`

### Fonte

Portal da Transparência do SNS

### Estado no projeto

Fonte principal do Projeto 1.

---

## Estrutura original do dataset

| Coluna original | Descrição | Tipo inicial |
|---|---|---|
| Período | Data/período do registo | Texto, convertido para data |
| Região/ARS | Região ou agregação territorial | Texto |
| Indicador | Nome completo do indicador | Texto |
| Valor | Valor numérico do indicador | Numérico |
| Unidade | Unidade de medida do indicador | Texto |
| ID | Identificador do registo | Texto |

---

## Colunas preparadas

| Coluna preparada | Origem | Descrição |
|---|---|---|
| periodo | Período | Data do registo em formato datetime |
| regiao_ars | Região/ARS | Região ou agregação territorial |
| indicador | Indicador | Nome completo do indicador |
| valor | Valor | Valor numérico do indicador |
| unidade | Unidade | Unidade de medida |
| id | ID | Identificador do registo |
| ano | periodo | Ano do registo |
| mes | periodo | Mês do registo |
| ano_mes | periodo | Ano e mês do registo |
| estado_ano | ano | Identifica se o ano é completo ou parcial |
| indicador_curto | indicador | Nome simplificado do indicador para análise |

---

## Indicadores principais

| Indicador original | Indicador curto | Unidade | Interpretação |
|---|---|---|---|
| Número estimado de episódios de urgência | episodios_urgencia | nº | Volume estimado de episódios de urgência |
| Taxa diária de atendimentos urgentes com prioridade verde ou azul | prioridade_verde_azul | % | Proporção de atendimentos classificados como prioridade verde ou azul |
| Taxa diária de atendimentos urgentes com internamento | taxa_internamento | % | Proporção de atendimentos urgentes que resultaram em internamento |
| Tempo médio de espera entre a triagem e a primeira observação médica (rede de urgência hospitalar) | tempo_medio_espera | minutos | Tempo médio entre a triagem e a primeira observação médica |

---

## Tabela analítica em formato largo

Foi criada uma tabela analítica em formato largo, designada no notebook como `df_wide`.

Nesta tabela, cada linha representa uma combinação de:

- período;
- região/agregação territorial;
- ano;
- mês;
- ano-mês;
- estado do ano.

Os indicadores principais passam a estar em colunas separadas:

| Coluna em `df_wide` | Descrição |
|---|---|
| episodios_urgencia | Número estimado de episódios de urgência |
| prioridade_verde_azul | Taxa diária de atendimentos urgentes com prioridade verde ou azul |
| taxa_internamento | Taxa diária de atendimentos urgentes com internamento |
| tempo_medio_espera | Tempo médio de espera entre triagem e primeira observação médica |

---

## Notas metodológicas

- O dataset original está em formato longo.
- A coluna `Período` foi convertida para formato datetime.
- Os nomes das colunas foram simplificados para facilitar a análise.
- A coluna `indicador_curto` foi criada para facilitar a transformação para formato largo.
- O ano de 2026 foi identificado como ano parcial.
- A agregação `Portugal Continental` representa o nível nacional e não deve ser comparada diretamente com as ARS.
- A ARS Algarve apresenta menor cobertura em alguns indicadores, especialmente em `tempo_medio_espera`.
- Os dados são agregados e não permitem análise individual dos doentes.