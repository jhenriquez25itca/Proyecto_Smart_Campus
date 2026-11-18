# Smart Campus Analytics: De la Ingesta al Valor Estratégico

![Institución](https://img.shields.io/badge/Instituci%C3%B3n-ITCA--FEPADE-firebrick)
![Carrera](https://img.shields.io/badge/Carrera-Ingenier%C3%ADa%20en%20Desarrollo%20de%20Software-blue)
![Ciclo](https://img.shields.io/badge/Ciclo-IV%20%7C%20Secci%C3%B3n%20IDS221-brightgreen)
![Versión](https://img.shields.io/badge/Versi%C3%B3n-3.0%20(Final)-orange)

Proyecto integrador de la asignatura **Gestión de Datos para Inteligencia Artificial y Big Data**, orientado a centralizar, gobernar, visualizar y modelar la operación de los laboratorios, talleres y recursos tecnológicos de las cuatro sedes de ITCA-FEPADE.

---

## 1. Descripción del Proyecto
**Smart Campus Analytics** resuelve la fragmentación de datos operativos en la gestión de infraestructura universitaria. A través de un pipeline reproducible de extremo a extremo, el proyecto integra registros de asistencia, catálogos de recursos y programación de mantenimientos para transformar datos dispersos en indicadores estratégicos de ocupación, alertas territoriales y modelos predictivos de demanda diaria.

---

## 2. Sector y Contexto del Problema
* **Sector:** Gestión de infraestructura universitaria y analítica educativa.
* **Problema Empresarial:** La información sobre el uso de laboratorios, disponibilidad de equipos y órdenes de mantenimiento residía en sistemas aislados y formatos heterogéneos, obligando a la administración a tomar decisiones basadas en percepciones y no en evidencia, con riesgo de sobrecupo en recursos críticos y mantenimientos reactivos.
* **Usuarios Beneficiados:**
  * *Coordinación de Laboratorios:* Planificación de horarios y redistribución de capacidad.
  * *Administración de Infraestructura:* Priorización de mantenimiento preventivo según criticidad.
  * *Estudiantes:* Mayor disponibilidad y confiabilidad de los recursos académicos.

---

## 3. Fuentes de Datos
El flujo parte de tres fuentes heterogéneas representativas de la operación institucional (ampliadas posteriormente a un histórico semestral de 10,000 sesiones entre el 15/01/2026 y el 14/07/2026):

| Fuente | Formato | Archivo | Descripción |
| :--- | :--- | :--- | :--- |
| **Asistencia y Uso** | CSV | `asistencia_labs.csv` | Registro operativo de entradas, salidas y estudiantes presentes por sesión. |
| **Catálogo de Recursos** | SQLite | `SmartCampus_Analytics.db` | Base de datos relacional con inventario de 20 recursos, sedes, edificios y capacidad máxima. |
| **Mantenimientos** | JSON | `mantenimientos.json` | Registros semiestructurados con estado operativo y nivel de prioridad técnica. |

---

## 4. Herramientas y Tecnologías
* **Lenguaje y Análisis:** Python 3.10+ (`pandas`, `numpy`, `scikit-learn`, `joblib`).
* **Procesamiento Big Data:** Apache Spark (`PySpark` en modo local, Spark SQL y almacenamiento columnar `Parquet` particionado).
* **Inteligencia de Negocios (BI):** Microsoft Power BI (Modelo estrella, Power Query y 12 medidas DAX).
* **Analítica Geoespacial:** ArcGIS Online (Capas de puntos, simbología de semáforo de demanda e intensidad).
* **Reportería y Automatización:** GitHub Actions, `matplotlib`, `jinja2`, `python-docx` y `weasyprint`.

---

## 5. Estructura del Repositorio
```text
Proyecto_Smart_Campus_Analytics_IDS221/
├── Avance de Proyecto/
│   ├── Avance1_Smart_Campus_Analytics_IDS221 (.docx / .pdf)
│   └── Avance2_Smart_Campus_Analytics_IDS221 (.docx / .pdf)
├── Datos/
│   ├── crudos/                    # Fuentes originales (CSV, SQLite, JSON)
│   ├── externos/                  # Registros de mantenimiento
│   ├── procesados/                # Datasets integrados y limpios (dataset_limpio_Smart_Campus.csv)
│   ├── analiticos/                # Salidas en formato Parquet particionado (4 bloques)
│   ├── gobernanza/                # Vista analítica minimizada y protegida
│   ├── geo/                       # Capa geográfica nacional (smartcampus_nacional_arcgis.csv)
│   └── Prediccion/                # Notebooks, métricas, predicciones y modelos .joblib
├── Visualizaciones/
│   └── SmartCampusFase2.pbix      # Dashboard interactivo y modelo semántico
├── Documentos/
│   ├── politica_gobernanza_Smart_Campus.md
│   ├── informe_smart_campus_v1.0 (.docx / .pdf)
│   └── generar_informe_smart_campus.yml
├── scripts/
│   └── generar_informe.py         # Script de generación automática de reportes
├── Evidencias/                    # Capturas de ejecución de notebooks, Power BI y ArcGIS
└── README.md                      # Documentación principal del proyecto
```

---

## 6. Guía de Reproducibilidad
Para regenerar los datasets procesados y reproducir el pipeline completo desde cero:

1. **Clonar el repositorio y preparar el entorno virtual:**
   ```bash
   git clone https://github.com/equipo-smartcampus/Proyecto_Smart_Campus_Analytics_IDS221.git
   cd Proyecto_Smart_Campus_Analytics_IDS221
   python -m venv venv
   source venv/bin/activate  # En Windows: venv\Scripts\activate
   pip install pandas numpy pyspark scikit-learn matplotlib jinja2 python-docx weasyprint joblib
   ```

2. **Ejecutar el Pipeline de Ingeniería de Datos (Guías 1 a 4):**
   * Ejecutar los notebooks de integración y limpieza para generar `Datos/procesados/dataset_limpio_Smart_Campus.csv`.
   * Ejecutar el pipeline de PySpark para exportar las particiones analíticas en `Datos/analiticos/campus_analiticas_parquet/`.

3. **Generar Capas Geográficas y Reportes (Guías 6 y 7):**
   * Ejecutar `Entregable_Fase_2_Proyecto_Smart_Campus_Analytics.ipynb` para exportar `Datos/geo/smartcampus_nacional_arcgis.csv`.
   * Ejecutar `python scripts/generar_informe.py` para compilar los reportes gerenciales en Word y PDF.

4. **Reproducir Modelado Predictivo (Guías 8 a 10):**
   * Ejecutar `EntrenamientoModelo_SmartCampus.ipynb` y `Optimizacion_Hiperparametros_SmartCampus.ipynb` (semilla fija `random_state = 42`) para regenerar las tablas comparativas y los artefactos `.joblib`.

5. **Explorar el Tablero de Control (Guía 5):**
   * Abrir `Visualizaciones/SmartCampusFase2.pbix` en Power BI Desktop y actualizar el origen apuntando a `dataset_limpio_Smart_Campus.csv`.

---

## 7. Resultados Principales
* **Desempeño Operativo:** Sobre 10,000 sesiones evaluadas (525,358 horas-estudiante acumuladas), la ocupación promedio global es de **70.78%**, manteniéndose estable a lo largo de los meses, días de la semana y franjas horarias.
* **Hallazgos Territoriales y de Capacidad:**
  * Los recursos de menor capacidad (25 puestos) concentran la saturación: *Taller Electrónica Naval* en La Unión (**89.58%**), *Sala Mac Animación* en Santa Tecla (**89.08%**) y *Taller Electricidad Industrial* en San Miguel (**87.32%**).
  * La sede de **Santa Ana** concentra el 100% de las sesiones no operativas (632 registros, equivalente al 25.28% de su operación), destacando la necesidad de mantenimiento preventivo en sus laboratorios.
* **Evaluación Predictiva (Machine Learning):**
  * Se evaluaron modelos de Regresión Lineal, Árbol de Decisión y Random Forest frente a un *Baseline de Media* mediante validación cruzada temporal (`TimeSeriesSplit`).
  * La optimización mediante `GridSearchCV` redujo el error del Random Forest en un **14.84%** (bajando el MAE de prueba de `196.69` a `167.50`), aunque el **Baseline de Media** (`MAE = 157.63`) se conserva como referencia oficial debido a la alta estabilidad temporal de la demanda diaria.

---

## 8. Gobernanza y Ética de Datos
* **Clasificación y Minimización:** Los atributos fueron catalogados según su sensibilidad. En la vista analítica (`dataset_publicable_Smart_Campus.csv`) se excluyeron identificadores directos (nombre, correo y teléfono).
* **Técnicas de Protección:** Se aplicó seudonimización irreversible mediante `SHA-256` con *salt* (`smartcampus-datos-sinteticos`) sobre los identificadores de estudiantes y generalización de edades por rangos decenales.
* **Control de Acceso y Retención:** Definición de matriz de permisos basada en roles (mínimo privilegio) y reglas de depuración de copias crudas al cierre del ciclo académico.

---

## 9. Limitaciones
1. **Horizonte Temporal:** Los datos corresponden a un único semestre simulado (181 días), lo que impide capturar estacionalidades interanuales completas.
2. **Granularidad Geográfica:** Las coordenadas empleadas en ArcGIS representan ubicaciones de referencia a nivel de edificio dentro de cada sede.
3. **Variables Predictoras:** El modelado actual utiliza exclusivamente variables de calendario y rezagos históricos (`lag_1`, `lag_7`, `media_movil_7`); incorporar el calendario de exámenes y eventos institucionales es el siguiente paso recomendado para capturar picos atípicos.

---

## 10. Control Documental y Contacto

### Historial de Versiones
| Versión | Fecha | Hito / Descripción | Estado |
| :--- | :--- | :--- | :--- |
| **1.0** | 23/09/2026 | Avance 1: Ingesta heterogénea, limpieza, arquitectura Spark y gobernanza (Guías 1–4). | Entregado |
| **2.0** | 21/10/2026 | Avance 2: Modelo estrella Power BI, capas ArcGIS, reportería automatizada y baseline IA (Guías 5–8). | Entregado |
| **3.0** | 18/11/2026 | Entrega Final: Entrenamiento comparativo, validación temporal y optimización de hiperparámetros (Guías 9–10). | Entregado |

### Equipo de Desarrollo (Sección IDS221 — Docente: Ing. Gilbert García)
| Integrante | Carnet | Rol Principal |
| :--- | :--- | :--- |
| **David Edgardo López Salazar** | `039125` | Líder de Proyecto / Integración, Power BI y Entrenamiento ML |
| **José Roberto Henríquez Calderón** | `098925` | Calidad de Datos, Limpieza y Reportería Automatizada |
| **Fernando Dagoberto García Hernández** | `038325` | Arquitectura Big Data (Spark), ArcGIS y Optimización GridSearchCV |
| **Jean Carlo Arbizu Orellana** | `053925` | Gobernanza, Ética de Datos y Fundamentos de Predicción |