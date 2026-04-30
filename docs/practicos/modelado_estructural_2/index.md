# **TP 3**. Predicción Estructural (B) { markdown data-toc-label = 'TP 3b ' }

## Recursos Online

* AlphaFold Server: [https://alphafoldserver.com/](https://alphafoldserver.com/)
* MolProbity: [http://molprobity.biochem.duke.edu/](http://molprobity.biochem.duke.edu/)
* UCLA-DOE LAB (Verify3D / Procheck): [https://saves.mbi.ucla.edu/](https://saves.mbi.ucla.edu/)
* IUPred2A: [https://iupred2a.elte.hu/](https://iupred2a.elte.hu/)
* ChimeraX o Chimera: descargar de [https://www.cgl.ucsf.edu/chimera/](https://www.cgl.ucsf.edu/chimera/)


## Objetivos Generales

* Utilizar AlphaFold Server para predecir estructuras de proteínas.
* Interpretar las métricas de confianza (pLDDT, PAE)
* Evaluar la calidad de los modelos con herramientas clásicas (MolProbity, Verify3D, Procheck).

---

## Modelado de Monómeros

### Ejercicio 1

La hemoglobina es una metaloproteína globular presente en los eritrocitos de todos los vertebrados, cuya función principal es el transporte reversible de oxígeno (O₂) desde los órganos respiratorios hacia los tejidos, y el retorno de dióxido de carbono (CO₂) y protones en sentido inverso, contribuyendo así a la homeostasis del pH sanguíneo. Su estructura cuaternaria es un tetrámero de aproximadamente 64,5 kDa, compuesto por dos pares de cadenas polipeptídicas (globinas), cada una de las cuales contiene un grupo hemo con un átomo de hierro ferroso (Fe²⁺) capaz de unir una molécula de O₂ en forma cooperativa.

En los humanos adultos, la hemoglobina mayoritaria (HbA, >95%) está formada por dos subunidades α (141 residuos) y dos subunidades β (146 residuos), cuya combinación se escribe como α₂β₂. Existen variantes menores: la HbA₂ (α₂δ₂, ~2-3%) y la hemoglobina fetal (HbF, α₂γ₂), predominante durante la vida intrauterina. La expresión de las diferentes subunidades está regulada durante el desarrollo: los genes de las globinas β y γ se localizan en el cromosoma 11, mientras que los de la globina α se encuentran en el cromosoma 16. Los cambios en la afinidad por el oxígeno entre la HbF y la HbA son clave para la transferencia placentaria de O₂.

En el adulto, la producción de HbF se restringe a células eritroides "productoras de HbF" (células F), pero mutaciones en los elementos reguladores del locus β-globina pueden dar lugar a la persistencia hereditaria de HbF (HPFH), condición que atenúa la severidad de enfermedades como la anemia falciforme o las talasemias.

La hemoglobina fetal humana contiene dos subunidades gamma (HBG1 y HBG2) en lugar de las subunidades beta de la hemoglobina adulta. La subunidad gamma-1 (UniProt P69891) es una proteína pequeña (147 residuos) que pliega en un dominio globular típico de la familia de las globinas. Su estructura es muy estable y ha sido resuelta experimentalmente con alta resolución.

En este ejercicio usted utilizará AlphaFold para predecir su estructura y evaluará qué tan buena es la predicción utilizando tanto las métricas propias del servidor como herramientas externas de validación.

#### Obtención de la secuencia

1. Ingrese a UniProt ([https://www.uniprot.org/](https://www.uniprot.org/))
2. Busque la subunidad gamma-1 ingresando el UniProt ID: P69891
3. Ingrese a la sección "Sequence" y copie la secuencia usando "Copy Sequence"

#### Predicción en AlphaFold Server

4. Ingrese a [AlphaFold Server](https://alphafoldserver.com/).
5. En la sección **Entity 1**, asegúrese de que el tipo sea **Protein**.
6. Pegue la secuencia anterior en el recuadro.
7. Haga clic en **Save job**, asigne un nombre (ej. `HBG1_monomer`) y active la opción **Use seed** (elija un número entero, ej. `42` para reproducibilidad).
8. Vuelva a la lista de trabajos, haga clic en el suyo y luego en **Continue and preview job**.
9. Confirme y envíe (**Confirm and submit job**). Espere unos minutos.

#### Análisis de los resultados en el servidor

Una vez finalizada la predicción, responda:

* **Observación general:** ¿La proteína parece compacta o presenta regiones extendidas? ¿Cuántos dominios identifica?
* **Gráfico de pLDDT (coloreado en la estructura 3D):** 
    - ¿Qué colores predominan? (azul = alta confianza >90, celeste = 70-90, amarillo = 50-70, naranja/rojo <50)
    - ¿Hay algún segmento con pLDDT < 70? ¿A qué posición(es) corresponde?
* **Gráfico PAE (Predicted Aligned Error):**
    - ¿Observa dos o más bloques bien definidos? ¿Sugiere que la proteína tiene un único dominio rígido?
    - ¿El error predicho entre residuos distantes es bajo o alto?

#### Descarga de modelos y validación externa

10. Descargue el archivo ZIP desde el servidor. Descomprímalo.
11. Elija el modelo con mejor `ranking_score` (generalmente `*_model_0.cif`). Conviértalo a formato PDB  (usar Chimera para abrir el .cif y guardar como .pdb).
12. Utilice **MolProbity** para evaluar la geometría:
    - Suba su archivo PDB a [MolProbity](http://molprobity.biochem.duke.edu/).
    - Seleccione las opciones estándar (Clashes, Ramachandran, Rotamer, Cβ deviations, CaBLAM, etc.).
    - Ejecute y examine el PDF de resultados.
    - Responda:
        * ¿Qué porcentaje de residuos se encuentra en regiones favorecidas del gráfico de Ramachandran? ¿Hay outliers?
        * ¿El clashscore es aceptable (generalmente < 5 para buena calidad)?
13. Utilice **Verify3D** y **Procheck** (dentro de [SAVES](https://saves.mbi.ucla.edu/)):
    - Suba el mismo PDB, marque **Verify3D** y **Procheck**.
    - Observe el gráfico de  **Verify3D**. ¿Más del 80% de los residuos tienen score > 0.1? ¿Qué residuos caen por debajo?
    - Analice el gráfico de Ramachandran “All residues” de **Procheck**. ¿Qué porcentaje de residuos está en zonas “core”? ¿Hay residuos en regiones prohibidas?

#### Comparación con estructura experimental 

1. Busque en el PDB una estructura de hemoglobina fetal humana que incluya la subunidad gamma (1FDH) y descargue el archivo .pdb. 
3. Superponga su modelo de AlphaFold con la cadena experimental usando Matchmaker (`Tools → Structure Comparison → MatchMaker`).
O bien, ingrese en la command line:

    ```
    mm #0 #1
    ```

4. Anote el RMSD global. ¿Es menor a 1.5 Å? ¿Cómo se distribuye el error?

#### Preguntas

1. ¿Considera que la predicción de AlphaFold para HBG1 es de alta calidad? Justifique usando pLDDT, PAE y las métricas de MolProbity/Verify3D.
2. ¿Qué región de la proteína mostró menor confianza? ¿Puede relacionarla con alguna característica biológica?

---

### Ejercicio 2
Como se mencionó en la introducción teórica, cada cadena polipeptídica de hemoglobina contiene un **grupo hemo** (protoporfirina IX con un átomo de hierro en el centro). Este grupo es esencial para la unión reversible del oxígeno. En el Ejercicio 1 modelamos la subunidad gamma-1 sola, sin su cofactor. Ahora vamos a modelar **la misma proteína** pero **incluyendo el hemo** como ligando.

#### Clonar y reutilizar el trabajo anterior

1. Ingrese a [AlphaFold Server](https://alphafoldserver.com/).
2. En la lista de trabajos, ubique el modelo que generó en el **Ejercicio 1** (hemoglobina gamma-1 sin ligandos).
3. Haga clic en los **tres puntos** a la derecha del nombre del trabajo.
4. Seleccione **"Clone and reuse"**. Esto creará una copia del trabajo con la misma secuencia y parámetros.

#### Agregar el grupo hemo como ligando

1. En la nueva ventana, haga clic en **"+ Add entity"**.
2. En **Entity type**, seleccione **"Ligand"**.
3. En **"Number of copies"**, deje **1**.
4. En el recuadro de búsqueda busque y seleccione **"HEM - Hem"**. 
5. Haga clic en **Save job**, asigne un nombre (ej. `HBG1_monomer_hem`) y active la opción **Use seed** (use la misma semilla que en el Ejercicio 1 para poder comparar).
6. Vuelva a la lista de trabajos, haga clic en su nuevo trabajo y luego en **Continue and preview job**.
7. Confirme y envíe (**Confirm and submit job**). Espere unos minutos.

#### Análisis de los resultados

Una vez finalizada la predicción, responda:

1. **Observación general:** ¿Qué cambios observa en la estructura 3D en comparación con el modelo del Ejercicio 1 (sin hemo)? 

2. **Gráfico de pLDDT:**  
  - ¿Qué colores predominan ahora?  
  - ¿Hay diferencias en los valores locales de pLDDT alrededor de la zona donde se ubica el hemo?  
  - ¿Alguna región que antes tenía baja confianza (ej. extremos) ahora mejoró o empeoró?
3. **Gráfico PAE:**  
  - ¿Se observa una interacción bien predicha entre la proteína y el ligando?

4. **Efecto del ligando:** ¿La inclusión del grupo hemo mejoró significativamente el pLDDT en el entorno del bolsillo de unión? ¿En qué medida?
5. **Comparación con estructura real:** Si tiene acceso al PDB de una hemoglobina (ej. 1FDH), ¿el hemo predicho por AlphaFold se superpone bien con el hemo experimental?
6. **Utilidad del modelado con ligandos:** ¿En qué casos recomendaría incluir cofactores o ligandos en una predicción con AlphaFold? ¿Siepmre es beneficioso?

#### (Opcional – Extra) Agregar también el ion hierro (Fe²⁺)

Si el tiempo y la paciencia lo permiten, puede realizarse un **tercer modelado** incorporando **dos entidades ligando**: el hemo **y** el ion Fe²⁺ por separado. El hemo ya contiene un átomo de hierro en su estructura, pero AlphaFold permite modelar el ion libre para estudiar su posición.

**Pasos adicionales:**

1. Clone nuevamente el trabajo del Ejercicio 1 (o el que ya tiene hemo).
2. Agregue **dos ligandos**:
   - El primero: **HEM** (1 copia).
   - El segundo: **FE** (ion hierro, código `FE`) con 1 copia.
3. Envíe y espere (el tiempo de cómputo será mayor, posiblemente 15-20 minutos).
4. Compare este modelo con los dos anteriores:

   - ¿El ion Fe²⁺ se ubica dentro del anillo del hemo?
   - ¿Cambian las métricas de confianza (pTM, ipTM) con respecto al modelo que solo tenía hemo?

---

### Ejercicio 3

#### Investigar en UniProt

1. Vamos a seguir trabajando con la misma proteína del ejercicio 1. Vuelvan a ingresar a [UniProt](https://www.uniprot.org/). 
2. En la página de la proteína, busquen la **PTM/processing**. ¿Que tipos de modificaciones postraduccionales aparecen en la página? ¿En qué posición ocurren?

#### Modelado de una PTM

Para este ejercicio, van a usar la **lisina en posición 83 (K83)** como ejemplo práctico. 

#### Modelado en AlphaFold Server

1. En AlphaFold Server, clonen el trabajo que hicieron en el **Ejercicio 1** (el modelo de HBG1 sin modificaciones).
2. En la entidad proteica, hagan clic en el menú vertical (⋮) → **"+ PTMs"**.
3. Se abrirá una ventana con la secuencia de 147 aminoácidos. **Localicen la lisina en posición 83** (la letra **K** número 83).
4. Hagan clic sobre esa **K**.
5. En el menú desplegable, seleccionen **"N6-Acetyl-L-lysine"**.
6. Guarden el cambio y cierren la ventana.
7. Mantengan la **misma semilla (seed)** que usaron en el Ejercicio 1.
8. Asígnenle un nombre, por ejemplo `HBG1_cetyl_L_lysine_K83`, y envíen el trabajo.

#### Comparar 

Una vez que el modelo acetilado esté listo, compárenlo con el modelo original:

- **pLDDT**: ¿La confianza local alrededor de la K83 cambió? ¿Se ve algún efecto en la región?
- **Métricas globales**: Comparen `pTM` y `ranking_score` entre ambos modelos.
- **Observación estructural**: Si pueden, superpongan los dos modelos en Chimera y observen el residuo modificado

---

## Modelado de dímeros

### Ejercicio 4

El receptor de neurotrofinas p75NTR (p75 neurotrophin receptor) es una proteína transmembrana clave en la supervivencia neuronal, la apoptosis y el crecimiento axonal. Su señalización está finamente regulada por interacciones con múltiples efectores citosólicos. Uno de ellos es la proteína RhoGDI (Rho GDP‑dissociation inhibitor), que controla la actividad de las GTPasas de la familia Rho. En respuesta a la fosforilación de RhoGDI por PKC, se promueve la interacción entre el dominio yuxtamembrana (JMD) de p75NTR y el dominio N‑terminal (NTD) de RhoGDI, lo que desencadena una vía de señalización que culmina en la retracción axonal y apoptosis.

La estructura tridimensional de este complejo fue resuelta recientemente por resonancia magnética nuclear (RMN) y depositada bajo el código **PDB 8X8T**. En este ejercicio, usted utilizará AlphaFold para predecir la estructura del complejo de dos maneras:

1. **Sin usar templates estructurales** – para evaluar qué tan bien el método predice de novo la interacción.
2. **Proporcionando el complejo experimental como template** – para analizar cómo el uso de información estructural previa modifica la calidad y la confianza de la predicción.

A partir de la entrada **8X8T**, el complejo está formado por dos cadenas (se utilizan las secuencias exactas de la estructura de RMN):

```
>Cadena A – Dominio N‑terminal de RhoGDI (residuos 2‑60 de la proteína completa UniProt P52565)**
MAEQEPTAEQLAQIAAENEEDEHSVNYKPPAQKSIQEIQELDKDDESLRKYKEALLGRVAVSADPNVPNVVVTGLTLVCSS
```

```
>Cadena B – Dominio yuxtamembrana de p75NTR (residuos 273‑332 de UniProt P08138)**
NLIPVYCSILAAVVVGLVAYIAFKRWNSCKQNKQGANSRPVNQTPPPEGEKLHSDSGISVDSQSLHDQQPHTQTASGQALKGDGGLYSSLPP
```
#### Predicción

1. Ingrese a [AlphaFold Server](https://alphafoldserver.com/).
2. Agregue dos entidades proteicas (**Add entity**).
   - **Entity 1:** pegue la secuencia de la **Cadena A** (RhoGDI‑NTD). Tipo *Protein*.
   - **Entity 2:** pegue la secuencia de la **Cadena B** (p75NTR‑JMD). Tipo *Protein*.
3. Asigne un nombre al trabajo, por ejemplo `p75_RhoGDI_sinTemplate`. Active “Use seed” para reproducibilidad.
4. Envíe el trabajo y espere los resultados (~5‑10 minutos).

#### Predicción con el uso del template 8X8T

1. Cree un **nuevo trabajo** con las mismas dos entidades proteicas y las mismas secuencias.
2. Acceda al [RCSB PDB](https://www.rcsb.org/structure/8X8T).
3. Descargue el archivo en formato PDB (opción “Download Files” → “mmCIFF Format”).
4. Guarde el archivo con el nombre `8x8t.cif` en una carpeta accesible.

Cuando descargás un archivo PDB que contiene múltiples cadenas (como 8X8T, que tiene cadena A y cadena B), vamos a separarlas en archivos individuales para usarlas como templates por separado.

#### Guardar cada cadena por separado usando el Model Panel

1. **Abrí el archivo PDB** en Chimera (`File → Open`).
2. **Abrí el Model Panel**: `Favorites → Model Panel`
3. **Identificá las cadenas**: En el Model Panel, cada cadena suele aparecer como un modelo separado (ej. `8x8t.cif (A)` y `8x8t.cif (B)`). Si no están separadas automáticamente:

   - Hacé clic en el modelo principal.
   - Usá `Select → Chain` y elegí la cadena que querés (A o B).
   - Luego `Actions → all`.

4. **Seleccioná la cadena que querés guardar** (ej. Cadena A).
5. **Guardala como archivo PDB**:
   - En el Model Panel, seleccioná **solo** el modelo que contiene la cadena A (podés desmarcar los otros modelos).
   - `File → Save PDB...`
   - Elegí un nombre, por ejemplo `8x8t_cadena_A.ciff`
6. **Repetí** para la cadena B.

#### Cargar los templados en Alphafold

1. Ingresá en los tres puntos a la derecha de la secuencia. En la sección **Templates settings**:
   - Seleccione la opción “Upload custom template” o “Provide mmCIF file”.
   - Suba el archivo generado descargado previamente correspondiente a la cadena.
   - **Verifique la asignación de cadenas:** asegúrese de que la cadena A del template corresponde a RhoGDI‑NTD (Entity 1) y la cadena B a p75NTR‑JMD (Entity 2). 
2. Envíe el trabajo y espere los resultados.

#### Análisis comparativo

Una vez que ambos trabajos estén listos, responda las siguientes preguntas utilizando las visualizaciones del servidor, los archivos descargados y Chimera.

**A. Métricas globales de confianza**

Descargue los archivos ZIP de ambos trabajos y abra los archivos `*_summary_confidences_0.json`. Complete la siguiente tabla:

| Predicción        | pTM | ipTM | ranking_score  | fraction_disordered |
|-------------------|-----|------|----------------|---------------------|
| Sin template      |     |      |                |                     |
| Con template 8X8T |     |      |                |                     |

- ¿Cuál de las dos predicciones tiene mejor ranking_score? ¿A qué atributos cree que se debe la diferencia?
- ¿El ipTM (interfaz) mejora al usar el template? ¿Qué interpretación biológica tiene esto?

**B. pLDDT por cadena**

En la visualización 3D del servidor, observe el coloreado por pLDDT para ambos modelos.

- ¿En qué modelo hay más regiones con pLDDT > 90 (azul)? 
- ¿Alguna de las dos cadenas presenta un aumento sistemático de confianza en el modelo con template? Especifique cuál.

**C. Gráfico de PAE (Predicted Aligned Error)**

Compare los diagramas de PAE de ambas predicciones.

- En el modelo sin template: ¿el error predicho entre residuos de la cadena A y la cadena B?
- En el modelo con template: ¿cambia esa región? ¿El template reduce la incertidumbre en la orientación relativa de los dos dominios?

### Ejercicio 5

La proteína del retinoblastoma (Rb) es un supresor tumoral que regula negativamente la progresión del ciclo celular. Su función principal es unirse a los factores de transcripción de la familia E2F (en particular E2F1 y su heterodímero con DP1), reclutando complejos remodeladores de cromatina y reprimiendo la transcripción de genes necesarios para la transición G1/S. La unión ocurre entre el dominio **C‑terminal de Rb** (RbC) y el **heterodímero E2F1/DP1**. Cuando Rb es fosforilada por quinasas ciclina‑dependientes (CDK), se libera de E2F/DP y se activa la transcripción.

La estructura cristalográfica de este complejo trimérico fue depositada con el código **2AZE**. Sin embargo, la estructura resuelta por cristalografía de rayos X (2,55 Å) incluye solo las regiones que son estables y ordenadas en el cristal. En solución, muchos fragmentos de E2F1, DP1 y Rb permanecen flexibles o desordenados, especialmente fuera de la interfaz de unión. 

En este ejercicio usted modelará el trímero completo y, por separado. 

#### Modelado de las tres secuencias:

##### Cadena 1 – E2F1 (UniProt Q01094, 437 residuos)

```
>sp|Q01094|E2F1_HUMAN Transcription factor E2F1 OS=Homo sapiens OX=9606 GN=E2F1 PE=1 SV=1
MALAGAPAGGPCAPALEALLGAGALRLLDSSQIVIISAAQDASAPPAPTGPAAPAAGPCDPDLLLFATPQAPRPTPSAPRPALGRPPVKRRLDLETDHQYLAESSGPARGRGRHPGKGVKSPGEKSRYETSLNLTTKRLELLSHSADGVVDLNWAAEVLKVQKRRIYDITNVLEGIQLIAKKSKNHIQWLGSHTTVGVGGRLEGLTQDLRQLQESEQQLDHLMNICTTQLRLLSEDTDSQRLAYVTCQDLRSIADPAEQMVMVIKAPPETQLQAVDSSENFQISLKSKQGPIDVFLCPEETVGGISPGKTPSQEVTSEEENRATDSATIVSPPPSSPPSSLTTDPSQSLLSLEQEPLLSRMGSLRAPVDEDRLSPLVAADSLLEHVREDFSGLLPEEFISLSPPHEALDYHFGLEEGEGIRDLFDCDFGDLTPLDF
```

##### Cadena 2 – DP1 (UniProt Q14186, 410 residuos)

```

>sp|Q14186|TFDP1_HUMAN Transcription factor Dp-1 OS=Homo sapiens OX=9606 GN=TFDP1 PE=1 SV=1
MAKDAGLIEANGELKVFIDQNLSPGKGVVSLVAVHPSTVNPLGKQLLPKTFGQSNVNIAQQVVIGTPQRPAASNTLVVGSPHTPSTHFASQNQPSDSSPWSAGKRNRKGEKNGKGLRHFSMKVCEKVQRKGTTSYNEVDELVAEFSAADNHILPNESAYDQKNIRRRVYDALNVLMAMNIISKEKKEIKWIGLPTNSAQECQNLEVERQRRLERIKQKQSQLQELILQQIAFKNLVQRNRHAEQQASRPPPPNSVIHLPFIIVNTSKKTVIDCSISDKFEYLFNFDNTFEIHDDIEVLKRMGMACGLESGSCSAEDLKMARSLVPKALEPYVTEMAQGTVGGVFITTAGSTSNGTRFSASDLTNGADGMLATSSNGSQYSGSRVETPVSYVGEDDEEDDDFNENDEDD
```

##### Cadena 3 – Rb (UniProt P06400, 928 residuos)

```
>sp|P06400|RB_HUMAN Retinoblastoma-associated protein OS=Homo sapiens OX=9606 GN=RB1 PE=1 SV=2
MPPKTPRKTAATAAAAAAEPPAPPPPPPPEEDPEQDSGPEDLPLVRLEFEETEEPDFTALCQKLKIPDHVRERAWLTWEKVSSVDGVLGGYIQKKKELWGICIFIAAVDLDEMSFTFTELQKNIEISVHKFFNLLKEIDTSTKVDNAMSRLLKKYDVLFALFSKLERTCELIYLTQPSSSISTEINSALVLKVSWITFLLAKGEVLQMEDDLVISFQLMLCVLDYFIKLSPPMLLKEPYKTAVIPINGSPRTPRRGQNRSARIAKQLENDTRIIEVLCKEHECNIDEVKNVYFKNFIPFMNSLGLVTSNGLPEVENLSKRYEEIYLKNKDLDARLFLDHDKTLQTDSIDSFETQRTPRKSNLDEEVNVIPPHTPVRTVMNTIQQLMMILNSASDQPSENLISYFNNCTVNPKESILKRVKDIGYIFKEKFAKAVGQGCVEIGSQRYKLGVRLYYRVMESMLKSEEERLSIQNFSKLLNDNIFHMSLLACALEVVMATYSRSTSQNLDSGTDLSFPWILNVLNLKAFDFYKVIESFIKAEGNLTREMIKHLERCEHRIMESLAWLSDSPLFDLIKQSKDREGPTDHLESACPLNLPLQNNHTAADMYLSPVRSPKKKGSTTRVNSTANAETQATSAFQTQKPLKSTSLSLFYKKVYRLAYLRLNTLCERLLSEHPELEHIIWTLFQHTLQNEYELMRDRHLDQIMMCSMYGICKVKNIDLKFKIIVTAYKDLPHAVQETFKRVLIKEEEYDSIIVFYNSVFMQRLKTNILQYASTRPPTLSPIPHIPRSPYKFPSSPLRIPGGNIYISPLKSPYKISEGLPTPTKMTPRSRILVSIGESFGTSEKFQKINQMVCNSDRVLKRSAEGSNPPKPLKKLRFDIEGSDEADGSKHLPGESKFQQKLAEMTSTRTRMQKQKMNDSMDTSNKEEK
```

Antes de modelar, explore las predicciones estructurales que ya están disponibles en la **AlphaFold Protein Structure Database** para cada una de las tres proteínas.

- Acceda a UniProt: [https://www.uniprot.org/](https://www.uniprot.org/)
- Busque los códigos **Q01094** (E2F1), **Q14186** (DP1) y **P06400** (Rb).
- En cada página, localice el botón “AlphaFold” o “3D structure” y haga clic para explorar el modelo predicho.

#### Modelado de Rb

1. Ingrese a [AlphaFold Server](https://alphafoldserver.com/).
2. En la **Entity 1**, configure tipo **Protein** y pegue la secuencia de Rb (completa, tal como aparece arriba).
3. Asigne un nombre descriptivo, por ejemplo `Rb`.
4. Active la opción **Use seed** y elija un número entero (ej. `12345`).
5. Envíe el trabajo y espere (aproximadamente 5‑10 min).
6. Cuando termine, descargue el archivo `.cif` del mejor modelo.

#### Modelado del trímero completo (E2F1 + DP1 + Rb)

Ahora modele el complejo con las secuencias **completas** de las tres proteínas.

1. En AlphaFold Server, cree un **nuevo trabajo**.
2. Agregue **tres entidades proteicas** con el botón “Add entity”.
   - **Entity 1:** E2F1.
   - **Entity 2:** DP1.
   - **Entity 3:** Rb.
3. Asegúrese de que el tipo de todas sea **Protein** y que el orden de las cadenas sea el indicado.
4. Asigne otro nombre, por ejemplo `Trimer_E2F1_DP1_Rb`.
5. Use la **misma semilla** (seed) que en el punto anterior.
6. Envíe el trabajo y espere (entre 15 y 30 min).

#### Comparación de la confianza entre el monómero y el trímero

Una vez que ambos trabajos estén listos, compare las métricas de confianza.

**A. Perfil de pLDDT por residuo**

- Sobre el modelo del **trímero**, identifique las cadenas que corresponden a la proteína elegida para modelar sola. ¿Esas regiones presentan ahora pLDDT más altos que cuando la proteína se modeló sola? ¿Dónde ocurre el aumento de confianza?
- ¿Qué pasa con los extremos N‑terminal y C‑terminal de E2F1 y DP1 en el trímero? ¿Siguen siendo desordenados o se ordenan en el complejo?

**B. Análisis del PAE (Predicted Aligned Error)**

Examine el gráfico de PAE del trímero.

- ¿El error predicho entre residuos de diferentes cadenas es bajo o alto?
- Identifique en el gráfico los bloques que representan interacciones **E2F1‑DP1** (heterodimerización) y **E2F1‑Rb** (unión reguladora). ¿Cuál es más confiable según el PAE?

#### Comparación con la estructura cristalográfica de referencia

1. Descargue el archivo PDB de 2AZE desde el RCSB (código `2aze`).
2. Abra el PDB en Chimera
3. Alinee su modelo del trímero completo contra el fragmento experimental usando **MatchMaker**..

- ¿Las regiones que están presentes en 2AZE y en su modelo coinciden con alta precisión (RMSD < 2 Å)?
- ¿Qué partes de su modelo se desvían más? ¿Corresponden a regiones que están ausentes en la estructura cristalográfica?

---

### Ejercicio extra 1

#### Predicción en AlphaFold Server

Utilice la isoforma CALM1 (UniProt P0DP23):

```
>sp|P0DP23|CALM1
MADQLTEEQIAEFKEAFSLFDKDGDGTITTKELGTVMRSLGQNPTEAELQDMINEVDADGNGTIDFPEFLTMMARKMKDTDSEEEIREAFRVFDKDGNGISAAELRHVMTNLGEKLTDEEVDEMIREADIDGDGQVNYEEFVQMMTAK
```

1. Copien la secuencia y créen un trabajo en AlphaFold Server.
2. Usen una semilla (seed) para reproducibilidad.
3. Envíen y esperen.

#### Análisis de los resultados en el servidor

Una vez que el servidor terminó, observen:

- El coloreado por pLDDT. ¿Hay regiones con baja confianza (amarillo, naranja, rojo)? ¿Dónde?
- El gráfico de PAE. ¿Se ven dos bloques diagonales separados por una zona de colores cálidos (error alto)?
- Anoten los valores de pTM y ranking_score del archivo `*_summary_confidences_0.json`.

#### Investigación en UniProt

Ahora vayan a [UniProt](https://www.uniprot.org/) y busquen la secuencia (pueden  usar la información del header). Identifiquen la proteína.

Lean con atención las secciones:

- **Function** (especialmente el recuadro “Miscellaneous” si existe).
- **Family & Domains**.
- **Cofactor**.

Respondan:

- ¿Cuál es el nombre real de esta proteína?
- ¿Qué molécula (ión, ligando) se menciona como esencial para su función?
- ¿Cuántas copias de esa molécula se unen a la proteína?
- ¿Qué cambio estructural produce esa unión?

#### Segundo modelado

Vuelvan a AlphaFold Server y creen un nuevo trabajo con **la misma secuencia proteica**, pero ahora agreguen el ion que descubrieron.

- Entity 1: la proteína (igual).
- Usen **Add entity → Ion**. Busquen el ligando por nombre
- Agreguen la cantidad de copias que indica UniProt.
- Usen la **misma semilla** que en el primer modelado.
- Envíen y esperen. (Este modelado demora bastante!)

#### Comparación de los resultados

Comparen los dos modelos (sin ligando y con ligando):

1. **pLDDT**: ¿la región que antes tenía baja confianza ahora mejoró?
2. **PAE**: ¿el gráfico de PAE pasó de mostrar dos bloques separados a un único bloque azul?
3. **Métricas globales**: completen esta tabla.

| Modelo  | pTM | ipTM | ranking_score  |
|---------|-----|------|----------------|
| Sin ion |     |      |                |
| Con ion |     |      |                |

**Opcional (Chimera)**: superpongan los dos modelos y observen las diferencias estructurales.
