# COVID_RNA_reading

Este proyecto consiste en una herramienta de análisis bioinformático desarrollada en R para procesar y comparar secuencias genómicas. El objetivo principal es identificar variaciones en la composición de nucleótidos entre la secuencia original del virus SARS-CoV-2 (Wuhan-Hu-1) y las variantes de preocupación (VOC) como Alfa, Beta y Gamma, facilitando la comprensión de la evolución viral a nivel molecular, indagando en las afectaciones de este virus en el territorio Méxicano y presentando un análisis bioinformático sobre las mismas.

## Funcionamiento del Código

Gestión de Dependencias: El script utiliza BiocManager para garantizar la instalación de Biostrings, una infraestructura diseñada para el manejo de cadenas biológicas largas que superan las capacidades de los strings estándar de R.

Ingesta de Datos: Se emplea la función readDNAStringSet() para parsear archivos de formato FASTA. Este proceso no solo lee el texto, sino que estructura los datos en un set de vectores indexados.

Normalización de Secuencias: El código convierte los sets de datos genómicos en vectores de caracteres (as.character) para permitir la manipulación directa y la comparación posicional.

Extracción por Índice: Se realiza una asignación selectiva de secuencias específicas (Wuhan, Alfa, Beta, etc.) basándose en su posición dentro del archivo original para realizar comparaciones uno a uno.

## Sobre el reporte

Contextualización Histórica: Documentación del avance de la pandemia desde una escala global hasta el nivel municipal, identificando la cepa original (Wuhan-Hu-1) como punto de partida.

Análisis Estadístico de Composición: Cálculo y visualización de la distribución de nucleótidos (A, C, G, T) y bases desconocidas (N).

Visualización Comparativa: Generación de gráficas de barras proporcionales y absolutas para contrastar la estabilidad genómica entre cepas.

## Áreas de Oportunidad

Sensibilidad al Directorio de Trabajo (Pathing): El entorno de R es sensible a la "visibilidad" sobre el archivo .fasta, el cual debe nombrarse "variantes_covid.fasta". El código asume que el archivo está en la raíz del proyecto, lo que lo hace frágil ante cambios de estructura de carpetas o ejecución desde archivos comprimidos.

Consumo de Memoria RAM: Al convertir DNAStringSet a as.character, R duplica el uso de memoria. Los archivos FASTA muy grandes (multigigabytes) causarían un desbordamiento de memoria (crash) en computadoras con pocos recursos.

Falta de Validación de Integridad: El código no verifica si el archivo FASTA contiene caracteres ambiguos (como "N") a los cuales clasifica como nucleótido desconocidos. Si el script intenta realizar cálculos matemáticos basados en la composición, estos caracteres no contemplados generarían sesgos o errores de ejecución.
