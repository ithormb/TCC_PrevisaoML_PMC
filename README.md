# Previsão do volume de vendas do varejo com machine learning

Trabalho de conclusão do **MBA em Data Science e Analytics (USP/ESALQ)**.

O objetivo é prever o **volume de vendas do comércio varejista ampliado**, medido pela Pesquisa Mensal de Comércio (PMC/IBGE), a partir de **13 séries macroeconômicas** que descrevem juros, inflação, crédito, renda, emprego, câmbio e confiança.

## Por que esse problema

O volume de vendas do varejo responde ao bolso e ao humor do consumidor: quanto custa o crédito, quanto a renda rende depois da inflação e quanto as famílias já estão endividadas. Antecipar esse movimento ajuda a planejar estoque, preço e produção.

## Dados

Todas as séries são públicas, mensais ou trimestrais, a partir de janeiro de 2012.

| Arquivo | Série | Fonte | Frequência |
|---|---|---|---|
| `db_ind_rend_vol_pmc.csv` | **Alvo:** índices de receita nominal e de volume de vendas do varejo ampliado, por atividade | IBGE (PMC) | mensal |
| `db_selic_acum_mes.csv` | Selic acumulada no mês, anualizada (SGS 4189) | Banco Central | mensal |
| `db_ipca.csv` | IPCA, número-índice | IBGE | mensal |
| `db_ipp.csv` | Índice de Preços ao Produtor, indústria geral | IBGE | mensal |
| `db_saldo_credito_pf.csv` | Saldo de crédito livre a pessoas físicas (SGS 20570) | Banco Central | mensal |
| `db_endividamentodasfamilias.csv` | Endividamento das famílias, exceto habitacional (SGS 29038) | Banco Central | mensal |
| `db_indice_conf_consumidor.csv` | Índice de Confiança do Consumidor (SGS 4393) | Banco Central | mensal |
| `db_indice_conf_comer.csv` | Índice de Confiança do Varejo Ampliado (ICOM) | FGV, via Ipeadata | mensal |
| `db_ind_taxacambio.csv` | Índice da taxa de câmbio real, real/dólar | Ipeadata | mensal |
| `db_balanco_comer.csv` | Balança comercial, saldo em US$ milhões (SGS 22707) | Banco Central | mensal |
| `db_rend_mensal.csv` | Rendimento médio mensal habitual | IBGE (PNAD Contínua) | trimestre móvel |
| `db_massarendimentomensal.csv` | Massa de rendimento mensal | IBGE (PNAD Contínua) | trimestral |
| `db_taxadesemprego.csv` | Pessoas desocupadas | IBGE (PNAD Contínua) | trimestral |
| `db_pib_trim.csv` | PIB a preços de mercado, número-índice | IBGE (Contas Nacionais) | trimestral |

## Como ler os arquivos

Os arquivos vêm no formato de exportação das fontes: separador `;`, vírgula decimal e, nas tabelas do IBGE, algumas linhas de cabeçalho e rodapé.

```python
import pandas as pd

selic = pd.read_csv("db_selic_acum_mes.csv", sep=";", decimal=",")
pmc = pd.read_csv("db_ind_rend_vol_pmc.csv", sep=";", decimal=",", encoding="utf-8")
```

As séries trimestrais precisam ser levadas para a frequência mensal antes de entrar no modelo junto com as demais.

## Stack

Python · Pandas · scikit-learn · séries temporais

## Autor

**Thomas Barbosa** · [Portfólio](https://ithormb.github.io) · [LinkedIn](https://www.linkedin.com/in/thomas-barbosa-silva/)
