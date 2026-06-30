# EduPredict - Plataforma de Predicción Académica con Machine Learning, RAG e IA Generativa

## Descripción

EduPredict es una plataforma web en desarrollo orientada al análisis académico de estudiantes mediante Machine Learning, APIs REST e inteligencia artificial generativa.

El proyecto comenzó como un sistema de predicción académica capaz de estimar la calificación final de un estudiante a partir de sus datos escolares. Su evolución técnica busca convertirlo en una solución de apoyo académico más completa, capaz de integrar modelos predictivos, recuperación de información documental, generación de reportes explicativos y prototipos de agentes inteligentes.

El objetivo principal es apoyar a administradores, docentes o tutores académicos en la detección temprana de estudiantes con posible bajo rendimiento o riesgo académico. El sistema no pretende reemplazar la toma de decisiones humanas, sino ofrecer información estructurada, explicable y documentada para facilitar el seguimiento oportuno.

---

## Enfoque técnico del proyecto

Este proyecto está diseñado como una plataforma de aprendizaje y portafolio para aplicar conceptos de:

- Machine Learning aplicado a datos académicos.
- Desarrollo backend con Django y APIs REST.
- Prototipado de servicios de IA.
- Experimentación con modelos de lenguaje.
- Recuperación aumentada por generación, conocida como RAG.
- Embeddings, chunking, bases vectoriales y búsqueda semántica.
- Construcción básica de agentes con herramientas internas.
- Documentación técnica, notebooks, comparativas y demos reutilizables.

Además del sistema principal, EduPredict contempla la creación de PoCs controladas para validar casos de uso relacionados con IA generativa, procesamiento documental y automatización de reportes académicos.

---

## Propósito del proyecto

El propósito de EduPredict es desarrollar un sistema inteligente de apoyo académico que combine modelos predictivos, análisis de datos, recuperación de información documental y generación automática de reportes.

A partir de datos académicos del estudiante, el sistema puede estimar su desempeño esperado y clasificar su nivel de riesgo. En futuras versiones, también podrá consultar documentos institucionales mediante RAG, generar recomendaciones personalizadas y producir reportes explicativos usando modelos de lenguaje.

De esta manera, el proyecto integra Machine Learning tradicional, desarrollo backend, bases de datos, APIs REST, RAG, agentes inteligentes y documentación técnica dentro de una solución aplicada al contexto educativo.

---

## Características actuales

- Registro y administración de estudiantes.
- Predicción automática de la calificación final.
- Clasificación del nivel de riesgo académico.
- Historial de predicciones.
- Integración de un modelo de Machine Learning mediante una API REST.
- Almacenamiento de información académica en PostgreSQL.
- Arquitectura modular para facilitar futuras mejoras.
- Documentación del flujo actual y del roadmap técnico.

---

## Características planeadas

- Generación automática de reportes académicos.
- Explicación de factores que influyen en la predicción.
- Panel de estadísticas y visualización de datos.
- Gráficas de rendimiento académico.
- Gestión de profesores, grupos y materias.
- Exportación de reportes en PDF y Excel.
- Autenticación con diferentes roles.
- Predicción específica del riesgo de deserción.
- Integración de documentos académicos mediante RAG.
- Chatbot académico para consultar reglamentos, temarios o lineamientos escolares.
- Agente académico capaz de consultar datos, llamar al modelo predictivo y generar recomendaciones.
- Comparación de respuestas entre distintos modelos LLM.
- Evaluación de prompts y documentación de resultados.
- Pruebas con embeddings, chunking, reranking y vector stores.
- Despliegue con Docker y Docker Compose.

---

## Arquitectura actual

```text
                    +----------------------+
                    |   Google Colab       |
                    | Entrenamiento Modelo |
                    +----------+-----------+
                               |
                               |
                  Modelo entrenado (.joblib)
                               |
                               v
                    +----------------------+
                    |      API REST        |
                    | Servicio de IA / ML  |
                    +----------+-----------+
                               |
                               |
                     Solicitud de predicción
                               |
                               v
                    +----------------------+
                    |    Django Web App    |
                    |  Gestión Académica   |
                    +----------+-----------+
                               |
                               |
                               v
                    +----------------------+
                    |     PostgreSQL       |
                    |  Datos Académicos    |
                    +----------------------+
```

---

## Arquitectura objetivo

```text
                    +----------------------+
                    |   Google Colab       |
                    | Entrenamiento ML     |
                    +----------+-----------+
                               |
                               v
                    +----------------------+
                    | Modelo Predictivo    |
                    | .joblib / Pipeline   |
                    +----------+-----------+
                               |
                               v
+-------------------+     +----------------------+     +----------------------+
| Documentos PDF    | --> | Sistema RAG          | --> | Base Vectorial        |
| Reglamentos       |     | Chunking + Retrieval |     | Chroma / pgvector     |
| Temarios          |     +----------+-----------+     +----------------------+
+-------------------+                |
                                     v
                    +----------------------+
                    |   Agente Académico   |
                    | Tools + LLM + RAG    |
                    +----------+-----------+
                               |
                               v
                    +----------------------+
                    |      API REST        |
                    | FastAPI / Django API |
                    +----------+-----------+
                               |
                               v
                    +----------------------+
                    |    Django Web App    |
                    | Dashboard Académico  |
                    +----------+-----------+
                               |
                               v
                    +----------------------+
                    |     PostgreSQL       |
                    | Alumnos / Riesgos    |
                    | Reportes / Usuarios  |
                    +----------------------+
```

---

## Flujo actual del sistema

1. El administrador inicia sesión.
2. Registra los datos académicos del estudiante.
3. La aplicación envía la información a la API REST.
4. El modelo de Machine Learning realiza la predicción.
5. La API devuelve la calificación estimada.
6. El sistema clasifica el nivel de riesgo académico.
7. La predicción se almacena en la base de datos.
8. El resultado se muestra en la aplicación web.

---

## Flujo objetivo del sistema

1. El administrador o tutor consulta el perfil de un estudiante.
2. El sistema recupera sus datos académicos desde PostgreSQL.
3. El modelo predictivo estima su calificación o nivel de riesgo.
4. El sistema RAG consulta documentos escolares relevantes.
5. Un agente académico integra la predicción, los datos del alumno y la información documental.
6. El sistema genera un reporte explicativo con:

   - Calificación estimada.
   - Nivel de riesgo.
   - Factores principales.
   - Recomendaciones.
   - Fuentes consultadas.
   - Limitaciones del análisis.

7. El reporte puede visualizarse en la plataforma o exportarse.

---

## Machine Learning

El modelo fue entrenado utilizando Google Colab a partir de un conjunto de datos académicos.

Actualmente, el modelo presenta un error aproximado de:

```text
±0.7 puntos en una escala de 0 a 10
```

Este resultado permite utilizar el modelo como una herramienta de apoyo para estimar el desempeño académico de un estudiante. La predicción no debe interpretarse como una decisión definitiva, sino como una señal de apoyo para detectar posibles casos que requieran seguimiento.

El flujo de Machine Learning contempla:

- Limpieza y preparación de datos.
- Entrenamiento en notebook.
- Validación del modelo.
- Exportación del modelo en formato `.joblib`.
- Integración del modelo con una API REST.
- Registro de predicciones para consulta posterior.

---

## Inteligencia Artificial Generativa

En futuras versiones, EduPredict integrará modelos de lenguaje para generar explicaciones y reportes académicos más claros.

El objetivo no es solo mostrar una calificación estimada, sino explicar de manera comprensible por qué un estudiante podría encontrarse en riesgo y qué acciones podrían considerarse para apoyarlo.

Ejemplo de reporte generado:

```text
Alumno: Juan Pérez
Riesgo académico: Alto
Calificación estimada: 58/100

Factores principales:
- Bajo desempeño en evaluaciones previas.
- Historial de faltas.
- Promedio cercano al mínimo aprobatorio.

Recomendación:
Se recomienda tutoría académica, seguimiento semanal y revisión de carga académica.

Limitación:
La predicción es una estimación basada en datos históricos y no debe tomarse como una decisión final.
```

---

## RAG con documentos académicos

El proyecto contempla la integración de un sistema RAG para consultar documentos escolares como:

- Reglamentos académicos.
- Lineamientos de evaluación.
- Temarios.
- Documentos institucionales.
- Criterios de aprobación.
- Políticas de reinscripción o baja.

Esto permitiría realizar preguntas como:

```text
¿Qué condiciones debe cumplir un alumno para aprobar?
¿Qué dice el reglamento sobre reinscripción?
¿Cuáles son las causas de baja académica?
Resume este documento en puntos clave.
```

El flujo propuesto para RAG incluye:

1. Carga de documentos PDF.
2. Extracción y limpieza de texto.
3. División del contenido en fragmentos.
4. Generación de embeddings.
5. Almacenamiento en Chroma o PostgreSQL con pgvector.
6. Recuperación de fragmentos relevantes.
7. Generación de respuestas con fuentes consultadas.

---

## Agente académico

Una de las metas principales del proyecto es construir un agente académico capaz de utilizar diferentes herramientas internas para generar análisis más completos.

El agente podría:

- Consultar datos de un alumno.
- Llamar al modelo predictivo.
- Revisar documentos escolares mediante RAG.
- Consultar historial de predicciones.
- Generar reportes explicativos.
- Proponer recomendaciones académicas.
- Indicar limitaciones del análisis.

Ejemplo de tools planeadas:

```text
get_student_profile(student_id)
predict_final_grade(student_data)
search_academic_documents(query)
get_prediction_history(student_id)
generate_academic_report(student_id)
```

Este componente busca acercar EduPredict a un sistema real de apoyo académico basado en IA, manteniendo la responsabilidad humana en la interpretación final de los resultados.

---

## Experimentación y PoCs

Además del desarrollo principal, el proyecto contempla la creación de prototipos controlados para validar alternativas técnicas antes de integrarlas al sistema.

Posibles PoCs:

- Comparación entre distintos modelos LLM para generación de reportes.
- Evaluación de prompts para obtener respuestas claras y estructuradas.
- Pruebas de chunking para documentos académicos.
- Comparación entre Chroma y pgvector como vector store.
- Pruebas de búsqueda semántica con embeddings.
- Evaluación de respuestas RAG con y sin fuentes.
- Demos internas en notebooks o scripts reutilizables.
- Conectores simples hacia APIs internas del sistema.

Cada PoC debe documentar:

- Objetivo del experimento.
- Herramientas utilizadas.
- Hipótesis técnica.
- Resultado obtenido.
- Limitaciones.
- Próximos pasos.

---

## Tecnologías utilizadas

### Machine Learning

- Python
- Google Colab
- Pandas
- NumPy
- Scikit-learn
- Joblib

### Backend

- Django
- Django REST Framework
- API REST

### Base de datos

- PostgreSQL

### Frontend

- HTML5
- CSS3
- Bootstrap

### Futuras integraciones de IA

- FastAPI
- Pydantic
- LLM API
- LlamaIndex
- LangChain
- Chroma
- PostgreSQL + pgvector
- Embeddings
- RAG
- Agentes con tools
- Prompt engineering
- Evaluación de respuestas generadas

### Procesamiento documental

- Carga de PDFs
- Extracción de texto
- Chunking
- OCR básico
- Metadata de documentos
- Búsqueda semántica

### Despliegue y desarrollo

- Git
- GitHub
- Docker
- Docker Compose
- Variables de entorno
- Logging
- Documentación técnica

---

## Estructura del proyecto

```text
EduPredict/
│
├── backend/
│   ├── alumnos/
│   ├── predicciones/
│   ├── usuarios/
│   └── api/
│
├── modelo_ml/
│   ├── modelo.joblib
│   ├── preprocesador.joblib
│   └── predictor.py
│
├── notebooks/
│   ├── entrenamiento_modelo.ipynb
│   ├── evaluacion_modelo.ipynb
│   └── experimentos_llm.ipynb
│
├── pocs/
│   ├── comparacion_llms/
│   ├── pruebas_embeddings/
│   ├── pruebas_chunking/
│   └── rag_demo/
│
├── rag/
│   ├── documentos/
│   ├── embeddings/
│   ├── retriever.py
│   └── rag_service.py
│
├── agente/
│   ├── tools/
│   ├── prompts/
│   └── agente_academico.py
│
├── docs/
│   ├── arquitectura.md
│   ├── decisiones_tecnicas.md
│   ├── experimentos.md
│   └── roadmap.md
│
├── templates/
│
├── static/
│
├── media/
│
├── requirements.txt
│
├── docker-compose.yml
│
└── README.md
```

---

## Objetivos del proyecto

- Integrar Machine Learning en una aplicación web.
- Automatizar la predicción del desempeño académico.
- Facilitar la identificación temprana de estudiantes en posible riesgo.
- Implementar una arquitectura basada en API REST.
- Aplicar buenas prácticas de desarrollo backend y ciencia de datos.
- Generar explicaciones claras sobre los resultados del modelo.
- Integrar documentos académicos mediante RAG.
- Construir un agente académico capaz de consultar datos, modelos y documentos.
- Crear PoCs para validar hipótesis técnicas de IA generativa.
- Comparar modelos, prompts, embeddings y estrategias de recuperación.
- Documentar el sistema como un proyecto profesional de portafolio.

---

## Competencias demostradas

Este proyecto permite demostrar competencias relacionadas con investigación, prototipado y desarrollo aplicado de IA:

- Creación de scripts, notebooks y prototipos.
- Investigación autónoma de herramientas y frameworks.
- Desarrollo de APIs REST para integrar modelos.
- Uso de Git y organización de repositorios.
- Trabajo con Python, PostgreSQL y Django.
- Documentación técnica de arquitectura, experimentos y decisiones.
- Evaluación de modelos predictivos.
- Diseño de flujos RAG.
- Experimentación con embeddings y vector stores.
- Diseño inicial de agentes con tools.
- Preparación de demos y materiales técnicos.

---

## Roadmap

### Fase 1: Sistema base con Machine Learning

- Entrenar modelo predictivo.
- Guardar modelo en formato `.joblib`.
- Crear API REST para predicciones.
- Crear aplicación web en Django.
- Registrar estudiantes.
- Guardar predicciones en PostgreSQL.

### Fase 2: Reportes y análisis

- Agregar historial de predicciones.
- Crear reportes por alumno.
- Agregar gráficas de rendimiento.
- Exportar reportes en PDF o Excel.
- Mostrar factores principales de riesgo.

### Fase 3: Experimentación con IA generativa

- Crear notebooks de prueba con modelos LLM.
- Diseñar prompts para generación de reportes.
- Comparar respuestas entre modelos.
- Documentar resultados, errores y limitaciones.
- Generar reportes académicos en formato estructurado.

### Fase 4: RAG académico

- Cargar documentos PDF.
- Dividir documentos en fragmentos.
- Generar embeddings.
- Almacenar información en Chroma o pgvector.
- Permitir preguntas sobre documentos escolares.
- Responder con fuentes consultadas.
- Evaluar estrategias de chunking y recuperación.

### Fase 5: Agente académico

- Crear tools para consultar alumnos.
- Crear tool para llamar al modelo predictivo.
- Crear tool para consultar documentos mediante RAG.
- Generar reportes automáticos con IA.
- Incluir recomendaciones y advertencias de uso.

### Fase 6: Despliegue

- Crear Dockerfile.
- Configurar Docker Compose.
- Integrar PostgreSQL y pgvector.
- Documentar instalación.
- Preparar despliegue en la nube.

---

## Estado del proyecto

🚧 En desarrollo

Actualmente el proyecto cuenta con un modelo de Machine Learning entrenado y validado. Se encuentra en desarrollo la integración con la aplicación web, la API REST y la base de datos.

La evolución del proyecto contempla la incorporación de RAG, agentes académicos, pruebas con modelos de lenguaje, procesamiento documental y generación automática de reportes.

---

## Autor

Donovan Amaury Alcántara Cruz

Estudiante de Ingeniería en Computación

Universidad Nacional Autónoma de México  
Facultad de Estudios Superiores Aragón

---

## Licencia

Este proyecto tiene fines educativos, académicos y de investigación.
