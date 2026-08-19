# 🎓 Previsão de Desempenho Acadêmico com Machine Learning

Projeto prático de Ciência de Dados desenvolvido para seminário acadêmico, focado na previsão da nota final de estudantes (`final_exam_score`) a partir de hábitos de estudo, histórico escolar e fatores socioeconômicos, utilizando o algoritmo **Random Forest Regressor**.

---

## 📌 Visão Geral do Problema

O objetivo principal é construir um modelo preditivo capaz de identificar antecipadamente alunos em risco de baixo rendimento, permitindo intervenções pedagógicas preventivas antes do exame final.

* **Dataset:** `student_performance_dataset.csv` (1.000 registros e 12 variáveis).
* **Variável Alvo (Target):** `final_exam_score` (nota contínua de 0 a 100).
* **Tipo de Aprendizado:** Supervisionado (Regressão).

---

## 📊 Principais Descobertas da Análise Exploratória (EDA)

* **Tempo de Estudo (`study_time_hours`):** Maior impacto positivo na nota final (correlação de **0,57**).
* **Histórico Escolar (`previous_grade`):** Forte indicador de desempenho contínuo (correlação de **0,41**).
* **Frequência (`attendance_percent`):** Relevante para a consistência das notas (correlação de **0,26**).

---

## 🛠️ Arquitetura do Pipeline de Pré-processamento

Para garantir a reprodutibilidade e evitar vazamento de dados (*Data Leakage*), todo o pré-processamento foi estruturado com `sklearn.pipeline.Pipeline`:

* **Tratamento Numérico:** Imputação de nulos pela mediana + Padronização Z-score (`StandardScaler`).
* **Tratamento Categórico:** Preenchimento de valores ausentes com `'Desconhecido'` + Codificação `OneHotEncoder`.
* **Remoção de Variaveis:** Descarte de `student_id` (irrelevante) e `final_grade` (evita *Data Leakage*).
* **Divisão dos Dados:** 80% para treino (800 amostras) e 20% para teste (200 amostras).

---

## 📈 Desempenho do Modelo (Random Forest)

| Métrica | Valor | Interpretação Prática |
| :--- | :---: | :--- |
| **R² Score** | `0.565` | Explica **56,5%** da variação das notas finais dos alunos. |
| **MAE (Erro Médio Absoluto)** | `5.31` | Margem de erro média de **5,3 pontos** na previsão da nota. |
| **RMSE (Raiz do Erro Quadrático Médio)** | `6.84` | Baixa penalização para erros discrepantes. |

### Top 3 Variáveis Mais Relevantes (Feature Importance)
1. **Horas de Estudo (`study_time_hours`):** ~38,9% do peso de decisão.
2. **Nota Anterior (`previous_grade`):** ~26,7% do peso de decisão.
3. **Frequência (`attendance_percent`):** ~15,9% do peso de decisão.

---

## 📁 Estrutura do Repositório

```text
.
├── student_performance_dataset.csv   # Dataset utilizado no projeto
├── seminario_ciencia_de_dados.ipynb  # Notebook com o código dividido em 5 etapas
└── README.md                         # Documentação do repositório
