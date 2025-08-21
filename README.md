<img src="https://github.com/hernancontigiani/ceia_memorias_especializacion/raw/master/Figures/logoFIUBA.jpg" width="500" align="center">

Procesamiento del Lenguaje Natural 1

Es una materia de la especialización en Inteligencia Artificial de la Universidad de Buenos Aires (UBA). 
Introduce los fundamentos del procesamiento de lenguaje natural. A lo largo de la cursada se abordan técnicas y herramientas clave para la representación, análisis y modelado del lenguaje humano mediante algoritmos computacionales.
La cursada de la materia se evaluó mediante cuatro desafios a realizar y los mismos fueron los siguientes: 

Desafío 1

Se abordó la clasificación de texto en 20 Newsgroups mediante un flujo simple y reproducible: limpieza básica, representación TF-IDF y entrenamiento de modelos clásicos (Naive Bayes y lineales). Se evaluó con train/test split y métricas F1/accuracy, a fin de comprender el recorrido esencial texto → vectores → clasificador y su eficiencia frente a enfoques más complejos.

Desafío 2

Se construyeron embeddings propios a partir de un corpus de letras mediante Word2Vec (Gensim), tras normalización y tokenización con NLTK. La calidad semántica de los vectores se examinó con vecinos más cercanos y visualizaciones (PCA/t-SNE), destacando el paso de representaciones dispersas a representaciones densas que capturan relaciones léxicas y de contexto.

Desafío 3

Se entrenó un modelo de lenguaje a nivel carácter con LSTM/GRU para predecir el siguiente carácter, usando ventanas deslizantes y teacher forcing. La capacidad generativa se exploró mediante greedy y beam search, evidenciando cómo el modelo aprende patrones ortográficos y estilísticos del corpus.

Desafío 4

Se desarrolló un chatbot seq2seq con atención: preprocesamiento completo (tokens <sos>/<eos>, diccionarios word2idx, padding/máscara), encoder BiLSTM con GloVe fijo, atención con máscara y tied output projection. Se entrenó con EarlyStopping/ReduceLROnPlateau y finetuning por fases; en inferencia se aplicaron greedy, beam (con length penalty) y sampling (temperatura, top-k/top-p), incorporando copy bias para mantener foco en el contenido de entrada.
