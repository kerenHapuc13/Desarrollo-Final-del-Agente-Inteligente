ChatRest – Agente Inteligente con FastAPI & NLP

Bienvenido al repositorio oficial de ChatRest, un agente inteligente capaz de interpretar mensajes, extraer entidades, clasificar intenciones y responder dinámicamente sobre un menú de restaurante.
Este sistema utiliza Machine Learning, NLP, FastAPI y un modelo entrenado desde cero.

Estructura del Proyecto
chatrest/
│── app.py
│── database.py
│── entities.py
│── index.html
│── intents.json
│── menu.json
│── model.pkl
│── train_intents.py
│── vectorizer.pkl
│── venv/
│── __pycache__/

1. app.py

Archivo principal del servidor FastAPI.

Incluye:

Endpoint POST /chat

Carga del modelo (model.pkl)

Carga del vectorizador (vectorizer.pkl)

Integración con entities.py

Integración con database.py

Lectura de respuestas desde intents.json

Este archivo se ejecuta con Uvicorn para iniciar el chatbot.

2. database.py

Simula una base de datos local.

Funciones principales:

get_menu(): devuelve los productos almacenados en menu.json.

Se usa cuando el bot detecta la intención consultar_menu.

3. entities.py

Lógica de NLP para extracción de entidades:

Fechas (con dateparser)

Cantidades

Nombres propios

Otros patrones de interés

Sus resultados enriquecen la respuesta final del agente.

4. model.pkl

Modelo de Machine Learning entrenado para clasificar intenciones.
Generado por train_intents.py usando scikit-learn.

Detecta intenciones como saludo, despedida, consultar menú, entre otras.

5. vectorizer.pkl

Vectorizador TF-IDF utilizado para convertir texto en vectores numéricos.
Debe usarse siempre junto al modelo entrenado para garantizar compatibilidad.

6. intents.json

Archivo que define los intents del chatbot.

Ejemplo:

{
  "tag": "saludo",
  "patterns": ["hola", "buenas", "qué tal"],
  "responses": ["¡Hola! ¿Cómo puedo ayudarte hoy?"]
}

7. menu.json

Base de datos del menú del restaurante.

Ejemplo:

{
  "name": "Pizza Pepperoni",
  "price": 28.0
}

8. train_intents.py

Script encargado de entrenar el modelo desde cero.

Realiza:

Carga de intents.json

Limpieza y construcción del dataset

Vectorización TF-IDF

Entrenamiento del clasificador

Guardado de model.pkl y vectorizer.pkl

Debe ejecutarse cada vez que se agreguen o modifiquen intents.

9. index.html

Interfaz HTML simple para probar el chatbot desde el navegador.

10. venv/

Entorno virtual del proyecto.
No se recomienda subirlo a GitHub.

11. pycache/

Archivos generados automáticamente por Python.

Dependencias

Instalar las dependencias necesarias:

pip install fastapi uvicorn scikit-learn python-dateutil dateparser joblib

Cómo Ejecutar el Proyecto
1. Activar el entorno virtual
venv\Scripts\activate

2. Ejecutar el servidor
uvicorn app:app --reload



4. Probar una petición

Body JSON:

{
  "message": "Muéstrame el menú"
}

Re-Entrenamiento del Modelo

Si agregas nuevos intents o modificas los existentes:

python train_intents.py


Esto generará nuevamente:

model.pkl

vectorizer.pkl

Reproducibilidad

Este repositorio incluye todo lo necesario para replicar el proyecto:

intents.json y menu.json

train_intents.py

model.pkl y vectorizer.pkl

Código del servidor FastAPI

Scripts complementarios (database.py, entities.py)

Licencia

Proyecto de uso académico.
Permitido para fines educativos, entregas y mejorías.

Autoras

Keren Saray Subiroz Galván

Keren Hapuc Subiroz Galván
