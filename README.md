# Amazon Reviews en español · Sesión 3 PLN

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

## Temas de la Sesión 3

El notebook explica cada decisión antes de mostrar sus resultados:

1. Ruta de trabajo, procedencia y etapas de auditoría.
2. Vocabulario aprendido únicamente con train y cobertura de palabras.
3. PAD (`0`) y OOV/UNK (`1`): ausencia frente a palabra desconocida.
4. Padding y truncamiento, con ejemplos reales, IDs y máscaras.
5. Por qué limitar vocabulario y longitud; qué información se pierde.
6. Masking y una comprobación de invariancia al añadir PAD.
7. Embeddings entrenables: dimensiones, parámetros y gradientes.
8. SimpleRNN, LSTM, GRU y BiLSTM, comparadas con TF-IDF.
9. Patrón **many-to-one**, distinguido de many-to-many alineado y sequence-to-sequence.
10. Conclusiones calculadas, errores por clase y pruebas de robustez.

La robustez usa 200 reseñas de test, **40 por estrella**, con semilla fija. El archivo
está ordenado por clase: tomar sus primeras filas sesgaría esta comprobación. Se comparan
las reseñas originales con mayúsculas/espacios, ausencia de tildes y una errata. Las
variantes modificadas son pruebas controladas; no forman parte del entrenamiento.

Todo el código está dentro del notebook. Los datos y modelos se generan localmente
en `amazon_reviews_es/`; no es necesario subir ni descargar otras carpetas.

## Material para estudiar y presentar

La carpeta [Entrega_Amazon_Sesion_3](Entrega_Amazon_Sesion_3) contiene cuatro documentos
opcionales. **No se necesitan para ejecutar el notebook.** Adaptan el formato del paquete
de la Sesión 2 al análisis actual, con cifras de esta ejecución:

| Archivo | Propósito |
|---|---|
| [Informe de resultados](Entrega_Amazon_Sesion_3/Explicacion_detallada_resultados_Sesion_3_PLN.pdf) | Auditoría, fundamentos, comparación, curvas, errores, robustez y conclusiones |
| [Presentación](Entrega_Amazon_Sesion_3/Presentacion_Amazon_RNN_LSTM_GRU_Sesion_3.pdf) | 12 diapositivas para explicar el experimento |
| [Pitch](Entrega_Amazon_Sesion_3/Pitch_Amazon_RNN_LSTM_GRU_Sesion_3.pdf) | Guion de 5–6 minutos, reparto propuesto y preguntas frecuentes |
| [Mapa interactivo](Entrega_Amazon_Sesion_3/Amazon_Sesion_3_Mapa_Interactivo.html) | Pestañas, demostración de longitud, comparación de modelos y revisión de errores |

Para usar el mapa, descargue el HTML con **Download raw file** y ábralo en su navegador.
GitHub muestra su código, no ejecuta el HTML. El archivo funciona sin internet, salvo
los enlaces externos; sus controles visualizan resultados guardados y no entrenan modelos.

Puede compartir el enlace de Colab para ejecutar, o el enlace de esta página para consultar
la entrega completa. También puede descargar todo desde **Code → Download ZIP**.

## Datos y límites

Fuente: [SetFit/amazon_reviews_multi_es](https://huggingface.co/datasets/SetFit/amazon_reviews_multi_es),
revisión `16015418b488c9186fce74b058877ea939ca934d`. Las huellas de los archivos están integradas en el
notebook y se verifican al descargar. No se generan ejemplos sintéticos. No se ejecutan
scripts remotos. Las estrellas aproximan satisfacción, no sentimiento perfecto.
La limpieza modifica el benchmark original y no garantiza separación por producto/autor.

La elección usa validación; test se consulta al final. Una sola semilla no prueba
superioridad estadística. En la ejecución local de referencia, TF-IDF obtuvo F1 macro
aproximado 0,494 y accuracy 50,1 %. Los tiempos y resultados pueden variar por entorno.
La versión ampliada de la Sesión 3 se ejecutó localmente: 18 celdas de código sin errores,
incluidos los cinco modelos, controles de masking/gradientes, robustez y recarga.
No se afirma una ejecución verificada
en una sesión remota de Colab. Las condiciones del corpus original siguen aplicando.
