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
    - ¿El error predicho entre residuos distantes es bajo (colores azules) o alto (rojo)?
* **Métricas globales:** Descargue el archivo ZIP y abra el archivo `*_summary_confidences_0.json`. Anote los valores de `pTM`, `ipTM` y `ranking_score`.

#### Descarga de modelos y validación externa

10. Descargue el archivo ZIP desde el servidor. Descomprímalo.
11. Elija el modelo con mejor `ranking_score` (generalmente `*_model_0.cif`). Conviértalo a formato PDB si lo prefiere (puede usar Chimera para abrir el .cif y guardar como .pdb).
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

### Preguntas

1. ¿Considera que la predicción de AlphaFold para HBG1 es de alta calidad? Justifique usando pLDDT, PAE y las métricas de MolProbity/Verify3D.
2. ¿Qué región de la proteína mostró menor confianza? ¿Puede relacionarla con alguna característica biológica?

---

### Ejercicio 2

#### Predicción en AlphaFold Server

Utilice la isoforma CALM1 (UniProt P0DP23):

```
>sp|P0DP23|CALM1
MADQLTEEQIAEFKEAFSLFDKDGDGTITTKELGTVMRSLGQNPTEAELQ
DMINEVDADGNGTIDFPEFLTMMARKMKDTDSEEEIREAFRVFDKDGNGY
ISAAELRHVMTNLGEKLTDEEVDEMIREADIDGDGQVNYEEFVQMMTAK
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

Respondan en su cuaderno:

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
- Envíen y esperen. (Este modelado demora bastante! Pueden seguir avanzando con el ejercicio 3 mientras termina de correr.)

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

<!--
Hasta acá llegué a revisar! Sigo más tarde
-->

<!--
### Ejercicio 3

El correcto funcionamiento de la proteína supresora de tumores p53 depende de su interacción con múltiples socios. Uno de ellos es el coactivador transcripcional CBP/p300, cuya unión es necesaria para la activación de genes que detienen el ciclo celular o inducen apoptosis. El dominio de transactivación (TAD) de p53 (residuos 1‑61) es **intrínsecamente desordenado** en solución. Por su parte, el dominio de unión a coactivadores nucleares (NCBD) de CBP (residuos 2059‑2111) es **parcialmente desordenado**, con una estructura de tipo “molten globule” residual. Cuando ambos dominios se encuentran, **se pliegan sinérgicamente**: NCBD adopta un haz de tres hélicesα y TAD forma dos hélicesα cortas que se insertan en una cavidad hidrofóbica de NCBD. Este fenómeno de “folding‑upon‑binding” es un ejemplo paradigmático de cómo las regiones desordenadas pueden adquirir estructura tridimensional sólo en presencia de su pareja de interacción.

<div align="center">
<img src="https://pmc.ncbi.nlm.nih.gov/articles/PMC3608666/bin/pone-0059627-g001.jpg" alt="Estructura del complejo NCBD-TAD (PDB 2L14)" width="400"/>
<p><b>Figura 1.</b> Estructura del complejo NCBD-TAD (PDB 2L14). NCBD se muestra en azul y TAD en naranja. Ambas proteínas se pliegan sinérgicamente al unirse.</p>
</div>

En este ejercicio usted utilizará AlphaFold para predecir la estructura de NCBD y TAD por separado y en complejo, y analizará si la interacción induce el plegamiento de regiones desordenadas.


####  Secuencias

**Dominio NCBD de CBP humano** (residuos 2059‑2111 de UniProt Q92793; 53 residuos)

```
>NCBD_human (CREBBP 2059-2111)
RKKIFKPEELRQALMPTLEALYRQDPESLPFRQPVDP
QLLGIPDYFDIVKNPMDLSTIKRKLDTGQYQEPW
```

**Dominio TAD de p53 humano** (residuos 1‑61 de UniProt P04637; 61 residuos)

```
>TAD_p53_human (TP53 1-61)
MEEPQSDPSVEPPLSQETFSDLWKLLPENNVLSPLPS
QAMDDLMLSPDDIEQWFTEDPGPDEAPRMPEAAP
```

#### Predicción de NCBD solo

1. En AlphaFold Server, cree un trabajo nuevo, tipo **Protein**.
2. Pegue la secuencia de **NCBD**.
3. Asigne un nombre (ej. `NCBD_solo`), active seed, y envíe.

#### Predicción de TAD solo

Realice el mismo procedimiento con la secuencia de TAD (nombre `TAD_solo`). 

#### Predicción del complejo NCBD‑TAD

1. Cree un nuevo trabajo. Agregue **dos entidades proteicas** utilizando el botón `Add entity`.
2. En Entity 1 pegue la secuencia de **NCBD**.
3. En Entity 2 pegue la secuencia de **TAD**.
4. Asegúrese de que el tipo de ambas sea **Protein**.
5. Nombre del trabajo: `NCBD_TAD_complejo`.
6. Envíe. Este complejo tiene ~114 residuos, por lo que el tiempo de cómputo será de aproximadamente 10‑15 minutos.

#### Análisis de resultados

Una vez finalizados todos los trabajos, responda las siguientes preguntas utilizando las visualizaciones del servidor y los archivos descargados.

**A. Análisis de NCBD solo**

1. Observe la estructura predicha de NCBD:
   - ¿Presenta una estructura globular compacta o aparecen segmentos extendidos/flexibles?
   - Coloree por pLDDT: ¿qué segmentos tienen pLDDT > 90? ¿Cuáles tienen pLDDT < 70?
2. Examine el gráfico de PAE:
   - ¿Se observan bloques diagonales bien definidos o hay áreas extensas de alto error (colores rojos)?
3. Compare con lo reportado en la literatura: NCBD en solución es parcialmente desordenado (molten globule) y sólo se pliega completamente al unir a sus socios[reference:1]. ¿La predicción de AlphaFold para NCBD solo refleja ese desorden? ¿Por qué?

**B. Análisis del complejo NCBD-TAD**

1. Descargue el modelo de mayor ranking (`_model_0.cif`).
2. Abra el modelo en Chimera. Coloréelo por pLDDT. 
   - ¿Ambas cadenas tienen ahora pLDDT consistentemente alto (>80) en las regiones que forman la interfaz?
   - ¿Alguna región permanece con baja confianza? ¿A qué cadena pertenece? ¿Coincide con algún linker o extremo flexible descripto en la literatura?
3. En el servidor, examine la visualización del PAE **entre cadenas**.
   - ¿El error predicho entre residuos de NCBD y TAD es bajo (azul) o alto (rojo)? ¿Indica esto que AlphaFold predice con confianza la orientación relativa de las dos proteínas?
4. Compare la estructura predicha con la estructura experimental de referencia (PDB 2L14). Acceda con Chimera:
   - Descargue del pdb el modelo 2L14.
   - Aísle las cadenas correspondientes a NCBD y TAD.
   - Superponga su modelo predicho con la estructura experimental usando Matchmaker. Calcule el RMSD global. ¿Es menor a 2 Å?

**C. Análisis de desorden con IUPred**

1. Ingrese a [IUPred2A](https://iupred2a.elte.hu/).
2. Pegue la secuencia de NCBD y ejecute (opción “long disorder”).
   - ¿Qué porcentaje de residuos de NCBD supera el umbral 0.5 (desorden)? ¿Coincide con las regiones de bajo pLDDT en el modelo de NCBD solo?
3. Repita para la secuencia de TAD.
   - TAD es un dominio de transactivación clásicamente desordenado. ¿IUPred lo predice como desordenado en su mayor parte?
4. ¿Qué esperaría para el gráfico de desorden si pudiera analizar el complejo? ¿Por qué?

**D. Comparación de métricas entre predicciones**

Complete la siguiente tabla con los valores obtenidos de los archivos `*_summary_confidences_0.json`.

| Trabajo             | pTM | Ranking score | Observación cualitativa (pLDDT > 70) |
|---------------------|-----|---------------|--------------------------------------|
| NCBD solo           |     |               |                                      |
| TAD solo (opcional) |     |               |                                      |
| Complejo NCBD-TAD   |     |               |                                      |

- ¿Cuál de las tres predicciones tiene el mejor ranking score? ¿Qué sugiere esto acerca de la capacidad de AlphaFold para modelar regiones desordenadas?

#### Comparación de los resultados (Ejercicio 2)
No te olvides de terminar el ejercicio 2! Ya terminó de correr el modelado con los iones?

### Ejercicio 4

El receptor de neurotrofinas p75NTR (p75 neurotrophin receptor) es una proteína transmembrana clave en la supervivencia neuronal, la apoptosis y el crecimiento axonal. Su señalización está finamente regulada por interacciones con múltiples efectores citosólicos. Uno de ellos es la proteína RhoGDI (Rho GDP‑dissociation inhibitor), que controla la actividad de las GTPasas de la familia Rho. En respuesta a la fosforilación de RhoGDI por PKC, se promueve la interacción entre el dominio yuxtamembrana (JMD) de p75NTR y el dominio N‑terminal (NTD) de RhoGDI, lo que desencadena una vía de señalización que culmina en la retracción axonal y apoptosis.

La estructura tridimensional de este complejo fue resuelta recientemente por resonancia magnética nuclear (RMN) y depositada bajo el código **PDB 8X8T**. En este ejercicio, usted utilizará AlphaFold para predecir la estructura del complejo de dos maneras:

1. **Sin usar templates estructurales** – para evaluar qué tan bien el método predice de novo la interacción.
2. **Proporcionando el complejo experimental como template** – para analizar cómo el uso de información estructural previa modifica la calidad y la confianza de la predicción.

A partir de la entrada **8X8T**, el complejo está formado por dos cadenas (se utilizan las secuencias exactas de la estructura de RMN):

```
>Cadena A – Dominio N‑terminal de RhoGDI (residuos 2‑60 de la proteína completa UniProt P52565)**
MAEQEPTAEQLAQIAAENEEDEHSVNYKPPAQKSIQEIQELDKDDESLRKYKEALLGRVAV
SADPNVPNVVVTGLTLVCSS
```

```
>Cadena B – Dominio yuxtamembrana de p75NTR (residuos 273‑332 de UniProt P08138)**
NLIPVYCSILAAVVVGLVAYIAFKRWNSCKQNKQGANSRPVNQTPPPEGEKLHSDSGI
SVDSQSLHDQQPHTQTASGQALKGDGGLYSSLPP
```
#### Predicción

1. Ingrese a [AlphaFold Server](https://alphafoldserver.com/).
2. Agregue dos entidades proteicas (**Add entity**).
   - **Entity 1:** pegue la secuencia de la **Cadena A** (RhoGDI‑NTD). Tipo *Protein*.
   - **Entity 2:** pegue la secuencia de la **Cadena B** (p75NTR‑JMD). Tipo *Protein*.
3. Asigne un nombre al trabajo, por ejemplo `p75_RhoGDI_sinTemplate`. Active “Use seed” (elija un número, ej. `12345`) para reproducibilidad.
4. En la sección **Templates**, deje la configuración por defecto (el servidor buscará automáticamente templates homólogos en el PDB). Si el servidor permite desactivar completamente los templates, hágalo (por ejemplo, desmarcando “Search for templates”). En caso de no poder desactivarlos, esta predicción representará la condición “estándar” y más adelante compararemos con la condición donde forzamos `8X8T`.
5. Envíe el trabajo y espere los resultados (~5‑10 minutos).

#### Predicción con el uso del template 8X8T

1. Cree un **nuevo trabajo** con las mismas dos entidades proteicas y las mismas secuencias.
2. Acceda al [RCSB PDB](https://www.rcsb.org/structure/8X8T) o al sitio espejo.
3. Descargue el archivo en formato PDB (opción “Download Files” → “PDB Format”).
4. Guarde el archivo con el nombre `8x8t.pdb` en una carpeta accesible.
5. Asígnele otro nombre, por ejemplo `p75_RhoGDI_conTemplate_8X8T`. Active la misma semilla (ej. `12345`).
3. En la sección **Templates**:
   - Seleccione la opción “Upload custom template” o “Provide PDB file”.
   - Suba el archivo `8x8t.pdb` descargado previamente.
   - **Verifique la asignación de cadenas:** asegúrese de que la cadena A del template corresponde a RhoGDI‑NTD (Entity 1) y la cadena B a p75NTR‑JMD (Entity 2). Si es necesario, ajuste manualmente el mapeo.
4. Envíe el trabajo y espere los resultados.

#### 4. Análisis comparativo

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

- En el modelo sin template: ¿el error predicho entre residuos de la cadena A y la cadena B (bloque fuera de la diagonal) es bajo (azul) o alto (rojo/amarillo)?
- En el modelo con template: ¿cambia esa región? ¿El template reduce la incertidumbre en la orientación relativa de los dos dominios?

**D. Comparación cualitativa con la estructura experimental**

1. Abra la estructura experimental `8x8t.pdb`.
2. Abra los dos modelos predichos (el `.cif` mejor rankeado de cada trabajo).
3. Superponga cada modelo con el experimental usando `MatchMaker` (referencia: 8X8T). Anote el RMSD global para ambos.
   - RMSD (modelo sin template vs 8X8T) = __________ Å
   - RMSD (modelo con template vs 8X8T) = __________ Å
4. Utilice `Tools → Structure Comparison → Match→Align` y luego coloree por RMSD por residuo (`Render by Attribute` → `mavRMSDca`).  
   - ¿Las regiones de mayor desviación corresponden a loops o extremos flexibles? ¿El template reduce esas desviaciones?

**E. Efecto sobre el desorden intrínseco (IUPred)**

1. Ingrese a [IUPred2A](https://iupred2a.elte.hu/).
2. Pegue la secuencia de **RhoGDI‑NTD** y ejecute (opción “long disorder”). Anote el porcentaje de residuos con score > 0.5.
3. Repita para **p75NTR‑JMD**.
4. Compare estos porcentajes con las regiones de bajo pLDDT que observó en las predicciones.  
   - ¿El uso del template aumenta el pLDDT en regiones que IUPred predice como desordenadas? ¿Qué implica esto sobre la capacidad de AlphaFold para modelar regiones flexibles cuando se dispone de un template?

#### Comparación de los resultados (Ejercicio 2)
Ya terminó de correr el ejercicio 2?

## Ejercicio 5

La proteína del retinoblastoma (Rb) es un supresor tumoral que regula negativamente la progresión del ciclo celular. Su función principal es unirse a los factores de transcripción de la familia E2F (en particular E2F1 y su heterodímero con DP1), reclutando complejos remodeladores de cromatina y reprimiendo la transcripción de genes necesarios para la transición G1/S. La unión ocurre entre el dominio **C‑terminal de Rb** (RbC) y el **heterodímero E2F1/DP1**. Cuando Rb es fosforilada por quinasas ciclina‑dependientes (CDK), se libera de E2F/DP y se activa la transcripción.

La estructura cristalográfica de este complejo trimérico fue depositada con el código **2AZE**. Sin embargo, la estructura resuelta por cristalografía de rayos X (2,55 Å) incluye solo las regiones que son estables y ordenadas en el cristal. En solución, muchos fragmentos de E2F1, DP1 y Rb permanecen flexibles o desordenados, especialmente fuera de la interfaz de unión. Esto convierte a cada proteína por separado en un **monómero “feo” desde el punto de vista del plegamiento**, pero al unirse entre sí adquieren estructuras más compactas con regiones ordenadas que pueden modelarse con alta confianza.

En este ejercicio usted modelará el trímero completo y, por separado, **la proteína que considere más “fea” luego de inspeccionar sus modelos de AlphaFold en UniProt**. Además, deberá leer sobre la estructura de **E2F1** para entender su arquitectura dominial y el significado funcional de las regiones desordenadas.

#### Modelado de las tres secuencias:

##### Cadena 1 – E2F1 (UniProt Q01094, 437 residuos)

```
>sp|Q01094|E2F1_HUMAN Transcription factor E2F1 OS=Homo sapiens OX=9606 GN=E2F1 PE=1 SV=1
MALAGAPAGGPCAPALEALLGAGALRLLDSSQIVIISAAQDASAPPAPTGPAAPAAGPCD
PDLLLFATPQAPRPTPSAPRPALGRPPVKRRLDLETDHQYLAESSGPARGRGRHPGKGVK
SPGEKSRYETSLNLTTKRFLELLSHSADGVVDLNWAAEVLKVQKRRIYDITNVLEGIQLI
AKKSKNHIQWLGSHTTVGVGGRLEGLTQDLRQLQESEQQLDHLMNICTTQLRLLSEDTDS
QRLAYVTCQDLRSIADPAEQMVMVIKAPPETQLQAVDSSENFQISLKSKQGPIDVFLCPE
ETVGGISPGKTPSQEVTSEEENRATDSATIVSPPPSSPPSSLTTDPSQSLLSLEQEPLLS
RMGSLRAPVDEDRLSPLVAADSLLEHVREDFSGLLPEEFISLSPPHEALDYHFGLEEGEG
IRDLFDCDFGDLTPLDF
```

##### Cadena 2 – DP1 (UniProt Q14186, 410 residuos)

```

>sp|Q14186|TFDP1_HUMAN Transcription factor Dp-1 OS=Homo sapiens OX=9606 GN=TFDP1 PE=1 SV=1
MAKDAGLIEANGELKVFIDQNLSPGKGVVSLVAVHPSTVNPLGKQLLPKTFGQSNVNIAQ
QVVIGTPQRPAASNTLVVGSPHTPSTHFASQNQPSDSSPWSAGKRNRKGEKNGKGLRHFS
MKVCEKVQRKGTTSYNEVADELVAEFSAADNHILPNESAYDQKNIRRRVYDALNVLMAMN
IISKEKKEIKWIGLPTNSAQECQNLEVERQRRLERIKQKQSQLQELILQQIAFKNLVQRN
RHAEQQASRPPPPNSVIHLPFIIVNTSKKTVIDCSISNDKFEYLFNFDNTFEIHDDIEVL
KRMGMACGLESGSCSAEDLKMARSLVPKALEPYVTEMAQGTVGGVFITTAGSTSNGTRFS
ASDLTNGADGMLATSSNGSQYSGSRVETPVSYVGEDDEEDDDFNENDEDD
```

##### Cadena 3 – Rb (UniProt P06400, 928 residuos)

```
>sp|P06400|RB_HUMAN Retinoblastoma-associated protein OS=Homo sapiens OX=9606 GN=RB1 PE=1 SV=2
MPPKTPRKTAATAAAAAAEPPAPPPPPPPEEDPEQDSGPEDLPLVRLEFEETEEPDFTAL
CQKLKIPDHVRERAWLTWEKVSSVDGVLGGYIQKKKELWGICIFIAAVDLDEMSFTFTEL
QKNIEISVHKFFNLLKEIDTSTKVDNAMSRLLKKYDVLFALFSKLERTCELIYLTQPSSS
ISTEINSALVLKVSWITFLLAKGEVLQMEDDLVISFQLMLCVLDYFIKLSPPMLLKEPYK
TAVIPINGSPRTPRRGQNRSARIAKQLENDTRIIEVLCKEHECNIDEVKNVYFKNFIPFM
NSLGLVTSNGLPEVENLSKRYEEIYLKNKDLDARLFLDHDKTLQTDSIDSFETQRTPRKS
NLDEEVNVIPPHTPVRTVMNTIQQLMMILNSASDQPSENLISYFNNCTVNPKESILKRVK
DIGYIFKEKFAKAVGQGCVEIGSQRYKLGVRLYYRVMESMLKSEEERLSIQNFSKLLNDN
IFHMSLLACALEVVMATYSRSTSQNLDSGTDLSFPWILNVLNLKAFDFYKVIESFIKAEG
NLTREMIKHLERCEHRIMESLAWLSDSPLFDLIKQSKDREGPTDHLESACPLNLPLQNNH
TAADMYLSPVRSPKKKGSTTRVNSTANAETQATSAFQTQKPLKSTSLSLFYKKVYRLAYL
RLNTLCERLLSEHPELEHIIWTLFQHTLQNEYELMRDRHLDQIMMCSMYGICKVKNIDLK
FKIIVTAYKDLPHAVQETFKRVLIKEEEYDSIIVFYNSVFMQRLKTNILQYASTRPPTLS
PIPHIPRSPYKFPSSPLRIPGGNIYISPLKSPYKISEGLPTPTKMTPRSRILVSIGESFG
TSEKFQKINQMVCNSDRVLKRSAEGSNPPKPLKKLRFDIEGSDEADGSKHLPGESKFQQK
LAEMTSTRTRMQKQKMNDSMDTSNKEEK
```

Antes de modelar, explore las predicciones estructurales que ya están disponibles en la **AlphaFold Protein Structure Database** para cada una de las tres proteínas.

- Acceda a UniProt: [https://www.uniprot.org/](https://www.uniprot.org/)
- Busque los códigos **Q01094** (E2F1), **Q14186** (DP1) y **P06400** (Rb).
- En cada página, localice el botón “AlphaFold” o “3D structure” y haga clic para abrir el modelo predicho.
- Observe el coloreado por pLDDT:
  - **Azul** (pLDDT > 90): muy alta confianza.
  - **Celeste** (pLDDT 70‑90): buena confianza.
  - **Amarillo** (pLDDT 50‑70): baja confianza (posiblemente flexible).
  - **Naranja/Rojo** (pLDDT < 50): muy baja confianza, probablemente desordenado.
- Registre el **valor medio de pLDDT** que se indica en la página (suele aparecer en una tabla o en el pie de la visualización).

**Pregunta 1:**  
Según los modelos de AlphaFold en UniProt, ¿cuál de las tres proteínas tiene el **promedio de pLDDT más bajo** y la **mayor proporción de residuos con pLDDT < 70**? Justifique su respuesta con valores aproximados. Seleccionar esta proteína para el siguiente paso

#### Modelado del monómero de peor calidad

Una vez elegida la proteína de peor calidad, modele esa única cadena con AlphaFold Server.

1. Ingrese a [AlphaFold Server](https://alphafoldserver.com/).
2. En la **Entity 1**, configure tipo **Protein** y pegue la secuencia de la proteína seleccionada (completa, tal como aparece arriba).
3. Asigne un nombre descriptivo, por ejemplo `Monomer_FEO_E2F1` (o la que corresponda).
4. Active la opción **Use seed** y elija un número entero (ej. `12345`).
5. Envíe el trabajo y espere (aproximadamente 5‑10 min, dependiendo del tamaño).
6. Cuando termine, descargue el archivo `.cif` del mejor modelo.

#### Modelado del trímero completo (E2F1 + DP1 + Rb)

Ahora modele el complejo que aparece en la estructura 2AZE, pero con las secuencias **completas** de las tres proteínas.

1. En AlphaFold Server, cree un **nuevo trabajo**.
2. Agregue **tres entidades proteicas** con el botón “Add entity”.
   - **Entity 1:** E2F1.
   - **Entity 2:** DP1.
   - **Entity 3:** Rb.
3. Asegúrese de que el tipo de todas sea **Protein** y que el orden de las cadenas sea el indicado.
4. Asigne otro nombre, por ejemplo `Trimer_E2F1_DP1_Rb`.
5. Use la **misma semilla** (seed) que en el punto anterior.
6. Envíe el trabajo y espere (el tiempo de cómputo será mayor, entre 15 y 30 min).

#### Comparación de la confianza entre el monómero y el trímero

Una vez que ambos trabajos estén listos, compare las métricas de confianza.

**A. Métricas globales**

Descargue los archivos ZIP de ambos trabajos y abra los archivos `*_summary_confidences_0.json`. Complete la siguiente tabla:

| Predicción             | pTM | ipTM | ranking_score  | fraction_disordered |
|------------------------|-----|------|----------------|---------------------|
| Monómero               |     |      |                |                     |
| Trímero completo       |     |      |                |                     |

- ¿Cuál de los dos trabajo tiene mejor `ranking_score`? ¿Qué parámetro(s) contribuyen más a esa diferencia?

**B. Perfil de pLDDT por residuo**

Visualice los modelos en Chimera (o en la propia interfaz del servidor) coloreando por b‑factor (pLDDT). Utilice el comando:

rangecolor bfactor 0 orange red 50 white 100 dodger blue


- Sobre el modelo del **trímero**, identifique las cadenas que corresponden a la proteína “fea” elegida. ¿Esas regiones presentan ahora pLDDT más altos que cuando la proteína se modeló sola? ¿Dónde ocurre el aumento de confianza?
- ¿Qué pasa con los extremos N‑terminal y C‑terminal de E2F1 y DP1 en el trímero? ¿Siguen siendo desordenados o se ordenan en el complejo?

**C. Análisis del PAE (Predicted Aligned Error)**

Examine el gráfico de PAE del trímero.

- ¿El error predicho entre residuos de diferentes cadenas es bajo (colores azules) o alto (rojo/amarillo)?
- Identifique en el gráfico los bloques que representan interacciones **E2F1‑DP1** (heterodimerización) y **E2F1‑Rb** (unión reguladora). ¿Cuál es más confiable según el PAE?

**D. Lectura obligatoria – Estructura de E2F1**

Antes de continuar, se debe leer sobre la **estructura y arquitectura dominial de E2F1**. Se sugiere consultar:

- La entrada de **UniProt Q01094** y la pestaña “Family & Domains”.
- La página de **InterPro** asociada (IPR003316, IPR037239, etc.).
- El artículo original de la estructura 2AZE: Rubin et al., *Cell* (2005) – disponible en PubMed.
- Opcional: revisar el **AlphaFold model** de E2F1 en UniProt para identificar visualmente la región ordenada (dominio de unión a DP y Rb) y los extremos desordenados.

**Pregunta 2 (para responder luego de la lectura):**  
Explique brevemente cuáles son los **dominios principales de E2F1** y cuál es su función en la regulación del ciclo celular. ¿Cómo se relaciona la presencia de regiones intrínsecamente desordenadas con la capacidad de E2F1 de unirse a múltiples socios (DP1, Rb, p300/CBP, etc.)?

#### 5. Comparación con la estructura cristalográfica de referencia

1. Descargue el archivo PDB de 2AZE desde el RCSB (código `2aze`).
2. Abra el PDB en Chimera y aísle las tres cadenas (A: DP1, B: E2F1, C: Rb-Cterminal). Notará que 2AZE solo contiene **fragmentos** de las proteínas completas (los dominios que son estables en el cristal).
3. Alinee su modelo del trímero completo contra el fragmento experimental usando **MatchMaker**.
4. Anote el **RMSD global** para los átomos superpuestos (lo que solapa, porque el modelo experimental es más corto).

- ¿Las regiones que están presentes en 2AZE y en su modelo coinciden con alta precisión (RMSD < 2 Å)?
- ¿Qué partes de su modelo se desvían más? ¿Corresponden a regiones que están ausentes en la estructura cristalográfica?

#### Comparación de los resultados (Ejercicio 2)
Ahora si terminó de correr el ejercicio 2?

-->