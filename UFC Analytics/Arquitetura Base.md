---
Conteúdo:
tags:
  - Projects
created: 2026-05-20T09:30:00
---
### Stack recomendada

**Uma única stack, Python do começo ao fim.** Isso reduz curva de aprendizado, facilita integração entre camadas e tem ecossistema maduro para todas as etapas.

#### Coleta de dados (Ingestão)

A fonte principal é o **ufcstats.com**, que é pública e bem estruturada. Você complementa com Tapology e odds opcionalmente.

`requests` + `BeautifulSoup` ou `Playwright` para scraping dinâmico. `Scrapy` se quiser um pipeline mais robusto e agendado. Para começar rápido, existe o dataset do UFC no Kaggle já pronto com mais de 5.000 lutas.

---
#### Armazenamento

**PostgreSQL** para dados relacionais (lutadores, lutas, eventos) — rode local com Docker. **DuckDB** ou arquivos **Parquet** para a feature store analítica, pois são extremamente rápidos para queries colunares sem precisar de servidor.

#### Transformação e Feature Engineering

`Pandas` ou `Polars` (mais rápido) para limpeza e criação de features. As features mais preditivas em literatura de MMA são diferença de alcance, win rate nos últimos 3 anos, acurácia de strikes, takedown defense e nível de oponentes passados (Elo-like rating).

`Great Expectations` para validação de qualidade dos dados antes de treinar.

---
#### Machine Learning

|Modelo|Quando usar|
|---|---|
|`XGBoost` / `LightGBM`|Ponto de partida, melhor custo-benefício|
|`RandomForest`|Baseline, boa interpretabilidade|
|`Logistic Regression`|Benchmark simples|
|`PyTorch`|Se quiser sequência de lutas (histórico temporal)|

Para tracking de experimentos: **MLflow** (log de métricas, artefatos, versionamento de modelos). Para tuning de hiperparâmetros: **Optuna**.

Avaliação: foque em `log-loss` e `ROC-AUC` — acurácia pura engana em dados desbalanceados.

#### Produto final (API + Dashboard)

**FastAPI** para servir as predições via API REST (input: dois lutadores → output: probabilidade de vitória + features de cada um). **Streamlit** para o dashboard interativo, que é o mais rápido de desenvolver. Para deploy: **Railway** ou **Render** (gratuitos no tier inicial), com a API containerizada em **Docker**.

---
![[Pasted image 20260520213810.png]]
