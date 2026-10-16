# impacto_cambio_renda_brasileiros-
Overview
This project examines whether and how the exchange rate (BRL/USD) affects income inequality in Brazil. Instead of looking for a direct link between the two variables, the report studies the transmission channels through which exchange rate movements reach households and workers.
Part	Topic
1	Exchange rate, inflation, and purchasing power: pass-through to the IPCA, its timing, and its impact across income brackets
2	Exchange rate, employment, and earnings in tradable sectors (Agriculture and General Industry)
3	Exchange rate and income inequality: Gini index, limits of survey data, and the price channel
Research Question
Does the exchange rate affect income inequality in Brazil, and through which channels (prices, employment, earnings) does this effect operate?
Main Findings
<details open> <summary><b>Part 1 — Prices and purchasing power</b></summary>
The exchange rate transmits to inflation with a lag. Cross-correlation is negative at lags 0 to 2 months and positive from month 3, peaking at 0.432 in month 5.
In the VAR(3), the IPCA response to an exchange rate shock peaks at +0.40 in the second quarter (about 5–6 months), with the 95% interval above zero.
Until mid-2025, lower-income brackets had higher inflation peaks (above 5.40%). In February 2026 the pattern reversed: the lowest bracket fell to 3.20% (from 4.31% in January), while the highest rose to 4.60% and reached 5.26% in May.
Comparing January–May averages of 2025 and 2026, inflation of the lowest bracket fell from 4.99% to 3.83% (-1.16 p.p.), versus 5.26% to 4.80% (-0.46 p.p.) for the highest.
Local projections indicate a food-at-home pass-through of 0.19 after 12 months and 0.37 after 24 months (BCB estimates: about 0.26 and 0.33).
</details> <details> <summary><b>Part 2 — Employment and earnings in tradable sectors</b></summary>
In 2025, Industry accounted for 77.6% of the exports of the two sectors and Agriculture for 22.4%. Imports represented 7.2% of Agriculture's trade flow and 50.3% of Industry's.
Real depreciation did not translate automatically into more jobs. In 2025 the employment index (2012 = 100) was 102.7 in Industry and 77.7 in Agriculture.
Real earnings ended 2025 about 33.2% above the 2012 average in Agriculture and 9.3% in Industry. The earnings premium of Industry over Agriculture fell from 89.6% (Q1 2012) to a low of 41.1% (Q3 2022) and ended at 48.5% (Q4 2025).
Combined employment-earnings indicator in 2025: 112.3 (Industry) and 103.6 (Agriculture). In Agriculture, higher earnings offset a deep loss of jobs.
Yearly changes in the real exchange rate and employment show no stable pattern.
Labor remained about three quarters of household income (75.7% in 2012, 75.1% in 2025), while social programs rose from 1.5% to 3.5%.
</details> <details> <summary><b>Part 3 — Inequality</b></summary>
The Gini index and the exchange rate show no stable relationship. Gini hit its lowest value in 2024 (0.506) and rose to 0.511 in 2025.
Household surveys understate the top: cumulative real growth was 5.1% for the richest 1% (PNAD) against almost 49% for the richest 0.1% (tax records).
Average real income and the exchange rate show no significant relationship.
Price channel: food inflation correlates strongly with exchange rate changes (r = 0.68, p = 0.007). Housing (r = 0.26, p = 0.39) and transport (r = 0.22, p = 0.47) do not.
Essential items take 70.6% of low-income budgets vs. 45.5% for high-income. Food alone: 22.0% vs. 7.6%.
The yearly change in the inflation gap between the lowest and highest income brackets correlates strongly with the exchange rate change (r = 0.73, p = 0.005).
</details>
Conclusion: the exchange rate does not seem to affect inequality through a direct statistical link with the Gini index. The evidence points to indirect channels, especially food prices, whose weight is larger in the budgets of poorer households.
The distinction between observed associations and causal effects is essential when interpreting these results.
Data Sources
Data	Source	Identifier / file
Dólar Ptax (daily, sell)	Banco Central do Brasil (SGS)	series 1
IPCA, monthly change	Banco Central do Brasil (SGS)	series 433
Commodities index	Banco Central do Brasil (SGS)	series 27574
IPCA by group (food, housing, transport)	IBGE via BCB (SGS)	series 3697, 1635, 1636, 1639
Employment-related series	Banco Central do Brasil (SGS)	series 11752
IPCA by income bracket	Ipea, Grupo de Conjuntura/Dimac	Ipea Inflation Indicator by Income Bracket
IPCA by group	IBGE / SIDRA	tables 1419 and 7060
Foreign trade by sector	MDIC / Comex Stat	Imp-exp-comexstat.xlsx
Employed persons by sector	IBGE / PNAD Contínua	SIDRA 4362 (Dados.sidra.xlsx)
Real earnings by sector	IBGE / PNAD Contínua	SIDRA 5442 (Dados.sidra.xlsx, Sidra.trim.trab.xlsx)
Household income composition	IBGE / PNAD Contínua	SIDRA 7429 (Composicao.renda.sidra.xlsx)
Household spending structure	IBGE, POF 2017–2018	—
Gini index	IBGE (PNAD Contínua) and Ipeadata	—
Top income growth	Receita Federal (IRPF) via FGV/IBRE	—
BCB series are downloaded through the SGS API (api.bcb.gov.br). Some figures in Part 3 are typed directly in the code, based on the sources cited in the chart captions.
Methodology
Data collection: BCB API for exchange rate and inflation; SIDRA and Comex Stat spreadsheets for labor market and trade; Ipea for inflation by income bracket.
Data preparation: monthly and quarterly aggregation, log returns (100 × log differences), quarterly IPCA by compounding, indices with 2012 = 100, and annual percentage changes.
Cross-correlation: dollar return (t) vs. IPCA (t+k), lags from -6 to +6 months.
VAR(3): quarterly exchange rate change and IPCA, orthogonalized impulse-response function (bootstrap with 1,000 runs, 95% interval, 12 quarters).
Local projections: food-at-home inflation on exchange rate and commodity changes.
   π(t,t+h) = α_h + β_h · Δln(Câmbio_t) + γ_h · Δln(Commodity_t) + ε(t+h)
Sectoral indicators: export share, import orientation, employment and earnings indices, earnings gap, and combined employment-earnings indicator with decomposition.
Inequality analysis: year-over-year correlations between exchange rate changes and Gini, average income, IPCA by group, and the inflation gap between income brackets.
Repository Structure
text
.
├── cambio-desigualdadeV2.Rmd        # Source code and report text
├── Imp-exp-comexstat.xlsx           # Comex Stat: exports and imports by sector
├── Dados.sidra.xlsx                 # SIDRA 4362 and 5442
├── Sidra.trim.trab.xlsx             # SIDRA quarterly labor data
├── Composicao.renda.sidra.xlsx      # SIDRA 7429
└── README.md

How to Reproduce
Requirements: R, RStudio (recommended), internet access, and the four Excel files above in the same folder as the .Rmd.
Clone the repository:
bash
   git clone https://github.com/SEU-USUARIO/NOME-DO-REPOSITORIO.git
Open cambio-desigualdadeV2.Rmd in RStudio.
Install the required packages:
r
   install.packages(c(
     "vars", "lmtest", "sandwich", "jsonlite", "httr", "plotly",
     "highcharter", "htmlwidgets", "readxl", "janitor", "rbcb",
     "GetBCBData", "scales", "lubridate", "tidyverse"
   ))
Click Knit to generate the HTML report.
Notes:
The document stops with a message if a package or spreadsheet is missing.
On Windows, the code creates a C:/Rtemp folder to avoid pandoc errors with accented paths.
Several chunks use the current date as the end of the sample (Sys.Date()), so results may change over time.
Limitations
Descriptive evidence alone does not establish a causal relationship between the exchange rate and inequality.
Correlations are bivariate, and annual correlations rely on few observations (about 13 years).
The VAR has two variables and the orthogonalized response depends on the variable ordering. It does not control for output gap, inflation expectations, or climate shocks.
The local projection is a simplified specification and differs moderately from BCB estimates.
The Gini index is based on PNAD Contínua, which understates top incomes, and part of the series is typed manually.
The 2020–2021 pandemic and the 2015–2016 recession dominate several of the observed movements, and the 2026 data are recent and may be revised.

Authors
João Pedro Godinho	
Giulia Loschiavo	
Maria Eduarda Gomes	
Developed at IbMacro BH.

