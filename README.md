# 📡 Telecom X — Análisis de Evasión de Clientes

Proyecto de análisis de datos enfocado en identificar los factores que impulsan la **deserción de clientes (churn)** en la empresa de telecomunicaciones **Telecom X**. A través de un pipeline ETL completo y un Análisis Exploratorio de Datos (EDA), se extraen insights accionables para diseñar estrategias de retención.

---

## 📋 Tabla de Contenidos

- [Descripción](#-descripción)
- [Tecnologías](#-tecnologías)
- [Estructura del Proyecto](#-estructura-del-proyecto)
- [Pipeline de Datos](#-pipeline-de-datos)
- [Hallazgos Principales](#-hallazgos-principales)
- [Recomendaciones Estratégicas](#-recomendaciones-estratégicas)
- [Cómo Ejecutar](#-cómo-ejecutar)
- [Fuente de Datos](#-fuente-de-datos)

---

## 📖 Descripción

Telecom X enfrenta una tasa de deserción del **26.6%** en su base de clientes. Este proyecto aplica técnicas de ciencia de datos para:

1. **Extraer** datos desde una fuente JSON remota.
2. **Transformar** y limpiar los datos para asegurar su calidad e integridad.
3. **Analizar** patrones de comportamiento que diferencian a los clientes que permanecen de los que abandonan el servicio.
4. **Generar recomendaciones** basadas en evidencia para reducir la rotación.

El análisis se realiza sobre una muestra final de **7,032 registros** válidos con **21 variables analíticas**.

---

## 🛠 Tecnologías

| Herramienta | Uso |
| :--- | :--- |
| **Python 3** | Lenguaje principal |
| **Pandas** | Manipulación y limpieza de datos |
| **NumPy** | Operaciones numéricas |
| **Matplotlib** | Visualización de datos |
| **Seaborn** | Gráficos estadísticos |
| **Requests** | Extracción de datos vía API |

---

## 📁 Estructura del Proyecto

```
.
├── TelecomX_parte_1.ipynb   # Notebook con el análisis completo (ETL + EDA + Informe)
└── README.md                # Documentación del proyecto
```

---

## ⚙ Pipeline de Datos

### 1. Extracción
- Consumo de datos en formato JSON desde un repositorio remoto.
- Conversión inicial a DataFrame de Pandas.

### 2. Transformación
- **Normalización JSON:** Aplanamiento de estructuras anidadas con `pd.json_normalize`.
- **Limpieza de datos:**
  - Eliminación de registros con valores vacíos o nulos.
  - Corrección de tipos de dato (e.g., `Charges.Total` de string a float).
  - Reemplazo de valores redundantes como `"No phone service"` y `"No internet service"` por `"No"`.
- **Estandarización:**
  - Codificación binaria de variables categóricas (`Yes`/`No` → `1`/`0`).
  - Renombramiento de columnas al español para mayor claridad.
- **Ingeniería de variables:** Creación de la columna `Cuentas_Diarias` (cargos mensuales / 31).

### 3. Carga y Análisis
- Análisis descriptivo de la distribución de variables.
- Visualizaciones de la distribución de churn por variables categóricas y numéricas.
- Generación de informe final con diagnóstico estratégico.

---

## 💡 Hallazgos Principales

| Hallazgo | Detalle |
| :--- | :--- |
| **Tasa de retención** | 73.4% de la base se mantiene activa; 26.6% abandonó el servicio. |
| **Contratos mes a mes** | Son el principal motor de la fuga. Los contratos anuales logran >90% de retención. |
| **Método de pago** | Los cheques electrónicos triplican el riesgo de abandono frente a métodos automáticos. |
| **Fibra óptica** | Genera más cancelaciones que otros servicios de internet, sugiriendo insatisfacción precio/calidad. |
| **Periodo crítico** | El primer año es la "zona roja"; superarlo aumenta exponencialmente la probabilidad de permanencia. |
| **Ticket promedio** | La deserción es más frecuente en cuentas con cargos elevados (~$80 USD). |

---

## 🚀 Recomendaciones Estratégicas

| Eje de Intervención | Propuesta |
| :--- | :--- |
| **Acompañamiento Inicial** | Programa de bienvenida intensivo durante el primer año para reducir la rotación temprana. |
| **Transformación de Pagos** | Bonificaciones por domiciliación bancaria para eliminar fricción financiera. |
| **Calidad de Servicio** | Auditoría técnica y ajuste de tarifas en Fibra Óptica para recuperar valor percibido. |
| **Estrategia de Vínculo** | Empaquetar Soporte Premium en planes base para fortalecer barreras de salida. |

---

## ▶ Cómo Ejecutar

1. **Clonar el repositorio:**
   ```bash
   git clone https://github.com/Basurero2/Challenge-Telecom-X-an-lisis-de-evasi-n-de-clientes---1.git
   ```

2. **Instalar las dependencias:**
   ```bash
   pip install pandas numpy matplotlib seaborn requests
   ```

3. **Abrir el notebook:**
   ```bash
   jupyter notebook TelecomX_parte_1.ipynb
   ```

4. **Ejecutar todas las celdas** para reproducir el análisis completo.

---

## 📦 Fuente de Datos

Los datos se obtienen del siguiente repositorio público:

```
https://raw.githubusercontent.com/alura-cursos/challenge2-data-science-LATAM/refs/heads/main/TelecomX_Data.json
```

El dataset contiene información de clientes de una empresa de telecomunicaciones, incluyendo datos demográficos, servicios contratados, información financiera y el estado de abandono (churn).

---

> **Proyecto desarrollado como parte del Challenge de Data Science de Alura LATAM.**
