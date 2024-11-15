# Anexos

## Recursos de Cómputo

Existen 27 particiones para solicitar recursos en el cluster, el nombre de cada una 
de estas particiones hace referencia a los recursos máximos que se pueden solicitar. 
Por ejemplo, la partición *q1d-80p* tiene como tiempo de ejecución máximo 1 día 
utilizando hasta 80 CPUs.

***Tabla 1. Particiones en el clúster Yoltla***

| **Nombre de la particion** | **Tiempo máximo** | **Formato simplificado y extenso de SLURM** | **Número de CPUs** | **Tipo de nodo** |
|----------------------------|-------------------|---------------------------------------------|--------------------|------------------|
| q1h-20p     | 1 hora      | 0-1  / 1:00:00       | 20              | 1x nc       |
| q1d-20p     | 1 día       | 1-0  / 1-00:00:00    | 20              | 1x nc       |
| q4d-20p     | 4 días      | 4-0  / 4-00:00:00    | 20              | 1x nc       |
| q7d-20p     | 7 días      | 7-0  / 7-00:00:00    | 20              | 1x nc       |
| q1h-40p     | 1 hora      | 0-1  / 1:00:00       | 40              | 2x nc       |
| q1d-40p     | 1 día       | 1-0  / 1-00:00:00    | 40              | 2x nc       |
| q4d-40p     | 4 días      | 4-0  / 4-00:00:00    | 40              | 2x nc       |
| q1h-80p     | 1 hora      | 0-1  / 1:00:00       | 80              | 4x nc       |
| q12h-80p    | 12 horas    | 0-12 / 12:00:00      | 80              | 4x nc       |
| q1d-80p     | 1 día       | 1-0  / 1-00:00:00    | 80              | 4x nc       |
| q4d-80p     | 4 días      | 4-0  / 4-00:00:00    | 80              | 4x nc       |
| q1h-160p    | 1 hora      | 0-1  / 1:00:00       | 160             | 8x nc       |
| q12h-160p   | 12 horas    | 0-12 / 12:00:00      | 160             | 8x nc       |
| q1d-160p    | 1 día       | 1-0  / 1-00:00:00    | 160             | 8x nc       |
| q1h-320p    | 1 hora      | 0-1  / 1:00:00       | 320             | 16x nc      |
| q12h-320p   | 12 horas    | 0-12 / 12:00:00      | 320             | 16x nc      |
| q1d-320p    | 1 día       | 1-0  / 1-00:00:00    | 320             | 16x nc      |
| tt2d-80p    | 2 días      | 2-0  / 2-00:00:00    | 80              | 4x tt       |
| tt2d-100p   | 2 días      | 2-0  / 2-00:00:00    | 100             | 5x tt       |
| tt1d-160p   | 1 día       | 1-0  / 1-00:00:00    | 160             | 8x tt       |
| tt12h-320p  | 12 horas    | 0-12 / 12:00:00      | 320             | 16x tt      |
| tt2d-64p    | 2 días      | 2-0  / 2-00:00:00    | 64p             | 2x tt       |
| tt1d-128p   | 1 día       | 1-0  / 1-00:00:00    | 128             | 4x tt       |
| tt1d-256p   | 1 día       | 1-0  / 1-00:00:00    | 256             | 8x tt       |
| tt1d-512p   | 1 días      | 1-0  / 1-00:00:00    | 512             | 16x tt      |
| gpus        | 4 días      | 4-0  / 4-00:00:00    | 2 / 4 / 8  GPU  | nc          |
| vgpus       | 4 días      | 4-0  / 4-00:00:00    | 2 / 4 GPU       | nc          |

```admonish note title="NOTA"
La información que se presenta puede ser diferente a la disponible en el clúster, 
por favor ejecute el comando:

        sjstat -c

en los nodos de acceso para ver la lista completa/actualizada de los nodos disponibles.
```

***Tabla2. Nodos de cómputo en el clúster Yoltla***

|  **Tipo de nodo**  | **Número de CPUs** | **Memoria RAM** |
|--------------------|:------------------:|:---------------:|
| Cómputo CPU - nc   | 20                 | 64 GB           |
| Cómputo GPU - nc   | 20                 | 64 GB           |
| Cómputo VGPU - nc  | 36                 | 128 GB          |
| Cómputo VGPU - nc  | 36                 | 256 GB          |
| Cómputo CPU - tt   | 20                 | 128 GB          |
| Cómputo CPU - tt   | 32                 | 256 GB          |

## Directivas de SLURM

### Nombre del trabajo
```
    --job-name=trabajo
```
Establece el nombre del trabajo. Si no se establece un nombre para el trabajo, el 
nombre por default será el nombre del script.

### Salida estándar
```
    --output=salida
```
Establece el nombre del archivo en el que se escribiran los mensajes del flujo de 
la \"salida estándar\". Si no se establece un nombre para este archivo, el nombre 
por default será *slurm-\<ID del trabajo\>.out*.

Por ejemplo:
```
    #SBATCH --output=salida-%j.out
```

indica que se debe crear el archivo *salida-\<ID del trabajo\>.out* para guardar 
los mensajes del flujo de la \"salida estándar\".

### Error estándar
```
    --error=error
```
Establece el nombre del archivo en el que se escribiran los mensajes del flujo de 
\"error estándar\". Si no se establece un nombre para este archivo, el nombre por 
default será *slurm-\<ID del trabajo\>.out*.

Por ejemplo:
```
    #SBATCH --error=error-%j.out
```
indica que se debe crear el archivo *error-\<ID del trabajo\>.out* para guardar los 
mensajes del flujo del \"error estándar\".

### Nombre de la partición
```
    --partition=partición
```

Estable el nombre de la partición donde se formará el trabajo para ser atendido 
(ver sección [Recursos de cómputo](#recursos-de-cómputo)). Si no se establece 
una partición, el sistema formará el trabajo en la partición default *q1h-20p*.

### Tiempo máximo de ejecución
```
    --time=dd-hh:mm:ss
```
Establece el tiempo máximo de uso de los nodos de cómputo, el trabajo puede terminar 
de ejecutarse en menos tiempo (caso deseado) o no terminar en el tiempo solicitado, 
en este último caso el programa es notificado mediante una señal SIGTERM seguida por 
la señal SIGKILL.

En caso de omitir esta directiva, el tiempo máximo se establecerá según la partición. 
En general se recomienda establecer el tiempo, si es menor que el máximo permitido 
por la partición, ya que permitirá al algoritmo "backfill" seleccionar el trabajo 
para su ejecución antes que otros trabajos que le preceden.

***Tabla 3. Formatos válidos de la directiva time***

| **Tiempo**                        | **Formato**                       |
|-----------------------------------|-----------------------------------|
| minutos                           | `--time=35`                       |
| minutos:segundos                  | `--time=35:20`                    |
| horas:minutos:segundos            | `--time=1:35:20`                  |
| días-horas                        | `--time=1-0` - `--time=0-1`       |
| días-horas:minutos                | `--time=4-1:35`                   |
| días-horas:minutos:segundos       | `--time=4-1:35:20`                |

### Número de nodos
```
    --nodes=#
```
Estable la cantidad de nodos de cómputo a utilizar para la ejecución del trabajo. Es
necesario indicar el número de nodos dependiendo de la partición solicitada ya que 
de lo contrario el trabajo será rechazado.

### Número de tareas por nodo
```
    --ntasks-per-node=#
    --tasks-per-node=#
```
Estas dos directivas son equivalentes y establecen la cantidad tareas a ejecutar en 
los nodos asignados. Cada una de las tareas será atendida por un core diferente.

En el entorno de SLURM una tarea es una copia del programa que se ejecutará en el 
nodo o nodos asignados.

### Número de CPUs por tarea
```
    --cpus-per-task=#
```
Establece la cantidad de CPUs que utilizará una tarea en cada uno de los nodos asignados. 
Esta directiva es útil para ejecuciones de programas de memoria compartida (OpenMP) 
ya que solamente se ejecuta una copia (tarea) del programa y posteriormente se crean 
hilos necesarios para atender las partes paralelas.

La cantidad de hilos que se crearán durante la ejecución de un programa de memoria 
compartida (OpenMP) es controlada en el archivo de entrada de la tarea o por medio de 
la variable de ambiente OMP_NUM_THREADS (ver sección [Scripts de ejemplo](#scripts-de-ejemplo)).

### Memoria por nodo
```
    --mem=#
```
Establece la memoria requerida por nodo. Las unidades predeterminadas son megabytes (MB). 
Se pueden especificar diferentes unidades usando el sufijo [K|M|G|T].

### Correo eléctronico
```
    --mail-user=email
```
Establece el correo eléctronico en el que el usuario recibira notificaciones de los cambios 
de estado de un trabajo.

### Tipo de notificaciones
```
    --mail-type=eventos
```
Establece los eventos que se notificarán por correo electrónico.

Por ejemplo:
```
    #SBATCH --mail-type=BEGIN,END,FAIL
```
indica que se debe enviar una notificación cuando el trabajo inicie, termine o falle.

***Tabla 4. Valores válidos en la directiva mail-type***

| **Valor**       | **Descripción**                   |
|-----------------|-----------------------------------|
| NONE            | No recibir ninguna notificación.  |
| BEGIN           | Notificar el inicio del trabajo.  |
| END             | Notificar el fin del trabajo.     |
| FAIL            | Notificar si el trabajo falla.    |
| INVALID_DEPEND  | Notificar si el trabajo tiene una dependencia inválida. |
| TIME_LIMIT      | Notificar si el trabajo alcanzo su límite de tiempo.    |
| ARRAY_TASKS     | Recibir una notificación por cada trabajo en el array.  |
| ALL             | Recibir todas las notificaciones. |

## SLURM Environment Variables

SLURM cuenta con una serie de variables de entorno que pueden ser utilizadas dentro 
de un script. A continuación se listan las variables más comunes:

| **Variable** | **Descripción** |
|--------------|-----------------|
| SLURM_ARRAY_TASK_COUNT  | Número de tareas en el array de trabajos. |
| SLURM_ARRAY_TASK_ID     | Índice del elemento actual del array de trabajos. |
| SLURM_ARRAY_TASK_MAX    | Índice del último elemento del array de trabajos. |
| SLURM_ARRAY_TASK_MIN    | Índice del primer elemento del array de trabajos. |
| SLURM_ARRAY_JOB_ID      | ID del trabajo maestro del array de trabajos. |
| SLURM_CLUSTER_NAME      | Nombre del clúster en el que se ejecuta el trabajo. |
| SLURM_CPUS_ON_NODE      | Número de CPUs en el nodo asignado. |
| SLURM_CPUS_PER_GPU      | Número de CPUs solicitadas por GPU. |
| SLURM_CPUS_PER_TASK     | Número de CPUs solicitadas por tarea. |
| SLURM_GPUS              | Número de GPUs solicitadas.       |
| SLURM_GPUS_PER_NODE     | Número de GPUs solicitadas por nodo |
| SLURM_JOB_ACCOUNT       | Nombre de la cuenta que envío el trabajo. |
| SLURM_JOB_ID            | ID del trabajo.                   |
| SLURM_JOB_DEPENDENCY    | Dependencias del trabajo.         |
| SLURM_JOB_NAME          | Nombre del trabajo.               |
| SLURM_JOB_NODELIST      | Lista de nodos asignados al trabajo. |
| SLURM_JOB_NUM_NODES     | Número de nodos asignados del trabajo. |
| SLURM_JOB_PARTITION     | Nombre de la partición en la que se ejecuta el trabajo. |
| SLURM_NODEID            | IDs de los nodos asignados.       |
| SLURMD_NODENAME         | Nombre del nodo que ejecuta el trabajo. |
| SLURM_NTASKS            | Número de tareas solicitadas.     |
| SLURM_NTASKS_PER_GPU    | Número de tareas solicitadas por GPU. |
| SLURM_NTASKS_PER_NODE   | Número de tareas solicitadas por nodo. |
| SLURM_SUBMIT_DIR        | Directorio desde el que se envió el trabajo. |

Para obtener la lista completa de variables y su descripción, consulte la sección 
[OUTPUT ENVIRONMENT VARIABLES](https://slurm.schedmd.com/sbatch.html#lbAK) en la página
[sbatch](https://slurm.schedmd.com/sbatch.html) de la documentación oficial de SLURM.

## Job State Codes

Los trabajos suelen pasar por varios estados en el curso de su ejecución, y cada uno 
de estos estados se identifica con un código. A continuación se listan los códigos más comunes:

| **Código** | **Estado** | **Descripción** |
|------------|------------|-----------------|
| CA | CANCELLED | El trabajo fue cancelado explícitamente por el usuario o el administrador del sistema. El trabajo puede haberse iniciado o no. |
| CD | COMPLETED | El trabajo ha terminado todos los procesos en todos los nodos. |
| CF | CONFIGURING | Se han asignado recursos al trabajo, pero aún no están listos para su uso. |
| CG | COMPLETING | El trabajo está en proceso de finalización. Es posible que algunos procesos en algunos nodos aún estén activos. |
| F | FAILED | El trabajo terminó con una condición de falla. |
| NF | NODE_FAIL |El trabajo terminó debido a la falla de uno o más nodos asignados. |
| PD | PENDING | El trabajo está esperando la asignación de recursos. |
| R | RUNNING | El trabajo se está ejecutando. |
| TO | TIMEOUT | El trabajo finalizó al alcanzar su límite de tiempo. |

Para obtener la lista completa de códigos y su descripción, consulte la sección 
[JOB STATE CODES](https://slurm.schedmd.com/squeue.html#lbAG) en la página 
[squeue](https://slurm.schedmd.com/squeue.html) de la documentación oficial de SLURM.

## Job Reason Codes

Estos códigos identifican la razón por la que un trabajo está esperando su ejecución. 
Un trabajo puede estar esperando por más de un motivo, en cuyo caso solo se muestra uno 
de esos motivos. A continuación se listan los códigos más comunes:

| **Razón** | **Descripción** |
|-----------|-----------------|
| Dependency         | El trabajo está esperando a que se complete un trabajo dependiente.|   
| NodeDown           | Un nodo requerido por el trabajo está inactivo. |
| PartitionNodeLimit | La cantidad de nodos requeridos por este trabajo está fuera de los límites de la partición. |
| PartitionTimeLimit | El límite de tiempo del trabajo excede el límite de tiempo de la partición. |
| Priority           | Existen uno o más trabajos de mayor prioridad para esta partición. |
| ReqNodeNotAvail    | Algunos nodos requeridos por el trabajo no están disponibles actualmente. Los nodos pueden estar en uso o sin responder. |
| Resources          | El trabajo está esperando que haya recursos disponibles. |
| TimeLimit          | El trabajo agotó su límite de tiempo. |

Para obtener la lista completa de códigos y su descripción, consulte la sección 
[JOB REASON CODES](https://slurm.schedmd.com/squeue.html#lbAF) en la página 
[squeue](https://slurm.schedmd.com/squeue.html) de la documentación oficial de SLURM.

## Job Accounting Fields

| **Campo** | **Descripción** |
|-----------|-----------------|
| AllocCPUS | Número de CPUs asignados al trabajo. |
| AllocNodes | Número de nodos asignados al trabajo. |
| Account | Nombre de la cuenta bajo la que se ejecutó el trabajo. |
| End | Hora de término del trabajo. |
| ExitCode | Código de salida del trabajo. |
| JobID | Número de identificación del trabajo. |
| JobName | Nombre del trabajo. |
| NodeList | Lista de nodos asignados al trabajo. |
| Partition | Partición asignada al trabajo. |
| Start | Hora de inicio del trabajo. |
| State | Estado del trabajo. |
| Submit | Hora en que se envió el trabajo. |

Para obtener la lista completa de campos y su descripción, consulte la sección 
[Job Accounting Fields](https://slurm.schedmd.com/sacct.html#lbAF) en la página
[sacct](https://slurm.schedmd.com/sacct.html) de la documentación oficial de SLURM.

## Compiladores de memoria distribuida

|  | **Intel Suite** | **OpenMPI** | **HPCX** | **Mvapich2** |
|-----|--------------|-------------|----------|--------------|
| C   | mpiicc   | mpicc  | mpicc  | mpicc  |
| C++ | mpiicc   | mpicxx | mpicxx | mpicxx |
| F90 | mpiifort | mpif90 | mpif90 | mpif90 |
| F77 | mpiifort | mpif77 | mpif77 | mpif77 |
| MPI LAUNCH | mpirun <br> mpiexec.hydra | mpirun <br> mpiexec | mpirun <br> mpiexec | mpirun <br> mpiexec.hydra |

## Opciones para compilar en memoria compartida

|       | **GNU** | **Intel Suite** |
|-------|---------|-----------------|
| Compilador de lenguaje C | gcc | icc |
| Compilador de lenguaje C++ | g++ | icpc |
| Compilador de lenguaje Fortran | gfortran | ifort |
| Threads openmp | -fopenmp | -openmp |
| phreads | -pthread | -pthread |
| Optimización de código | -O0<br>-O1<br>-O2<br>-O3<br>-ffast-math | -O0<br>-O1<br>-O2<br>-O3<br>-fast |
| Reporte de mensajes de<br> precaución en la compilación | -Wall | -Wall |
| Habilitar AVX | -mavx | -mavx |
| Habilitar AVX2<br>(solo para nodos tt) |  | -march=core-avx2<br><br>-axCORE-AVX512<br>-axCORE-AVX2<br>-axAVX |

```admonish note title="NOTA"
Si utiliza las opciones -march y -ax, el compilador no generará instrucciones específicas
de Intel. Esto permite generar un solo archivo que podrá ejecutarse en cualquier tipo
de procesador, con la optimización adecuada que se determinará en tiempo de ejecución.
```

```admonish warning title="IMPORTANTE"
Tenga cuidado al utilizar la opción -fast, ya que establece, entre otras opciones, la 
opción -xHost automáticamente durante la compilación. La opción -xHost le dice al 
compilador que genere instrucciones específicas para el procesador anfitrión de compilación.
```

## Scripts de ejemplo

### Tareas seriales

Trabajo con 20 tareas seriales.
```
#!/bin/bash
#
### Partición q1h-20p ###
#SBATCH --partition=q1h-20p

#
### Nombre del trabajo ###
#SBATCH --job-name=programax20

#
### El trabajo requiere de 1 nodo, donde se ejecutarán 20 tareas ###
### Por default por cada nodo solicitado SLURM asume que se ###
### ejecutará una tarea. ###
### LA DIRECTIVA #SBATCH --nodes=1 NO RESERVA NODOS COMPLETOS ###
### ES NECESARIO INDICAR EXPLÍCITAMENTE LA CANTIDAD DE TAREAS ###
### QUE SE EJECUTARÁN EN LOS NODOS SOLICITADOS ###
#SBATCH --nodes=1
#SBATCH --ntasks-per-node=20

#
### Se solicitan 30 minutos para este trabajo ###
#SBATCH --time=30:00

#
### A continuación todos los comandos necesarios para ejecutar las ###
### 20 tareas ### 

# Cargamos el modulo correspondiente al programa que ejecutaremos
module load <modulefiles/app>

# Indicamos al shell bash que a partir de esta línea, imprima en error
# estándar “STDERR” cada comando antes de ser ejecutado.
# Útil para fines de diagnostico
set -x

# SLURM comienza la ejecución del trabajo en el mismo directorio donde
# se invoco el comando sbatch. El siguiente comando es opcional
cd $SLURM_SUBMIT_DIR

# Ejecutamos cada una de las 20 tareas (en segundo plano)
# en este caso con archivos de entrada diferentes
programa input1 &
programa input2 &
…
…
programa input20 &


# De antemano no sabemos el orden en que terminarán cada una de
# las 20 tareas que fueron lanzadas en segundo plano.
# Nos auxiliaremos del comando interno de bash “wait” para detener
# la ejecución del script (trabajo) hasta que todos los procesos
# lanzados en segundo plano hayan finalizado.
#
# Sin esta instrucción el script terminara y SLURM dará por
# finalizado el trabajo y terminando por medio de señales “kill”
# cualquier tarea asociada al trabajo, en este caso los procesos
# lanzados en segundo plano.
wait
```

### OpenMP

Trabajo con 1 tares utilizando 20 CPUs.
```
#!/bin/bash
#
### Partición q1h-20p ###
#SBATCH --partition=q1h-20p

#
### Nombre del trabajo ###
#SBATCH --job-name=programa_OMP

#
### La salida estándar “STDOUT” de la tarea será redirigida al ###
### archivo programa_OMP.o%j. %j será remplazado por el ###
### identificador asignado al trabajo. ###
#SBATCH --output=programa_OMP.o%j

#
### El error estándar “STDERR” de la tarea será redirigida al ###
### archivo programa_OMP.e%j. %j será remplazado por el ###
### identificador asignado al trabajo. ###
#SBATCH --error=programa_OMP.e%j

#
### Indicamos a SLURM que esta tarea ocupara 20 cores. ###
### NO ESTABLECER ESTA OPCIÓN TENDRÁ COMO RESULTADO QUE LOS HILOS ##
### CREADOS POR EL PROGRAMA SEAN RESTRINGIDOS A UN SOLO CORE EN ##
### EN EL NODO DE CÓMPUTO, AFECTANDO CON ESTO DRÁSTICAMENTE EL ###
### RENDIMIENTO ###
#SBATCH --cpus-per-task=20

#
### Se solicitan 30 minutos para este trabajo ###
#SBATCH --time=30:00
#
### A continuación todos los comandos necesarios para ejecutar la ###
### tarea ###

# Cargamos el modulo correspondiente al programa que ejecutaremos. 
module load <modulefiles/app>

# Indicamos al shell bash que a partir de esta línea, imprima en error
# estándar “STDERR” cada comando antes de ser ejecutado.
# Útil para fines de diagnostico.
set -x

# SLURM comienza la ejecución del trabajo en el mismo directorio donde
# se invoco el comando sbatch. El siguiente comando es opcional
cd $SLURM_SUBMIT_DIR

# Consultamos los cores que podemos utilizar así como el limite para
# el segmento de memoria de pila o “stack size”
grep Cpus_allowed_list: /proc/self/status
grep "Max stack size" /proc/self/limits
ulimit -s

# Ejecutamos la tarea en primer plano programa
input1
```

### MPI

Trabajo con 2 nodos y 32 tareas por nodo.
```
#!/bin/bash
#
### Partición tt2d-64p ###
#SBATCH --partition=tt2d-64p

#
### Nombre del trabajo ###
#SBATCH --job-name=programa_MPI

#
### La salida estándar “STDOUT” de la tarea será redirigida al ###
### archivo programa_MPI.o%j. %j será remplazado por el ###
### identificador asignado al trabajo. ###
#SBATCH --output=programa_MPI.o%j

# ### El error estándar “STDERR” de la tarea será redirigida al ###
### archivo programa_MPI.e%j. %j será remplazado por el ###
### identificador asignado al trabajo. ###
#SBATCH --error=programa_MPI.e%j

#
### El trabajo requiere de 2 nodos, cada uno ejecutará 32 tareas. ###
#SBATCH --nodes=2
#SBATCH --ntasks-per-node=32

#
### Se solicitan 2 días para este trabajo ###
#SBATCH --time=2-0
#
### A continuación todos los comandos necesarios para ejecutar la ###
### tarea ###

# Cargamos el modulo correspondiente al programa que ejecutaremos.
module load <modulefiles/app>

# Indicamos al shell bash que a partir de esta línea, imprima en error
# estándar “STDERR” cada comando antes de ser ejecutado.
# Útil para fines de diagnostico.
set -x

# SLURM comienza la ejecución del trabajo en el mismo directorio donde
# se invoco el comando sbatch. El siguiente comando es opcional
cd $SLURM_SUBMIT_DIR

# Obtenemos la lista de nodos asignados en el archivo nodes.list
scontrol show hostname $SLURM_NODELIST > nodes.list

# Ejecutamos el programa nwchem por medio de mpiexec.hydra:
# 64 tareas (-np $SLURM_NTASKS)
# 32 tareas por nodo (-ppn $SLURM_NTASKS_PER_NODE)

MPI_COM=”mpiexec.hydra -bootstrap rsh -f ./hostlist.dat ”
$MPI_COM -ppn $SLURM_NTASKS_PER_NODE -np $SLURM_NTASKS nwchem input.nw
```

### GPUS

Trabajo con 1 nodo utilizando GPUS.
```
#!/bin/bash
#
### Partición gpus ###
#SBATCH --partition=gpus

#
### Nombre del trabajo ###
#SBATCH --job-name=programa_GPU

#
### La salida estándar “STDOUT” de la tarea será redirigida al ###
### archivo programa_GPU.o%j. %j se remplazará por el ###
### identificador asignado al trabajo. ###
#SBATCH --output=programa_GPU.o%j

#
### El error estándar “STDERR” de la tarea será redirigida al ###
### archivo programa_GPU.e%j. %j se remplazará por el ###
### identificador asignado al trabajo. ###
#SBATCH --error=programa_GPU.e%j

#
### El trabajo requiere de 1 nodo, dependiendo de la aplicación ###
### es la cantidad de tareas a ejecutar. En este caso asumiremos ###
### que 2 tareas cada una de ellas trabajando en una tarjeta GPU ###
#SBATCH --nodes=1
#SBATCH --ntasks-per-node=2

#
### El cluster yoltla cuenta con nodos GPU:
### 16 con 2 tarjetas. ###
### 4 con 4 tarjetas. ###
### 2 con 8 tarjetas. ###
### y nodos VGPU:
### 2 con 2 tarjetas. ###
### 1 con 4 tarjetas. ###
### Para solicitar los recursos cómputo, que en este caso son ###
### las tarjetas GPU o VGPU, debemos indicar a slurm la cantidad de ###
### tarjetas que requerimos para ejecutar nuestro programa. ###
### --gres=gpu:2
### --gres=gpu:4
### --gres=gpu:8
###
### Con base en esta información se nos asignará el nodo con el ###
### número de tarjetas solicitas. En este ejemplo solicitaremos ###
### un nodo con 2 tarjetas.
#SBATCH --gres=gpu:2

#
### Se solicitan 2 días para este trabajo ###
#SBATCH --time=2-0

#
### A continuación todos los comandos necesarios para ejecutar la ###
### tarea ###

# Cargamos el modulo correspondiente al programa que ejecutaremos.
module load <modulefiles/app>

# Indicamos al shell bash que a partir de esta línea, imprima en error
# estándar “STDERR” cada comando antes de ser ejecutado.
# Útil para fines de diagnostico.
set -x

# SLURM comienza la ejecución del trabajo en el mismo directorio donde
# se invoco el comando sbatch. El siguiente comando es opcional
cd $SLURM_SUBMIT_DIR

# Consultamos los cores que podemos utilizar así como el limite para
# el segmento de memoria de pila o “stack size”
grep Cpus_allowed_list: /proc/self/status
grep "Max stack size" /proc/self/limits
ulimit -s
echo $CUDA_VISIBLE_DEVICES

programa-GPU input
```
