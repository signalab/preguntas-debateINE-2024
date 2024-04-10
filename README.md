# preguntas-debateINE-2024
Documentación técnica sobre el proceso de Selección de Preguntas de Redes Sociales para el 1er Debate Presidencial INE 2024 (Formato A), realizado por Signa_Lab ITESO, por encargo del Instituto Nacional Electoral (INE), en el marco del proceso electoral 2023-2024 en México.

## Tabla de Contenidos
1. [Presentación](#presentación)
2. [Etapas de la Metodología](#etapas-de-la-metodología)
3. [Anexos en este repositorio](#anexos-en-este-repositorio)
4. [Análisis exploratorio de datos recibidos](#análisis-exploratorio-de-datos-recibidos)
5. [Dependencias e instalación](#dependencias-e-instalación)
6. [Otras herramientas utilizadas](#otras-herramientas-utilizadas)
7. [Licencia](#licencia)
8. [Créditos](#créditos)
9. [Referencias](#referencias)

---

## Presentación
Para el primer Debate Presidencial del domingo 7 de abril de 2024, organizado por el Instituto Nacional Electoral (INE) y titulado “La Sociedad que Queremos”, se dispuso un formulario digital para que la ciudadanía pudiera hacer preguntas sobre cada uno de los temas propuestos para el mismo. Para el procesamiento y selección de preguntas a considerar por las personas moderadoras del Debate, el INE diseñó una metodología específica para el Formato A de este primer debate (INE, 2024) y designó a una institución académica externa, Signa_Lab ITESO, para obtener 18 preguntas seleccionadas por frecuencia, representativas de cada tema, y 90 seleccionadas por aleatoriedad, distribuidas por cada región del país (Norte, Centro y Sur).

**Nota:** El Informe Final completo sobre este proyecto, así como los anexos con el código y todos los datos con los que se realizó el trabajo, se entregó por parte de Signa_Lab ITESO al INE el día 10 de abril de 2024. El presente repositorio contiene la totalidad del código desarrollado para el proyecto, documentado en cuadernos de Python (Jupyter Notebook), y un archivo de datos, en formato CSV, con el diccionario de términos proscritos utilizados para la depuración inicial.


Los temas definidos por el INE para este primer debate presidencial fueron:
- Educación
- Salud
- Combate a la corrupción
- Transparencia
- No discriminación y grupos vulnerables
- Violencia en contra de las mujeres

La metodología indicaba seleccionar **108 preguntas, 18 por frecuencia y 90 por aleatoriedad**, distribuidas de la siguiente manera:

### 18 Preguntas Seleccionadas por Frecuencia:
| Tema                                                  | Número de preguntas |
|-------------------------------------------------------|---------------------|
| Educación                                             | 3 preguntas         |
| Salud                                                 | 3 preguntas         |
| Combate a la corrupción                               | 3 preguntas         |
| Transparencia                                         | 3 preguntas         |
| No discriminación y grupos vulnerables                | 3 preguntas         |
| Violencia en contra de las mujeres                       | 3 preguntas         |


### 90 Preguntas Seleccionadas por Aleatoriedad:

| Tema                                                  | Región del país | Número de preguntas |
|-------------------------------------------------------|------------------|---------------------|
| Educación                                             | Norte, Sur y Centro | 15 preguntas (5 por región)       |
| Salud                                                 | Norte, Sur y Centro | 15 preguntas (5 por región)         |
| Combate a la corrupción                               | Norte, Sur y Centro | 15 preguntas (5 por región)         |
| Transparencia                                         | Norte, Sur y Centro | 15 preguntas (5 por región)         |
| No discriminación y grupos vulnerables                 | Norte, Sur y Centro | 15 preguntas (5 por región)         |
| Violencia en contra de las mujeres                       | Norte, Sur y Centro | 15 preguntas (5 por región)         |
 
---

## Etapas de la Metodología
A partir de la metodología diseñada por el INE para la [Selección de Preguntas del Debate Presidencial Formato A](https://repositoriodocumental.ine.mx/xmlui/bitstream/handle/123456789/164296/CGex202402-08-ap-3-a1.pdf), se definió un plan de trabajo por etapas que se resume a continuación:

### Etapa 0. Entrega de base de datos
El INE entregó a representantes del ITESO una base de datos, en dos archivos de formato Excel, con los **13,484 registros** que contenían las **24 mil preguntas** que el instituto recolectó en su sitio web durante el mes que estuvo abierta la convocatoria para que los ciudadanos y ciudadanas pudieran formular sus preguntas. Esta base de datos fue transportada a Guadalajara, donde, bajo la supervisión de expertos en ciberseguridad del ITESO, se aseguró su integridad y se descargó en sistemas aislados de la red, siguiendo las estrictas medidas de seguridad solicitadas por el INE.
 
### Etapa 1. Preparación de la base de datos 
Esta fase estuvo dedicada a que el equipo revisara y depurara la base de datos. Para llevar a cabo este proceso se realizaron dos acciones. La primera consistió en el desarrollo de un diccionario de términos proscritos, elaborado por el equipo de Signa_Lab ITESO en atención a los criterios del INE, que ayudara a identificar preguntas que contenían lenguaje ofensivo o bien sesgos políticos, para cumplir con los criterios de elegibilidad definidos por el INE. El diccionario final estuvo compuesto por 519 de estos términos; como resultado de este proceso, **se eliminaron 1,117 preguntas**. La segunda fase fue utilizar código informático que permitiera detectar aquellas preguntas cuya redacción fuera idéntica, para catalogarlas como repetidas. A partir de la utilización de este código se descartaron **1,664 preguntas duplicadas**. Cabe aclarar que se eliminaron las repeticiones, pero sí se incluyó una instancia de cada pregunta duplicada para ser tomada en cuenta para los siguientes procesos. Mediante estas dos fases, el equipo depuró eficazmente la base de datos, lo cual arrojó un **total de 21,219 preguntas** libres de términos proscritos y duplicados.
 
### Etapa 2. Obtención de la muestra estratificada y clasificación por región 
El propósito de la segunda etapa fue obtener una muestra estratificada para la selección de preguntas. El formulario creado por el INE para la captura de preguntas de los ciudadanos se basó en dos criterios esenciales: temático y territorial. En el aspecto temático, los participantes seleccionaron uno de los temas sugeridos para el debate, y pudieron formular una pregunta pertinente a esa categoría. Respecto al criterio territorial, debían especificar la entidad del país desde la cual realizaron su consulta, la cual fue categorizada posteriormente por el INE como perteneciente a región norte, centro o sur. El equipo de Signa_Lab ITESO implementó una fórmula estadística que arrojó una muestra estratificada por tema y por región **compuesta por 1,701 preguntas**, que representan fielmente la distribución por región y por tema de las 21,219 preguntas depuradas en la etapa anterior.
 
### Etapa 3. Selección de las preguntas
En esta etapa se llevó a cabo un ejercicio computarizado, a través de herramientas de inteligencia artificial y de lingüística de corpus, para la preselección de preguntas. El proceso incluyó el desarrollo de un algoritmo, con la implementación de un modelo de lenguaje de software libre, que permitió la identificación de similitud semántica entre las preguntas de la muestra estratificada. Este algoritmo analizó 1,024 dimensiones dentro de cada pregunta y con ello, las agrupó en clústeres a partir de sus similitudes. Como resultado de este trabajo, se extrajeron **18 preguntas preseleccionadas por frecuencia y 90 preguntas preseleccionadas aleatoriamente**.
 
### Etapa 4. Revisión de preguntas
En la cuarta etapa, el equipo de Signa_Lab ITESO realizó una revisión manual de las 108 preguntas seleccionadas, con el acompañamiento y supervisión del cumplimiento de criterios de elegibilidad por parte de la representación del INE. Durante la primera ronda de revisión, se identificó que 28 preguntas tenían errores de coherencia argumentativa, de sintaxis, de neutralidad y/o de pertinencia temática. Estas características están claramente señaladas como criterios de invalidación en la metodología del INE, por lo que se procedió a su eliminación y reemplazo por otras de la muestra estratificada por tema y región. Es importante señalar que los motivos de reemplazo de las preguntas no se debieron a errores en el proceso de depuración, sino a fallos y sesgos de origen en el propio registro de la ciudadanía. En la revisión subsiguiente de las nuevas 28 preguntas, 11 aún contaron con alguno de estos criterios para ser invalidadas. Un tercer y cuarto ejercicio de revisión resultaron en la eliminación de dos y una pregunta, respectivamente, por contener alguna de estas cualidades. La **tasa total de reemplazo fue del 2.47%** en relación con las 1,701 preguntas de la muestra estratificada.

### Etapa 5 Plazos establecidos
Esta es una etapa transversal en el proyecto. Para cumplir con esta etapa, se diseñó un plan de trabajo bajo el acompañamiento de la Coordinación Nacional de Comunicación Social (CNCS) y de la Oficialía Electoral del INE. Durante los días 22 al 29 de marzo, se produjeron bitácoras diarias detallando las actividades sucedidas en las jornadas de procesamiento de la base de datos en Signa_Lab ITESO, de las que dio fe la representación de la Oficialía Electoral del INE.


### Etapa 6 Informe final
La última etapa del proyecto consiste en la redacción de un Informe Final, 9 días posteriores a la entrega de las preguntas. En dicho informe se desarrolló a detalle la metodología aplicada y se acompañó de una serie de anexos con los datos procesados, el código desarrollado, compilaciones de gráficas generadas tras el análisis exploratorio de datos en distintas etapas y las bitácoras de trabajo diario del 22 al 29 de marzo.

---

## Anexos en este repositorio
En el directorio de Anexos de este repositorio, se encuentran todos los cuadernos de código utilizados para las distintas etapas del proceso y el diccionario de términos proscritos para la depuración inicial, desarrollados por Signa_Lab ITESO.

**Nota:** En este repositorio se publica el código necesario para replicar el ejercicio con los datos en el formato en que fueron entregados originalmente a Signa_Lab ITESO. Los conjuntos de datos procesados a lo largo de cada una de las etapas se entregaron al INE en el Informe Final de este proyecto, para asegurar la transparencia, trazabilidad y replicabilidad del ejercicio ante la autoridad electoral, misma que es la institución competente para definir la modalidad y canales adecuados para hacer pública dicha información.

### Cuadernos de Código (*Jupyter Notebooks*)
#### [Cuaderno 01. Depuración, A.E.D. y Elaboración de Muestra Estratificada](anexos/01_Signa_Lab_DebateINE2024_Depuración_AED_Muestra_repo.ipynb)
  - Procesamiento y concatenación de registros originales (13,484 entradas a formulario del INE)
  - Análisis exploratorio de datos de 13,484 registros recibidos (por región, entidad, edad, género, grupos en situación de discriminación, fecha de entrada)
  - Extracción de 24,000 preguntas de los 13,484 registros recibidos, asignación de IDs y exportar archivo de datos tabulares (CSV) con 24,000 preguntas originales.
  - Limpieza y procesamiento de texto para identificación de similitud y análisis semántico (remover *stop words*)
  - Depuración de preguntas desde diccionarios con términos proscritos de acuerdo a metodología del INE (1,117 preguntas).
  - Depuración de preguntas por repeticiones exactas en su formulación sin *stop words* (1,664 preguntas).
  - Concatenar tabla y exportar archivo de datos tabulares (CSV) con preguntas descartadas, con su respectivo razonamiento (2,781 preguntas).
  - Consolidar tabla y exportar archivo de datos tabulares (CSV) con 21,219 preguntas de población depurada.
  - Análisis exploratorio de datos de población depurada de 21,219 preguntas (por tema, región, entidad, edad, género, grupos en situación de discriminación).
  - Cálculo y elaboración de muestra estratificada.
  - Extracción aleatoria de 1,701 preguntas por región y tema, de acuerdo al cálculo de la muestra estraficada. 
  - Consolidar y exportar archivo de datos tabulares (CSV) con 1,701 preguntas de muestra estratificada.


#### [Cuaderno 02.  Generación de Relaciones Semánticas (*Embeddings*)](anexos/02_Signa_Lab_DebateINE2024_Generación_embeddings-repo.ipynb)
  - Importar conjuntos de datos de preguntas por tema en muestra estratificada (1,701 preguntas).
  - Importar modelo de lenguaje, [intfloat/multilingual-e5-large-instruct](https://huggingface.co/intfloat/multilingual-e5-large-instruct/tree/main), desde su ejecución local, para el procesamiento de relaciones semánticas (*embeddings*).
  - Procesamiento individual del conjunto de preguntas de cada tema en la muestra estratificada para generar relaciones semánticas (*embeddings*) de 1,024 dimensiones.
  - Consolidar tablas y exportar archivo de datos tabulares (CSV) con relaciones semánticas generadas por pregunta de cada tema en la muestra.

#### Cuaderno 03. Análisis Semántico, Selección por Frecuencia y por Aleatoriedad (6 versiones distintas, 1 por cada tema del debate: [Combate a la Corrupción](anexos/03_Signa_Lab_DebateINE2024_Análisis_semántico_selección_frecuencia_aleatoriedad_Corrupcion-repo.ipynb), [Educación](anexos/03_Signa_Lab_DebateINE2024_Análisis_semántico_selección_frecuencia_aleatoriedad_Educacion-repo.ipynb), [No discriminación y grupos vulnerables](anexos/03_Signa_Lab_DebateINE2024_Análisis_semántico_selección_frecuencia_aleatoriedad_NoDiscriminacion-repo.ipynb), [Salud](anexos/03_Signa_Lab_DebateINE2024_Análisis_semántico_selección_frecuencia_aleatoriedad_Salud-repo.ipynb), [Transparencia](anexos/03_Signa_Lab_DebateINE2024_Análisis_semántico_selección_frecuencia_aleatoriedad_Transparencia-repo.ipynb), [Violencia en contra de las mujeres](anexos/03_Signa_Lab_DebateINE2024_Análisis_semántico_selección_frecuencia_aleatoriedad_ViolenciaMujeres-repo.ipynb))
  - Importar conjunto de datos de preguntas por tema en muestra estratificada con relaciones semánticas generadas (*embeddings*), de 1,024 dimensiones.
  - Importar modelo de lenguaje, [intfloat/multilingual-e5-large-instruct](https://huggingface.co/intfloat/multilingual-e5-large-instruct/tree/main), desde su ejecución local, para realizar consultas semánticas basadas en las relaciones calculadas (*embeddings*).
  - Aplicar algoritmo de reducción de dimensionalidades (UMAP) para agregar nueva columna a lo datos importados con relaciones semánticas de 3 dimensiones, para orientar su clusterización y visualización.
  - Definir número de clústeres (grupos de preguntas similares por tema) a procesar a partir de la implementación cruzada de dos métodos para la evaluación del número óptimo de clústeres (Método del Codo y Método de Silueta).
  - Aplicar algoritmo de clusterización (K-means) a partir del número de clústeres definido previamente para el tema en paso anterior.
  - Visualizar relaciones semánticas y clústeres en 3D de preguntas del tema
  - Calcular frecuencias ponderadas de enegramas (por palabra TF-IDF, bigramas y trigramas) de la muestra completa del tema y de cada uno de los 3 clústers con mayor número de preguntas (preguntas similares con mayor frecuencia en el tema).
  - Cotejar resultados de análisis de enegramas y utilizarlos para formular consultas semánticas por cada clúster.
  - Revisar listado de preguntas más afines a cada consulta semántica y elegir aquellas que son más representativas de la temática identificada (núcleo semántico) y que mejor cumplen con criterios de claridad, buena sintaxtis y neutralidad (con el acompañamiento y supervisión de la representación del INE).
  - Indicar IDs de 3 preguntas elegidas por frecuencia, 1 por cada uno de los 3 clústeres más grandes, y retirarla del resto de la muestra del tema para evitar su reaparición en la selección por aleatoriedad.
  - Realizar selección aleatoria de 5 preguntas por región del tema, con la implementación de una “semilla” (*seed number*) para garantizar la transparencia, trazabilidad y replicabilidad de la extracción aleatoria efectuada.
  - Concatenar tabla de preguntas elegidas por frecuencia y por aleatoriedad del tema y exportar archivo de datos tabulares (CSV) con 18 preguntas preseleccionadas para su revisión.

#### [Cuaderno 04. Revisión de preguntas](anexos/04_Signa_Lab_DebateINE2024_Revisión_de_preguntas-repo.ipynb)
  - Importar conjunto de datos con 108 preguntas preseleccionadas por frecuencia y aleatoriedad de todos los temas, con revisión manual aplicada, donde se verificó por cada pregunta, con el acompañamiento y supervisión de personas representantes del INE, el cumplimiento de criterios definidos en la metodología. En el caso de las preguntas en las que se identificó su necesidad de reemplazo, se indicó el razonamiento por cada una. A su vez, para el caso de las preguntas aprobadas en revisión, con la supervisión y aprobación de la representación del INE, se realizaron ajustes mínimos de redacción, puntuación y ortografía, procurando respetar al máximo el sentido original de la pregunta, para facilitar su lectura por parte de la moderación del debate.
  - Inicializar contador para tasa de reemplazo (en 0), a sumar por cada ronda de revisión y calcular la tasa de reemplazo global, con base en la muestra estratificada de 1,701 preguntas.
  - Para el caso de reemplazos de preguntas preseleccionadas por frecuencia (que solo fue necesario en la 1ra ronda de revisión), indicar IDs de pregunta a reemplazar y a alternativa a incorporporar, después realizar de nuevo el análisis semántico del tema y clúster correspondiente.
  - Para el caso de reemplazos de preguntas preseleccionadas por aleatoriedad, fijar una semilla para garantizar la replicabilidad de la extracción aleatoria y reemplazar las preguntas indicadas con necesidad de reemplazo en revisión manual, tomando sus respectivos datos de región y tema para la selección de la alternativa correspondiente para cada pregunta reemplazada, de acuerdo a la distribución requerida por la metodología para preguntas aleaotorias.
  - Consolidar tabla y exportar archivo de datos tabulares (CSV) con nueva preselección de preguntas con reemplazos efectuados.
  - Repetir proceso de revisión y reemplazos (se requirieron 5 rondas de revisión) hasta conseguir 108 preguntas que, bajo la validación de las personas representantes del INE, cumplen a cabalidad con los criterios de selección definidos en la metodología.
  - Cerrar cálculo de tasa de reemplazo, que resultó en 2.74% con base en el tamaño de la muestra estratificada de 1,701 preguntas seleccionables.
  - Consolidar tabla y exportar archivo de datos tabulares (CSV) con selección de 108 preguntas seleccionadas para revisión final.

#### [Cuaderno 05. Análisis exploratorio de resultados](anexos/05_Signa_Lab_DebateINE2024_Análisis_Exploratorio_Resultados-repo.ipynb)
  - Importar conjuntos de datos exportados etapas anteriores (13,484 registros en formulario, 24,000 preguntas sin depurar, 2,781 preguntas descartadas, 21,219. preguntas en población depurada, 1,701 preguntas en muestra estratificada).
  - Análisis exploratorio de datos de 13,484 registros recibidos (por región, entidad, edad, género, grupos en situación de discriminación, fecha de entrada).
  - Análisis exploratorio de datos de población depurada de 21,219 preguntas (por tema, región, entidad, edad, género, grupos en situación de discriminación), así como de relación y razonamiento de depuración de las 2,781 preguntas descartadas.

#### [Diccionario desarrollado por Signa_Lab ITESO para depuración de preguntas por términos proscritos](anexos/anexos/debateINE_diccionarios_depuracion_25mar_1406hrs.csv)
Signa_Lab ITESO desarrolló un diccionario de términos proscritos para la depuración de preguntas para el debate presidencial. Este diccionario integró elementos de un lexicón de términos ofensivos previamente elaborado por el laboratorio (Signa_Lab, 2022), diccionarios externos y términos ofensivos extraídos de conjuntos de datos masivos de redes sociales del repositorio de descargas de Signa_Lab ITESO, como parte del trabajo continuo de monitoreo y análisis del laboratorio.

El diccionario se dividió en términos ofensivos y en términos referidos a sesgos partidistas (menciones a candidaturas, partidos políticos y presidentes de partidos), ideológicos y de religión. Las pruebas llevadas a cabo por el laboratorio antes de recibir las preguntas permitieron afinar la lista y ampliar las variaciones de varios de estos términos. La versión final del diccionario utilizada con la base de datos de preguntas para el debate contuvo un total de **519 términos proscritos**. 

---

## Análisis exploratorio de datos recibidos
A continuación se comparten algunas gráficas selectas surgidas tras el análisis exploratorio de datos sobre los registros recibidos, las preguntas de la población depurada y las preguntas de la muestra estratificada de las que se hizo la selección final de 108 preguntas a considerar por la moderación del Debate.

**Nota:** La colección completa de gráficas generadas a partir de las distintas etapas de análisis exploratorio de datos pueden encontrarse en los cuadernos de código del presente repositorio y fueron integradas, a su vez, como Anexos en el Informe Final entregado al INE por Signa_Lab ITESO el 10 de abril de 2024.


### 13,483 registros recibidos (entradas a diccionario):

#### Registros por región:
![01-1_registros_por-region_01](https://github.com/signalabiteso/preguntas-debateINE-2024/assets/157540247/e8fecdce-41c5-4a1d-b966-d5c9b6aa7bd9)


#### Registros por entidad:
![01-3_registros_por-entidad_01](https://github.com/signalabiteso/preguntas-debateINE-2024/assets/157540247/803f449f-a1aa-4fb3-9304-576ee894c572)


#### Registros por rango de edad:
![02-4_registros_por-edad_rangos-porcentajes_01](https://github.com/signalabiteso/preguntas-debateINE-2024/assets/157540247/bb2982b3-2945-4fbb-88bc-d76195306c7a)


#### Registros por género:
![03-3_registros_por-género_porcentajes-nulos-válido_01](https://github.com/signalabiteso/preguntas-debateINE-2024/assets/157540247/31faf02b-92bb-439e-992c-4bcf1b39e1a9)

![03-4_registros_por-género_porcentajes-género_01](https://github.com/signalabiteso/preguntas-debateINE-2024/assets/157540247/0e200e93-17b2-4be1-b760-81af8b888a4b)


#### Registros por pertenencia a grupo en situación de discriminación:
![04-3_registros_por-GSD_nulos-válidos-porcentajes_01](https://github.com/signalabiteso/preguntas-debateINE-2024/assets/157540247/a52c2f13-9cf3-43ff-ae81-065c6b590fd7)

![04-4_registros_por-GSD_grupos-porcentajes_01](https://github.com/signalabiteso/preguntas-debateINE-2024/assets/157540247/05888d62-fef3-40ce-abf7-3f695a95ed12)



### 24,000 preguntas en depuración inicial

#### Relación entre preguntas depuradas y descartadas:
![01-1_preguntas_depuradas-descartadas-porcentajes_01](https://github.com/signalabiteso/preguntas-debateINE-2024/assets/157540247/3bc01f0e-805f-4460-8d88-bcade20b90eb)


#### Preguntas descartadas por diccionarios según la categoría de términos proscritos presentes:
![01-2_preguntas_depuradas-descartadas-diccionarios-categorias_01](https://github.com/signalabiteso/preguntas-debateINE-2024/assets/157540247/fae2cc0f-9cab-4564-ae61-e7802f75b8e7)



### 21,219 preguntas en población depurada

#### Preguntas por tema en población depurada:
![02-1_preguntas_por-tema_01](https://github.com/signalabiteso/preguntas-debateINE-2024/assets/157540247/97bfda49-edda-4249-b77c-e34b8796fee5)



#### Preguntas por región y tema en población depurada:
![02-3_preguntas_por-tema-region-porcentajes_04](https://github.com/signalabiteso/preguntas-debateINE-2024/assets/157540247/82b244b1-b931-471f-a824-cfb5b704d708)


#### Preguntas por edad y tema en población depurada:
![03-3_preguntas_por-rango-edad-tema_02-porcentajes](https://github.com/signalabiteso/preguntas-debateINE-2024/assets/157540247/ee68b6e2-c258-4017-8895-e7f8033a88a1)


#### Preguntas por género y tema en población depurada:
![04-4_preguntas_por-genero-tema_01](https://github.com/signalabiteso/preguntas-debateINE-2024/assets/157540247/100dfe99-a0c1-4f2a-a49d-577fbf881df9)


#### Preguntas por grupo en situación de discriminación y tema en población depurada:
![05-5_preguntas_por-GSD-grupos-tema-porcentaje_02](https://github.com/signalabiteso/preguntas-debateINE-2024/assets/157540247/5c533e36-41d3-42e4-90f7-705f6ccc27f8)



### Análisis semántico por tema en la muestra estratificada de 1,701 preguntas

#### a. Educación:

##### Relaciones semánticas y clústeres de muestra de preguntas del tema Educación:
![gráfica_análisis_semántico_educación_01-1_clústers](https://github.com/signalabiteso/preguntas-debateINE-2024/assets/157540247/e287ff58-db75-48a9-837a-b85a39be2d43)

##### Bigramas con mayor frecuencia en muestra de tema Educación:
![gráfica_análisis_semántico_educación_01-3_bigrama](https://github.com/signalabiteso/preguntas-debateINE-2024/assets/157540247/b9eae4e4-a444-40fb-a6f9-23289231e374)


#### b. Salud:

##### Relaciones semánticas y clústeres de muestra de preguntas del tema Salud:
![gráfica_análisis_semántico_salud_01-1_clústers](https://github.com/signalabiteso/preguntas-debateINE-2024/assets/157540247/713c16db-5fae-4e4e-a55e-3ac152b89cc3)


##### Bigramas con mayor frecuencia en muestra de tema Salud:
![gráfica_análisis_semántico_salud_01-3_bigrama](https://github.com/signalabiteso/preguntas-debateINE-2024/assets/157540247/0e3d7bca-0ce4-423f-a480-7da5ded0d7ec)


#### c. Transparencia:

##### Relaciones semánticas y clústeres de muestra de preguntas del tema Transparencia:
![gráfica_análisis_semántico_transparencia_01-1_clústers](https://github.com/signalabiteso/preguntas-debateINE-2024/assets/157540247/2fe032d0-af0f-48c9-865f-589bbf928d17)

##### Bigramas con mayor frecuencia en muestra de tema Transparencia:
![gráfica_análisis_semántico_transparencia_01-3_bigrama](https://github.com/signalabiteso/preguntas-debateINE-2024/assets/157540247/10a444c2-ef09-4d61-b488-454f3b7bd986)


#### d. No discriminación y grupos vulnerables:

##### Relaciones semánticas y clústeres de muestra de preguntas del tema No discriminación y grupos vulnerables:
![gráfica_análisis_semántico_noDiscrimanción_01-1_clústers](https://github.com/signalabiteso/preguntas-debateINE-2024/assets/157540247/b0e1c26d-1750-4d9b-9af7-4cd5351648c1)


##### Bigramas con mayor frecuencia en muestra de tema No discriminación y grupos vulnerables:
![gráfica_análisis_semántico_noDiscriminación_01-3_bigrama](https://github.com/signalabiteso/preguntas-debateINE-2024/assets/157540247/6fa9da9c-d6a2-4a49-9739-47bd142d0f3e)



#### e. Violencia en contra de las mujeres:

##### Relaciones semánticas y clústeres de muestra de preguntas del tema Violencia en contra de las mujeres:
![gráfica_análisis_semántico_violenciaMujeres_01-1_clústers](https://github.com/signalabiteso/preguntas-debateINE-2024/assets/157540247/e893a270-2f8b-49b6-8f6a-7b359bf4cd93)


##### Bigramas con mayor frecuencia ponderada en muestra de tema Violencia en contra de las mujeres:
![gráfica_análisis_semántico_violenciaMujeres_01-3_bigramas](https://github.com/signalabiteso/preguntas-debateINE-2024/assets/157540247/ac38607f-5ccb-4eda-bdbf-a117602eea7f)


---


## Dependencias e instalación

### Entorno de ejecución
El código desarrollado y contenido en los cuadernos de este repositorio requiere la instalación de [Python versión 3.9](https://www.python.org/downloads/) o más alta.

Aunque el software para ejecutar los cuadernos de código, [Jupter Notebook](https://jupyter.org/install), puede ser instalado de manera individual, se recomienda hacer la instalación completa de la paquetería contenida en [Anaconda](https://www.anaconda.com/download) que, además de Jupyter Notebook, incluye una gran cantidad de las librerías de software libre requeridas para la ejecución del código en los cuadernos de este repositorio. Su instalación es gratuita y compatible con sistemas operativos de Windows, macOS y Linux.

### Librerías y dependencias de Python
Para instalar las dependencias requeridas, cada **[cuaderno de código](anexos/)** contiene una primera celda que debe ejecutarse al inicio para asegurar la correcta instalación de las librerías y herramientas necesarias para replicar el funcionamiento del código.

### Modelo de lenguaje
Después de probar con múltiples alternativas, se eligió para la implementación de los cuadernos de código del modelo de lenguaje [intfloat/multilingual-e5-large-instruct](https://huggingface.co/intfloat/multilingual-e5-large-instruct/tree/main). Este modelo, además de ser de software libre, lo cual garantiza la transparencia, trazabilidad y replicabilidad de su uso, produjo los mejores resultados entre las pruebas preliminares ejecutadas. Lo anterior se atribuye a su mayor densidad semántica (1024 dimensiones), a la presencia considerable de contenido en español en sus datos de entrenamiento (Wang et al, 2024) y a su capacidad de añadir tareas específicas vinculadas a la ejecución de consultas de búsqueda semántica, lo cual permitió una mayor precisión en su orientación para explorar las preguntas a seleccionar como más frecuentes por tema.

Este modelo puede ser ejecutado tanto desde su repositorio en la nube como localmente, [descargando sus archivos](https://huggingface.co/intfloat/multilingual-e5-large-instruct/tree/main) y alojándolos en una carpeta, de la que se debe indicar su ruta:

```Python
# Ejemplo de ruta para cargar modelo de lenguaje localmente desde una carpeta con todos sus archivos:
modelo = "./modelos/multilingual-e5-large-instruct"

# Ejemplo de ruta para cargar modelo de lenguaje desde repositorio en la nube de Hugging Face:
modelo = "intfloat/multilingual-e5-large-instruct"

# Cargar modelo para embeddings
embedder = SentenceTransformer(modelo)
```

---

## Otras herramientas utilizadas
Para la exploración manual de datos y relaciones semánticas, en distintas etapas que lo requirieron como complemento al trabajo y al análisis desarrollado desde el código, se utilizaron las siguientes aplicaciones de escritorio y de software libre:
- [OpenRefine v3.7.9](https://openrefine.org/download) - Exploración y transformación de datos tabulares.
- [Libre Office v.24.2.2](https://es.libreoffice.org/descarga/libreoffice/) - Exploración de datos tabulares.
- [AntConc v4.2.4](https://www.laurenceanthony.net/software/antconc/) - Cálculo y exploración de enegramas.
- [Gephi v0.92](https://gephi.org/) - Análisis exploratorio y visualización de grafos (bigramas)

## Licencia
El código y contenidos de este repositorio están publicados como software libre bajo la [Licencia MIT](LICENSE), que corresponde a la misma licencia del modelo de lenguaje utilizado [intfloat/multilingual-e5-large-instruct](https://huggingface.co/intfloat/multilingual-e5-large-instruct)

---

## Créditos
### Realizado por el equipo de Signa_Lab ITESO:
Instituto Tecnológico y de Estudios Superiores de Occidente (ITESO)
Tlaquepaque, Jalisco, México.

- **Coordinación del proyecto:** 
Víctor Hugo Ábrego Molina

- **Supervisión del desarrollo tecnológico, documentación y visualización de datos:** 
Diego Arredondo Ortiz

- **Coordinación operativa, supervisión de desarrollo de diccionarios y análisis semántico:** 
Paloma López Portillo Vázquez

- **Programación de cuadernos de código para limpieza, depuración y análisis exploratorio de datos,  análisis semántico y selección aleatoria**: 
Javier de la Torre Silva y José Luis Almendarez González

- **Diseño muestral y asesoría en estadística aplicada:** 
Radamanto Portilla Tinajero

- **Asesoría en análisis semántico y exploración de datos:** 
Luz María Sandoval Zavala y Héctor Piña Camacho

- **Asistencia técnica, exploración de datos y  visualización de grafos:** 
Eduardo G. de Quevedo Sánchez

- **Desarrollo de diccionarios, pruebas de depuración  y análisis semántico:**
Ana Sánchez Muñóz, Daniela Hernández Ramírez, Fernanda Verduzco Hernández y Vanessa Briseño Ramos

- **Documentación del proceso y realización de bitácoras:**
Víctor Húgo Ábrego Molina, Diego Arredondo Ortiz, Vanessa Briseño Ramos y Fernanda Verduzco Hernández


### Con el acompañamiento y supervisión del personal del INE:
- **Diseño de metodología y supervisión de su cumplimiento (CNCS INE):**
Ana Cristina Levy Covarrubias y Zaira Ivonne Medina Gómez 

- **Supervisión desde Oficialía Electoral del INE:**
Irene Maldonado Cavazos, Adrián Sánchez Saez y Pedro Alejandro Mendoza Carretero

---

## Referencias
- Bird, Steven, Edward Loper & Ewan Klein (2009). *Natural Language Processing with Python*. O'Reilly Media Inc.
- Guzmán Falcón, E. (2018). *Detección de lenguaje ofensivo en Twitter basada en expansión automática de lexicones*. Instituto Nacional de Astrofísica, Óptica y Electrónica. [https://inaoe.repositorioinstitucional.mx/jspui/bitstream/1009/1722/1/GuzmanFE.pdf](https://inaoe.repositorioinstitucional.mx/jspui/bitstream/1009/1722/1/GuzmanFE.pdf)
- Hunston, S. (2022). *Corpora in Applied Linguistics* (2a ed.). Cambridge University Press. [https://doi.org/10.1017/9781108616218](https://doi.org/10.1017/9781108616218)
- Instituto Nacional Electoral. (2024). *Acuerdo INE/CG95/2024*. Acuerdo del Consejo General del Instituto Nacional Electoral por el que se define la metodología, así como la instancia que seleccionará las preguntas provenientes de redes sociales relativas al Formato Tipo A que se utilizará en el Primer Debate Presidencial en el Proceso Electoral Federal 2023-2024. Repositorio Documental INE. [https://repositoriodocumental.ine.mx/xmlui/bitstream/handle/123456789/164296/CGex202402-08-ap-3.pdf](https://repositoriodocumental.ine.mx/xmlui/bitstream/handle/123456789/164296/CGex202402-08-ap-3.pdf)
- Instituto Nacional Electoral. (2024). *Anexo I. Metodología Selección de Preguntas para Debate Formato A*. Repositorio Documental INE. [https://repositoriodocumental.ine.mx/xmlui/bitstream/handle/123456789/164296/CGex202402-08-ap-3-a1.pdf](https://repositoriodocumental.ine.mx/xmlui/bitstream/handle/123456789/164296/CGex202402-08-ap-3-a1.pdf)
- Kiss, T., & Strunk, J. (2006). *Unsupervised Multilingual Sentence Boundary Detection*. Computational Linguistics, 32(4), 485-525. [https://doi.org/10.1162/coli.2006.32.4.485](https://doi.org/10.1162/coli.2006.32.4.485)
- Longhi, J. (2021). *Mapping information and identifying disinformation based on digital humanities methods: From accuracy to plasticity*. Digital Scholarship in the Humanities, 36 (4), 980–998. [https://doi.org/10.1093/llc/fqab005](https://doi.org/10.1093/llc/fqab005)
- McInnes, L., Healy, J., & Melville, J. (2018). *Umap: Uniform manifold approximation and projection for dimension reduction*. arXiv preprint arXiv:1802.03426. [https://arxiv.org/abs/1802.03426](https://arxiv.org/abs/1802.03426)
- Pedregosa, F., Varoquaux, G., Gramfort, A., Michel, V., Thirion, B., Grisel, O., Blondel, M., Prettenhofer, P., Weiss, R., Dubourg, V., Vanderplas, J., Passos, A., Cournapeau, D., Brucher, M., Perrot, M., Duchesnay, E., & others. (2011). *Scikit-learn: Machine Learning in Python*. Journal of Machine Learning Research, 12, 2825–2830.
- Reimers, N., & Gurevych, I. (2019). *Sentence-BERT: Sentence Embeddings using Siamese BERT-Networks* (arXiv:1908.10084). arXiv. [http://arxiv.org/abs/1908.10084](http://arxiv.org/abs/1908.10084)
- Rousseeuw, P. (1987). *Silhouettes: a Graphical Aid to the Interpretation and Validation of Cluster Analysis*. Computational and Applied Mathematics. 20: 53–65. doi:10.1016/0377-0427(87)90125-7.
- Signa_Lab ITESO. (2022). *Lexicon para identificar violencia con razón de género*. Signa_Lab ITESO.
- Spärck-Jones, K. (1972). A statistical interpretation of term specificity and its application in retrieval. Journal of Documentation, 28(1), 11-21. [https://www.staff.city.ac.uk/~sbrp622/idfpapers/ksj_orig.pdf](https://www.staff.city.ac.uk/~sbrp622/idfpapers/ksj_orig.pdf)
- Thorndike, R. (1953). *Who Belongs in the Family?*. Psychometrika. 18 (4): 267–276. doi:10.1007/BF02289263. S2CID 120467216.
- Wang, L., Yang, N., Huang, X., Yang, L., Majumder, R., & Wei, F. (2024). *Multilingual E5 Text Embeddings: A Technical Report* (arXiv:2402.05672). arXiv. [http://arxiv.org/abs/2402.05672](http://arxiv.org/abs/2402.05672)
