# Gaussian

## Descripción

Gaussian es un programa popular de química computacional. Es un paquete
de estructura electrónica capaz de predecir muchas propiedades de
átomos, moléculas, sistemas reactivos, etc. Por ejemplo:

-   Energías moleculares

-   Estructuras

-   Frecuencias vibratorias

-   Densidades de electrones

-   Utilizando el método Hartree-Fock, teoría funcional de densidad,
    mecánica molecular y varios métodos híbridos

## Módulos

En el clúster se encuentran disponibles los siguientes módulos para el
uso de la aplicación Gaussian:

-   gaussian/09

-   gaussian/09-sse4

### Diferencias entre versiones

La principal diferencia entre el módulo *gaussian/09* y el módulo
*gaussian/09-sse4*, es que el módulo *gaussian/09-sse4*, además de los
conjuntos de instrucciones anteriores, puede hacer uso del conjunto de
instrucciones SSE4.

```admonish warning title="IMPORTANTE"
La versión de Gaussian instalada en el clúster sólo permite utilizar
paralelización de memoria compartida, por lo que los trabajos que
utilicen esta aplicación, deberán enviarse a particiones con un sólo
nodo:

-   q1h-20p

-   q1d-20p

-   q4d-20p

-   q7d-20p
```

### Cargar aplicación

Para cargar la aplicación `Gaussian`, utilice el siguiente comando:
```
module load <módulo>
```

Por ejemplo, para cargar el modulo `gaussian/09`, ejecute el comando:
```
module load gaussian/09
```

## Archivos de entrada

La entrada de la aplicación Gaussian consiste en una serie de líneas en
un archivo de texto ASCII. La estructura básica de un archivo de entrada
gaussiano incluye varias secciones diferentes:

| **Sección** | **Descripción** |
|:-----------:|-----------------|
| Comandos Link 0 | Localiza y asigna un nombre a los archivos reutilizables. |
| Ruta | Especifica el tipo de cálculo deseado, la química del modelo y otras opciones. |
| Título | Breve descripción del cálculo. Esta sección es necesaria en la entrada, pero el programa Gaussian no la interpreta de ninguna manera. Aparece en la salida con fines de identificación y descripción. Normalmente, esta sección puede con tener el nombre del compuesto, su simetría, el estado electrónico y cualquier otra información relevante. La sección del título no puede exceder las cinco líneas y debe ir seguida de una línea final en blanco. Los siguientes caracteres deben evitarse en la sección de título: @ # ! - _ \\. |
| Especificación de la <br> molécula | Especifica el sistema molecular que se va a estudiar. |
| Secciones adicionales <br> opcionales | Entrada adicional necesaria para tipos de trabajo específicos. |

### Secciones

En la siguiente tabla se muestran todas las posibles secciones que
pueden aparecer dentro de un archivo de entrada Gaussian, junto con las
palabras clave asociadas a cada una de ellas.

| **Sección** | **Palabras clave** | **¿Última líne en blanco?** |
|-------------|--------------------|:---------------------------:|
| Comandos Link 0 | Comandos '%' | No |
| Sección de ruta (# líneas) | Todas | Sí |
| Superposiciones adicionales | ExtraOverlays | Sí |
| Sección de título | Todos excepto Geom = AllCheck | Sí |
| Especificación de la molécula | Todos excepto Geom = AllCheck | Sí |
| Especificaciones de conectividad | Geom = Connect o ModConnect | Sí |
| Alteraciones de átomos congelados | Geom = Connect o ModConnect | Sí |
| Modificaciones a las coordenadas | Opt = ModRedundant | Sí |
| 2do título y especificación de la molécula | Opt = QST2 o QST3 | Sí para ambos |
| Especificaciones de conectividad para el segundo conjunto de coordenadas | Geom = Connect o ModConnect y Opt = QST2 o QST3 | Sí |
| 2o Alteraciones a átomos congelados | Geom = ReadFreeze | Sí |
| Modificaciones al segundo conjunto de coordenadas | Opt = QST2 o QST3 | Sí para ambos |
| 3er título y estructura inicial de TS | Opt = QST3 | Sí |
| Especificaciones de conectividad para el 3er conjunto de coordenadas | Geom = Connect o ModConnect Opt = (ModRedun, QST3) | Sí |
| 3o Alteraciones a átomos congelados | Geom = ReadFreeze | Sí |
| Modificaciones al tercer conjunto de coordenadas | Opt = (ModRedun, QST3) | Sí |
| Información de estructura secundaria PDB | Automático si información de residuos en la especificación de la molécula | Sí |
| Masas atómicas | Opción ReadIsotopes | Sí |
| Parámetros de mecánica molecular | HardFirst, SoftFirst, SoftOnly, Modify | Sí |
| Frecuencia de interés | CPHF = RdFreq | Sí |
| Distribución de cargos de fondo | Charge | Sí |
| Entrada BOMD / ADMP (1 o más secciones) | Entrada requerida de ADMP y BOMD y opciones ReadVelocity, ReadMWVelocity | Sí |
| Entrada PCM | SCRF = (iteración externa, lectura) | Sí |
| Coordenadas para la tabla IRC | IRC (Informe = Leer) | Sí |
| Restricciones armónicas | Geom = Leer armónico | Sí |
| Parámetros semi-empíricos (formato gaussiano) | Opción de entrada, AM1 = Both | Sí |
| Parámetros semi-empíricos (formato MOPAC) | opciones: MOPAC , Both | Sí |
| Especificación del conjunto básico | Gen, GenECP, ExtraBasis | Sí |
| Modificaciones del conjunto de bases | Massage | Sí |
| Coeficientes de campo finito | Field = Read | Sí |
| Especificación ECP | Pseudo = Cards, GenECP | Sí |
| Especificación del conjunto de bases de ajuste de densidad | ExtraDensityBasis | Sí |
| Entrada del modelo de solvatación PCM | SCRF = Read | Sí |
| Parámetros DFTB | DFTB | Sí |
| Fuente de la conjetura inicial | Guess = Input | Sí |
| Tipos de simetría para combinar | Guess = LowSymm | No |
| Especificaciones orbitales (Alfa y Beta por separado) | Guess = Cards | Sí |
| Alteraciones orbitales (Alfa y Beta separados) | Guess = Alter | Sí |
| Reordenamiento orbital (Alfa y Beta separados) | Guess = Permute | Sí |
| Par orbitales / GVB | GVB | No |
| Ponderaciones para el promedio de estado CAS | CASSCF = StateAverage | No |
| Estados de interés para el acoplamiento de órbitas de espín | CASSCF = SpinOrbit | No |
| Información de congelación orbital | Opciones de ReadWindow | Sí |
| Orbitales EPT para refinar | EPT = ReadOrbitals | Sí |
| Lista de átomos para constantes de acoplamiento espín-espín | NMR = ReadAtoms | Sí |
| Radios atómicos alternativos | Pop = ReadRadii o ReadAtRadii | Sí |
| Datos de propiedades electrostáticas | Prop = Read u Opt | Sí |
| Entrada NBO | Pop = NBORead | No |
| Selección del modo normal armónico | Freq = SelectNormalModes | Sí |
| Entrada de rotor obstaculizada | Freq = ReadHindered | Sí |
| Selección del modo normal anarmónico | Freq = SelectAnharmonicNormalModes | Sí |
| Modos normales para FCHT | Freq = SelectFCHTNormalModes | Sí |
| Entrada para Anharmonic | Freq = ReadAnharmonic | Sí |
| Entrada para FCHT | Freq = ReadFCHT | Sí |
| Nombre de archivo de salida de Pickett | Output = Pickett | No |
| Nombre de archivo de salida de PROAIMS | Output = WFN | No |

``` admonish warning title="IMPORTANTE"
Para utilizar todos los procesadores de la partición, debe agregar el
comando Link 0:

    %nprocshared=20

al archivo de entrada de Gaussian.
```

Para obtener más información, consulte la página [Gaussian 09 Input
Overview](http://wild.life.nctu.edu.tw/~jsyu/compchem/g09/g09ur/m_input.htm).

### Ejemplo

A continuación se presenta un ejemplo de un archivo de entrada de
Gaussian:

    %Chk=heavy                      Sección Link 0
    # HF/6-31G(d) Opt=ModRedundant  Sección de Ruta

    Opt job                         Sección de Título

    0   1                           Sección de especificación de Molécula
    O  -0.464   0.177   0.0
    H  -0.464   1.137   0.0
    H   0.441  -0.143   0.0
                                    Secciones adicionales opcionales
    3 8                             Agrega un enlace y un ángulo a las coordenadas internas
    2 1 3                           Coordenadas usadas durante la optimización de energía

Este trabajo solicita una optimización de geometría. La sección de
entrada que sigue a la especificación de la molécula es utilizada por la
palabra clave `Opt = ModRedundant`, y sirve para agregar un enlace y un
ángulo adicionales en las coordenadas internas utilizadas en la
optimización de la geometría.

## Scripts de ejemplo

Puede encontrar scripts de ejemplo de la aplicación Gaussian en el
siguiente directorio:
```
/LUSTRE/scripts_ejemplo/Gaussian
```

## Errores frecuentes

| **Error** | **Traducción** |
|-----------|----------------|
| `Error termination in Ntr Err: ntran open failure returned to fopen. Segmentation fault` | No se puede abrir un archivo. |
| `Out-of-memory error in routine UFChkP (IEnd= 12292175 MxCore=6291456) Use %Mem=12MW to provide the minimum amount of memory required to complete this step.  Error termination via Lnk1e at Thu Feb 2 13:05:32 2006.` | La memoria predeterminada (6 MW, configurada en `$GAUSS_MEMDEF`) es demasiado pequeña para un archivo. | 
| `galloc: could not allocate memory.: Resource temporarily unavailable` | No hay suficiente memoria. |
| `Out-of-memory error in routine ...` | No hay suficiente memoria. |
| `End of file in GetChg. Error termination via Lnk1e ...` | No hay suficiente memoria. |
| `IMax=3 JMax=2 DiffMx= 0.00D+00 Unable to allocate space to process matrices in G2DrvN: NAtomX= 58 NBasis= 762 NBas6D= 762 MDV1= 6291106 MinMem= 105955841.` | Gaussian tiene 6 MW de memoria libre (MDV1) pero requiere al menos 106 MW (MinMem). |
| `Estimate disk for full transformation -677255533 words. Semi-Direct transformation. Bad length for file.` | MaxDisk se ha configurado demasiado bajo. |
| `Error termination in NtrErr: NtrErr Called from FileIO.` | El cálculo ha superado el límite máximo de maxcyc. |
| `Erroneous read. Read 0 instead of 6258688. fd = 4 g_read` | Se superó la cuota de disco o el tamaño del disco. También podría deberse a una falla del disco o al tiempo de espera de NFS. |
| `Erroneous write. Write 8192 instead of 12288. fd = 4 orig len = 12288 left = 12288 g_write` | Se superó la cuota de disco o el tamaño del disco. También podría deberse a una falla del disco o al tiempo de espera de NFS. |
| `PGFIO/stdio: Permission denied PGFIO-F-/OPEN/unit=11/error code returned by host stdio - 13. File name = /scratch/Gau-##.inp In source file ml0.f, at line number 177` | El usuario no tiene permiso de escritura para `$GAUSS_SCRDIR`. |
| `QPERR — A SYNTAX ERROR WAS DETECTED IN THE INPUT LINE.` | Se detectó un error de sintaxis en la entrada. Hay algunas pautas en el archivo de salida debajo de esta línea. |

## Licencia

La aplicación Gaussian solo está disponible para miembros de la
comunidad UAM.

## Referencias

-   [Página oficial de Gaussian](https://gaussian.com/)
