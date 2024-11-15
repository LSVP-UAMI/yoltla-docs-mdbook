# LAMMPS

## Descrepción

Large-scale Atomic/Molecular Massively Parallel Simulator (LAMMPS) es un
programa de simulación molecular que modela conjuntos de partículas en
estado líquido, sólido o gaseoso. Puede modelar sistemas atómicos,
poliméricos, biológicos, de estado sólido (metales, cerámicas, óxidos),
granulares, de grano grueso o macroscópicos utilizando una variedad de
potenciales interatómicos (campos de fuerza) y condiciones de contorno.
Puede modelar sistemas 2d o 3d con solo unas pocas o hasta millones de
partículas.

LAMMPS fue diseñado para funcionar de manera eficiente en equipos
paralelos. Utiliza la interfaz de paso de mensajes (MPI) para la
comunicación en paralelo.

## Módulos

En el clúster se encuentran disponibles los siguientes módulos para el
uso de la aplicación LAMMPS:

-   intel/16.3.210/impi/impi-5.1.3/lammps/11092016

-   lammps/2018/05/lmp_mpi-gpu

-   lammps/2018/12/lmp-cpu

-   lammps/2019/08/lmp-gpu

### Diferencias entre versiones

| **Módulo** | **GPU** | **Memoria compartida** | **Memoria distribuida** | **Man pages** |
|------------|---------|------------------------|-------------------------|---------------|
| intel/16.3.210/impi/mpi-5.1.3/<br><br>lammps/11092016 | No | Sí | Sí | No |
| lammps/2018/05/lmp_mpi-gpu | Sí | No | Sí | No |
| lammps/2018/12/lmp-cpu | No | Sí | Sí | No | 
| lammps/2019/08/lmp-gpu | Sí | No | Sí | No |

### Cargar aplicación

Para cargar la aplicación `LAMMPS`, utilice el siguiente comando:
```
    module load <módulo>
```

Por ejemplo, para cargar el modulo *lammps/2019/08/lmp-gpu*, ejecute el
comando:
```
    module load lammps/2019/08/lmp-gpu
```
## Archivo de entrada

Un script de entrada de LAMMPS (archivo de texto) normalmente consta de
4 partes:

1.  Inicialización

2.  Definición del sistema

3.  Configuración de la simulación

4.  Ejecución de la simulación

Las 2 últimas partes se pueden repetir tantas veces como se desee. Es
decir, ejecutar la simulación, modificar algunos parámetros y continuar
con la misma, etc. Cada una de las 4 partes se describen ahora con mayor
detalle. (Recuerde que la mayoria de los comandos de LAMMPS ayudan a
modelar el sistema que se desea simular.)

### 1. Inicialización

Establece los parámetros que deben definirse antes de que los átomos se
creen o se lean desde un archivo. Los comandos más relevantes son:

| **Comando** | **Descripción** |
|-------------|-----------------| 
| `units` | Este comando establece las unidades en las que se realizará una simulación. Normalmente, se definen al principio del script de entrada. |
| `dimension` | Establece las dimensiones en las que se realizará la simulación 2D o 3D. Por defecto, LAMMPS ejecuta simulaciones en 3D. Este comando debe usarse antes de definir la caja de simulación a través de los comandos `create_box` o `read_data`. |
| `newton` | Este comando activa o desactiva el uso de la tercera ley de Newton para interacciones vinculadas y por pares. Para la mayoría de los problemas, activar la tercera ley de Newton significa un modesto ahorro en cálculo. |
| `processors` | Especifica cómo se asignan los cores del procesador. |
| `boundary` | Establece las condiciones a la frontera periódicas que se usaran para la caja de simulación. Una sola letra asigna el mismo estilo tanto a la cara inferior como a la superior de la caja de simulación. Dos letras asignan el primer estilo a la cara inferior y el segundo estilo a la cara superior. El tamaño inicial de la caja de simulación lo establecen los comandos `create_box`, `read_data` o `read_restart`. |
| `atom_style` | Define los atributos que estaran asociados a cada átomo o conjuntos de atomos. Este comando debe usarse antes de configurar una simulación mediante un comando `create_box`, `read_data` o `read_restart`. |
| `atom_modify` | Modifica los atributos de los átomos que se definieron con el comando `atom_style`. |

Los parámetros de campos de fuerza que se quieren usar se pueden definir
dentro del script de entrada de LAMMPS:

| **Comando** | **Descripción** |
|-------------|-----------------| 
| `pair_style` | Establece el tipo de potencial interatómico por pares que se desea usar. |
| `bond_style` | Establece el tipo de enlace entre dos o más átomos. |
| `angle_style` | Establece los ángulos entre tres átomos. |
| `dihedral_style` | Establece los ángulos diedros entre cuatro átomos. |
| `ìmproper_style` | Establece los ángulos impropios entre cuatro átomos. |

### 2. Definición del sistema

Hay 3 formas de definir la celda de simulación y reservar espacio para
la información del campo de fuerza y llenarlo con átomos en LAMMPS.

1.  Leerlos desde un archivo de datos.

2.  Un archivo de reinicio mediante los comandos `read_data` o
    `read_restart`, respectivamente. Estos archivos también pueden
    contener información de topología molecular.

3.  Crear una celda de simulación y llenarla con átomos en una red (sin
    topología molecular), usando estos comandos:

    | **Comando** | **Descripción** |
    |-------------|-----------------| 
    | `lattice` | Se defince el tipo de arreglo o celda unitaria que se desea usar. Para simulaciones en 3D: sc, bcc, fcc, hcp y diamond. Para simulaciones en 2D: sq, sq2 y hex. |
    | `region` | Este comando define una región geométrica donde estará la caja de simulación. |
    | `create_box` | Este comando crea la caja de simulación basado en una región geométrica especifica. |
    | `create_atoms` | Este comando crea los átomos o moléculas dentro de la caja de simulación, es una alternativa a la lectura de un archivo a través de un comando `read_data` o `read_restart`. |
    | `read_dump` | Lee la información del sistema modelado desde un archivo tipo "dump". |
    
La caja de simulación se puede duplicar para hacer crecer al sistema
modelado usando el comando `replicate`.

### 3. Configuración de la simulación

Una vez que se definen las características topologicas o configuración
del sistema a simular, se pueden especificar coeficientes de campo de
fuerza, opciones de salida y más.

Los coeficientes de campo de fuerza se definen con los siguientes
comandos:

| **Comando** | **Descripción** |
|-------------|-----------------| 
| `pair_coeff` | Especifica los coeficientes de campo de fuerza por pares para uno o más pares de tipos de átomos. |
| `bond_coeff` | Especifica los coeficientes del campo de fuerza de enlace para dos o más tipos de átomos. |
| `angle_coeff` | Especifica los coeficientes del campo de fuerza del ángulo para dos o más átomos. |
| `dihedral_coeff` | Especifica los coeficientes del campo de fuerza de los ángulos diedros. |
| `improper_coeff` | Especifica los coeficientes de campo de fuerza de los ángulos impropios. |
| `kspace_style` | Define un solucionador de largo alcance para que LAMMPS utilice cada paso de tiempo para calcular interacciones Coulombic de largo alcance |
| `dielectric` | Establece la constante dieléctrica dentro de la caja de simulación. |

Estos comandos establecen varios parámetros de simulación:

| **Comando** | **Descripción** |
|-------------|-----------------| 
| `neighbor` | Este comando establece la distancia en la que se construirá la lista de vecinos por pares. |
| `neigh_modify` | Este comando establece parámetros que modifican la construcción de la lista de vecinos. |
| `group` | Se pueden definir grupos de atomos para asignarles las mismas propiedades. El ID de grupo se puede usar en otros comandos como `fix`, `compute`, `dump`, o `velocity`. |
| `timestep` | Establece el tamaño del paso de tiempo para realizar las simulaciones. Consulte el comando de `units` para conocer las unidades de tiempo asociadas con el sistema que va a simular. |
| `reset_timestep` | Reinicia o asigna el paso de tiempo. |
| `run_style` | Establece el tipo de integrador que se usará. |

Las correcciones imponen una variedad de condiciones de contorno,
integración de tiempo y opciones de diagnóstico. El comando `fix` viene
en muchas opciones.

Se pueden especificar varios cálculos para su ejecución durante una
simulación utilizando los comandos:

| **Comando** | **Descripción** |
|-------------|-----------------| 
| `compute` | Define un cálculo que se realizará en un grupo de átomos. |
| `compute_modify` | Modifica uno o más parámetros de un cálculo previamente definido. |
| `variable`     | Este comando asigna un nombre a una variable para su evaluación durante una simulación. |

Las opciones de salida se establecen mediante los comandos:

| **Comando** | **Descripción** |
|-------------|-----------------| 
| `thermo`  | Imprime en pantalla la información termodinámica (por ejemplo, energía total, temperatura, densidad, presión) en intervalos de tiempo durante la simulación. |
| `dump`  | Guarda parametros de la simulación para visualiazarlos con alguna herramienta de visualización. |
| `restart` | Escribe un archivo de reinicio binario con el estado actual de la simulación cada ciertos pasos de tiempo. |

### 4. Ejecución de la simulación

Se ejecuta una simulación de dinámica molecular utilizando el comando
`run`. La minimización de energía (estática molecular) se realiza
mediante el comando `minimize`. Se puede ejecutar una simulación de
templado paralelo (réplica-intercambio) utilizando el comando `temper`.

## Ejecución

### CPU
```
    mpiexec.hydra -bootstrap slurm -np 20 lammps -in lammps.input
```

| <!----> | <!----> |
|---------|---------|
| `mpiexec.hydra` | Se ejecuta LAMMPS en paralelo a través de `mpiexec.hydra`, debe conocer el comando que controla cómo se asignan las tareas MPI, así como las opciones de los nodos de la máquina en la que está ejecutando. Esta configuración puede mejorar el rendimiento. Es recomendable vincular tareas MPI (procesos) a la cantidad de núcleos físicos. |
| `-bootstrap slurm` | Opción necesario para que el cluster Yoltla pueda ejecutar en varios Cpu's y Nodos. |
| `-np` | Opción para escoger la cantidad de procesos a ejecutar. |
| `-in` | Opción para escoger el achivo de entrada (input) a ejecutar. Se puede usar tambien el operador de redirección `<` para escoger el achivo, pero no siempre funcionará cuando se ejecute en paralelo con `mpirun` o `mpiexec.hydra`; para esos sistemas se requiere el formato `-in`. |

### GPU
```
    mpiexec.hydra -bootstrap slurm -np 20 lmp_mpi-gpu -sf gpu -pk gpu 1 -in lammps.input
```

| <!----> | <!----> |
|---------|---------|
| `mpiexec.hydra` | Se ejecuta LAMMPS en paralelo a través de `mpiexec.hydra`, debe conocer el comando que controla cómo se asignan las tareas MPI, así como las opciones de los nodos de la máquina en la que está ejecutando. Esta configuración puede mejorar el rendimiento. Es recomendable vincular tareas MPI (procesos) a la cantidad de núcleos físicos. |
| `-bootstrap slurm` | Opción necesario para el cluster Yoltla para ejecutar en varios Cpu's y Nodos. |
| `-np` | Opción para escoger la cantidad de procesos a ejecutar. |
| `-in` | Opción para escoger el achivo de entrada (input) a ejecutar. Se puede usar tambien el operador de redirección `<` para escoger el achivo, pero no siempre funcionará cuando se ejecute en paralelo con `mpirun` o `mpiexec.hydra`; para esos sistemas se requiere el formato `-in`. |
| `-sf gpu` | El comando \"-sf gpu\", detecta la cantidad de gpu en el equipo disponible. |
| `-pk gpu` | El comando `-pk` invoca configuraciones específicas del paquete GPU. El uso del comando `-pk gpu` permite establecer explícitamente el número de GPU a utilizar y opciones adicionales. |

Mas información del comando `-pk`
[aquí](https://docs.lammps.org/package.html).

## Scripts de ejemplo

Puede encontrar scripts de ejemplo de la aplicación LAMMPS en el
siguiente directorio:
```
    /LUSTRE/scripts_ejemplo/Lammps
```

## Errores frecuentes

LAMMPS detecta muchos errores del script de entrada y se imprime un
mensaje de ERROR o ADVERTENCIA. A continuación se listan los errores más
comunes:

| **Error** | **Descripción** |
|-----------|-----------------| 
| `1-3 bond count is inconsistent` | Se detectó una inconsistencia al calcular el número de 1-3 vecinos para cada átomo. Esto probablemente significa que algo anda mal con las topologías de enlace que ha definido. |
| `Accelerator sharing is not currently supported on system` | Varios procesos MPI no pueden compartir el acelerador en su sistema. Para las GPU NVIDIA, consulte el comando `nvidia-smi` para cambiar esta configuración. |
| `All angle coeffs are not set` | Todos los coeficientes de ángulo deben establecerse en el archivo de datos o mediante el comando `angle_coeff` antes de ejecutar una simulación. |
| `All bond coeffs are not set` | Todos los coeficientes de enlace deben establecerse en el archivo de datos o mediante el comando `bond_coeff` antes de ejecutar una simulación. |
| `Angle atom missing in delete_bonds` | El comando `delete_bonds` no puede encontrar uno o más átomos en un ángulo particular en un procesador en particular. El corte por pares es demasiado corto o los átomos están demasiado separados para formar un ángulo válido. |
| `Angle extent > half of periodic box length` | Este error fue detectado por la configuración `neigh_modify check yes`. Los átomos de los ángulos están tan separados que es ambiguo cómo debería definirse. |
| `Angle_coeff command before angle_style is defined` | Los coeficientes no se pueden establecer en el archivo de datos o mediante el comando `angle_coeff` hasta que se haya asignado un `angle_style`. |
| `Angle_coeff command before simulation box is defined` | El comando `angle_coeff` no se puede utilizar antes de un comando `read_data`, `read_restart` o `create_box`. |
| `Atom count is inconsistent, cannot write data file` | La suma de átomos en los procesadores no es igual al número global de átomos. Probablemente se hayan perdido algunos átomos. |
| `Atom in too many rigid bodies - boost MAXBODY` | Fix poems tiene un parámetro `MAXBODY` (en fix_poems.cpp) que determina el número máximo de cuerpos rígidos a los que puede pertenecer un solo átomo (es decir, una unión multicuerpo). Los cuerpos que ha definido superan este límite. |

### Consideraciones importantes

LAMMPS se ejecuta leyendo los comandos del script de entrada, una línea
a la vez.

En muchos casos, el orden de los comandos en un script de entrada no es
importante. Sin embargo, se aplican las siguientes reglas:

1.  LAMMPS no lee todo el script de entrada y luego realiza una
    simulación con todos los ajustes. Por el contrario, la secuencia de
    comandos de entrada se lee una línea a la vez y cada comando entra
    en vigor cuando se lee. Por lo tanto, esta secuencia de comandos:
    ```
        timestep 0.5
        run      100
        run      100
    ```

    hace algo diferente a esta secuencia:
    ```
        run      100
        timestep 0.5
        run      100
    ```

    En el primer caso, el intervalo de tiempo especificado (0,5 fs) se
    utiliza para dos simulaciones de 100 intervalos de tiempo cada una.
    En el segundo caso, se usa el paso de tiempo predeterminado (1.0 fs)
    para la primera simulación de 100 pasos y se usa un paso de tiempo
    de 0.5 fs para la segunda

2.  Algunos comandos solo son válidos cuando siguen otros comandos. Por
    ejemplo, no puede establecer la temperatura de un grupo de átomos
    hasta que se hayan definido los átomos y se utilice un comando de
    grupo para definir qué átomos pertenecen al grupo.

3.  A veces, el comando B utilizará valores que se pueden establecer con
    el comando A. Esto significa que el comando A debe preceder al
    comando B en el script de entrada para que tenga el efecto deseado.
    Por ejemplo, el comando `read_data` inicializa el sistema
    configurando la caja de simulación y asignando átomos a los
    procesadores. Si no se desean valores predeterminados, los
    procesadores y los comandos de límites deben usarse antes de
    `read_data` para decirle a LAMMPS cómo asignar procesadores a la
    caja de simulación.

## Licencia

LAMMPS es un código fuente abierto disponible gratuitamente, distribuido
bajo los términos de la Licencia Pública GNU.

Para obtener más información, consulte la página [LAMMPS open-source
license](https://lammps.sandia.gov/doc/Intro_opensource.html)

## Referencias

-   [Página oficial de LAMMPS](https://lammps.sandia.gov/)
