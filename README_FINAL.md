# Determinantes económicos, sociales y demográficos de la migración en Colombia

## Autores

- Alan Steven Ríos Munar  
- Juan Esteban Samaniego Poveda  
- Sebastian Casas Poloche  

**Universidad Externado de Colombia**  
IA con aplicaciones en economía — 2026

---

## 📌 Descripción del proyecto

Este proyecto analiza los factores económicos, sociales y demográficos que influyen en la migración interna en Colombia utilizando datos de la GEIH 2025 del DANE.

El objetivo principal es estimar la probabilidad de que una persona migre dentro del país e identificar las variables que más influyen en dicha decisión.

---

## 🎯 Objetivo

- Estimar la probabilidad de migración interna en Colombia.
- Identificar perfiles con mayor propensión a migrar.
- Analizar factores asociados a la movilidad territorial.
- Generar herramientas útiles para política pública.

---

## 🧠 Metodología

- Análisis exploratorio de datos (EDA)
- Regresión logística
- Random Forest
- XGBoost
- SHAP Values
- K-Prototypes Clustering
- Threshold Tuning

---

## 📊 Dataset

### Fuente principal
- Gran Encuesta Integrada de Hogares (GEIH) — DANE 2025

### Características
- Más de 3 millones de registros
- Variables demográficas, laborales y socioeconómicas
- Problema de clasificación binaria

---

## 📈 Principales hallazgos

- La afiliación a salud es uno de los principales factores de retención territorial.
- La migración se concentra en población joven y en edad productiva.
- Bogotá y Antioquia continúan como principales polos de atracción migratoria.
- La informalidad laboral aumenta la probabilidad de migrar.

---

## 🏆 Modelo campeón

**XGBoost + Tomek Links**

| Métrica | Resultado |
|---|---|
| ROC-AUC | 0.7663 |
| Recall | 0.7469 |
| PR-AUC | 0.1102 |

---

## 📂 Estructura del proyecto

```bash
📂 migracion-colombia
│
├── data
├── notebooks
├── outputs
├── models
├── visualizations
└── README.md
```

---

## 🚀 Tecnologías utilizadas

- Python
- Pandas
- NumPy
- Scikit-Learn
- XGBoost
- SHAP
- GeoPandas

---

## 📌 Conclusión

La migración interna en Colombia no depende únicamente del ingreso monetario. Factores como la formalidad laboral, la afiliación al sistema de salud y las desigualdades territoriales tienen un papel central en la movilidad de la población.

---

## 👨‍💻 Autores

Juan Esteban Samaniego  
Alan Steven Ríos Munar  
Sebastian Casas Poloche
