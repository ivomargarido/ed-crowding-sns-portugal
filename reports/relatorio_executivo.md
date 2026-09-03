# Relatório executivo  
## Análise exploratória da pressão assistencial nas urgências hospitalares do SNS

## Enquadramento

Este projeto analisou indicadores públicos de urgência hospitalar em Portugal Continental, com o objetivo de identificar padrões temporais e regionais associados à pressão assistencial nos serviços de urgência.

A análise foi realizada com dados públicos agregados do Portal da Transparência do SNS, no âmbito de um projeto de portefólio em Health Data Science.

O objetivo não foi avaliar desempenho clínico, qualidade assistencial ou decisões individuais, mas sim demonstrar como dados públicos podem ser utilizados para monitorizar sinais de pressão assistencial e apoiar análises operacionais futuras.

## Pergunta de análise

Como evolui a pressão assistencial nos serviços de urgência hospitalar do SNS em Portugal Continental e que indicadores públicos permitem monitorizar padrões de congestionamento ao longo do tempo e entre regiões?

## Indicadores analisados

Foram analisados quatro indicadores principais:

- número estimado de episódios de urgência;
- tempo médio de espera entre a triagem e a primeira observação médica;
- taxa diária de atendimentos urgentes com internamento;
- taxa diária de atendimentos urgentes com prioridade verde ou azul, expressa em episódios urgentes por 100.000 residentes.

## Metodologia

A análise seguiu um fluxo estruturado:

1. compreensão inicial dos dados;
2. avaliação da qualidade e cobertura temporal;
3. preparação da tabela analítica;
4. separação entre análise nacional e regional;
5. análise exploratória temporal;
6. comparação regional dos principais indicadores;
7. síntese dos achados;
8. identificação de limitações e próximos passos.

As comparações anuais foram restringidas aos anos classificados como completos, reduzindo o risco de interpretações enviesadas por anos parciais ou falhas pontuais nos dados.

## Principais achados

Entre os anos completos, 2019 apresentou a maior média diária de episódios de urgência em Portugal Continental, enquanto 2020 apresentou a menor média diária.

Apesar da redução no volume de episódios em 2020, esse ano apresentou a maior taxa média de internamento entre os anos completos analisados, sugerindo uma alteração no perfil dos episódios atendidos.

O tempo médio de espera revelou-se um dos indicadores mais relevantes para monitorizar sinais de pressão assistencial. Entre os anos completos, o maior tempo médio anual foi observado em 2024.

Na comparação regional, a ARS Norte apresentou o maior volume médio diário de episódios de urgência. Este resultado deve ser interpretado como volume absoluto de atividade, não ajustado à população servida, número de hospitais ou capacidade instalada.

A ARS Lisboa e Vale do Tejo destacou-se pelo maior tempo médio de espera e também pelo maior valor médio da taxa diária de episódios com prioridade verde ou azul por 100.000 residentes.

A ARS Algarve apresentou a maior taxa média de internamento, embora este resultado deva ser interpretado com cautela devido às limitações de cobertura identificadas para esta região em alguns indicadores.

## Valor analítico do projeto

Este projeto demonstra a capacidade de transformar dados públicos agregados numa análise estruturada, documentada e reutilizável.

Foram produzidos outputs em formato de notebook, gráficos e tabelas, permitindo que os resultados sejam reutilizados em relatório, dashboard ou análises posteriores.

A análise permite identificar períodos e regiões com sinais mais marcados de pressão assistencial, funcionando como ponto de partida para investigação operacional mais detalhada.

## Limitações

A análise utiliza dados públicos e agregados. Não existe informação ao nível do episódio individual, hospital, equipa clínica ou percurso completo do utente.

Os resultados não permitem estabelecer causalidade, avaliar decisões clínicas individuais, medir diretamente qualidade assistencial ou definir prioridades automáticas de investimento.

A comparação regional não está ajustada à população servida, número de hospitais, recursos humanos, camas disponíveis, capacidade instalada ou organização dos fluxos assistenciais.

Foram também identificadas limitações de cobertura temporal, incluindo anos parciais, falhas pontuais e menor cobertura da ARS Algarve em alguns indicadores.

## Conclusão

Os indicadores públicos analisados permitem construir uma leitura estruturada da pressão assistencial nas urgências hospitalares do SNS.

Embora a análise seja exploratória e descritiva, permite identificar padrões relevantes na evolução temporal e regional dos indicadores, contribuindo para uma base analítica que pode ser aprofundada com dados mais granulares e contextuais.

O projeto demonstra competências em preparação de dados, validação de qualidade, análise exploratória, visualização, interpretação crítica e comunicação de resultados em contexto de saúde.