# 🔍 Detecção de Fraude em Cartão de Crédito

**Projeto de Machine Learning para identificar transações fraudulentas com alta precisão.**

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-%23F7931E.svg?style=flat&logo=scikit-learn&logoColor=white)
![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=flat&logo=pandas&logoColor=white)
![Imbalanced-learn](https://img.shields.io/badge/imbalanced--learn-007ACC?style=flat)
![GitHub](https://img.shields.io/badge/GitHub-100000?style=flat&logo=github&logoColor=white)

---

## 📋 Sobre o Projeto

Este projeto tem como objetivo desenvolver um modelo de **Machine Learning** capaz de detectar transações fraudulentas em cartões de crédito com alto recall e boa precisão, minimizando tanto a perda financeira quanto o incômodo aos clientes legítimos.

Trabalhei com o dataset clássico **Credit Card Fraud Detection** (284.807 transações), extremamente desbalanceado (apenas 0,17% de fraudes).

---

## 🎯 Problema de Negócio

- **99,83%** das transações são normais.
- Fraudes causam grandes prejuízos financeiros.
- Bloquear muitas transações legítimas prejudica a experiência do cliente.
- Necessidade de um modelo com **alto Recall** (capturar o máximo de fraudes) e **Precision** aceitável.

---

## 📊 Dataset

- **Fonte**: [Kaggle / TensorFlow](https://storage.googleapis.com/download.tensorflow.org/data/creditcard.csv)
- **Tamanho**: 284.807 transações
- **Período**: 2 dias (setembro de 2013)
- **Features**: 28 variáveis PCA (V1 a V28) + `Time` + `Amount` + `Class` (0 = normal, 1 = fraude)

---

## ⚡ Principais Desafios

- Desbalanceamento extremo (0,17% de fraudes)
- Distribuição assimétrica da variável `Amount`
- Features já anonimizadas (PCA)
- Necessidade de alta interpretabilidade e robustez

---

## 🛠️ O que Foi Feito

### 1. Análise Exploratória e Pré-processamento
- Análise do desbalanceamento
- Criação de `Amount_log` e `Amount_scaled`
- Separação estratificada dos dados

### 2. Modelagem

**Modelos testados:**
- Logistic Regression (Baseline)
- Random Forest + `class_weight='balanced'`
- **BalancedRandomForestClassifier** (melhor desempenho)
- EasyEnsembleClassifier
- Isolation Forest (detecção de anomalias)
- Threshold Tuning (0.3)

**Técnicas de Balanceamento:**
- Undersampling
- SMOTE (Oversampling)
- Class Weight
- Ensemble com undersampling

### 3. Avaliação

- **ROC Curve** e **Precision-Recall Curve**
- Foco principal na **Precision-Recall Curve** (mais adequada para dados desbalanceados)
- Ajuste de threshold para maximizar o recall sem perder muita precisão

---

## 📈 Resultados

| Modelo                              | Recall (Fraude) | Precision (Fraude) | AUC     | Comentário                  |
|-------------------------------------|-----------------|--------------------|---------|-----------------------------|
| Logistic Regression                 | 0.68            | 0.84               | 0.934   | Baseline                    |
| Logistic + Threshold 0.3            | 0.72            | 0.80               | 0.934   | Melhora no Recall           |
| RandomForest + class_weight         | **0.76**        | 0.84               | -       | Excelente equilíbrio        |
| **BalancedRandomForestClassifier**  | **0.78+**       | **0.82~**          | -       | **Melhor modelo escolhido** |

**Melhor Modelo:** `BalancedRandomForestClassifier`

**Justificativa:** Excelente recall, boa precisão, robusto e fácil de explicar em ambiente de negócio.

---

## 🧰 Tecnologias Utilizadas

- **Python 3.10+**
- Pandas, NumPy, Matplotlib, Seaborn
- Scikit-learn
- Imbalanced-learn
- XGBoost (em desenvolvimento)
- Jupyter Notebook

---
