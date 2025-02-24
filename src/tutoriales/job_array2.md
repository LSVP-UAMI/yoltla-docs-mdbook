# Job Array

Los Job Arrays en Slurm son una herramienta poderosa que permite enviar y 
gestionar colecciones de trabajos similares de manera rápida y eficiente. Con 
los Job Arrays, es posible enviar millones de tareas en milisegundos (sujeto a 
los límites de tamaño configurados). Todos los trabajos en un Job Array deben 
tener las mismas opciones iniciales (por ejemplo, tamaño, límite de tiempo, 
etc.), aunque es posible modificar algunas de estas opciones después de que el 
trabajo haya comenzado su ejecución utilizando el comando `scontrol.`

<!--
En este tutorial, exploraremos cómo utilizar Job Arrays en Slurm, incluyendo 
cómo enviar trabajos, gestionar variables de entorno, y utilizar comandos como 
`scancel` y `squeue` para gestionar y monitorear los Job Arrays.
-->
## Enviar un Job Array

Para enviar un Job Array, se utiliza el comando `sbatch` con la opción 
`--array` o `-a.` Esta opción permite especificar los índices del array, que 
pueden ser valores específicos, un rango de valores, o un rango con un tamaño 
de paso.

><center>
>
> **Ejemplos de uso**
></center>
>
>**1. Índices consecutivos**
>
>```bash
>sbatch --array=0-31 -N1 script.sh
>```
>Este comando envía un array con índices de 0 a 31, utilizando un nodo 
>(`-N1`) por tarea.

>**2. Índices específicos**
>
>```bash
>sbatch --array=1,3,5,7 -N1 script.sh
>```
>Este ejemplo ejecuta el script solo para los índices 1, 3, 5, y 7.

>**3. Rango con paso**
>
>```bash        
>sbatch --array=1-7:2 -N1 script.sh
>```
>En este caso, se ejecuta el script para los índices 1, 3, 5, y 7, 
>con un paso de tamaño 2.

>**4. Limitando tareas simultáneas**
>
>```bash
>sbatch --array=0-15%4 -N1 script.sh
>```
>Esto limita el número de tareas simultáneas a 4, lo que puede ser útil para 
>controlar el uso de recursos.

## Variables de Entorno en Job Arrays

Cuando se ejecuta un Job Array, Slurm establece varias variables de entorno 
que pueden ser útiles para gestionar y diferenciar las tareas dentro del array:

* `SLURM_ARRAY_JOB_ID`: El ID del primer trabajo en el array.
* `SLURM_ARRAY_TASK_ID`: El índice de la tarea actual dentro del array.
* `SLURM_ARRAY_TASK_COUNT`: El número total de tareas en el array.
* `SLURM_ARRAY_TASK_MAX`: El índice más alto en el array.
* `SLURM_ARRAY_TASK_MIN`: El índice más bajo en el array.

><center>
>
>**Ejemplo de Variables de Entorno**
></center>
>
>Supongamos que enviamos un Job Array con el siguiente comando:
>```bash
>$ sbatch --array=1-3 -N1 scrip.sh
>```
>
>Si Slurm responde con:
>```bash
>Submitted batch job 36
>```
>
>Las variables de entorno para cada tarea serán:
>```bash
>Tarea 1:
>    SLURM_JOB_ID=36
>    SLURM_ARRAY_JOB_ID=36
>    SLURM_ARRAY_TASK_ID=3
>    SLURM_ARRAY_TASK_COUNT=3
>    SLURM_ARRAY_TASK_MAX=3
>    SLURM_ARRAY_TASK_MIN=1
>
>Tarea 2: 
>    SLURM_JOB_ID=37
>    SLURM_ARRAY_JOB_ID=36
>    SLURM_ARRAY_TASK_ID=1
>    SLURM_ARRAY_TASK_COUNT=3
>    SLURM_ARRAY_TASK_MAX=3
>    SLURM_ARRAY_TASK_MIN=1
>
>Tarea 3: 
>    SLURM_JOB_ID=38
>    SLURM_ARRAY_JOB_ID=36
>    SLURM_ARRAY_TASK_ID=2
>    SLURM_ARRAY_TASK_COUNT=3
>    SLURM_ARRAY_TASK_MAX=3
>    SLURM_ARRAY_TASK_MIN=1
>```    

## Nombres de Archivos de Salida

Slurm permite personalizar los nombres de los archivos de salida (stdout, 
stderr) utilizando los siguientes placeholders:

* `%A`: Será reemplazado por el valor de `SLURM_ARRAY_JOB_ID`.
* `%a`: Será reemplazado por el valor de `SLURM_ARRAY_TASK_ID`.

**Ejemplo de Uso**
```bash
$ sbatch -o slurm-%A_%a.out --array=1-3 -N1 script.sh
```

Esto generará archivos de salida con los nombres:

* `slurm-36_1.out`
* `slurm-36_2.out`
* `slurm-36_3.out`


## Cancelar Job Arrays con scancel

El comando `scancel` permite cancelar Job Arrays de manera selectiva o completa.

><center>
>
>**Ejemplos de uso**
></center>
>
>**1. Cancelar tareas específicas de un Job Array:**
>```bash
>$ scancel 20_[1-3]  # Cancela las tareas 1, 2 y 3 del Job Array 20
>$ scancel 20_4 20_5 # Cancela las tareas 4 y 5 del Job Array 20
>```
>
>**2. Cancelar todas las tareas de un Job Array:**
>```bash
>$ scancel 20  # Cancela todas las tareas del Job Array 20
>```
>
>**3. Cancelar la tarea actual (útil en scripts):**
>```bash
>if [[ -z $SLURM_ARRAY_JOB_ID ]]; then
>    scancel $SLURM_JOB_ID
>else
>    scancel ${SLURM_ARRAY_JOB_ID}_${SLURM_ARRAY_TASK_ID}
>fi
>```


## Monitorear Job Arrays con squeue

El comando `squeue` permite monitorear los Job Arrays. Por defecto, muestra 
todas las tareas de un Job Array en una sola línea, pero también se puede 
mostrar una tarea por línea.

><center>
>
>**Ejemplos de Uso**
></center>
>
>**1. Mostrar todas las tareas de un Job Array en una línea:**
>```bash
>$ squeue
>JOBID     PARTITION  NAME  USER  ST  TIME  NODES NODELIST(REASON)
>1080_[5-1024]  debug   tmp   mac  PD  0:00      1 (Resources)
>1080_1         debug   tmp   mac   R  0:17      1 tux0
>1080_2         debug   tmp   mac   R  0:16      1 tux1
>1080_3         debug   tmp   mac   R  0:03      1 tux2
>1080_4         debug   tmp   mac   R  0:03      1 tux3
>```
>
>**2. Mostrar una tarea por línea:**
>```bash
>$ squeue -r
>JOBID PARTITION  NAME  USER  ST  TIME  NODES NODELIST(REASON)
>1082_3     debug   tmp   mac  PD  0:00      1 (Resources)
>1082_4     debug   tmp   mac  PD  0:00      1 (Priority)
>1080     debug   tmp   mac   R  0:17      1 tux0
>1081     debug   tmp   mac   R  0:16      1 tux1
>1082_1     debug   tmp   mac   R  0:03      1 tux2
>1082_2     debug   tmp   mac   R  0:03      1 tux3
>```
>
>**3. Filtrar por tareas específicas:**
>```bash
>$ squeue -j 1234_2,1234_3
>```

# Falta agregar las opciones de formato -j, -s y las opciones %F, %k

## Comando scontrol con Job Arrays

El comando `scontrol` permite gestionar y modificar trabajos en Slurm. 
Cuando se trabaja con Job Arrays, `scontrol` permite mostrar y actualizar 
información específica de los arrays, así como realizar operaciones 
como suspender, reanudar o modificar tareas individuales.

### Mostrar Información de Job Arrays

Al usar `scontrol show job`, se muestran dos nuevos campos relacionados con 
Job Arrays:

* `JobID`: Identificador único del trabajo.
* `ArrayJobID`: El JobID del primer elemento del Job Array.
* `ArrayTaskID`: El índice de la tarea dentro del array (puede ser un número 
único o un rango).

Estos campos solo se muestran si el trabajo es parte de un Job Array.

**Ejemplo**
```bash
$ scontrol show job 21845_2
```

Esto mostrará detalles específicos de la tarea 2 del Job Array 21845.


### Modificar Trabajos en un Job Array

Se puede modificar todos los elementos de un Job Array especificando solo el 
`ArrayJobID`, o modificar tareas individuales usando `ArrayJobID_ArrayTaskID`.

><center>
>
>**Ejemplos de uso**
></center>
>
>**1. Cambiar el nombre de una tarea específica:**
>```bash
>$ scontrol update JobID=21845_2 name=arturo
>```
>
>**2. Suspender todas las tareas de un Job Array:**
>```bash
>$ scontrol suspend 21845
>```
>
>**3. Reanudar una tarea específica:**
>```bash
>$ scontrol resume 21845_3
>```
>
>**4. Reanudar todas las tareas de un Job Array:**
>```bash
>    $ scontrol resume 21845
>```


## Dependencias entre Job Arrays

Slurm permite definir dependencias entre trabajos, incluyendo Job Arrays. Las 
dependencias se pueden establecer para esperar a que un Job Array completo o 
tareas específicas finalicen antes de ejecutar otro trabajo.

**Tipos de Dependencias**

* **after:** El trabajo se ejecuta después de que todas las tareas del Job Array 
hayan comenzado.

* **afterany:** El trabajo se ejecuta después de que todas las tareas del Job 
Array hayan finalizado.

* **aftercorr:** El trabajo se ejecuta después de que la tarea correspondiente en 
el Job Array haya finalizado exitosamente.

* **afterok:** El trabajo se ejecuta después de que todas las tareas del Job Array 
hayan finalizado exitosamente.

* **afternotok:** El trabajo se ejecuta después de que todas las tareas del Job 
Array hayan finalizado, y al menos una haya fallado.

><center>
>
>**Ejemplos de uso**
></center>
>
>**1. Esperar a que una tarea específica finalice:**
>```bash
>$ sbatch --depend=after:123_4 my.job
>```
>
>**2. Esperar a que varias tareas específicas finalicen exitosamente:**
>```bash
>    $ sbatch --depend=afterok:123_4:123_8 my.job2
>```
>
>**3. Esperar a que todo el Job Array finalice:**
>```bash
>$ sbatch --depend=afterany:123 my.job
>```
>
>**4. Esperar a que todo el Job Array finalice exitosamente:**
>```bash
>$ sbatch --depend=afterok:123 my.job
>```
>
>**5. Esperar a que todo el Job Array finalice y al menos una tarea falle:**
>```bash
>$ sbatch --depend=afternotok:123 my.job
>```

## Otros Comandos y Consideraciones

Algunos comandos de Slurm no reconocen Job Arrays directamente y requieren el 
uso de Job IDs únicos para cada tarea. Estos comandos incluyen:

* **sbcast**
* **sprio**
* **sreport**
* **sshare**
* **sstat**

Por otro lado, los siguientes comandos han sido modificados para soportar Job 
Arrays:

* **sacct:** Permite especificar Job IDs o elementos de Job Arrays.
* **sattach:** Permite adjuntarse a tareas específicas de un Job Array.
* **strigger:** Permite definir triggers para Job Arrays.
* **sview:** Muestra los campos `ArrayJobId` y `ArrayTaskId` (o "N/A" si no es un Job 
Array).


## Administración del Sistema

### Configuración de Job Arrays

Slurm introduce un parámetro de configuración llamado `MaxArraySize`, que 
controla el tamaño máximo de un Job Array.

* El índice mínimo que un usuario puede especificar es 0.
* El índice máximo es `MaxArraySize` - 1.
* El valor predeterminado de `MaxArraySize` es 1001.
* El valor máximo soportado es 4000001.

Es importante tener en cuenta este parámetro, ya que los Job Arrays permiten a 
los usuarios enviar grandes cantidades de trabajos rápidamente.

### Optimización del Planificador

El plugin `sched/backfill` ha sido modificado para mejorar el rendimiento con 
Job Arrays. Si un elemento del Job Array no es ejecutable o afecta la 
planificación de otros trabajos, los elementos restantes se omiten rápidamente.

### Escalabilidad

Slurm crea un único registro de trabajo cuando se envía un Job Array. Los 
registros adicionales se crean solo cuando es necesario, generalmente cuando 
una tarea comienza a ejecutarse. Esto proporciona un mecanismo escalable para 
gestionar grandes cantidades de trabajos.


<!-- Paguina por revisar slurm
https://documentation-its-umich-edu.translate.goog/node/4986?_x_tr_sl=en&_x_tr_tl=es&_x_tr_hl=es&_x_tr_pto=tc
-->