# Previsão de Demanda de Defensivos Agrícolas
### Reduzindo perdas por excesso de estoque na revenda agrícola com Machine Learning

![Python](https://img.shields.io/badge/Python-3.10+-blue?logo=python&logoColor=white)
![Status](https://img.shields.io/badge/Status-Em%20Desenvolvimento-yellow)
![Área](https://img.shields.io/badge/Área-Agronegócio-green)
![ML](https://img.shields.io/badge/ML-Séries%20Temporais-orange)

---

## Contexto do Problema

Revendas agrícolas frequentemente antecipam compras de defensivos com base na expectativa de demanda — como inseticidas para cigarrinha-do-milho na safrinha. Quando a demanda não se concretiza, o estoque fica parado, gerando capital imobilizado, risco de vencimento dos produtos e pressão nas margens por descontos forçados.

> *"A revenda puxou para demanda de cigarrinha no milho safrinha e está sobrando no estoque. Pouca incidência."*  
> — Justificativa comercial real que motivou este projeto

---

## Objetivo

Desenvolver um modelo de previsão de demanda para produtos fitossanitários, incorporando variáveis como calendário agrícola (safra/safrinha), condições climáticas da região, preço da commodity (milho) e histórico de incidência de pragas.

---

## Estrutura do Repositório

```
demand-forecast-agro/
│
├── data/
│   ├── raw/              # Dados brutos (vendas, clima, CONAB)
│   ├── processed/        # Dados tratados e prontos para modelagem
│   └── external/         # Fontes externas: INMET, CEPEA, CONAB
│
├── notebooks/
│   ├── 01_EDA.ipynb
│   ├── 02_feature_engineering.ipynb
│   ├── 03_modeling.ipynb
│   └── 04_evaluation.ipynb
│
├── src/
│   ├── data_prep.py
│   ├── features.py
│   ├── model.py
│   └── predict.py
│
├── dashboard/
├── requirements.txt
└── README.md
```

---

## Metodologia

O projeto segue a metodologia CRISP-DM: entendimento do negócio, análise exploratória dos dados, preparação, modelagem, avaliação e implantação via dashboard.

---

## Fontes de Dados

| Fonte | Tipo de Dado |
|---|---|
| ERP interno | Histórico de vendas por produto e nota fiscal |
| CONAB | Área plantada por cultura e região |
| INMET | Dados climáticos históricos |
| CEPEA/ESALQ | Preço do milho |
| Embrapa | Incidência de pragas por safra |

---

## Modelos

| Modelo | Justificativa |
|---|---|
| SARIMA | Baseline com sazonalidade explícita |
| Prophet | Robusto para sazonalidade múltipla e calendário agrícola |
| XGBoost | Incorpora variáveis externas como clima e preço de commodity |

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
git clone https://github.com/seu-usuario/demand-forecast-agro.git
cd demand-forecast-agro

python -m venv venv
source venv/bin/activate  # Linux/Mac
venv\Scripts\activate     # Windows

pip install -r requirements.txt

jupyter notebook notebooks/

# Dashboard (opcional)
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

## Roadmap

- [x] Definição do problema de negócio
- [x] Estrutura do repositório
- [ ] Coleta e limpeza dos dados históricos
- [ ] Análise Exploratória (EDA)
- [ ] Feature Engineering
- [ ] Treinamento e avaliação dos modelos
- [ ] Dashboard interativo em Streamlit

---

## Autor

**[Maria Clara Gonçalves]**  
LinkedIn: www.linkedin.com/in/maria-clara-gonçalves-50b22b2bb
GitHub: https://github.com/mariaclarads/agro-demand-forecast/edit/main/README.md

---

## Licença

Este projeto está sob a licença MIT. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.
