# 🥊 UFC Data Analytics & Prediction Engine

Este projeto implementa uma plataforma end-to-end de Engenharia e Análise de Dados focada no universo do MMA (UFC). O objetivo principal é capturar dados históricos e biográficos de lutadores através de APIs externas, processar e estruturar essas informações em uma pipeline de dados robusta e aplicar modelos de Machine Learning para prever o resultado de combates futuros. Como entrega de valor, o sistema gera dinamicamente infográficos no formato `.svg` com o comparativo ("Tale of the Tape") e as probabilidades da luta.

> 💡 **Princípio de Engenharia:** Dados brutos são como petróleo; não possuem valor prático até que sejam refinados. Este projeto foca intensamente na construção de pipelines que transformam registros brutos e desorganizados em ativos de inteligência limpos, estruturados e prontos para consumo.

---

## 🏗️ Arquitetura do Projeto

O sistema é dividido em duas frentes principais que operam de forma isolada, garantindo modularidade e escalabilidade:

### 1. Pipeline de ETL (Data Engineering)
Responsável por garantir a qualidade, consistência e integridade da informação:
*   **Extract:** Captura de dados brutos de eventos e lutadores via APIs externas/Scraping e armazenamento em camada *Raw*.
*   **Transform:** Limpeza de dados nulos, padronização de strings, tipagem estrita e conversão de medidas americanas para o sistema métrico ($cm$ e $kg$).
*   **Load:** Armazenamento dos dados estruturados em um banco de dados relacional (PostgreSQL/SQLite).

### 2. Pipeline de Machine Learning & Analytics (Data Science)
Responsável por gerar inteligência preditiva com base no histórico do banco de dados:
*   **Feature Engineering:** Cálculo de janelas temporais móveis (ex: sequência de vitórias, média de golpes conectados e absorvidos por minuto nas últimas lutas).
*   **Treinamento:** Pipeline automatizada de treino, validação cruzada temporal (para evitar *data leakage*) e exportação do modelo preditivo (`.pkl`).
*   **Inferência e Visualização:** Consumo do modelo treinado para calcular as probabilidades de novos confrontos e injeção dinâmica desses dados em um template `.svg`.

---

## 🛠️ Tecnologias e Ferramentas

*   **Linguagem Principal:** Python 3
*   **Engenharia de Dados:** Pandas / SQLAlchemy / Requests
*   **Machine Learning:** Scikit-Learn / XGBoost
*   **Visualização (Output):** Jinja2 / SVG Templates
*   **Banco de Dados:** PostgreSQL (ou SQLite para desenvolvimento local)

---

## 🚀 Como Executar o Projeto

*(Instruções de execução a serem adicionadas conforme o desenvolvimento avança)*
