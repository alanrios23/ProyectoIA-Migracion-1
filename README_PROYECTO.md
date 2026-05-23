# Determinantes económicos, sociales y demográficos de la migración en Colombia 🇨🇴

> *Machine Learning + Economía aplicada para entender por qué migran los colombianos.*

---

## 👥 Autores

- Alan Steven Ríos Munar  
- Juan Esteban Samaniego Poveda  
- Sebastian Casas Poloche  

**Universidad Externado de Colombia**  
IA con aplicaciones en economía — 2026

---

# 🚀 ¿De qué trata este proyecto?

La migración interna en Colombia refleja mucho más que movimientos poblacionales:  
expone desigualdades económicas, laborales y territoriales entre regiones.

En este proyecto construimos un modelo de *Machine Learning interpretable* capaz de estimar la probabilidad de que una persona migre dentro del país utilizando microdatos de la GEIH 2025 del DANE.

Además de predecir migración, el proyecto identifica qué factores realmente impulsan la movilidad territorial mediante interpretabilidad con SHAP y técnicas de clustering.

---

# 🎯 Objetivos

✅ Estimar la probabilidad de migración interna en Colombia  
✅ Identificar perfiles con mayor propensión a migrar  
✅ Detectar variables socioeconómicas clave  
✅ Construir herramientas útiles para política pública  
✅ Interpretar modelos de ML desde un enfoque económico y social

---

# 🧠 Metodología

El proyecto combina técnicas estadísticas, econométricas y de Machine Learning:

- 📊 Análisis Exploratorio de Datos (EDA)
- 🤖 Regresión Logística
- 🌳 Random Forest
- ⚡ XGBoost
- 🔍 Interpretabilidad con SHAP Values
- 🧩 Clustering con K-Prototypes
- 🎯 Threshold Tuning
- ⚖️ Manejo de clases desbalanceadas
  - Tomek Links
  - Scale Pos Weight

---

# 📂 Dataset

## Fuente

- Gran Encuesta Integrada de Hogares (GEIH) — DANE 2025

## Características principales

| Característica | Valor |
|---|---|
| Registros | +3 millones |
| Tipo de problema | Clasificación binaria |
| Variable objetivo | Migración interna |
| Variables | Sociales, laborales, económicas y demográficas |

---

# 📈 Hallazgos más importantes

## 🏥 La salud importa más que el ingreso

El modelo encontró que la afiliación al sistema de salud y la formalidad institucional tienen un impacto mayor sobre la migración que el propio nivel salarial.

---

## 👨‍👩‍👧 La migración es joven

La mayor concentración migratoria se encuentra en población:

- joven
- económicamente activa
- en etapa de inserción laboral

---

## 🌆 Colombia sigue centralizándose

Los principales polos de atracción migratoria continúan siendo:

- Bogotá
- Antioquia

Lo que evidencia fuertes desigualdades territoriales entre regiones.

---

## 💼 La informalidad impulsa la movilidad

La ausencia de estabilidad laboral y seguridad social aumenta significativamente la probabilidad de migrar.

---

# 🏆 Modelo campeón

## ⚡ XGBoost + Tomek Links

| Métrica | Resultado |
|---|---|
| ROC-AUC | **0.7663** |
| Recall | **0.7469** |
| PR-AUC | **0.1102** |
| F1-Score | **0.0934** |
| Umbral óptimo | **0.454** |

---

# 🔍 Interpretabilidad del modelo

Se utilizaron valores SHAP para entender cómo cada variable afecta la probabilidad de migración.

Las variables más importantes fueron:

1. Edad
2. Departamento
3. Afiliación a salud
4. Ingreso
5. Educación

Esto permitió pasar de un modelo predictivo a una herramienta útil para toma de decisiones públicas.

---

# 🧩 Clustering migratorio

Mediante K-Prototypes se identificaron perfiles migratorios diferenciados, permitiendo caracterizar grupos con dinámicas similares de movilidad territorial.

Los clusters muestran:

- diferencias laborales
- brechas regionales
- patrones de informalidad
- concentración urbana

---

# 📌 Conclusiones

La migración interna en Colombia no depende únicamente del ingreso monetario.

El proyecto evidencia que factores como:

- la formalidad laboral,
- la afiliación al sistema de salud,
- la edad,
- y las desigualdades territoriales

son determinantes clave en la decisión de migrar.

El modelo desarrollado logra identificar aproximadamente **3 de cada 4 migrantes reales**, convirtiéndose en una herramienta con potencial para focalización de política pública y planeación territorial.

---

# 👨‍💻 Autores

**Juan Esteban Samaniego**  
**Alan Steven Ríos Munar**  
**Sebastian Casas Poloche**

---

## ⭐ Si este proyecto te pareció interesante...

¡No olvides darle una estrella al repositorio!
