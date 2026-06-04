# Limitações

## Limitações gerais dos dados

Este projeto utiliza dados públicos agregados do SNS. Estes dados são úteis para análise operacional e monitorização, mas têm limitações importantes.

Os dados não permitem análise individual dos doentes, nem permitem avaliar diretamente resultados clínicos, diagnósticos, gravidade individual, consumo de recursos ou qualidade dos cuidados prestados.

---

## Dados agregados

A unidade de análise é agregada por período, região e indicador.

Isto significa que não é possível saber:

- quantos doentes esperaram acima de determinado tempo;
- qual foi a distribuição real dos tempos de espera;
- quais foram os diagnósticos dos episódios;
- que doentes foram internados;
- que doentes tiveram agravamento clínico;
- que recursos estavam disponíveis em cada período.

Por este motivo, as conclusões devem ser interpretadas como padrões agregados de monitorização, e não como inferências clínicas individuais.

---

## Tempo médio de espera

O indicador de tempo médio de espera entre triagem e primeira observação médica é uma métrica central deste projeto, mas apresenta limitações.

A média pode esconder situações extremas. Por exemplo, dois períodos podem ter o mesmo tempo médio, mas distribuições muito diferentes de espera.

Sem dados individuais ou percentis, não é possível avaliar:

- quantos doentes esperaram muito acima da média;
- a mediana do tempo de espera;
- a proporção de doentes observados dentro do tempo recomendado pela prioridade de triagem;
- a variabilidade individual da espera.

---

## Comparação entre regiões

As ARS representam agregações regionais e podem ter perfis assistenciais diferentes.

Comparações diretas entre regiões devem ser interpretadas com cautela, porque os dados disponíveis não ajustam para:

- dimensão populacional;
- envelhecimento da população;
- número de hospitais;
- capacidade instalada;
- número de profissionais;
- disponibilidade de camas;
- case-mix dos doentes;
- pressão nos cuidados de saúde primários;
- diferenças locais de acesso aos cuidados.

Assim, este projeto não pretende classificar regiões como “melhores” ou “piores”.

---

## Portugal Continental

A categoria `Portugal Continental` representa uma agregação nacional.

Por esse motivo, não deve ser comparada diretamente com as ARS em análises regionais, rankings ou comparações de volume.

Neste projeto, `Portugal Continental` será usada apenas para análise nacional, enquanto as ARS serão usadas para análise regional.

---

## ARS Algarve

A análise inicial identificou menor cobertura de dados na ARS Algarve em alguns indicadores, especialmente no indicador `tempo_medio_espera`.

Após a transformação para formato largo, os valores em falta ficaram concentrados na ARS Algarve:

- `prioridade_verde_azul`;
- `taxa_internamento`;
- `tempo_medio_espera`.

Além disso, vários valores extremos relevantes também ocorreram na ARS Algarve.

Por este motivo, os resultados regionais envolvendo a ARS Algarve serão interpretados com cautela.

---

## Ano de 2026

O ano de 2026 está incluído no projeto por representar a informação mais recente disponível.

No entanto, 2026 é um ano parcial, uma vez que os dados disponíveis terminam em maio de 2026.

Assim, 2026 não deve ser comparado diretamente com anos completos em análises anuais. Sempre que necessário, será identificado como ano parcial ou analisado apenas em comparações de períodos equivalentes.

---

## Causalidade

Este projeto tem natureza exploratória e descritiva.

As análises podem identificar associações entre indicadores, como volume de episódios, tempo médio de espera, taxa de internamento e prioridade de triagem.

No entanto, estas associações não devem ser interpretadas como relações causais.

Por exemplo, um aumento do volume de atendimentos pode estar associado a maior tempo médio de espera, mas os dados disponíveis não permitem concluir que o volume causou diretamente o aumento da espera.

---

## Triagem e baixa prioridade

A proporção de episódios com prioridade verde ou azul pode ajudar a caracterizar o perfil da procura.

No entanto, este indicador não deve ser interpretado automaticamente como uso inadequado da urgência.

Episódios de menor prioridade podem estar associados a múltiplos fatores, incluindo acesso a cuidados primários, literacia em saúde, ansiedade perante sintomas, disponibilidade de alternativas assistenciais e orientação por outros serviços.

---

## Valores em falta e extremos

Nesta fase exploratória, não será feita imputação de valores em falta.

Os valores extremos serão mantidos no dataset, mas serão analisados e interpretados com cautela.

Quando necessário, serão feitas análises complementares para perceber se determinados resultados são influenciados por falhas de cobertura, valores extremos ou agregações específicas.