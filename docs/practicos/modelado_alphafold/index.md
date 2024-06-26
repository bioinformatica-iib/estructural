# **TP 4**. Modelado por Homología - Parte II { markdown data-toc-label = 'TP 4'}

## Recursos Online

* ColabFold For AlphaFold2 using MMseqs2: [Aquí](https://colab.research.google.com/github/sokrypton/ColabFold/blob/main/AlphaFold2.ipynb)

## Requisitos

Para este ejercicio es necesario poseer una cuenta de gmail para poder acceder a las notebooks del Colab.

## Objetivos
* Familiarizarse con el uso del predictor AlphaFold2 y criterios que permiten evaluar los resultados obtenidos, los alcances y las limitaciones de las predicciones obtenidas.

## AlphaFold2 (AF2)
En los últimos años, hubo un crecimiento continuo en el número de estructuras de proteínas determinadas experimentalmente depositadas en el PDB (actualmente ~220.000). Esto, junto con la explosión de la secuenciación (millones de secuencias) y el desarrollo de técnicas de deep learning benefició el desarrollo de algoritmos de predicción de estructura tridimensional de proteínas. Hasta el 2021, los algoritmos de predicción de estructura tridimensional de proteínas se basan en dos aspectos complementarios: las interacciones físicas (o contactos) o la historia evolutiva de la proteína. Sin embargo, y a pesar de los avances, la mayoría de los algoritmos de predicción no son muy precisos si se carece de un homólogo cercano con una estructura tridimensional resuelta experimentalmente.
A partir de la secuencia primaria de una proteína (Fig 1), AlphaFold2 utiliza una red neuronal para la predicción estructural de alta precisión (en la mayoría de los casos), la cual aumenta con el uso de estructuras homólogas. AlphaFold2 puede incluso predecir con alta precisión las cadenas laterales si el backbone es preciso.

<p style="text-align:center">
<img src="./img/alphafold_fig1.png" alt="" style="max-width:70%">
</p>
<figcaption style="text-align:center;max-width:70%"> Figura 1. Algoritmo de predicción de estructuras AlphaFold2. </figcaption>

### Arquitectura
AlphaFold2 utiliza una arquitectura de red que utiliza como inputs el alineamiento de secuencias (MSAs) y una representación de todos los pares de residuos de la secuencia. Mediante un algoritmo iterativo que se basa en la arquitectura Evoformer, se procesan los inputs y en conjunto con un módulo estructural se genera una representación tridimensional de la proteína query. 

### Métricas de confianza
AlphaFold2 incorpora métricas de confianza de la predicción. La principal métrica de confianza es el test **pLDDT** (predicted local-distance difference test) el cual es un predictor confiable del test de diferencias en las distancias Cα (IDDT-Cα) y evalúa principalmente la correctitud del modelo a nivel local (estimando el error en distancias de un Cα con Cα vecinos en un rango de 15Å). La segunda métrica se denomina **PAE** (por Predicted Aligned error) y compara el error en la predicción de pares de residuos, esto es el error sobre el residuo y cuando las estructuras real y predicha son alineadas sobre el residuo x. Esta medida permite la identificación global de unidades de plegamiento (dominios) y permite predecir si dos dominios guardan relaciones espaciales definidas, o si tienen variabilidad (por ejemplo, si están conectadas por un linker flexible).

<p style="text-align:center">
<img src="./img/pae-3.png" alt="" style="max-width:60%">
<img src="./img/pae-8.png" alt="" style="max-width:60%">
</p>
<figcaption style="text-align:center;max-width:60%"> Figura 2. Arriba. Se pueden observar dos dominios globulares, pero se desconoce la disposición espacial relativa entre ellos. Abajo. Se puede observar que además de identificar los dominios globulares, se predien correctamente pares de residuos interdominios. </figcaption>

### Costo computacional
AlphaFold2 consume muchísimos recursos. Por lo tanto, muchas proteínas de organismos modelos están siendo modeladas y puestas a disposición de la comunidad científica en una base de datos: [https://alphafold.ebi.ac.uk/](https://alphafold.ebi.ac.uk/), como ya pudo observar en UniProt.

Afortunadamente, la comunidad científica rápidamente desarrolló distintas “colabs” o “notebooks” que permiten correr AlphaFold2 en una máquina remota. La única “desventaja” es que se debe contar con una cuenta de mail de gmail, en las versión gratuita de colab, debido al espacio en disco y capacidad de cómputo que se adjudica, sólo se pueden correr proteínas o complejos con menos de 1000 residuos, **cada cuenta de gmail puede usar un colab a la vez**.

Otra desventaja, es que no se pueden modificar muchos parámetros del modelado al usar un colab, en comparación con correr la simulación desde un script en una computadora o server propio. Sin embargo, los parámetros usados en el ColabFold de AlphaFold2 son los que fueron más ampliamente validados durante el desarrollo del método.

Existen distintos colabs que implementan AlphaFold2. En este curso utilizaremos uno en particular. (Todas las versiones están disponibles en el [github](https://github.com/sokrypton/ColabFold))


## AlphaFold2 - Ejercicios
Realizaremos ejercicios con dos proteínas. E7 del papilomavirus y la proteína de Cápside de flavivirus.

Los papilomavirus (PVs) son virus desnudos icosaédricos y poseen un genoma ADN doble cadena circular entre 5-8 Kb. Sus hospedadores incluyen una amplia variedad de vertebrados desde peces, reptiles, aves y mamíferos. Los PV infectan el epitelio mucoso y queratinizado y producen lesiones denominadas condilomas o papilomas y verrugas respectivamente y en humanos algunos PVs están asociados al cáncer cervical uterino, de la formación de tumores en el tracto urogenital y en las vı́as aéreas superiores.
La proteína E7 del papilomavirus comparte similitudes funcionales con la proteína E1A de adenovirus y el antígeno T del poliomavirus SV40. Las tres proteínas poseen actividades transformantes e interaccionan con la proteína retinoblastoma.
La interacción de la proteína E7 con Rb es responsable de la inducción de la síntesis de ADN y proliferación celular. La inmortalización y transformación de la célula infectada inducida por E7 es consecuencia de la interacción de E7 con Rb y numerosos blancos proteicos involucrados en crecimiento celular, transformación, transcripción, apoptosis y síntesis de ADN.

### Ejercicio 1. Modelado de un Monómero de E7
1. Ingrese al ColabFold que implementa MMseq2 [Aquí](https://colab.research.google.com/github/sokrypton/ColabFold/blob/main/AlphaFold2.ipynb) .

    !!! info 
        Si quiere que los cambios que realice sean guardados deberá agregar la notebook a su drive. Pero esto no es necesario.

2. En la parte superior, haga click en *Runtime* → *Change Runtime* y asegúrese que **T4 GPU** esté seleccionado.

3. **Preparando la corrida.**

    En el campo sequence query ingrese la secuencia (sin el encabezado indicado por el signo `>`) de la proteína E7 de HPV16.

    ```
    >sp|P03129|VE7_HPV16 Protein E7 OS=Human papillomavirus type 16 OX=333760 GN=E7 PE=1 SV=1
    MHGDTPTLHEYMLDLQPETTDLYCYEQLNDSSEEEDEIDGPAGQAEPDRAHYNIVTFCCKCDSTLRLCVQSTHVDIRTLEDLLMGTLGIVCPICSQKP
    ```

    * En el campo jobname ingrese: E7_MONOMERO.
    * Asegúrese que use num_relax esté en **1**.

        !!! info
            Num_relax es el número de modelos que se van a relajar usando **Amber**. Amber permite mejorar la geometría de la unión peptídica y posición de rotámeros luego de la relajación de la estructura. Si bien no mejora la predicción, remueve violaciones estereoquímicas.

    * En template mode elija pdb100 ¿Qué le parece que es este campo?

    * Vaya a  *Runtime* →  *Run all*, o presione `Ctrl`+`F9`

    * Como por defecto este ColabFold crea 5 modelos hay que esperar (unos 20 minutos).

        !!! warning "Importante"

            No cierre la ventana y tampoco cierre la laptop porque la corrida entonces se detiene (no pasa nada si entra en suspensión).

    Al finalizar la corrida, los resultados serán descargados automáticamente como un archivo zip. Si esto no llegara a suceder, puede acceder al mismo haciendo click en el icono con forma de carpeta que se encuentra a la izquierda.

4. Una vez que terminó de correr, comience con el Ejercicio 2 (La corrida en AlphaFold2) y vuelva a este ejercicio.

5. Localice el archivo descargado y descomprímalo (el nombre del archivo comienza con `E7_MONOMERO`). Encontrará varios archivos, en particular:
    * `*_template_domain_names.json` Tiene los templados utilizados por AlphaFold2 si es que se usaron.
    * `Cite.bibtex` Contiene todas las citas correspondientes a los papers relacionados.
    * `Config.json` Contiene todos los parámetros utilizados en la corrida.
    * `*.a3m` Alineamiento
    * `*_coverage.png` Gráfico de la cobertura del alineamiento
    * `*_PAE.png` Gráfico del PAE por pares de residuos para todos los modelos.
    * `*_plddt.png` Gráfico del plddt por posición
    * `*_predicted_aligned_error_v1.json` Tiene los valores de PAE para todos los pares de todos los modelos.
    * `*_relaxed_*_model_*.pdb` Son los 5 modelos generados.
    * `*_relaxed_*_model_*.json` Son el PAE y pLDDT de cada modelo que se pueden utilizar para graficar.

6. Abra Chimera y cargue el modelo relajado (si no recuerda *File* → *Open …*).
7. Abra el pdb: 2b9d.
    * ¿Estaba esta estructura entre los templados?
    * ¿Por qué método fue determinada?
    * ¿A qué proteína corresponde? ¿De qué organismo?
8. Alinee las estructuras utilizando Matchmaker (si no recuerda, *Tools* → *Structure comparison* → *Matchmaker*)
    * ¿Cuál es el RMSD global?

    Si quieren ver el RMSD por posición sobre la estructura

    *Structure Comparison* → *Match align*
    
    Seleccione el par de modelos adecuado. *En residue-residue distance cutoff* seleccione el mismo umbral que utilizó en *Matchmaker* para *pruned atoms* (Por defecto es 2)
    
    Para colorear la estructura por RMSD (después de haber hecho *Match align*) vaya a: *Tools* → *Depiction* → *Render by Attribute*
    
    En **attributes** of asegúrese que esté seleccionado residues
    
    En el **recuadro de Models** asegúrese que estén ambos modelos seleccionados.
    
    En la pestaña **Render** seleccione **mavRMSDca** y luego haga clic en `Ok`.

9. Cierre el modelo correspondiente al pdb 2b9d. Via terminal tiene que ingresar el comando close seguido del número del modelo, por ejemplo:

    ```
    close #0
    ```

    cierra el modelo 0.

    O bien, en el **model panel**, seleccione el modelo correspondiente y haga clic en close.

10. Ahora abra los 4 modelos no relajados restantes (rankeados del 002 al 005), para eso, *File* → *Open…* y con el mouse seleccione los modelos manteniendo la tecla ctrl presionada.

11. Alinee los 5 modelos,
    * ¿cuál es el RMSD global?
12. Utilice **Match Align** para ver el alineamiento.
    * ¿Qué observa?
    * ¿Porque si las secuencias son todas iguales no aparece el n-terminal alineado?
13. Los valores de pLDDT están almacenados en la columna del pdb que corresponde a los b-factors. Coloree los modelos según este atributo ingresando en la command line:

    ```
    rangecolor bfactor 0 orange red 50 white 100 dodger blue
    ```

    * ¿Qué observa?

    Ahora cambie los valores para que el programa elija estos valores automaticamente:

    ```
    rangecolor bfactor min orange red mid white max dodger blue
    ```

    En el reply log se reportan los valores minimo, medio y máximo encontrados en la columna de b-factors.

    *  ¿Cuáles son el mínimo y el máximo?
    
    Ahora cambie el valor intermedio (antes puesto automáticamente) a 80 y el máximo a 100:

    ```
    rangecolor bfactor min orange red 80 white 100 dodger blue
    ```

    * ¿Observa diferencias con lo anterior? ¿Cuáles?
    
    Ahora corra:

    ```
    rangecolor bfactor 50 orange red 80 white 100 dodger blue
    ```
    
    * ¿Observa diferencias con lo anterior? ¿Cuáles?
    * ¿Porqué considera que elegimos 50 como valor mínimo?
    * ¿De qué posición a qué posición consideraría que el modelo es de confianza?

14. Por ahora investigue el gráfico de pLDDT, al final de la clase haremos una demostración del script en R para graficar estos valores.

    * ¿Qué observa?
    * ¿Puede identificar las ragiones con un pLDDT mayor a 70?
    * ¿Puede identificar las ragiones con un pLDDT entre 50 a 70?

    ---
    Abra R Studio. Ahora graficaremos los pLDDT por posición para cada uno de los modelos.

    ``` R
    # SCRIPT CORREGIDO
    install.packages("bio3d")
    library(bio3d)

    directorio <- "/directorio/donde/estan/los/modelos"

    archivos <- list.files(path = directorio,pattern = "_unrelaxed_",)

    # Creo la ruta completa para mi archivo 1
    miarchivo <- paste(directorio,archivos[1],sep="")

    # Leo el pdb usando la función read.pdb de la libraría bio3d
    mipdb <- read.pdb(file = miarchivo)

    # Creo una tabla con los datos de interés: el nro de residuo y el valor de plddt almacenado en el campo de b-factors y correspondiendo únicamente a los carbonos alpha.
    datos <- data.frame(Residue = mipdb$atom[mipdb$calpha,"resno"],
                        Rank_1 = mipdb$atom[mipdb$calpha,"b"])

    # uso un ciclo for para iterar sobre mi vector donde están guardados los nombres de los archivos y los guardo en distintas columnas de mi tabla datos.
    for (i in 2:length(archivos)){
        miarchivo2 <- paste(directorio,archivos[i],sep="")
        mipdb2 <- read.pdb(miarchivo2)
        nuevaColumna <- paste("Rank",i,sep="_")
        datos[nuevaColumna] <- mipdb2$atom[mipdb2$calpha,"b"]
    }

    # creo un vector de colores para utilizar en el plot
    colores <- c("red","blue","purple","green","orange")
    
    # creo el nombre del archivo que va a guardar mi plot.
    fileOUT <- paste(directorio,"E7_Monomero.png",sep="")

    # creo el dispositivo png
    png(filename = fileOUT, width=20,height=10,units = "cm",res=150)
    # empiezo un plot
    plot.new()
    # ploteo los valores del modelo 1
    plot(x = datos$Residue,
        y = datos$Rank_1,
        type = "l",
        xlab = "E7 Residue",
        ylab = "pLDDT",
        xlim = c(0,100),
        ylim = c(0,101),
        col = colores[1],
        xaxt='n',yaxt='n')

    # modifico los ejes x (1) e y (2)
    axis(side = 1, at = c(1,seq(5,100,by=5)),lwd=0,lwd.ticks = 1)
    axis(side = 2, at = seq(5,100,by=5),lwd=0,lwd.ticks = 1)

    # ploteo los valores de los otros modelos que están guardados en las columnas: 3,4,5,6
    for (i in 3:ncol(datos)){
        lines(x = datos$Residue,
                y = datos[,i],
                col = colores[i-1])
        }

    # creo la leyenda del plot
    legend(x = 60,y = 40,legend = paste(rep("rank",5),1:5,sep="-"),col = colores,lty = 1,ncol = 2)

    box(lwd=3) # creo un box en el plot

    dev.off() # cierro el dispositivo png
    ```

15. Encuentre el archivo corespondiente al gráfico del PAE.
    * ¿Qué interpreta?

16. En base a los resultados obtenidos, 
    * ¿Qué puede decir de la estructura de la proteína?
    * ¿Cuántos dominios posee? ¿ordenados o desordenados?
    * ¿Puede decir aproximadamente los límites?

17. Guarde la sesión y cierre chimera.

### Ejercicio 2. Modelado de un dímero de E7

1. En la parte superior, haga click en **Runtime** → **Disconnect** and delete Runtime

2. Preparando la corrida.

    Para indicar que se quiere correr un multímero se debe ingresar las secuencias separadas por `:`.
    En el campo sequence query ingrese las secuencias de la proteína E7 de HPV16. 

    ```
    MHGDTPTLHEYMLDLQPETTDLYCYEQLNDSSEEEDEIDGPAGQAEPDRAHYNIVTFCCKCDSTLRLCVQSTHVDIRTLEDLLMGTLGIVCPICSQKP:MHGDTPTLHEYMLDLQPETTDLYCYEQLNDSSEEEDEIDGPAGQAEPDRAHYNIVTFCCKCDSTLRLCVQSTHVDIRTLEDLLMGTLGIVCPICSQKP
    ```

    * En el campo jobname ingrese E7_DIMERO.
    * Asegúrese que use Num_relax esté en 1.

    * En template mode elija pdb100

    * Vaya a *Runtime* → *Run all*, o presione `Ctrl`+`F9`

    * Vuelta a esperar ... unos 20 minutos.


3. Abra Chimera. Y abra el pdb: 2F8B.

    Para eso ingrese en el command line:

    ```
    open 2f8b
    ```

    * ¿Qué observa? ¿A qué se debe?
    * Investigue en el rcsb la técnica por la que se obtuvo esta estructura y a qué proteína pertenece.
    * ¿Este pdb es utilizado como templado para el modelado? ¿por qué?

4. Abra el model Panel: *Favorites* → *Model Panel*

    Para que sea más fácil las observaciones vamos a trabajar con un único submodelo de cada cadena. Para esto, ingrese en la línea de comando:

    ```
    close #0.2-15
    ```

    * ¿Cuál es el estado de oligomerización de E7?

5. Coloree el modelo de blanco y oculte todos los residuos utilizando los siguientes comandos

    ```
    color white #0
    ~display
    ```

6. La proteína E7 en el dominio de dimerización contiene un sitio de unión a Zinc. Ubique el zn en la estructura.

    ```
    display @ZN; color red @ZN
    ```

    Ahora vamos a seleccionar los residuos más cercanos al zinc:

    ```
    sel :@zn zr<3
    display sel; color red,a sel; color byhet sel;~sel
    delete element.H
    ```

    * ¿Qué residuos se encuentran coordinando la unión a zinc?

6. Ubique el archivo zip que se generó con ColabFold y descomprímalo en su computadora. 
7. Identifique el archivo que corresponde al pLDDT.
    * ¿Qué región está modelada con alta confianza y cual no?
8. Identifique el archivo que corresponde al PAE.

    * Interprete el gráfico.
    * ¿Cuál de los 4 gráficos muestra los valores correspondientes para los pares de residuos de la cadena A, cual para la cadena B y cual para los pares de residuos de de las cadenas A y B?
    * ¿Cuáles son los límites el dominio globular, aproximadamente?

9. Elija el modelo relajado y alineelo utilizando Matchmaker contra la estructura de 2f8b.
    * ¿Cuál es el RMSD global?

10. Abra en chimera los 4 modelos no relajados (no considerar el que ya abrieron como relajado) que se generaron. Luego, alinee utilizando matchmaker y seleccionaremos las cisteínas que coordinan la unión al zinc.

    ```
    sel #1-5:58,61,91,94; display sel; color blue,a sel; color byhet sel; ~sel
    ```

    Coloree las cadenas A y B de los modelos predichos de distinto color

    ```
    sel #1-5:.A; color orange,r sel; ~sel
    sel #1-5:.B; color purple,r sel; ~sel
    ```

    Observe de cerca la ubicación de las cisteínas y responda.

    * ¿Considera que la predicción del sitio de unión de zinc es buena aún cuando no se incluye el ión en el modelado?

8. Coloree las cadenas de los modelos predichos según los valores de pLDDT.:

    ```
    rangecolor bfactor 50 orange red 50 white 100 dodger blue
    ```

    * ¿Qué observa?

    En base a todas las características observadas: pLDDT, PAE, coordinación de zinc,

    * ¿Pudo AF2 predecir el estado de oligomerización?

    * ¿Pudo AF2 predecir la coordinación del zinc?
    
    * ¿Qué opina del modelo?

9. Guarde la sesión y cierre chimera.

### Ejercicio 3. Predicción de la proteína de la cápside de los Flavivirus

Los flavivirus son virus envueltos y poseen un genoma ARN positivo simple cadena. El género incluye virus como ZIKA, Dengue, West nile virus y el virus de la fiebre amarilla de alta relevancia epidemiológica. Posee un amplio rango de hospedadores vertebrados y artrópodos.

El genoma ARN positivo se traduce como una poliproteína que luego es clivada en distintas proteínas, estructurales y no estructurales. Entre las proteínas estructurales se encuentra la proteína de la Cápside. Además del rol estructural de encapsidación del ARN viral, la proteína de la cápside interactúa con distintas proteínas del hospedador promoviendo la proliferación viral y por lo tanto, posee un rol importante en el ciclo reproductivo del virus.

1. En la parte superior, haga click en *Runtime* → *Disconnect* and delete Runtime

2. Modele en el ColabFold la proteína de la cápside del virus de dengue 2 (DENV2), utilice como nombre del trabajo, C_DENV2: 

    ```
    >sp|P14340|POLG_DEN2N|C|1-100
    MNNQRKKARNTPFNMLKRERNRVSTVQQLTKRFSLGMLQGRGPLKLFMALVAFLRFLTIPPTAGILKRWGTIKKSKAINVLRGFRKEIGRMLNILNRRRR
    ```

3. Mientras espera, abra Chimera y cargué el PDB: 1R6R.
    * ¿Qué observa?
    * ¿Cuántos modelos son? (Observe el reply log)
    * Investigue en el RCSB qué proteína y a qué organismo pertenece.

4. Quédese con un único modelo.
    ```
    close #0.2-21
    ```
5. Coloree las cadenas:

    ```
    rainbow chain
    ```
    
    * ¿Cuántas cadenas hay?

6. Para trabajar más fácil vamos a quedarnos con una única cadena. Pero primero vamos a ver que las cadenas son muy similares entre sí. Para esto debemos hacer que cada cadena sea un modelo utilizando el siguiente comando:

    ```
    split #0
    ```
    
    Luego, las alineamos con Matchmaker seleccionando sólo las cadenas que pertenezcan al pdb (recuerda seleccionar una como referencia y las restantes en “to match”).

    * ¿Observa diferencias significativas? ¿Cuál es el RMSD?

    Cierre las cadenas que no serán utilizadas

    ```
    close #0.2
    ```

7. Coloree por hélices.

    ```
    rainbow helix
    ```
    
8. Ubique los extremos de las cadenas. A continuación representaremos los residuos N-terminal y el C-terminal para ubicarnos más fácilmente.

    ```
    sel #0:21; namesel Nterminal
    represent stick Nterminal; display Nterminal 
    color white,a Nterminal
    sel #0:100; namesel Cterminal
    represent stick Cterminal; display Cterminal 
    color purple,a Cterminal
    ```

9. Cargué el PDB: 1SFK (Si no lo ve, aleje el zoom)
    * ¿Cuántos modelos son?
    * ¿Cuántas cadenas hay?
    * Investigue en el RCSB qué proteína y a qué organismo pertenece.

10. Coloree las cadenas:

    ```
    rainbow chain #1
    ```
    
    * ¿Puede encontrar los dímeros?

9. Para trabajar más fácil vamos a quedarnos nuevamente con una única cadena de 1SFK. 

    ```
    split #1
    ```

    Cierre las cadenas que no serán utilizadas

    ```
    close #1.2-8
    ```

10. Coloree por hélices.

    ```
    rainbow helix
    ```
    
    * ¿Puede observar la correspondencia con la proteína de la cápside de Dengue?

11. Alinee las dos estructuras.

    * ¿Qué observa?
    * ¿Qué ocurre con la hélice N-terminal? ¿Tiene movilidad?

12. Ubique los modelos predichos por AF2 para dengue, y carguelos en Chimera. Coloree por hélice. 

    ```
    rainbow helix
    ```
    
    * ¿Tienen el mismo número de hélices?
    * ¿Qué ocurre con la hélice N-terminal que se observaba en Dengue y Kunji?

13. Observe el gráfico de pLDDT.

    * ¿Qué puede decir de la predicción local del modelo?
    * ¿Puede identificar los límites de la raigón globular? ¿Esta región incluye a la hélice?

13. Coloree la estructura por pLDDT

    ```
    rangecolor bfactor 50 orange red 80 white 100 dodger blue #2-6
    ```

    Y oculte los modelos de DENV2

    ```
    ~ribbon #0-1;~display
    ```

    * ¿Qué puede decir de la predicción en la hélice N-terminal?

## Otros Recursos

* How to interpret AlphaFold2 structures
[https://www.youtube.com/watch?v=UqeQfRDA8Yk](https://www.youtube.com/watch?v=UqeQfRDA8Yk)

* AlphaFold Protein structure database
[https://alphafold.ebi.ac.uk/](https://alphafold.ebi.ac.uk/)
