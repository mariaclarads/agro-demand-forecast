# Previsão de Demanda de Defensivos Agrícolas
### Reduzindo perdas por excesso de estoque na revenda agrícola com Machine Learning

![Python](https://img.shields.io/badge/Python-3.10+-blue?logo=python&logoColor=white)
![Status](https://img.shields.io/badge/Status-Em%20Desenvolvimento-yellow)
![Área](https://img.shields.io/badge/Área-Agronegócio-green)
![ML](https://img.shields.io/badge/ML-Séries%20Temporais-orange)

---

## Contexto do Problema

Revendas agrícolas frequentemente antecipam compras de defensivos com base na expectativa de demanda — como inseticidas para cigarrinha-do-milho na safrinha. Quando a demanda não se concretiza, o estoque fica parado, gerando capital imobilizado, risco de vencimento dos produtos e pressão nas margens.

Um documento comercial real de devolução de estoque revelou que a queda de demanda teve causas concretas e mensuráveis:

- Chuva excessiva no período de plantio dificultou a germinação — o produtor não conseguiu plantar e não precisou de defensivo
- Seca no enchimento de grãos reduziu a produtividade — colheita ruim deixou o produtor sem caixa para investir na safra seguinte

Isso mostrou que prever a demanda de defensivos vai além do histórico de vendas. É preciso considerar o que aconteceu na lavoura.

---

## Objetivo

Prever a demanda de defensivos agrícolas com 60 a 90 dias de antecedência, incorporando variáveis climáticas, índice ENSO e produtividade regional, para que a revenda calibre o pedido antes de cada safra e evite excesso de estoque.

---

## O que diferencia este projeto

A maioria dos projetos de previsão de demanda usa apenas histórico de vendas. Este projeto incorpora variáveis que explicam *por que* a demanda cai — não só *quando* ela cai:

| Variável | Lógica de negócio |
|---|---|
| Precipitação no plantio | Chuva excessiva impede germinação — produtor não planta, não compra defensivo |
| Déficit hídrico no enchimento | Seca reduz produtividade — colheita ruim deixa o produtor sem caixa |
| Índice ENSO (El Niño / La Niña) | Antecipa o padrão climático com 3 a 6 meses de antecedência |
| Produtividade regional (sc/ha) | Safra ruim no ano anterior reduz a capacidade de compra na safra seguinte |
| Preço do milho | Preço alto melhora a margem do produtor e aumenta o investimento em defensivos |

---

## Estrutura do Repositório

```
agro-demand-forecast/
│
├── data/
│   ├── processed/        <- dados tratados e prontos para modelagem
│   └── external/         <- fontes públicas: CONAB, INMET, CEPEA, NOAA
│
├── notebooks/
│   ├── 01_EDA.ipynb                  <- análise exploratória
│   ├── 02_feature_engineering.ipynb  <- criação de variáveis
│   ├── 03_modeling.ipynb             <- treinamento dos modelos
│   └── 04_evaluation.ipynb           <- avaliação e comparação
│
├── src/
│   ├── data_prep.py
│   ├── features.py
│   └── model.py
│
├── dashboard/
│   └── app.py            <- dashboard em Streamlit
│
├── requirements.txt
└── README.md
```

---

## Metodologia

O projeto segue a metodologia CRISP-DM: entendimento do problema de negócio, análise exploratória dos dados, preparação e enriquecimento com variáveis externas, modelagem, avaliação e implantação via dashboard interativo.

---

## Fontes de Dados

| Fonte | Dado | Link |
|---|---|---|
| ERP interno | Histórico de vendas por produto e nota fiscal | — |
| INMET | Precipitação, temperatura e umidade mensais | bdmep.inmet.gov.br |
| NOAA | Índice ENSO (ONI) — El Niño e La Niña | psl.noaa.gov |
| CONAB | Produtividade do milho por estado e safra | conab.gov.br |
| CEPEA/ESALQ | Preço mensal do milho | cepea.esalq.usp.br |

---

## Modelos

| Modelo | Justificativa |
|---|---|
| Prophet | Baseline robusto para sazonalidade agrícola e calendário de safra |
| XGBoost | Incorpora todas as variáveis externas — clima, ENSO, produtividade e preço |

---

## Métricas de Avaliação

| Métrica | Descrição | Meta |
|---|---|---|
| MAPE | Erro percentual médio absoluto | < 20% |
| RMSE | Raiz do erro quadrático médio | Minimizar |
| Fill Rate | Percentual da demanda atendida sem ruptura | > 90% |

---

## Como Executar

```bash
git clone https://github.com/mariaclarads/agro-demand-forecast.git
cd agro-demand-forecast

python -m venv venv
source venv/bin/activate  # Mac/Linux
venv\Scripts\activate     # Windows

pip install -r requirements.txt

jupyter notebook notebooks/

# Dashboard
streamlit run dashboard/app.py
```

---

## Tecnologias

![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?logo=pandas&logoColor=white)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-F7931E?logo=scikit-learn&logoColor=white)
![XGBoost](https://img.shields.io/badge/XGBoost-FF6600)
![Streamlit](https://img.shields.io/badge/Streamlit-FF4B4B?logo=streamlit&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626?logo=jupyter&logoColor=white)

---

---

## Autor

**Maria Clara**
LinkedIn: [linkedin.com/in/seu-perfil](https://linkedin.com/in/seu-perfil)
GitHub: [github.com/mariaclarads](https://github.com/mariaclarads)

---

## Licença

Este projeto está sob a licença MIT. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.
