# Job Array

Job arrays en Slurm permiten enviar y gestionar colecciones de trabajos 
similares de manera rápida y sencilla. Son especialmente útiles cuando 
se requiere ejecutar múltiples tareas que comparten la misma configuración 
inicial (como el tamaño o el límite de tiempo), pero varían ligeramente 
en parámetros específicos.

**Ventajas de usar Job Arrays:**

* **Eficiencia en la gestión:** Se pueden enviar millones de tareas en 
milisegundos (dependiendo de la configuración del sistema).

* **Consistencia en configuración:** Todas las tareas comparten las mismas 
opciones iniciales.

* **Flexibilidad:** Se pueden modificar algunas opciones después de que el 
trabajo ha comenzado utilizando el comando `scontrol`.

**Ejemplos de uso de `scontrol`:**

    # Actualiza la configuración para todo el job array
    scontrol update job=101 ...

    # Actualiza la configuración para un trabajo específico dentro del array
    scontrol update job=101_1 ...


## ¿Qué es un Job Array?

Un Job Array es un conjunto de trabajos enviados con el comando `sbatch` 
utilizando la opción `--array` o `-a`. Todos los trabajos en el array comparten 
la misma configuración inicial y difieren únicamente en el valor de índice 
(`SLURM_ARRAY_TASK_ID`). Esto es útil para ejecutar múltiples instancias de 
un script con diferentes parámetros de entrada.

**Consideraciones importantes:**

* **Solo para trabajos batch:** No se pueden usar en trabajos interactivos.

* **Índices de array:** Se especifican con `--array` o `-a`, y pueden incluir:
    - Un rango (0-31)
    - Valores específicos (1,3,5,7)
    - Un rango con un paso (1-7:2)

* **Valor mínimo:** 0
* **Valor máximo:** Configurado por el parámetro `MaxArraySize` en Slurm.

>**Ejemplo 1: Índices consecutivos**
>
>```bash
>   sbatch --array=0-31 -N1 script.sh
>```
>Este comando envía un array con índices de 0 a 31, utilizando un nodo 
>(`-N1`) por tarea.

>**Ejemplo 2: Índices específicos**
>
>```bash
>   sbatch --array=1,3,5,7 -N1 script.sh
>```
>Este ejemplo ejecuta el script solo para los índices 1, 3, 5, y 7.

>**Ejemplo 3: Rango con paso**
>
>```bash        
>    sbatch --array=1-7:2 -N1 script.sh
>```
>En este caso, se ejecuta el script para los índices 1, 3, 5, y 7, 
>con un paso de tamaño 2.

>**Ejemplo 4: Limitando tareas simultáneas**
>
>```bash
>    sbatch --array=0-15%4 -N1 script.sh
>```
>Esto limita el número de tareas simultáneas a 4, lo que puede ser útil para 
>controlar el uso de recursos.


## Variables de entorno en Job Arrays

Cada tarea en un job array tiene acceso a variables de entorno específicas:

**`SLURM_ARRAY_JOB_ID`**: ID del primer trabajo del array.<br>
**`SLURM_ARRAY_TASK_ID`**: Índice del array para la tarea actual.<br>
**`SLURM_ARRAY_TASK_COUNT`**: Número total de tareas en el array.<br>
**`SLURM_ARRAY_TASK_MAX`**: Valor más alto de índice en el array.<br>
**`SLURM_ARRAY_TASK_MIN`**: Valor más bajo de índice en el array.


>**Ejemplo práctico**
>```bash
>    #!/bin/bash
>    #SBATCH --job-name=array_example
>    #SBATCH --output=output_%A_%a.out
>    #SBATCH --error=error_%A_%a.err
>    #SBATCH --array=0-4
>
>    echo "Job Array ID: $SLURM_ARRAY_JOB_ID"
>    echo "Task ID: $SLURM_ARRAY_TASK_ID"
>    echo "Total Tasks: $SLURM_ARRAY_TASK_COUNT"
>    echo "Running task with index $SLURM_ARRAY_TASK_ID"
>```
>
>Guarda este script como array_example.sh y ejecútalo con:
>```bash
>    sbatch array_example.sh
>```
>
>Esto creará 5 tareas con índices de 0 a 4, y generará archivos de salida y 
>error con el formato `output_<JobID>_<TaskID>.out`.


## Accediendo a archivos específicos

En muchos casos, las tareas del job array procesan diferentes archivos de 
entrada. Utilizando el índice de la tarea, se pueden acceder a diferentes 
archivos en el script.

>**Ejemplo: Procesando Archivos de Datos**
>```bash
>    #!/bin/bash
>    #SBATCH --job-name=array_files
>    #SBATCH --output=output_%A_%a.out
>    #SBATCH --array=0-3
>
>    # Asumiendo que tienes archivos data_0.txt, data_1.txt, ..., data_3.txt
>    INPUT_FILE="data_$SLURM_ARRAY_TASK_ID.txt"
>
>    echo "Procesando archivo: $INPUT_FILE"
>    cat $INPUT_FILE  # Aquí iría el procesamiento real
>```
>
>Ejecuta el script con:
>```bash
>    sbatch array_files.sh
>```
>
>Cada tarea procesará un archivo diferente (data_0.txt, data_1.txt, etc.).


## Gestión y monitorización de Job Arrays

Ver el estado de un job array.
```bash
squeue --job <JobID>
```

Cancelar todo el array
```bash
scancel <JobID>
```

Cancelar una tarea específica
```bash
scancel <JobID>_<TaskID>
```

Actualizar parámetros en ejecución
```bash
scontrol update job=<JobID>_<TaskID> ...
```

# Gestión de Job Arrays en Slurm

**Introducción**

En Slurm, los Job Arrays permiten enviar y gestionar colecciones de trabajos 
similares de manera eficiente. Además de facilitar el envío masivo de 
trabajos, ofrecen opciones flexibles para el manejo de archivos de salida y 
la administración de tareas en ejecución. Este tutorial cubre las siguientes 
funcionalidades:

* Nombres de archivos para `stdin`, `stdout` y `stderr` en job arrays.
* Uso del comando `scancel` para cancelar trabajos en un array.
* Monitoreo con `squeue` para visualizar el estado de los trabajos.

## Nombres de Archivos en Job Arrays (Formato de Nombres)

Al trabajar con job arrays, se pueden especificar nombres personalizados 
para los archivos de salida (`stdout`) y error (`stderr`) utilizando los 
siguientes identificadores:

* `%A`: Se reemplaza por el `SLURM_ARRAY_JOB_ID`, que es el ID del job array.

* `%a`: Se reemplaza por el `SLURM_ARRAY_TASK_ID`, que corresponde al índice 
de la tarea en el array.

El formato predeterminado para la salida de un job array es:
```
slurm-%A_%a.out
```

>**Ejemplo: Definiendo Nombres de Archivos**
>```
>sbatch -o slurm-%A_%a.out --array=1-3 -N1 script.sh
>```
>
>Esto generará los siguientes archivos de salida:
>
>    * slurm-XX_1.out
>    * slurm-XX_2.out
>    * slurm-XX_3.out
>
>Donde `XX` es el ID del job array.

```admonish note title="NOTA"
Si se utiliza `%A` y `%a` sin estar en un job array:

* `%A` se reemplaza por el Job ID.
* `%a` se reemplaza por `4294967294` (`0xfffffffe` o `NO_VAL`).
```


>**Ejemplo: Script con Nombres de Archivos Personalizados**
>```bash
>#!/bin/bash
>#SBATCH --job-name=array_example
>#SBATCH --output=output_%A_%a.out
>#SBATCH --error=error_%A_%a.err
>#SBATCH --array=0-3
>
>echo "Job Array ID: $SLURM_ARRAY_JOB_ID"
>echo "Task ID: $SLURM_ARRAY_TASK_ID"
>echo "Procesando tarea con índice $SLURM_ARRAY_TASK_ID"
>```
>
>Ejecuta el script con:
>```bash
>sbatch array_example.sh
>```
>
>Esto creará archivos de salida y error con el formato:
>
>* `output_<JobID>_<TaskID>.out`
>* `error_<JobID>_<TaskID>.err`

## Cancelando Job Arrays con scancel.

El comando `scancel` permite cancelar:

* Todo el job array.
* Tareas específicas en el array.
* Tareas utilizando expresiones regulares.

**Cancelar Todo el Job Array**
```bash
scancel <JobID>
```

**Cancelar Tareas Específicas**
```bash
# Cancela las tareas con índices 1 a 3 del array con Job ID 20
scancel 20_[1-3]

# Cancela las tareas con índices 4 y 5 del array con Job ID 20
scancel 20_4 20_5
```

**Cancelar desde Dentro de un Script**

Si se desea cancelar el trabajo actual desde un script, se puede usar la 
siguiente lógica:
```bash
if [[ -z $SLURM_ARRAY_JOB_ID ]]; then
scancel $SLURM_JOB_ID
else
scancel ${SLURM_ARRAY_JOB_ID}_${SLURM_ARRAY_TASK_ID}
fi
```
Este enfoque verifica si se está ejecutando dentro de un job array o no.
