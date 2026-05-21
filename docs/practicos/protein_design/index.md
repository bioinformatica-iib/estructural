# **TP 7**. Diseño de Proteínas { markdown data-toc-label = 'TP 7'}

## Materiales

[:fontawesome-solid-download: Materiales](data/7bh9_clean.pdb){ .md-button .md-button--primary }

[ :fontawesome-solid-link: Colab Notebook](https://colab.research.google.com/drive/1-qU3AiVauklK1zi2rIH352Qn_lzc0Gsw?usp=sharing){ .md-button .md-button--primary }

<!--
## Slides
* Slides [[PDF]](https://drive.google.com/file/d/1B6cIgEzZLLkmAf37mDhp_EmToNJBRPo3/view?usp=sharing)
-->

## Contexto Biológico
La infección por SARS-CoV-2 depende críticamente de la interacción entre la proteína **Spike** del virus y el receptor celular humano **ACE2**. Específicamente, el dominio de unión al receptor (**RBD**) de la Spike es la región que reconoce y se acopla a ACE2. Bloquear físicamente esta interfaz mediante una molécula diseñada a medida impide el anclaje del virus y, por lo tanto, neutraliza la infección celular.

## Objetivo del Práctico
En esta práctica vamos a implementar la primera etapa de una estrategia computacional de **diseño de proteínas *de novo***. El objetivo es generar un esqueleto proteico pequeño (minibinder) que esté geométricamente optimizado para interactuar de forma estable con los residuos clave (*hotspots*) del RBD.

Para lograrlo, utilizaremos un pipeline completo que combina herramientas basadas en redes neuronales generativas con métodos de evaluación energética y predicción estructural:
1. **RFdiffusion:** Generación de la estructura tridimensional del esqueleto (*backbone*) adaptada al blanco.
2. **PyRosetta:** Filtrado inicial de los candidatos según criterios empíricos de estabilidad y calidad estructural.
3. **ProteinMPNN:** Diseño de la secuencia exacta de aminoácidos óptima para el esqueleto seleccionado.
4. **ColabFold:** Validación por predicción de la estructura final y evaluación de la afinidad de unión.

## Preparación del Entorno

Para que el entorno de Colab reconozca tus archivos al instante y no tengas problemas de sincronización, seguí estos pasos en orden antes de ejecutar cualquier celda de la notebook:

### Paso 1: Configurar las carpetas en Google Drive
1. Abrí Google Drive en el navegador.
2. En la raíz de **Mi Unidad**, creá una carpeta nueva con este nombre exacto: `TP_07_Protein_design`
3. Entrá a esa carpeta y creá otra subcarpeta llamada exactamente: `Data`
4. Descargá el archivo de la estructura guía desde la sección de datos de la guía escrita del TP (el archivo se llama `7bh9_clean.pdb`).
5. Subilo adentro de la carpeta `Data` que acabás de crear. 

*La ruta final en tu Drive tiene que quedar así:* `Mi Unidad/TP_07_Protein_design/Data/7bh9_clean.pdb`

### Paso 2: Clonar la Notebook y activar GPU
1. Abrí la notebook del TP compartida por la cátedra.
2. **Hacé tu copia propia:** Andá a `Archivo` ➔ `Guardar una copia en Drive`. Cerrá la pestaña anterior y trabajá únicamente en tu copia.
3. **Activá la GPU:** Andá a `Entorno de ejecución` ➔ `Cambiar tipo de entorno de ejecución` y asegurate de que el acelerador sea **GPU** (T4 o superior).

### Paso 3: Montar el Drive y Verificar
1. Ejecutá la celda del **Bloque 0** y aceptá los permisos para vincular tu cuenta de Google Drive.
2. Al montarse por primera vez, el script leerá directamente la carpeta que preparaste en el Paso 1. 
3. Si hiciste los pasos en este orden, la celda va a encontrar el archivo inmediatamente y te va a mostrar el mensaje: `✅ PDB encontrado`. Ya podés continuar con el práctico en Google Colab!

