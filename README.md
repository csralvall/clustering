# Clustering

> Trabajo perteneciente a la cátedra "Text Mining" de Laura Alonso Alemany - FaMAF UNC. 2021

- _Corpus:_ compendio de noticias de "La Voz del Interior"
- _Referencias:_ 
    - [word_clustering](https://github.com/danibosch/word_clustering) 
    de [@danibosch](https://github.com/danibosch)
    - [textmining-clustering](https://github.com/facumolina/textmining-clustering) 
    de [@facumolina](https://github.com/facumolina/textmining-clustering)

## Configuracion:
    1. Descomprimir el archivo `lavoztextodump.txt.tar.gz` en el mismo
       directorio del jupyter-notebook.
    2. Ejecutar: 
    ```bash
    pip install -U pip wheel setuptools spacy numpy sklearn
    ```
    ```bash
    python -m spacy download es_core_news_sm
    ```
    3. Abrir jupyter y ejecutar el notebook.

## Etapas:

#### 1. Preprocesamiento:
   1. Limpieza del dataset:
   
       Se quitan simbolos no alfanumericos mediante regex.
       
       
   2. Procesamiento con el pipeline de spacy:
   
       El pipeline de spacy ejecuta las siguientes tareas:
       - Segmentacion en tokens.
       - Vectorizacion.
       - Analisis morfologico (genero, numero, etc.).
       - Analisis de dependencias.
       - Clasificacion por reglas.
       - Lematizacion.
       - Clasificacion de entidades.
       - Conteo de frecuencias de lemas (agregado).
       
       
   3. Filtrado:
   
      Se busca un subconjunto de tokens
      que cumplan las siguientes caracteristicas:
       - no contiene caracteres no alfabeticos
       - no es "stop word"
       - no expresa un numero
       
       
   4. Generacion de **features**:
   
      Por cada palabra del conjunto procesado en el paso anterior 
      generar un conjunto de features de acuerdo con:
       - el tipo de palabra.
       - su funcion sintactica.
       - su coocurrencia con palabras en su misma oracion (contexto).
       - el tipo de entidad que es, en el caso que lo sea.
       - la dependencia con su predecesor sintactico en el arbol de dependencias.
       
       
   5. Separacion de palabras y features.
   6. Vectorizacion de features.
   7. Normalizacion de features.
    

#### 2. Clusterizacion:
   1. Eleccion del numero de clusters.
   2. Seleccion del estado aleatorio para obtener resultados deterministicos.
   3. Instanciacion del algoritmo KMeans para obtener los clusters.
    
#### 3. Resultados:
   1. Conteo de palabras por cluster.
   2. Listado de clusters con la siguiente informacion:
      - Numero de cluster.
      - Features mas determinantes para ese cluster.
      - Palabras dentro del cluster.
