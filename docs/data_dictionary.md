# Dicionário de dados

## Projeto 1 — Monitorização da pressão assistencial nas urgências SNS

Este ficheiro documenta as fontes de dados, variáveis principais, significado esperado e notas metodológicas.

---

## Dataset principal

### Nome

Atividade nos Cuidados Saúde Hospitalares — Monitorização Sazonal

### Ficheiro local

data/raw/monitorizacao_sazonal_csh_raw.csv

### Fonte

Portal da Transparência do SNS

### Utilização no projeto

Este dataset será usado como fonte principal para analisar indicadores de pressão assistencial nas urgências hospitalares do SNS.

Indicadores esperados:

- episódios de urgência;
- tempo médio entre triagem e primeira observação médica;
- taxa de episódios urgentes com internamento;
- proporção de episódios com prioridade verde, azul ou branca;
- evolução temporal;
- comparação entre instituições.

---

## Variáveis principais esperadas

| Variável conceptual | Descrição | Utilização no projeto |
|---|---|---|
| Data/período | Período temporal do registo | Análise temporal e sazonalidade |
| Instituição/entidade | Hospital, centro hospitalar ou ULS | Comparação institucional |
| Região | Região de saúde, se disponível | Comparação regional |
| Episódios de urgência | Número de episódios ou atendimentos urgentes | Medir volume assistencial |
| Tempo médio de espera | Tempo médio entre triagem e primeira observação médica | Medir acesso e pressão operacional |
| Taxa de internamento | Proporção de episódios urgentes com internamento | Aproximar pressão de escoamento hospitalar |
| Baixa prioridade | Proporção de episódios com prioridade verde, azul ou branca | Caracterizar perfil da procura |

---

## Notas metodológicas

- Os dados são agregados e não permitem análise individual do doente.
- O tempo médio de espera pode esconder casos extremos.
- Comparações entre instituições devem ser interpretadas com cautela.
- A proporção de baixa prioridade não deve ser interpretada automaticamente como uso inadequado da urgência.
- O dataset bruto deve ser preservado sem alterações.