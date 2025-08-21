<img src="https://github.com/hernancontigiani/ceia_memorias_especializacion/raw/master/Figures/logoFIUBA.jpg" width="500" align="center">

Procesamiento del Lenguaje Natural 1

Procesamiento del Lenguaje Natural 1 es una materia de la especialización en Inteligencia Artificial de la Universidad de Buenos Aires (UBA). 
Introduce los fundamentos del procesamiento de lenguaje natural. A lo largo de la cursada se abordan técnicas y herramientas clave para la representación, análisis y modelado del lenguaje humano mediante algoritmos computacionales.
La cursada de la materia se evaluó con cuatro desafios y los mismos fueron los siguientes: 

Desafío 1

En el Desafío 1 abordamos una tarea de clasificación de texto con el dataset 20 Newsgroups (cargando con fetch_20newsgroups y removiendo headers/footers/quotes para reducir ruido). Aplicamos un preprocesamiento liviano y representamos los documentos mediante TF-IDF (bag-of-words), priorizando una canalización simple y reproducible. Entrenamos modelos clásicos de NLP tradicional, en particular Naive Bayes (Multinomial/Complement) y clasificadores lineales, evaluando con train/test split y métricas como F1 y accuracy. El objetivo fue entender de punta a punta el flujo básico —de texto crudo a vectores y a un clasificador— y apreciar su eficiencia y relación costo/beneficio frente a alternativas más complejas.

Desafío 2

En el Desafío 2 trabajamos en NLP distribuido: construir embeddings propios (vectores densos) a partir de un corpus de letras —p. ej., Eminem—. El flujo incluyó descompresión y carga del corpus, normalización y tokenización con NLTK (minúsculas, limpieza, stopwords) y la preparación de oraciones tokenizadas para entrenar un modelo tipo Word2Vec (CBOW/Skip-gram) con Gensim. El objetivo conceptual fue pasar de representaciones dispersas (TF-IDF del desafío anterior) a representaciones semánticas continuas, evaluando la calidad de los vectores mediante vecinos más cercanos/similitud y, opcionalmente, reducciones PCA/t-SNE para visualizar la estructura. Con esto se entiende cómo entrenar, guardar y reutilizar embeddings propios y por qué capturan relaciones léxicas/contextuales que mejoran tareas posteriores.

Desafío 3

En el Desafío 3 construimos un modelo de lenguaje a nivel carácter: partiendo de un corpus de texto, hicimos limpieza y tokenización por caracteres, armamos los diccionarios carácter↔índice y generamos ventanas deslizantes para el entrenamiento (X = secuencias de longitud fija, y = siguiente carácter). Entrenamos redes recurrentes (LSTM/GRU) con embeddings/caracteres para predecir el próximo carácter (aprendizaje autorregresivo con teacher forcing), monitoreando loss / val_loss. Finalmente, evaluamos la calidad generativa con decodificación greedy y beam search, que permiten sintetizar texto desde un seed y observar cómo el modelo captura patrones ortográficos y estilísticos del corpus.

Desafío 4

En el Desafío 4 desarrollamos un chatbot seq2seq con atención en Keras/TensorFlow: partimos de data_volunteers.json, hicimos el preprocesamiento completo (normalización, tokenización, diccionarios word2idx separados para entrada y salida, inserción de <sos>/<eos>, y armado de encoder_input_sequences, decoder_output_sequences y decoder_targets, con longitudes p95/p99 y padding/máscara). En el modelo usamos encoder bidireccional (LSTM), embeddings GloVe fijos en el encoder, puente de estados al decoder, atención con máscara para ignorar <pad>, tied output projection (pesos de salida atados a la matriz de embedding del decoder) y layer norm. Entrenamos con teacher forcing, EarlyStopping + ReduceLROnPlateau, y dos/tres fases de finetuning; registramos loss/val_loss y accuracy y guardamos artefactos (diccionarios, matrices de embedding, pesos). Para inferencia separamos encoder_infer y decoder_infer y probamos greedy, beam search (con length penalty, mínima longitud y bloqueo de n-gramas repetidos) y sampling (temperatura, top-k/top-p), añadiendo un copy/lexical bias para favorecer términos del input, logrando respuestas más centradas y fluidas.
