# Determinantes de la Migración Interna en Colombia
### Enfoque probabilístico y machine learning — GEIH 2025

**Autores:** Alan Steven Ríos Munar · Juan Esteban Samaniego Poveda · Sebastian Casas Poloche  
**Curso:** IA con aplicaciones en economía — Universidad Externado de Colombia  
**Docente:** Lina María Castro · 2026

---

## Descripción

Este proyecto predice la migración interna en Colombia usando microdatos de la Gran Encuesta Integrada de Hogares (GEIH) del DANE para 2025. Se modela como clasificación binaria: ¿migró el individuo entre departamentos en los últimos 12 meses?

La base de datos supera los 3 millones de registros con un fuerte desbalance de clases (~2.53% migrantes). El flujo metodológico está diseñado para ser libre de *data leakage*: limpieza → split → EDA (solo train) → preprocesamiento (solo train) → GridSearchCV con Pipeline → evaluación sobre test original no balanceado.

**Modelo campeón:** XGBoost + Tomek Links (dentro de `ImbPipeline`), evaluado sobre test en distribución real.

---

## Estructura del proyecto

```
.
├── Proyecto_Final_Definitiva.ipynb   # Notebook maestro (flujo completo)
├── Entrega_final.docx                # Informe académico del proyecto
├── requirements.txt                  # Dependencias
└── README.md
```

Archivos generados al ejecutar el notebook:

```
GEIH_Predicciones_Test.csv            # Checkpoint: migrantes predichos con destino
importancias_modelo_campeon.csv       # Feature importances del modelo campeón
migrantes_test_con_destino.csv        # Test set con destino predicho
diagnostico_final.png                 # Curvas ROC, PR, confusión, distribución de probabilidades
shap_summary.png / shap_bar.png       # Análisis SHAP
comparacion_xgb_submuestreo_pipeline.png
comparacion_modelos_recall.png
validacion_geografica_modelo.png      # Mapas de calor por departamento
```

---

## Flujo del notebook

| Paso | Descripción |
|------|-------------|
| 0 | Instalación de librerías y montaje de Google Drive |
| 1 | Construcción de la base GEIH (concat mensual 2022–2025, merge módulos CG/FT/M/O) |
| 2 | Limpieza y construcción de features (`grupo_edad`, `formalidad`, `log_ingreso`, etc.) |
| 3 | Split estratificado 80/20 — test sellado |
| 4 | EDA exclusivamente sobre train |
| 5 | Preprocesamiento: imputación y escalado fit solo en train |
| 6 | GridSearchCV sobre submuestra 20% del train (Logística, Árbol, RF, XGBoost) |
| 6b | XGBoost + Tomek Links y + Cluster Centroids vía `ImbPipeline` (sin leakage) |
| 7 | Selección del campeón por Recall CV, re-entrenamiento sobre train completo |
| 7b | Modelo de destino: XGBoost multiclase para predecir departamento de llegada |
| 8 | Ajuste de umbral maximizando Recall (Precision ≥ 5%) |
| 9 | Evaluación final sobre test original no balanceado |
| 10 | Feature importances + análisis SHAP |
| 11 | Checkpoint: guardar predicciones en Drive |
| 12 | Clustering K-Prototypes sobre migrantes reales (perfiles socioeconómicos) |
| 13 | Mapas de calor departamentales: flujo real vs flujo predicho |

---

## Variables del modelo

| Variable | Descripción |
|----------|-------------|
| `edad` | Edad del individuo |
| `sexo` | 1 = Hombre, 0 = Mujer |
| `clase` | 1 = Urbano, 0 = Rural |
| `Educacion` | Nivel educativo (1–13) |
| `grupo_edad` | Grupos: 0-18 / 19-25 / 26-45 / 46-60 / 60+ |
| `log_ingreso` | Log(1 + ingreso total) |
| `formalidad` | 0=No ocupado, 1=Formal, 2=Parc. formal, 3=Informal |
| `estado_laboral` | 1=Ocupado, 2=Desocupado, 3=Inactivo |
| `afiliado_salud` | Afiliación al sistema de salud |
| `regimen_salud` | Régimen de salud |
| `cotiza_salud` | Cotiza a salud |
| `cotiza_pension` | Cotiza a pensión |
| `depto_actual` | Código DANE del departamento actual |
| **`target_migro`** | **Variable objetivo**: 1 si migró interdepartamentalmente |

---

## Hallazgos principales

- La **afiliación al sistema de salud y la formalidad laboral** son el principal factor de retención territorial, por encima del nivel de ingresos.
- La migración es un fenómeno de **población joven** (mediana ~25 años) en etapa de inserción laboral.
- **Bogotá y Antioquia** son los principales polos de atracción demográfica.
- Los **desocupados** presentan mayor propensión a migrar (11% vs 7% en no migrantes).
- La corrección metodológica del *data leakage* en v5 (ClusterCentroids antes del CV) redujo el ROC-AUC de ~0.99 a valores realistas.

---

## Requisitos

- Python 3.10+
- Google Colab (recomendado por acceso a Google Drive y GPU)
- Datos GEIH 2022–2025 disponibles en Google Drive bajo `/content/drive/MyDrive/GEIH/`

Ver `requirements.txt` para las dependencias exactas.

---

## Ejecución

1. Subir el notebook a Google Colab.
2. Montar Google Drive con la estructura de carpetas GEIH.
3. Ejecutar las celdas en orden. Si ya existe `GEIH_Proyecto.csv` en Drive, omitir el paso 1.
4. Para saltar directamente a los mapas o clustering, cargar el checkpoint desde el paso 11.
