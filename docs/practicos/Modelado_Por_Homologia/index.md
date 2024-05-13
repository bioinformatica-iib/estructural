
# **TP 3**. Modelado por Homología - Parte I  { markdown data-toc-label = 'TP 3' }

## Recursos Online

* HHPred: [https://toolkit.tuebingen.mpg.de/tools/hhpred](https://toolkit.tuebingen.mpg.de/tools/hhpred)
* UCLA-DOE LAB: [https://saves.mbi.ucla.edu/](https://saves.mbi.ucla.edu/)

## Materiales

[:fontawesome-solid-download: Materiales](https://drive.google.com/file/d/1XjpchOpDP5wdxmrLQlW3B6li8j-ceRKK/view?usp=sharing){ .md-button .md-button--primary }

## Objetivos

* Familiarizarse con las técnicas de modelado por homología
* Analizar la calidad de los modelos obtenidos

## Ejercicio 1. Modelado mistery protein.

Luego de dos años y numerosos intentos fallidos, usted logra determinar por resonancia magnética nuclear una región de una proteína misteriosa y deposita la estructura en la base de datos de proteínas PDB (PDB: 1F46).

Años después ocurre una pandemia de una enfermedad respiratoria causada por *Actinobacillus pleuropneumoniae* que está causando un rápido aumento en la mortalidad de la población porcina, trayendo terribles consecuencias en la actividad económica mundial. Una vez que se logró aislar la cepa responsable, se cree que una proteína que comparte casi el 25 % de identidad con su proteína misteriosa es un posible blanco para el diseño de una droga. Sin embargo, se desconoce la estructura de la misma. Como usted es el único experto en esa proteína en el mundo, la Asociación del Centro Médico Epidemiológico (ACME) se pone en contacto con usted en busca de una solución. Para solucionar el problema, Ud. decide primero intentar un modelado por homología de la nueva proteína.

1. Ingrese la secuencia de la proteína misteriosa patogénica en [HHPred](https://toolkit.tuebingen.mpg.de/tools/hhpred)

    ```
    >Pathogenic Mistery Protein
    MELHILFFILAGLLIAVLISFSLWSARREKSRIFSNTFSTRPPSTPINNIVSDVPPSLNPQSYAQT
    TGQHGETEADNPVQIQQEVESSLREIKINLPGQDSAAYQSKVEETPIYSGQPVLPVQPQYQTQVQY
    QTQPQHIEPAFTQAPQSPIAEATSVLEQSVEELERQAAQGDVDIYSDASVRVELAKNSMQADSVAE
    QKPVAENNMLTLYVVAPEGQQFRGDYVVQSLEALGFQYGEYQIFHRHQHMGNSASPVIFSVANMMQ
    PGIFDLTKIEHFSTVGLVLFMHLPSEGNDVVNFKLLLKTTENLAQALGGFVLNEHREIFDENSRQS
    YLARVS
    ```

2.  Haga click en **Submit** en la parte inferior de la página y seleccione el hit que le parezca más conveniente:
    
    * ¿por qué es el más conveniente?
    * ¿Que e-value tiene?
    * ¿que porcentaje de identidad posee con su proteína misteriosa (en la pate inferior está el alineamiento)?
    
    Luego seleccione en la parte superior **Model using selection**. 

    * ¿Qué se muestra en la nueva ventana? (Mueva la barra inferior para ver que hay en la ventana).

3. Haga click en **Forward to Modeller** y luego en **Submit**.

    !!! warning "Atencion"
    
        De ser necesario ingrese la siguiente key: **MODELIRANJE** en el recuadro que dice **Modeller key** y luego haga click en Submit.

    * ¿Qué aparece en la nueva ventana?

4. Descargue el archivo PDB (**Download PDB File**)

5. La herramienta **Verify3D** permite determinar la compatibilidad de un modelo 3D de una proteína con su secuencia aminoacídica en base a cuál es el ambiente en el cual se encuentra cada residuo y la compatibilidad con la estructura secundaria en la que se encuentra.  

    Vaya a la web de [UCLA-DOE LAB](https://saves.mbi.ucla.edu/), suba el archivo PDB obtenido en el paso anterior y clickee en **Run programs**.

    * Seleccione **Verify3D** y espere por los resultados.

    El gráfico reporta la calidad del modelo por posición y en él se observan tres regiones:  

    !!! Info

        * Posiciones con **score menor a cero** están **mal** modeladas,
        * Posiciones con **score entre cero y 0.2** están **pobremente** modeladas,
        * Posiciones con **score mayor a 0.2** están modeladas con **buena calidad**.

    **Verify 3D** asigna como aceptado a un modelo con más del 80% de las posiciones posiciones con un score promedio en el área **bien modelada**.

    Observe el resultado obtenido (Si tarda haga click en el botón *Check status*) y responda:  
    
    * ¿Cuál es el porcentaje de residuos con un score promedio en el **área de bien modelados**?
    * ¿Qué región está **pobremente modelada** según **Verify 3D**?

6. La herramienta **Procheck** permite analizar la calidad de la geometría de los residuos en una estructura proteica dada en comparación a parámetros estereoquímicos derivados de estructuras tridimensionales de alta resolución ya conocidas.

    En la parte superior de la página de los resultados de **Verify 3D** vaya a **Control Panel**

    Seleccione **Procheck** y espere por los resultados.

    * Investigue el **Ramachandran Plot**. Reconozca las regiones a los distintos elementos de estructura secundaria y responda:
        * ¿Cuántas estructuras se utilizaron para construir este Ramachandran?
        * ¿Qué residuos no están en el área esperada?
        * ¿Qué criterio se utiliza para considerar que el modelo es de buena calidad?
        * ¿Qué porcentaje de residuos en la estructura modelada se encuentran en las regiones más favorecidas?

    * Investigue los gráficos de ramchandran para todos los residuos en **All Ramachandrans** debe elegir el pdf.
        * ¿Cuántas estructuras se utilizaron para construir este Ramachandran?
        * ¿Qué residuos no están en el área esperada?

    * Investigue los gráficos de las longitudes de enlace en la cadena principal (M/c bond lengths) y los ángulos de unión de la cadena principal (M/c bond angles).  
        * ¿Existen aminoácidos que se alejen significativamente de los resultados esperados?

7. En base a los resultados obtenidos por **Verify 3D** y **ProCheck** responda: ¿Es bueno el modelo? ¿Por qué?

8. Abra chimera y busque el modelo que determinó usted años atrás:

    *File* → *Fetch by ID* → 1F46

    (¿Recuerda cómo hacerlo por la línea de comandos?)

    Si no funciona, el pdb se encuentra en su carpeta de datos y puede utilizar:

    *File → Open*

9. Luego, cargue en la misma ventana de Chimera la estructura de la proteína misteriosa patogénica

    *File → Open*

10. Para tener una noción de cuán similar es la estructura de dos proteínas, podemos realizar un **Alineamiento Estructural**, que consiste en superponer las estructuras de ambas proteínas en el espacio intentando alinear sus cadenas aminoacídicas. Alinear estructuras en chimera es muy fácil, sólo requiere un comando.  
  
    Vaya a *Tools → Structure Comparison → MatchMaker*
    
    Se abrirá una nueva ventana.

    * En *Reference structure* (el panel de la izquierda) puede seleccionar una de las estructuras de referencia. Esta estructura es la que se mantendrá fija. (**Ej. 1F46**)  

    * En *Structure(s) to match* (el panel de la derecha) seleccione la estructura que será superpuesta y alineada con la que se eligió como referencia. (Ej. el modelo)

    * En *Matching* asegurése que *Iterate by pruning long atom pairs untilo no pair exceeds* está clickeado.

    * Piense, ¿Porqué está utilizando el PDB:1F46?

    * Observe el resultado del alineamiento: ¿Son parecidas las estructuras? ¿En donde se observan las mayores diferencias?

    Vaya a *Favorites → Reply Log*

    * ¿Cuál es el RMSD global reportado?

11. Para ver cómo se corresponde el grado de similitud estructural con el grado de similitud en secuencia podemos realizar un alineamiento de ambas secuencias guiado por el alineamiento estructural. Para esto, vaya a:

    *Tools → Structure comparison → “Match->Align”*

    **Ahora, observando la estructura y el alineamiento responda:**  

    **I.** ¿Qué son las regiones marcadas en rosa en el alineamiento?  

    **II.** ¿Este alineamiento, identifica regiones que no alinean estructuralmente? ¿A qué se debe?

    **III.** En la parte superior de la ventana del alineamiento de secuencia vaya a **Headers** y seleccione RMSD:*ca*

    * ¿Qué regiones poseen mayor RMSD? ¿A qué elementos estructurales corresponden? Para responder esto, seleccione estas regiones con el mouse en el alineamiento y visualícelas en la estructura alineada.

12. Para cuantificar el alineamiento de secuencia obtenido, podemos calcular el % de identidad de secuencia. Para ello, en la ventana del alineamiento de secuencias vaya a:

    *Info → Percent identity*.

    Seleccione una estructura en *Compare* y la otra estructura en *with*. En *Divide by* seleccione *longer sequence length*. Presiona en Ok.  

    * ¿Qué valor de identidad de secuencia obtiene? ¿Porque cree que difiere del reportado anteriormente?

    * En la parte superior de la ventana del alineamiento de secuencia vaya a Headers y seleccione *Conservation* ¿Las sustituciones observadas en las secuencias son conservativas?  

    * En base a los resultados obtenidos. ¿Intentaría obtener experimentalmente la estructura de la nueva proteína, o confiaría en el modelo?  

## Ejercicio 2. Modelado por homología de una proteína de Rana.
Usted es un famoso ecólogo que desde siempre sintió un especial interés por las ranas. Durante un viaje de campaña se encontró con unas ranas muy inusuales que poseían una fascinante coloración azul. Luego de años de investigación y muchos subsidios invertidos, su becario descubrió que esta coloración se debe a la existencia de una proteína en la linfa de las ranas que es capaz de conjugar biliverdina. Luego de aislar la proteína, obtiene su secuencia:

```Bash
>Hypsiboas_punctatus_BP
MRVLLILGVVVLSTLAFAHHEEGHHDDEDLKDDHDPFLPEDHKKALFVYQKPALNNINFA
FKMYRQLARDHPTENIVISPVSISSALALLSLGAKGHTHSQIVERLGYNTSEIPEQQIHE
SFHKQLDVVDDKDRDLEFEHGNALFTCKEHKIHQTFLDDAKKFYHSEVIPTDFKNTEEAK
NQINSYVEKSTHGKITNILDSVDQDAMIALINFIYLRANWQHPFDEKLTKEGDFHVDKDT
TVKVPFMRRRGIYKMAYTDDIIMVTIPYNGSVEMFLAMTKMGKLSELEQNLNRERSLKWR
EIMQYQLIDLSLPKLSVSGILNLKETLSKLGIVDVFSNHADLSGITDESHLKVSKAIHKA
MMSFDEHGTEAAPATAAEADPLMLPPHFKFDYPFIFRVQDLKTKNPLLVGRIANPQK
```

Utilizando la secuencia, el becario busca en las bases de datos y descubre que su proteína es homóloga a una superfamilia de proteínas conocidas como *serpinas* compartiendo un 43% de identidad de secuencia con la proteína de humanos.  

Para entender las diferencias con la proteína de humanos, estuvo muy interesado en obtener la estructura tridimensional de la proteína de rana. Sin embargo, todos los intentos de cristalización fallaron rotundamente. Su subsidio se está terminando rápidamente pero afortunadamente, un becario muy interesado en bioinformática y el modelado por homología lo salva de su desesperación.  

Utilizando la herramienta **HHPred** el becario encontró que el mejor template era: 3NE4, Chain A, correspondiente al inhibidor de tripsina humano (Alpha-1-antitrypsin, P01009). Utilizando herramientas de modelado desarrolla un modelo 3D y le asegura que el modelo es de muy buena calidad.  

Desconfiando de los resultados de su becario, Ud. decide analizar la calidad del modelo obtenido. Para esto utiliza todas las herramientas que conoce:

1. Utilice el modelo creado por su becario (`Hypsiboas_punctatus_BP.pdb`) que se encuentra en los materiales. Utilice las herramientas aprendidas en el punto anterior ([Verify3D](https://saves.mbi.ucla.edu/)) e investigue los resultados obtenidos.

    * ¿Le parece que su becario estaba en lo cierto, o equivocado?  

2. Para explicar las diferencias obtenidas analizaremos las estructuras como se indica en los puntos siguientes usando **Chimera** 

3. Utilizando el modelo generado y el PDB (3NE4) utilizado como molde realice un alineamiento estructural en Chimera (*Tools → Structure Comparison → MatchMaker*).

    * ¿Cuál es el RMSD global?
    * ¿Qué diferencias observa en las estructuras alineadas?
    * ¿Tiene relación con lo obtenido por **Verify3D**?

4. En Chimera observe el alineamiento de secuencia (*Tools → Structure Comparison Match -> Align*).

    * ¿En qué regiones hay mayor número de Gaps?
    * Observe el RMSD por posición utilizando el RMSD:ca. ¿En qué regiones se observan las mayores diferencias? ¿A qué estructura corresponde? ¿Por qué cree que ocurre esto?

5. El algoritmo IUPred será estudiado en mayor profundidad en las próximas clases, por lo tanto, responda brevemete.

    IUPred es un predictor de desorden. El score de IUPred varía entre 0 y 1. Un umbral muy utilizado es 0.5. Un score de IUPred mayor a 0.5 se considera una región predicha desordenada o flexible y un score de IUPred menor a 0.5 se considera una región predicha globular u ordenada.

    En el gráfico, el eje x son las posiciones de la secuencia y en el eje y el *score* de IUPred que va de 0 a 1.

    Ingrese la secuencia de la rana en [IUPRed2A](https://iupred2a.elte.hu/plot). 

    * ¿Qué relación encuentra con lo obtenido por Verify3D? 

6. En base a los resultados de su análisis, responda:

    * ¿Pudo explicar todas las regiones de menor calidad reportadas por **Verify3D**?

7. Ud. Se sacó un nuevo subsidio donde tiene plata para seguir haciendo estudios estructurales de esta proteína: 

    * ¿le daría alguna indicación a su nuevo becario, para que tenga más suerte al intentar cristalizarla?
