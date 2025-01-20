# Preguntas frecuentes

## SLURM

### ¿Qué es SLURM?

Es un sistema de código abierto para manejar recursos de clústeres. Es
tolerante a fallas y es altamente escalable para clústeres de Linux
grandes y pequeños.

### ¿Qué versión de SLURM está intalada en el clúster?

La versión 17.11.5.

## Trabajos

### ¿Qué es un trabajo?

SLURM da el nombre de trabajo (job) a los recursos de cómputo (nodos con
sus correspondientes cores) asignados a un usuario por un determinado
periodo de tiempo.

### ¿Comó envío un trabajo?

Utilice el comando `sbatch` seguido del nombre de su script:
``` 
sbatch <nombre del script>
```

Para obtener más información, consulte la sección 
[Enviar un trabajo](../tutoriales/envio_y_administracion_de_trabajos.md#enviar-un-trabajo).

### ¿Comó consulto un trabajo?

Utilice el comando `squeue` seguido de la opción `-j` y el ID de su
trabajo:
```
squeue -j <ID del trabajo>
```

Para obtener más información, consulte la sección 
[Consultar un trabajo](../tutoriales/envio_y_administracion_de_trabajos.md#consultar-un-trabajo).

### ¿Comó cancelo un trabajo?

Utilice el comando `scancel` seguido del ID de su trabajo:
```
scancel <ID del trabajo>
```

Para obtener más información, consulte la sección 
[Cancelar un trabajo](../tutoriales/envio_y_administracion_de_trabajos.md#cancelar-un-trabajo).

### ¿Qué son los Job State Codes?

Son códigos que identifican el estado de un trabajo.
Para obtener más información, consulte la sección 
[Job State Codes](../anexos/anexos.md#job-state-codes).

### ¿Qué son los Job Reason Codes?

Son códigos que identifican la razón por la que un trabajo está
esperando su ejecución.
Para obtener más información, consulte la sección 
[Job Reason Codes](../anexos/anexos.md#job-reason-codes).

## Aplicaciones

### ¿Qué es un módulo?

Es un archivo que contiene la información necesaria para configurar el
shell para una aplicación.

### ¿Comó listo las módulos del clúster?

Utilice el comando `module` seguido del subcomando `avail`:
```
module avail
```

Para obtener más información, consulte la sección 
[Listar los módulos del clúster](../tutoriales/aplicaciones_del_cluster.md#listar-los-módulos-del-clúster).

### ¿Comó cargo un módulo?

Utilice el comando `module` seguido del subcomando `load` y el nombre
del módulo a cargar:
```
module load <módulo>
```

Para obtener más información, consulte la sección 
[Cargar un módulo](../tutoriales/aplicaciones_del_cluster.md#cargar-un-módulo).

### ¿Comó listo todos los módulos cargados?

Utilice el comando `module` seguido del subcomando `list`:
```
module list
```

Para obtener más información, consulte la sección 
[Listar los módulos cargados](../tutoriales/aplicaciones_del_cluster.md#listar-los-módulos-cargados).

### ¿Comó descargo un módulo?

Utilice el comando `module` seguido del subcomando `unload` y el nombre
del módulo a descargar:
```
module unload <módulo>
```

Para obtener más información, consulte la sección 
[Descargar un módulo](../tutoriales/aplicaciones_del_cluster.md#descargar-un-módulo).

### ¿Comó descargo todos los módulos cargados?

Utilice el comando `module` seguido del subcomando `purge`:
```
module purge
```

Para obtener más información, consulte la sección 
[Descargar todos los módulos cargados](../tutoriales/aplicaciones_del_cluster.md#descargar-todos-los-módulos-cargados).
