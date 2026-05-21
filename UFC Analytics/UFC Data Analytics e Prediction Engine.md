### 1. Visão Geral

O objetivo é construir um pipeline de dados ponta-a-ponta que extraia informações de lutadores e eventos de APIs externas, processe esses dados para gerar insights estatísticos e utilize modelos de Machine Learning e analise de dados para prever o vencedor de combates futuros. O "produto" final para o usuário será um relatório visual gerado dinamicamente.

### 2. Arquitetura Proposta

Para garantir que seu projeto cubra Engenharia e Análise, a estrutura deve seguir este fluxo:

1. **Ingestão:** Scripts Python consumindo APIs (ex: FightMetric, UFC API oficial ou scraping via Beautiful Soup/Selenium).

2. **Processamento (ETL):** Limpeza de dados nulos, normalização de nomes e conversão de unidades (pés/polegadas para cm).

3. **Análise e ML:** Criação de features (ex: "média de knockdowns nas últimas 3 lutas") e treinamento do modelo.

---
### 3. Requisitos do Sistema

#### **Requisitos Funcionais (RF)**

- **RF01:** O sistema deve coletar dados históricos de lutas e perfis de lutadores.
    
- **RF02:** O sistema deve calcular métricas de performance (Striking Accuracy, Grappling Rate, etc.).
    
- **RF03:** O sistema deve prever a probabilidade de vitória de cada lutador em um confronto específico.
    
- **RF04:** O sistema deve exportar um infográfico em `.svg` contendo o "Tale of the Tape" (comparativo físico) e a probabilidade calculada.

#### **Requisitos Não-Funcionais (RNF)**

- **RNF01:** O processamento de dados deve ser idempotente (rodar várias vezes sem duplicar dados).
    
- **RNF02:** O modelo de predição deve ter uma acurácia mínima alvo (ex: 50%, dado que lutas são imprevisíveis).
    
- **RNF03:** O código deve ser modular e documentado.