# Envío y administración de trabajos

## Enviar un trabajo

Para enviar un trabajo, utilice el comando `sbatch` seguido del nombre de su script:
```
    sbatch <nombre del script>
```

Por ejemplo, para enviar el script _hola_mundo.slrm_, ejecute el comando:
```
    [pepe@yoltla0 ~]$ sbatch hola_mundo.slrm 
    Submitted batch job 787047
```

Cada trabajo tiene un identificar único, este identificador le permite consultar, actualizar 
o cancelar el trabajo. En este ejemplo, el número _787047_ es el identificador del trabajo.

Para obtener más información de este comando, consulte la página [sbatch](https://slurm.schedmd.com/sbatch.html) 
de la documentación oficial de SLURM.

## Consultar un trabajo

Para consultar un trabajo en el clúster, utilice el comando `squeue` seguido de la opción 
`-j` y el ID de su trabajo:
```
    squeue -j <ID del trabajo>
```

```admonish tip title="TIP"
Para consultar varios trabajos con un solo comando, use el formato:

    squeue -j <ID del trabajo 1>,<ID del trabajo 2>,<ID del trabajo 3>,....
```

```admonish tip title="TIP"
Para consultar todos sus trabajos, utilice el comando `squeue` seguido de la opción
 `-u` y su nombre de usuario:

    squeue -u <nombre de usuario>
```

Por ejemplo, para consultar el trabajo con ID 786836, ejecute el comando:
```
[pepe@yoltla0 ~]$ squeue -j 786836
            JOBID PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON)
            786836   q1h-20p ley_coul     pepe PD       0:00      1 (Resources)
```

En la siguiente tabla se da una descripción de los campos que conforman la salida anterior:

|   **Campo**   |   **Descripción**     |
|---------------|-----------------------|
|   JOBID       |   ID del trabajo.     |
|   PARTITION   |   Partición asignada al trabajo.  |
|   NAME        |   Nombre del trabajo. |
|   USER        |   Nombre del usuario que envió el trabajo.  |
|   ST          |   Estado del trabajo (ver sección [Job State Codes](./anexos.md#job-state-codes)). |
|   TIME        |   Tiempo de ejecución del trabajo.  |
|   NODES       |   Número de nodos asignados al trabajo.  |
|   NODELIST(REASON)  | Razón por la que el trabajo está esperando su ejecución(ver sección [Job Reason Codes](./anexos.md#job-reason-codes)).<br>Nodos en que se ejecuta el trabajo.  |

```admonish note title="NOTA"
Si ejecuta el comando `squeue` sin ninguna opción, se mostrarán todos los trabajos 
que se encuentran actualmente en el clúster:

    [pepe@yoltla0 ~]$ squeue
        JOBID PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON)
        752085 tt1d-128p simulaci   c.3925  R   18:56:03      4 tt[95-98]
        783540   q1d-20p  energia   c.8417  R      50:09      1 nc18
        783055  q12h-80p fisica_c   c.5553  R    5:37:45      4 nc[69,131,133-134]
        783545   q4d-40p biologia   c.6547 PD       0:00      2 (Resources)
            .         .        .        .  .          .      .                  .    
            .         .        .        .  .          .      .                  .    
            .         .        .        .  .          .      .                  .    
```

Para obtener más información de este comando, consulte la página [squeue](https://slurm.schedmd.com/squeue.html) 
de la documentación oficial de SLURM.

## Cancelar un trabajo

Para cancelar un trabajo, utilice el comando `scancel` seguido del ID del trabajo:
```
    scancel <ID del trabajo>
```
Al utilizar el comando `scancel` no obtendrá ningún mensaje por parte del sistema.

```admonish tip title="TIP"
Para cancelar varios trabajos con un solo comando, use el formato:
    
    scancel <ID del trabajo 1>,<ID del trabajo 2>,<ID del trabajo 3>,...
```

Por ejemplo, para cancelar el trabajo con ID 786836, ejecute el comando:
```
    [pepe@yoltla0 ~]$ scancel 786836
```

```admonish note title="NOTA"
Solo el usuario propietario del trabajo puede cancelarlo.
```

Para obtener más información de este comando, consulte la página [scancel](https://slurm.schedmd.com/scancel.html) 
de la documentación oficial de SLURM.