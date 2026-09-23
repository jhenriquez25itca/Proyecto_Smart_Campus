
# Gobernanza de datos: Smart Campus Analytics

# 1. Objetivo
Establecer las reglas para recolectar, tratar, almacenar y publicar los datos del proyecto, de modo que los resultados sean confiables, verificables y respetuosos con la privacidad de las personas.

# 2. Roles y responsabilidades
- Propietario de los datos: la institución (coordinación académica y unidad de laboratorios), que autoriza el uso de la información.
- Analista de datos: limpia, transforma y analiza los datos, y documenta cada paso.
- Responsable de calidad: valida que los indicadores y las cifras coincidan con las fuentes.
- Usuarios del informe: dirección y coordinadores, con acceso solo a resultados agregados.

# 3. Fuentes y calidad de los datos
- Cada fuente (asistencia, ocupación de laboratorios, horarios, recursos tecnológicos) queda registrada con su origen, periodo y frecuencia de actualización.
- Se aplican controles básicos: revisión de valores nulos, duplicados, formatos de fecha y hora, y rangos válidos.
- Los criterios de limpieza (qué se elimina, qué se imputa y por qué) se documentan en el notebook.

# 4. Privacidad y ética
- Se trabaja con datos agregados por curso, laboratorio o franja horaria; no se identifica a estudiantes ni docentes de forma individual.
- Se eliminan o anonimizan nombres, correos, identificadores y cualquier dato personal antes del análisis.
- No se publican ubicaciones sensibles ni información que permita identificar a una persona.
- Los datos se usan únicamente para el fin académico del proyecto.

# 5. Seguridad y acceso
- El acceso a los datos originales se limita a los integrantes del equipo.
- Los archivos se almacenan en un repositorio compartido con permisos controlados, sin datos sensibles en el notebook público.
- Se conserva una copia de los datos crudos, sin modificar, separada de los datos procesados.

# 6. Trazabilidad y transparencia
- Se mantiene una **matriz de trazabilidad** que relaciona cada hallazgo con su fuente, indicador y visualización.
- Se documentan filtros, transformaciones y fórmulas de cada KPI, con control de versiones del notebook y de los conjuntos de datos.
- Las limitaciones (periodo corto, datos faltantes, baja granularidad) se declaran de forma explícita en el informe.

# 7. Ciclo de vida de los datos
1. Recolección: obtención de los datos con autorización.
2. Procesamiento: limpieza, transformación y validación.
3. Análisis y publicación: dashboard e informes con resultados agregados.
4. Conservación y eliminación: los datos se conservan mientras dure el proyecto y luego se eliminan o se archivan de forma anonimizada.

# 8. Revisión
El equipo revisará estas reglas al inicio de cada entrega para confirmar que se cumplen y actualizarlas si cambian las fuentes o el alcance del proyecto.
