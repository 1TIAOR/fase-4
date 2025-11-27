# Classificação de Variedades de Grãos de Trigo
 — CRISP-DM  
Atividade da FASE 04 / CTWP / Capítulo 3

Este projeto aplica a metodologia **CRISP-DM** para desenvolver um modelo de aprendizado de máquina capaz de classificar três variedades de grãos de trigo a partir de suas características físicas.  
O objetivo é automatizar um processo que, em cooperativas agrícolas de pequeno porte, normalmente é feito manualmente e está sujeito a erros humanos.

---

## 1. Dataset Utilizado

O dataset utilizado é o **Seeds Dataset**, disponível no UCI Machine Learning Repository:

🔗 https://archive.ics.uci.edu/dataset/236/seeds

Ele contém **210 amostras** distribuídas igualmente entre três variedades de trigo:

- **1 — Kama**  
- **2 — Rosa**  
- **3 — Canadian**

### Atributos:
- area  
- perimeter  
- compactness  
- length_kernel  
- width_kernel  
- asymmetry_coeff  
- length_groove  
- class (variável alvo)

---

## 2. Metodologia (CRISP-DM)

### **2.1 Business Understanding**
A classificação automática dos grãos ajuda na padronização e eficiência do processo de seleção, reduzindo erros humanos em cooperativas agrícolas de pequeno porte.

### 2.2 Data Understanding
Foram realizadas:
- Visualização das primeiras linhas  
- Estatísticas descritivas  
- Histogramas  
- Boxplots  
- Pairplot (dispersão por classe)  
- Matriz de correlação  

Principais observações:
- As features **area**, **perimeter**, **length_kernel**, **width_kernel** e **length_groove** têm forte correlação entre si.  
- Não existem valores ausentes.  
- Há alguns outliers em *compactness* e *asymmetry_coeff*, mas não prejudicam o modelo.

### 2.3 Data Preparation
- Separação dos dados em **70% treino / 30% teste**  
- Padronização com **StandardScaler**  
- Preparação das features e do target  

---

## 3. Modelagem

Modelos testados:
- KNN  
- SVM  
- Random Forest  
- Naive Bayes  
- Logistic Regression  

Métricas utilizadas:
- Acurácia  
- Precisão  
- Recall  
- F1-score  
- Matriz de confusão  

---

## 4. Resultados Obtidos

### Acurácia dos modelos

| Modelo | Acurácia |
|--------|---------|
| **Random Forest** | **0.9206** |
| KNN | 0.8730 |
| SVM | 0.8730 |
| Logistic Regression | 0.8571 |
| Naive Bayes | 0.8254 |

### Acurácia dos modelos otimizados

| Modelo | Tunado | Antes |
|--------|--------|--------|
| **KNN** | **0.9048** | 0.8730 |
| SVM | 0.8571 | 0.8730 |
| Random Forest | 0.8889 | 0.9206 |

###  Observações:
- O **Random Forest** foi o melhor modelo no baseline.  
- O **KNN** foi o que mais melhorou após tuning.  
- O SVM não apresentou melhora com tuning nesta base específica.  
- As features mais importantes (via RandomForest) foram:  
  1. area  
  2. perimeter  
  3. length_groove  
  4. width_kernel  

---

## 5. Conclusão

- O problema é **viável** para ser resolvido com machine learning, atingindo mais de **90% de acurácia**.  
- O modelo pode auxiliar cooperativas agrícolas a classificarem grãos com mais padrão e menos erro manual.  
- As features relacionadas ao **tamanho do grão** foram as mais relevantes.  
- Modelos simples (como KNN) apresentaram ótimo desempenho.  
- Random Forest mostrou maior estabilidade e melhor desempenho geral.

### Limitações:
- Dataset pequeno (210 amostras).  
- Medidas físicas podem variar dependendo do método de coleta.  
- Uma solução real exigiria coleta contínua e sensores calibrados. 
