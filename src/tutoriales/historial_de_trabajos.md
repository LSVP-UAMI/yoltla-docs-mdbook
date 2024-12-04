# Historial de trabajos

## Consultar el historial de trabajos

Para consultar su historial de trabajos, utilice el siguiente comando:
```
    sacct
```

A continuación se muestra un ejemplo de la salida del comando `sacct`:
```
    [pepe@yoltla0 ~]$ sacct
        JobID    JobName  Partition    Account  AllocCPUS      State ExitCode
    ------------ ---------- ---------- ---------- ---------- ---------- --------
    817539       prueba_ga+    q1d-20p       pepe         20     FAILED      1:0 
    817539.batch      batch                  pepe         20     FAILED      1:0
    817540       prueba_ga+    q1d-20p       pepe         20     FAILED      1:0 
    817540.batch      batch                  pepe         20     FAILED      1:0
    817543       script_ga+    q1h-20p       pepe         20    RUNNING      0:0 

```

En la siguiente tabla se da una descripción de los campos que conforman la salida anterior:


|   Campo     |   Descripción  |
|-------------|----------------|
|   JobID     | Número de identificación del trabajo. |
|   JobName   | Nombre del trabajo.            |
|   Partition | Partición asignada al trabajo. |
|   Account   | Nombre de la cuenta bajo la que se ejecutó el trabajo.|
|   AllocCPUS | Número de CPUs asignados al trabajo.|
|   State     | Estado del trabajo.            |
|   ExitCode  | Código de salida del trabajo.  |

```admonish tip title="TIP"
Puede utilizar la opción `-X` para que solo se muestren las estadísticas relevantes 
de sus trabajos, sin tomar en consideración los pasos de los mismos:

    [pepe@yoltla0 ~]$ sacct -X
        JobID    JobName  Partition    Account  AllocCPUS      State ExitCode
    ------------ ---------- ---------- ---------- ---------- ---------- --------
    817539       prueba_ga+    q1d-20p       pepe         20     FAILED      1:0 
    817540       prueba_ga+    q1d-20p       pepe         20     FAILED      1:0 
    817543       script_ga+    q1h-20p       pepe         20    RUNNING      0:0 
```

## Filtrar el historial de trabajos

Por defecto, al ejecutar el comando `sacct` solo se mostrarán sus
trabajos del día actual, sin embargo, puede utilizar diferentes opciones
con este comando para poder filtrar su historial de trabajos:

|   Opción                   |      Descripción             |
|----------------------------|------------------------------|   
| --jobs=\<lista de IDs>     | Muestra todos los trabajos cuyo ID coincida con alguno de los indicados en la lista. |
| --name=<lista de nombres>  | Muestra todos los trabajos cuyo nombre coincida con alguno de los indicados en la lista. |
| --state=<lista de estados> |  Muestra todos los trabajos cuyo estado coincida con alguno de los indicados en la lista (ver sección [Job State Codes](../anexos/anexos.md#job-state-codes)). |
| --partition=<lista de particiones> | Muestra todos los trabajos cuya partición coincida con alguna de las indicadas en la lista (ver sección [Recursos de cómputo](../anexos/anexos.md#recursos-de-cómputo)). |
| --starttime=AAAA-MM-DD     | Muestra todos los trabajos que fueron enviados a partir de la fecha indicada. |
| --endtime=AAAA-MM-DD       | Muestra todos los trabajos que fueron enviados antes de la fecha indicada. |

Por ejemplo, para consultar todos los trabajos cuyo nombre sea
*simulacion*, tengan el estado *COMPLETED* o *FAILED*, y hayan sido
enviados entre el *01/04/2021* y el *01/05/2021*, ejecute el comando:
```
[pepe@yoltla0 ~]$ sacct -X --name=simulacion --state=COMPLETED,FAILED --starttime=2021-04-01 --endtime=2021-05-01
        JobID    JobName  Partition    Account  AllocCPUS      State ExitCode
------------ ---------- ---------- ---------- ---------- ---------- --------
776552       simulacion    q1h-20p       pepe         20     FAILED      2:0
787047       simulacion    q1h-20p       pepe         20  COMPLETED      0:0
790569       simulacion    q1h-20p       pepe         20  COMPLETED      0:0
```

## Dar formato al historial de trabajos

Además de poder filtrar su historial de trabajos, también puede indicar el formato en 
que se muestra esta información. Utilice la opción `--format` para indicar que campos 
(ver sección [Job Accounting Fields](../anexos/anexos.md#job-accounting-fields)) desea 
que se desplieguen en la salida del comando `sacct`:
```
    sacct --format=<lista de campos>
```

```admonish tip title="TIP"
Puede imprimir la lista de todos los campos que se pueden especificar en la opción 
`--format`, utilizando el comando `sacct` seguido de la opción `-e`:

       sacct -e
```

Por ejemplo, para consultar los campos *JobID*, *JobName*, *State* y *NodeList*, de todos 
sus trabajos del día actual, que se encuentran en estado *RUNNING*, ejecute el comando:

```
[pepe@yoltla0 ~]$  sacct -X --format=JobID,JobName,State,NodeList --state=RUNNING
    JobID    JobName      State        NodeList
------------ ---------- ---------- ---------------
817543       script_ga+    RUNNING            nc87
```

Para obtener más información de este comando, consulte la página [sacct](https://slurm.schedmd.com/sacct.html) 
de la documentación oficial de SLURM.