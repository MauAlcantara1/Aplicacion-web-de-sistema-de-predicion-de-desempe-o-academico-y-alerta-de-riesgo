# Aplicacion-web-de-sistema-de-predicion-de-desempe-o-academico-y-alerta-de-riesgo


# EduPredict - Sistema de Predicción Académica con Machine Learning

## Descripción

**EduPredict** es una aplicación web desarrollada para apoyar la detección temprana de estudiantes con posible bajo rendimiento académico mediante el uso de técnicas de Machine Learning.

El sistema permite que un administrador registre la información académica de un estudiante y obtenga una predicción de su calificación final. A partir de esta predicción, la aplicación clasifica el nivel de riesgo académico del alumno para facilitar la toma de decisiones y el seguimiento oportuno.

El proyecto busca demostrar la integración de un modelo de Machine Learning con una aplicación web utilizando una arquitectura basada en API REST.

---

# Características

* Registro y administración de estudiantes.
* Predicción automática de la calificación final.
* Clasificación del nivel de riesgo académico.
* Historial de predicciones.
* Integración de un modelo de Machine Learning mediante una API REST.
* Arquitectura modular para facilitar futuras mejoras.

---

# Arquitectura

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
                    | Servicio de IA       |
                    +----------+-----------+
                               |
                               |
                     Solicitud de predicción
                               |
                               v
                    +----------------------+
                    |     Django Web App   |
                    +----------+-----------+
                               |
                               |
                               v
                    +----------------------+
                    |     PostgreSQL       |
                    +----------------------+
```

---

# Tecnologías utilizadas

## Machine Learning

* Python
* Google Colab
* Pandas
* NumPy
* Scikit-learn

## Backend

* Django
* Django REST Framework

## Base de datos

* PostgreSQL

## Frontend

* HTML5
* CSS3
* Bootstrap

## Control de versiones

* Git
* GitHub

---

# Flujo del sistema

1. El administrador inicia sesión.
2. Registra los datos del estudiante.
3. La aplicación envía la información a la API REST.
4. El modelo realiza la predicción.
5. La API devuelve la calificación estimada.
6. El sistema almacena la predicción en la base de datos.
7. Se muestra el resultado junto con el nivel de riesgo.

---

# Machine Learning

El modelo fue entrenado utilizando Google Colab a partir de un conjunto de datos académicos.

Actualmente el modelo presenta un error aproximado de:

* **±0.7 puntos** en una escala de **0 a 10**.

Este nivel de precisión permite utilizar el modelo como una herramienta de apoyo para la detección de estudiantes con posible bajo rendimiento.

---

# Estructura del proyecto

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
├── templates/
│
├── static/
│
├── media/
│
├── requirements.txt
│
└── README.md
```

---

# Futuras mejoras

* Panel de estadísticas.
* Gráficas de rendimiento académico.
* Gestión de profesores y grupos.
* Exportación de reportes en PDF y Excel.
* Autenticación con diferentes roles.
* Predicción del riesgo de deserción mediante clasificación.
* Entrenamiento automático de nuevos modelos.
* Dashboard administrativo con indicadores.

---

# Objetivos del proyecto

* Integrar Machine Learning en una aplicación web.
* Automatizar la predicción del desempeño académico.
* Facilitar la identificación temprana de estudiantes en riesgo.
* Implementar una arquitectura basada en API REST.
* Aplicar buenas prácticas de desarrollo Backend y Ciencia de Datos.

---

# Estado del proyecto

🚧 En desarrollo

Actualmente el proyecto cuenta con un modelo de Machine Learning entrenado y validado. Se encuentra en desarrollo la integración con la aplicación web y la API REST.

---

# Autor

**Donovan Amaury Alcántara Cruz**

Estudiante de Ingeniería en Computación

Universidad Nacional Autónoma de México (UNAM)

---

# Licencia

Este proyecto tiene fines educativos y de investigación.
