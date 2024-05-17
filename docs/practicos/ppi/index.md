
# **TP 5.** Interacciones proteína-proteína { markdown data-toc-label = 'TP 5'}

## Recursos Online
* Intact: [https://www.ebi.ac.uk/intact/home](https://www.ebi.ac.uk/intact/home)
* STRING: [https://string-db.org/](https://string-db.org/)
* KEGG. [https://www.kegg.jp/kegg/pathway.html](https://www.kegg.jp/kegg/pathway.html)

## Objetivos
* Familiarizarse con el uso de la base de datos de interacciones proteína-proteína
* Entender los distintos tipos de evidencia experimental, o no experimental, que se puede tener para el estudio de interacciones proteína-proteína
* Entender los distintos tipos de interacciones proteína-proteína que se pueden detectar experimentalmente

## Introducción
Las interacciones proteína-proteína son esenciales en casi todos los procesos celulares, por lo tanto es uno de los campos más estudiados ya que su entendimiento es crucial para comprender la fisiología celular en estados normales o anormales (como enfermedades) y para el desarrollo de drogas. Además, el conocimiento de las distintas interacciones permitiría identificar posibles roles funcionales para proteínas aún no caracterizadas.

Las interacciones proteína-proteína son contactos físicos que ocurren entre determinadas proteínas. Estos contactos son específicos, ocurren entre regiones de interacción de las proteínas, definen una función específica y pueden ser transiente o estables.

Una interacción estable define un complejo proteico, mientras que una interacción transiente es una interacción breve que puede llevar a un cambio mayor y son la parte dinámica del interactoma celular.

Las interacciones proteína-proteína forman redes de interacción. El conjunto de redes de interacción dentro de una célula define el interactoma celular en un contexto biológico determinado.

Los datos relacionados con interacciones proteína-proteína aumentó muchísimo en la última década debido al desarrollo de técnicas high-throughput para detectar interacciones proteína-proteína (espectroscopía de masa, el ensayo de doble híbrido en levaduras, phage display) permitiendo determinar interactomas cada vez más completos y complejos. Sin embargo, esta información es aún incompleta y ruidosa ya que todos los métodos de detección proteína-proteína tienen sus limitaciones en relación al contexto fisiológico de la interacción.

Existen numerosas bases de datos de interacciones proteína-proteína.

Se pueden clasificar entre tres tipos principales:

* **Bases de datos primarias:** Colectan información experimental exclusivamente. Por ejemplo: IntAct, MINT y MatrixDB.
* **Bases de datos secundarias o meta-bases de datos:** Integran datos anotados (o curados) de bases de datos primarias en una base de datos. Por ejemplo, APID y PINA.
* **Bases de datos predictivas:** Combinan los datos experimentales de las bases de datos primarias con predicciones computacionales. Por ejemplo, STRING y UniHI.

## IntAct
IntAct es una base de datos pública de interacciones moleculares. Es mantenida por un grupo de curadores y desarrolladores en el European Bioinformatics Institute (EMBL-EBI, Hinxton, UK) y es la base de datos más abarcativa de interacciones moleculares. Los datos de interacciones moleculares son curados a partir de la literatura. Si bien la mayoría de las interacciones almacenadas en IntAct son interacciones proteína-proteína, existen otras interacciones que involucran pequeños compuestos químicos o ácidos nucleicos. IntAct además es miembro del consorcio internacional de intercambio molecular (International Molecular Exchange Consortium, IMEx). El objetivo de este consorcio es unificar el esfuerzo de curación de los datos experimentales de interacciones moleculares.

## IntAct - Ejercicios

### Ejercicio 1. Interacciones de la Proteína Retinoblastoma (Rb)
1. Busque en Intact la proteína retinoblastoma (Rb) humana usando su accession number (P06400).

    !!! Warning
    
        En esta base de datos no se puede utilizar el nombre de la entrada UniProt.

2. El resultado de IntAct es visualizado de dos maneras:

    * Mediante una **red** donde los nodos son proteínas o moléculas, que están conectados por edges que pueden representar distintas cosas como: número de experimentos anotados, nivel de confianza, entre otros.
    * Mediante una **tabla de interacciones** y una **tabla de interactores**, en ambos casos con columnas que pueden ser modificadas según el interés del usuario.

    En la parte superior de la tabla, hay dos pestañas que permiten cambiar entre Interacciones e Interactores. También, se puede observar el número total de interacciones que existen para Rb y el número total de interactores que existen para Rb.

    * ¿Cuántas interacciones hay?
    * ¿Cuántos interactores hay?

3. En la parte superior de la tabla de interacciones haga click en *Column Toggle* y tilde *Species A* y *Species B*. Esto hará que aparezcan las columnas que indican el organismo del cual provienen los interactores A y B.
    Mostrando de a 25 entradas en la tabla de interacciones, observe en la página 1 y en la página 13 de los resultados:
    * ¿Aparece más de un organismo?
    * ¿Por qué cree que esto ocurre?
    * ¿Siempre el interactor A y el interactor B provienen de la misma especie? ¿Por qué?

4. Si quisiéramos resultados para un único organismo, en la parte superior de la página de resultados se encuentran los Filtros.

    En el filtro: *Interactor Species* observe las distintas especies que hay. 

    * ¿Hay muchos patógenos que interactúen con Rb?

    Seleccione interacciones que sean entre Rb y otra proteína Humana tildando la especie correspondiente: *Homo sapiens* y luego seleccionando que #sea **Intra** especie con el botón *Filter out cross-species interactions*.

    <p style="text-align:center">
    <img src="./img/Intact_fig2.png" alt="" style="max-width:80%">
    </p>

5. En el filtro: *Interactor Type* observe los distintos tipos de interactores que hay. Luego seleccione de manera que los interactores sean sólo **proteínas**.

6. Investigue el filtro *Interaction Detection Method*. 
    * ¿Qué tipos de técnicas experimentales hay?
    * ¿Todas las técnicas proveen evidencia de interacción directa entre proteínas?
    * ¿Puede dar algunos ejemplos de cuáles son evidencia directa y cuáles indirecta?

7. Investigue el filtro *Interaction Type*.
    * ¿Qué tipos de interacciones considera IntAct?
    * ¿Cuáles son interacciones directas y cuáles son indirectas?

8. Seleccione distintos tipos de interacciones en *Interaction Type* y observe los distintos tipos de técnicas experimentales en el filtro *Interaction Detection Method*.
    * ¿Coincide alguna con los ejemplos de evidencia directa e indirecta que usted seleccionó?

9. IntAct utiliza un método de puntuación para puntuar las interacciones observadas con un índice denominado el **MI score**.

    !!! Info

        El MI score es un método de puntuación modificable y heurístico que tiene en consideración tres factores:

        * El método de detección de la interacción: Observada, predicha o inferida.
        * El tipo de interacción: Direct interaction, physical association, co-localization etc
        * El número de publicaciones que reportan una interacción específica.

        En definitiva, el MI score provee un sistema de puntuación que representa el grado de confianza de una interacción en particular evaluando el grado de anotación/curación de la interacción en una base de datos. A mayor evidencia experimental que apoya la interacción, mayor es la puntuación.

        * La evidencia derivada de algoritmos predictivos o métodos de text-mining contribuye menos al score final.
        
        * La combinación de métodos experimentales de baja puntuación (por ejemplo, colocalización) con evidencia no experimental da una mayor puntuación que cada uno por separado.

    * A la derecha de la red de interacción está la leyenda. ¿Qué representan los edges sólidos?
    * A la izquierda de la red de interacción, destildá la opción *Expand*. ¿Qué representa ahora el color de los edges? ¿y el ancho?

    Utiliza el filtro MI Score que se encuentra en la parte superior y encuentra los interactores con el mayor score.

    * ¿Cuántos interactores hay?
    * ¿Cuántas interacciones hay?
    * ¿Qué tipo de evidencia experimental poseen?
    * ¿Cuánta evidencia posee cada interactor?


## STRING
La base de datos STRING contiene datos de interacciones proteína-proteína conocidos y predichos. Los datos derivan de experimentos high-throughput, datos de co-expresión, literatura y contexto genómico. Abarca más de 5 millones de proteínas de más de 1100 organismos. 

## STRING - Ejercicios

### Ejercicio 1. Interacciones de la Proteína Retinoblastoma (Rb)

1. En STRING se puede realizar una búsqueda por el o los nombres de la proteína, o el identificador, múltiples proteínas, múltiples secuencias, organismos o familias de proteínas.

    Haga click en Search y en protein name e ingrese “retinoblastoma”

    * Observe el resultado. ¿Por qué hay más de un resultado? ¿Cuál es el que deseamos?

    En el campo *protein name* también puede ingresar el accession number: P06400.

    El número de interactores que devuelve la red puede cambiarse en la pestaña *Settings*, por defecto está elegido 10. Por lo cual devuelve los 10 interactores con mejor puntuación en STRING. La red también puede expandirse utilizando los botones *more/less* para obtener una segunda capa de interacción con proteínas que conectan con la primera capa aunque no necesariamente con Rb.

    * Presione *More*, ¿observa algún interactor que no interactúe con Rb?

    ??? info "Nota en score de STRING"

        Puede haber uno o más scores en STRING para cada interacción proteína-proteína.

        Estos scores no se relacionan con la fuerza o especificidad de la interacción. Son indicadores de confianza de STRING. Es decir, dada la evidencia disponible, cuán probable es que esa interacción sea verdadera.

        Un score de 0.5 indicaría que una de cada dos interacciones es errónea, o sea, sería un falso positivo.

        Para la mayoría de los tipos de evidencia hay dos scores:

        * **normal score**

        * **transferred score:** Este score se calcula a partir de datos que no provienen del organismo de interés si no de otro organismo y luego es *transferido* vía homología.

2. Presione en *Less*, y haga click en E2F4 y observe la información disponible. Haga click en el edge que conecta E2F4 y RB1:
    * De los siete tipos de origen de evidencia ¿De dónde proviene la evidencia de interacción entre estas dos proteínas?

3. Vaya a *Legend* y responda:
    * ¿Todas las interacciones entre las proteínas de esta red tienen evidencia **experimental** asociada?

4. ¿Se encuentran los interactores con mayor score detectados en IntAct?

5. Vaya a *Analysis*. Luego, Vaya a la sección *KEGG Pathways* de la tabla y asegúrese que esté ordenada por *strength* de mayor a menor. Luego, haga click en el nodo **Rb1** de la red de interacción y luego seleccione *Show this node's terms in the analysis table*. Observe que en la tabla se resaltan los términos enriquecidos en cada base de datos relacionados con Rb.
    * ¿A qué corresponden las primeras 10 líneas de KEGG?

    ??? info "KEGG PATHWAY"

        *KEGG (Kyoto Encyclopedia of Genes and Genomes)* es una colección de bases de datos. 

        * KEGG Pathway es una de las base de datos de KEGG que almacena mapas de rutas para las funciones celulares y de organismos.

        * El *strength* (como dice en *explain columns* en la parte superior de la primera tabla) es claculado como Log~10~(observado / esperado).
        
        Esta medida describe cuan grande es el efecto de enriquecimiento. Es la relación entre:
        
            1. El número de proteínas en la red que están anotadas con un término.
            2. El número de proteínas que se espera que están anotadas con ese término en una red *random* con el mismo tamaño.

6. Elija los dos interactores de mayor score detectados en Intact y haga lo mismo.
    * ¿Cuáles son los KEGG pathways comunes a las tres proteínas?

7. En la sección KEGG pathways haga click en el **identificador** que corresponde a Cell Cycle.
    * ¿Puede encontrar a Rb?
    * ¿Encuentra a los interactores con mayor evidencia?
    * ¿Puede nombrar al menos una enzima que fosforile a Rb y otra que la desfosforile?


## Ejercicios

### Ejercicio 1. Interacciones de la Proteína Spike de SARS-COV2

1. Busque en IntAct las interacciónes que existen de la proteína Spike de SARS-COV2 (P0DTC2) con humanos (recuerde usar los filtros para ver interacciones sólo con humanos). 

    A la izquierda de la red tilde la opción de agrupar por Species. 
    
    * ¿Cuántas proteínas Spike observa en la red? 
    
    Coloque el puntero sobre el nodo y encuentre los identificadores.
    
    * ¿Son los mismos?

2. Haga clic en la que el identificador es: P0DTC2-PRO_0000449647, verá que la tabla en la parte inferior sólo muestra las interacciones relacionadas con esta proteína. Siga el link a Uniprot:

    * ¿A qué corresponde?

3. Haga click en la que el identificador es: P59594. En la tabla haga click en el ícono que se encuentra en la primera columna. Se abrirá una nueva ventana con detalles de la interacción, que están detallados en la parte inferior.

    * ¿Por qué cree que se obtuvo esta proteína?

4. ¿Qué tipo de evidencia hay para las interacciones identificadas?
5. Destilde la opción *Expand*.
    * ¿Cuales son las proteínas con más evidencia?
    * ¿Poseen evidencia estructural?
    * ¿Qué técnicas se utilizaron?

### Ejercicio 2. Análisis de interacción RBD-ACE2: Reconocimiento de superficie de Contacto
El objetivo de este ejercicio consiste en analizar la superficie de interacción entre RBD y ACE2. Se focalizará en la identificación de los residuos involucrados y en la determinación de la naturaleza de las interacciones. En particular se intentará establecer si existe algún contacto estrecho que estabilice la región RBM.

1. Abrir Chimera y abrir el archivo “6m0j.pdb” utilizando el atajo que se encuentra a la derecha de la ventana.

2. Esconder todos los átomos y colorear la visualización “ribbon” de acuerdo a su estructura secundaria.

    *Actions* → *Atoms/Bonds* → *hide*

    *Tools* → *Depiction* → *Color Secondary Structure* y `OK`

3. Recorrer la región de RBD que pudiera estar involucrada en la interacción con ACE2. La región RBM comprende los residuos Asn 437 y Tyr 508 de RBD. Marque esta región en el panel de secuencia.

    * ¿Qué tipos de estructura secundaria se encuentran en esta región de Spike?
    * ¿Cuál es la más abundante?
    * ¿Y en ACE2 cual es la estructura secundaria probablemente involucrada en la interacción? 
   
4. Se seleccionarán las regiones de ACE2 y RBD involucradas en la interacción. Para tal fin se utilizará la línea de comandos y a las selecciones se les asignarán los nombres “enACE2” y “enRBD” respectivamente.

    ```
    select :19-46.a,75-84.a,324-331.a,352-359.a,388-393.a
    namesel enACE2
    select :403-423.e,437-508.e; namesel enRBD
    ```
    
    Para acceder con mayor facilidad, se fijará la ventana de selecciones con nombre. De esta manera el menú queda en una ventana accesoria permitiendo acceder fácilmente a las selecciones previamente nombradas.

    *Select* → *Named Selections* (buscar la línea de puntos por arriba de “enACE2”)

    * ¿Qué ocurre al presionar el nombre de las selecciones en esta nueva ventana?

5. Colorear ambas regiones de modo que se puedan diferenciar de forma sencilla. 
6. Utilizar la ventana de selecciones previamente fijada para seleccionar la región “enACE2” y luego asignarle un color distintivo (evitando los colores “rojo”, “azul” y “amarillo”). 

    *Actions* → *Color*

    Recuerde que también puede hacerlo por línea de comandos:

    ```
    color green,a,r enACE2
    ```

    De esta forma se habrán coloreado tanto la representación **ribbon** (por eso la `r`), como los átomos (por eso la `a`) de cada residuo en la selección. Esto último dificulta distinguir los diferentes elementos químicos. Por lo tanto, adicionalmente se utilizará la coloración **by heteroatom**.

    *Actions* → *Color* → *by heteroatom*

    Recuerde que también puede hacerlo por línea de comandos:

    ```
    color byhetero enACE2
    ```

    Repetir la operación seleccionando en la ventana de selecciones “enRBD”.

    *Actions* → *Color* (elegir un color)
    *Actions* → *Color* → *by heteroatom* (para poder distinguir mejor los elementos químicos)

    Por línea de comandos:

    ```
    color pink,a,r enRBD
    color byhetero enRBD
    ```

7. Como primer abordaje para la identificación de contactos entre ambas cadenas, se seleccionarán con la línea de comandos aquellos residuos de ACE2 que tengan al menos un átomo a una distancia menor de 4 Å de un residuo de RBD. Estos residuos se denominarán “resACE2”. 

    ```
    select :.e zr < 4 & :.a; namesel resACE2
    ```

    * ¿Qué aparece ahora en la ventana de selecciones nombradas? ¿Utilizando la “lupa verde”, cuántos residuos involucra esta selección?   

8. De manera similar se procede con los residuos de RBD, y a esta selección se la llamará “resRBD”.

    ```
    select resACE2 zr < 4 & :.e; namesel resRBD
    ```

    * ¿Cuántos residuos abarca esta selección? En las ventanas de secuencias explorar qué residuos se resaltan al tocar las selecciones “enACE2”, “resACE2”, “enRBD” y “resRBD”.

9. Visualizar las cadenas laterales de los residuos en “resACE2” y “resRBD” utilizando la ventana de selecciones (asegurarse que se encuentren seleccionados). 

    *Actions* → *Atoms/Bonds* → *show*

    Por línea de comandos:

    ```
    display resACE2
    display resRBD
    ```

    Experimentar diferentes representaciones para los átomos de las cadenas laterales seleccionadas.

    *Actions* → *Atoms/Bonds* → *stick/ball stick/sphere/wire*

    ```
    represent stick
    represent bs
    represent sphere
    represent wire
    ```

10. A continuación, se hará foco en analizar algunas interacciones establecidas entre los residuos de RBD y los correspondientes de ACE2 utilizando la línea de comandos. Para las cuatro interacciones descriptas abajo, analice y responda:

    * ¿De qué tipo de interacción se trata? **I-** interacción hidrofóbica, **II-** puente de hidrógeno, **III-** puente salino. 
    * ¿Los contactos se dan entre residuos de cadena principal o lateral? 
    * Determine para cada caso la distancia de contacto.

    Para responder este punto, haga cada una de las cuatro selecciones indicadas a continuación, observe las interacciones y realice las mediciones como hizo previamente. Pista: si sospecha que hay un puente de hidrógeno puede buscarlo utilizando los comandos usados previamente de la siguiente manera:

    Luego de seleccionar el par de residuos correspondiente:

    *Tools* → *Structure Analysis* → *FindHBond*

    En la ventana puede tildarse la opción: *Only find H-bonds* y seleccionar *with both ends selected*.

    Luego presione `OK`.

    **Gln 493 (RBD); Glu 35(ACE2)**

    ```
    ~select; ~display; select :493.e, 35.a; namesel Q493-E35; display Q493-E35; focus Q493-E35; represent stick
    ```

    **Lys 417 (RBD); Asp 30 (ACE2)**
    ```
    ~select; ~display; select :417.e, 30.a; namesel K417-D30; display K417-D30; focus K417-D30; represent stick
    ```

    **Tyr 449 (RBD); Gln 42 (ACE2)**
    ```
    ~select; ~display; select :449.e, 42.a; namesel Y449-Q42; display Y449-Q42; focus Y449-Q42; represent stick
    ```

    **Phe 486 (RBD); Leu 79, Met 82, Tyr 83 (ACE2)**
    ```
    ~select; ~display; select :486.e, 79.a, 82-83.a; namesel F486-L79-M82-Y83; display F486-L79-M82-Y83; focus F486-L79-M82-Y83; represent stick
    ```

    Para Volver a la visualización completa de “resACE2” y “resRBD”. 

    ```
    ~select; ~display; display resACE2 | resRBD; focus resACE2 | resRBD; represent stick
    ```

11. Salvar y cerrar sesión.

    *File* → *Save Session As…*
    *File* → *Close Session*

<!---
## Recordings
- Cierre [[MP4]](https://drive.google.com/file/d/1QgWc-uD7JdZ2DHDW6e5tnod6JaISA1Vq/view?usp=sharing)
-->

## Otros recursos

* https://www.ebi.ac.uk/training/online/courses/protein-interactions-and-their-importance/

* https://www.ebi.ac.uk/training/online/courses/network-analysis-of-protein-interaction-data-an-introduction/

* https://www.ebi.ac.uk/training/online/courses/intact-quick-tour/submitting-data-to-intact/

* https://biochem.slu.edu/bchm628/handouts/2013/PPI_Tutorial_2011.pdf

* https://www.ebi.ac.uk/intact/documentation/user-guide
