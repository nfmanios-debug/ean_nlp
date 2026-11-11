# Amazon Reviews en español · PLN

[![Abrir en Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/nfmanios-debug/ean_nlp/blob/main/NLP_Amazon_Reviews_ES.ipynb)

**Un solo notebook, sin archivos adicionales.** Compara TF-IDF + regresión logística,
SimpleRNN, LSTM, GRU y BiLSTM para predecir de 1 a 5 estrellas con reseñas reales.

## En Colab

1. Pulse **Abrir en Colab**.
2. Conecte una sesión y seleccione **Entorno de ejecución → Ejecutar todas**.
3. Espere a que termine. El notebook prepara las librerías y descarga los datos.

No necesita cargar CSV, copiar scripts, proporcionar claves ni montar Google Drive.
La primera ejecución necesita internet. Puede tardar varios minutos. Descargue el
notebook ejecutado para conservar sus salidas antes de cerrar la sesión de Colab.

## En VS Code

1. Descargue [NLP_Amazon_Reviews_ES.ipynb](NLP_Amazon_Reviews_ES.ipynb).
2. Ábralo con las extensiones **Python** y **Jupyter** instaladas.
3. Seleccione un kernel Python 3.10–3.13 (verificado con 3.11) y pulse **Run All**.

El notebook instala las librerías ausentes en el kernel elegido. Si no tiene un
kernel disponible, VS Code puede solicitar instalar `ipykernel`. Recomendamos un
entorno virtual para separar las dependencias de otros proyectos. Si una actualización
de librerías precargadas requiere reiniciar, el notebook lo indicará explícitamente.
Para repetir desde cero, reinicie el kernel antes de Run All.

## Qué muestra

- Fuente real, etiquetas y auditoría de duplicados/conflictos.
- 20.000 reseñas de entrenamiento y 4.905 por conjunto de validación/prueba limpio.
- Explicación de los cinco modelos, embeddings, secuencias y sobreajuste.
- Accuracy, F1 macro, precision, recall, log loss, error en estrellas y tiempos.
- Curvas, matrices, errores reales y análisis por longitud y negaciones.

Todo el código está dentro del notebook. Los datos y modelos se generan localmente
en `amazon_reviews_es/`; no es necesario subir ni descargar otras carpetas.

## Datos y límites

Fuente: [SetFit/amazon_reviews_multi_es](https://huggingface.co/datasets/SetFit/amazon_reviews_multi_es),
revisión `16015418b488c9186fce74b058877ea939ca934d`. Las huellas de los archivos están integradas en el
notebook y se verifican al descargar. No se generan ejemplos sintéticos. No se ejecutan
scripts remotos. Las estrellas aproximan satisfacción, no sentimiento perfecto.
La limpieza modifica el benchmark original y no garantiza separación por producto/autor.

La elección usa validación; test se consulta al final. Una sola semilla no prueba
superioridad estadística. En la ejecución local de referencia, TF-IDF obtuvo F1 macro
aproximado 0,494 y accuracy 50,1 %. Los tiempos y resultados pueden variar por entorno.
La variante autónoma se comprueba localmente; no se afirma una ejecución verificada
en una sesión remota de Colab. Las condiciones del corpus original siguen aplicando.
