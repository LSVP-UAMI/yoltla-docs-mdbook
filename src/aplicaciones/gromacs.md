# GROMACS

## Descripción 

GROMACS es un paquete versátil para realizar dinámica molecular, es
decir, simular las ecuaciones de movimiento de Newton para sistemas con
cientos a millones de partículas.

Está diseñado principalmente para moléculas bioquímicas como proteínas,
lípidos y ácidos nucleicos que tienen muchas interacciones enlazadas
complicadas, pero dado que GROMACS es extremadamente rápido para
calcular las interacciones no enlazadas (que normalmente dominan las
simulaciones), muchos grupos también lo utilizan para la investigación
de sistemas biológicos, por ejemplo: polímeros.

## Módulos

En el clúster se encuentran disponibles los siguientes módulos para el
uso de la aplicación GROMACS:

-   intel/15.2.164/impi/5.0.3.48/gromacs/4.5_d

-   intel/15.2.164/impi/5.0.3.48/gromacs/4.6.7

-   intel/15.2.164/impi/5.0.3.48/gromacs/5.0.7-d

-   intel/15.2.164/impi/5.0.3.48/gromacs/5.0.7-s

-   intel/15.6.232/impi/5.0.3.49/gromacs/5.1.4-s

-   cuda/7.5/intel/15.2.164/impi/5.0.3.48/gromacs/5.0.7-s

-   cuda/7.5/intel/15.6.232/impi/5.0.3.49/gromacs/5.1.4-s

-   gromacs/2016.3

-   gromacs/2016.5

-   gromacs/2018

-   gromacs/2019.2

-   gromacs/5.1.5-CUDA

-   plumed/gromacs/2016.5

-   plumed/gromacs/2016.5-gpu

-   plumed/gromacs/2018.1

-   plumed/gromacs/2018.1-gpu


### Diferencias entre versiones

**Man pages**

Todos los módulos de GROMACS cuentan con man pages.

**Memoria compartida**

Todos los módulos de GROMACS, a excepción de los que se listan a
continuación, pueden utilizar memoria compartida:

-   intel/15.2.164/impi/5.0.3.48/gromacs/4.5_d

-   intel/15.2.164/impi/5.0.3.48/gromacs/4.6.7

**Memoria deitribuida**

Todos los módulos de GROMACS pueden utilizar memoria distribuida.

**GPU**

Los siguientes módulos de GROMACS pueden utilizar los nodos GPU/VGPU del
clúster:

-   cuda/7.5/intel/15.2.164/impi/5.0.3.48/gromacs/5.0.7-s

-   cuda/7.5/intel/15.6.232/impi/5.0.3.49/gromacs/5.1.4-s

-   gromacs/2016.3

-   gromacs/2016.5

-   gromacs/2018

-   gromacs/2019.2

-   gromacs/5.1.5-CUDA

-   plumed/gromacs/2016.5-gpu

-   plumed/gromacs/2018.1-gpu

**PLUMED**

PLUMED es una biblioteca de código abierto desarrollada por la comunidad
que proporciona una amplia gama de métodos diferentes, que incluyen:

-   Algoritmos de muestreo mejorado

-   Métodos de energía libre

-   Herramientas para analizar la gran cantidad de datos producidos por
    simulaciones de dinámica molecular (MD)

Estas técnicas se pueden usar en combinación con una gran caja de
herramientas de variables colectivas que describen procesos complejos en
física, química, ciencia de materiales y biología.

Los siguientes módulos de GROMACS pueden trabajar con PLUMED:

-   plumed/gromacs/2016.5

-   plumed/gromacs/2016.5-gpu

-   plumed/gromacs/2018.1

-   plumed/gromacs/2018.1-gpu

### Cargar aplicación

Para cargar la aplicación  `GROMACS`, utilice el siguiente comando:
```
module load <módulo>
```

Por ejemplo, para cargar el modulo `gromacs/2019.2`, ejecute el comando:
```
module load gromacs/2019.2
```

## Archivos de entrada

GROMACS es fácil de usar, con topologías y archivos de parámetros. Aquí
hay una descripción general de los tipos de archivos GROMACS más
importantes que encontrará.

### Archivo de topología molecular (.top)

El archivo de topología molecular es generado por el programa
`gmx pdb2gmx`. Este traduce un archivo de estructura `pdb` de cualquier
péptido o proteína a un archivo de topología molecular. Este archivo de
topología contiene una descripción completa de todas las interacciones
en su péptido o proteína.

### Archivo de estructura moleculer(.gro, .pdb)

Cuando se ejecuta `gmx pdb2gmx` para generar una topología molecular,
también traduce el archivo de estructura (archivo `pdb`) a un archivo de
estructura GROMOS (archivo `gro`). La principal diferencia entre un 
archivo `pdb` y un archivo gromos es su formato y que un archivo `gro` 
también puede contener velocidades. Sin embargo, si no necesita las 
velocidades, también puede usar un archivo `pdb` en todos los programas.

### Archivo de parámetros de dinámica molecular (.mdp) 

El archivo de parámetros de dinámica molecular (`mdp`) contiene toda la
información sobre la simulación de dinámica molecular en sí, por
ejemplo, paso de tiempo, número de pasos, temperatura, presión, etc.

### Archivo de índice (.ndx)

A veces, es posible que necesite un archivo de índice para especificar
acciones en grupos de átomos (por ejemplo, acoplamiento de temperatura,
aceleraciones, congelación). Por lo general, los grupos de índices
predeterminados serán suficientes.

### Archivo de entrada (.tpr)

Es la combinación de la estructura molecular (archivo `gro`), topología
(archivo `top`) parámetros MD (archivo `mdp`) y (opcionalmente) el
archivo de índice (`ndx`) para generar un archivo de entrada de
ejecución (`extensión tpr`). Este archivo contiene toda la información
necesaria para iniciar una simulación con GROMACS. El comando
`gmx grompp` procesa todos los archivos de entrada y genera el archivo
`tpr`.

### Archivo de trayectoria (.trr, .tng o .xtc)

Una vez que el archivo de entrada de ejecución esté disponible, podemos
iniciar la simulación. El programa que inicia la simulación se llama
`gmx mdrun` (o a veces simplemente `mdrun` o `mdrun_mpi`). El único
archivo de entrada de `gmx mdrun` que normalmente necesita para iniciar
una ejecución es el archivo de entrada de ejecución (`archivo tpr`). Los
archivos de salida típicos de `gmx mdrun` son el archivo de trayectoria
(archivo `trr`), un archivo de registro (archivo `log`) y quizás un
archivo de punto de control (archivo `cpt`).

Puede consultar archivos de muestra en la página [File
formats](https://manual.gromacs.org/documentation/5.1/user-guide/file-formats.html)
de la documentación oficial de GROMACS.

## Scripts de ejemplo

Puede encontrar scripts de ejemplo de la aplicación GROMACS en el
siguiente directorio:
```
/LUSTRE/scripts_ejemplo/Gromacs
```

## Errores frecuentes

| **Error** | **Descripción** |
|-----------|-----------------|
| No se puede asignar memoria | La secuencia de comandos ejecutada ha intentado asignar memoria para ser utilizada en el cálculo, pero no puede debido a memoria insuficiente. <br><br> Las posibles soluciones son: <br><br> **-** Reducir el alcance del número de átomos seleccionados para el análisis. <br><br> **-** Reducir la longitud del archivo de trayectoria que se está procesando. <br><br> **-** En algunos casos, la confusión entre Ångström y nm puede llevar a los usuarios a querer generar una caja de agua que sea 10\^3 veces más grande de lo que creen que es (por ejemplo, genbox).|
| Al usar `pdb2gmx`: <br> El residuo *XXX* no se encuentra en la base de datos de topología de residuos | Esto significa que el campo de fuerza que seleccionó mientras ejecutaba `pdb2gmx` no tiene una entrada en la base de datos de residuos para XXX. La entrada de la base de datos de residuos es necesaria tanto para moléculas independientes (por ejemplo, formaldehído) como para un péptido (estándar o no estándar). Esta entrada define los tipos de átomos, la conectividad, los tipos de interacción enlazados y no enlazados para el residuo y es necesario usar `pdb2gmx` para construir un archivo `.top`. Es posible que falte una entrada en la base de datos de residuos simplemente porque la base de datos no contiene el residuo en absoluto o porque el nombre es diferente. <br><br> Si desea usar `pdb2gmx` para generar automáticamente su topología, debe asegurarse de que la entrada `.rtp` adecuada esté presente dentro del campo de fuerza deseado y tenga el mismo nombre que el bloque de construcción que está tratando de usar. Si llama a su molécula \"HIS\", entonces `pdb2gmx` no construirá mágicamente una molécula aleatoria; intentará construir histidina, basándose en la entrada \[HIS\] en el archivo `.rtp`, por lo que buscará las entradas atómicas exactas para histidina, ni más ni menos.|
| Enlaces largos y / o <br> átomos faltantes | Probablemente falten átomos anteriormente en el archivo `.pdb`, lo que hace que `pdb2gmx` se vuelva loco. Verifique la salida de pantalla de `pdb2gmx`, ya que le dirá cuál falta. Luego agregue los átomos en su archivo `pdb`, la minimización de energía los colocará en el lugar correcto. |
| El identificador de cadena *X* se usó en dos bloques no secuenciales | Esto significa que dentro del archivo de coordenadas alimentado a pdb2gmx , la cadena X se ha dividido, posiblemente por la inserción incorrecta de una molécula dentro de otra. La solución es simple: mueva la molécula insertada a una ubicación dentro del archivo para que no divida otra molécula. <br><br> Este mensaje también puede significar que se ha utilizado el mismo identificador de cadena para dos cadenas independientes. En ese caso, cambie el nombre de la segunda cadena a un identificador único. |
| El átomo X en el residuo YYY no se encuentra en la entrada `rtp` | Si está intentando ensamblar una topología usando `pdb2gmx`, se espera que los nombres de los átomos coincidan con los que se encuentran en el archivo `.rtp` que definen los bloques de construcción en su estructura. En la mayoría de los casos, el problema surge de una falta de coincidencia de nombres, así que simplemente cambie el nombre de los átomos en su archivo de coordenadas de manera apropiada. En otros casos, es posible que esté suministrando una estructura que tiene residuos que no se ajustan a las expectativas del campo de fuerza , en cuyo caso debe investigar por qué está ocurriendo tal diferencia y tomar una decisión basada en lo que encuentre - use un diferente campo de fuerza, editar manualmente la estructura, etc. |
| Al usar `grompp`: `Found a second defaults directive file`| Esto se debe a que la directiva aparece más de una vez en los archivos de topología o campo de fuerza del sistema; solo puede aparecer una vez. Una causa típica de esto es que se establecen segundos valores predeterminados en un archivo de topología incluido, `.itp` , que se obtuvo en otro lugar. |
| `Invalidad order for directive xxx` | Las directivas en los archivos *.top* y *.itp* tienen reglas sobre el orden en el que pueden aparecer, y este error se ve cuando se viola el orden. <br><br> En particular, el \"orden no válido para los valores predeterminados de las directivas\" es el resultado de que se establezcan valores predeterminados en la topología o forzar archivos de campo en la ubicación inapropiada; la sección solo puede aparecer una vez y debe ser la primera directiva de la topología. |
| `Incorrect numbre of parameters`| Mire el archivo de topología del sistema.  No ha proporcionado suficientes parámetros para una de las definiciones vinculadas. A veces, esto también ocurre si ha alterado el mecanismo de inclusión de archivos o el formato de archivo de topología cuando editó el archivo. |
| `Fatal error: No such moleculetype XXX` | Cada tipo de molécula en su sección de su archivo `.top` debe tener una sección correspondiente definida previamente, ya sea en el archivo `.top` o en un archivo `.itp` incluido. Su archivo `.top` no tiene esa definición para la molécula indicada.  Verifique el contenido de los archivos relevantes, cómo ha nombrado a sus moléculas y cómo ha intentado referirse a ellas más adelante. Preste atención al estado y/o declaraciones. |
| Al usar `mdrun: Stepsize too small, or no change in energy. Converged to machine precision, but not to the requested precision` | Esto no es un error como tal. Simplemente le informa que durante el proceso de minimización de energía alcanzó el límite posible para minimizar la estructura con sus parámetros actuales. No significa que el sistema no se haya minimizado por completo, pero en algunas situaciones ese puede ser el caso. |
| `LINCS/SETTLE/SHAKE warnings` | A veces, cuando se ejecuta la dinámica, `mdrun` puede dejar de repente (tal vez después de escribir varios archivos `PDB`) tras una serie de advertencias sobre los algoritmos de restricción (por ejemplo `LINCS`, `SETTLE` o `SHAKE`) se escriben en el archivo de registro. Estos algoritmos se utilizan a menudo para restringir las longitudes y / o ángulos de los enlaces.  Cuando un sistema está explotando\" (es decir, la explosión debido a las fuerzas divergentes), las restricciones son por lo general lo primero que debe fallar. Esto no significa necesariamente que deba solucionar los problemas del algoritmo de restricción. Por lo general, es una señal de algo más fundamentalmente incorrecto (físicamente poco realista) en su sistema. |
| `Can not do Conjugate Gradients with constraints` | Esto significa que no puede minimizar la energía con el algoritmo de gradiente conjugado si su topología tiene restricciones definidas. |
| `Range Checking error` | Por lo general, esto significa que su simulación está explotando . Probablemente necesite hacer una mejor minimización y / o equilibrio de energía y / o diseño de topología.|

Para obtener más información, consulte la página
[ERRORS](http://www.gromacs.org/Documentation/Errors) de la
documentación oficial de GROMACS.

## Licencia

GROMACS es software libre, disponible bajo la GNU Lesser General Public
License (LGPL), versión 2.1.

Para obtener más información, consulte la página [About
GROMACS](http://www.gromacs.org/about).

## Referencias

-   [Página oficial de GROMACS](https://www.gromacs.org/)
