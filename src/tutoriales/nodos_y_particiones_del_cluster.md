# Nodos y particiones del clúster

Los nodos (recursos de cómputo) del clúster están agrupados en particiones. Cada una de 
estas particiones tiene diferentes características, como el tiempo máximo de uso o el 
número de CPUs que pueden utilizarse. 

## Consultar las particiones del clúster

Para consultar las particiones disponibles en el clúster, utilice el siguiente comando:
```
sinfo -o "%.10P %.6a %.11l %.6D %.5c %N"
```

A continuación se muestra de manera parcial la salida de este comando:
```
    [pepe@yoltla0 ~]$ sinfo -o "%.10P %.6a %.11l %.6D %.5c %N"
     PARTITION  AVAIL   TIMELIMIT  NODES  CPUS NODELIST
      q1h-20p*     up     1:00:00    154    20 nc[1-4,7-56,61-104,113-156,165-176]
       q1d-20p     up  1-00:00:00    154    20 nc[1-4,7-56,61-104,113-156,165-176]
       q4d-20p     up  4-00:00:00    154    20 nc[1-4,7-56,61-104,113-156,165-176]
       q7d-20p     up  7-00:00:00    154    20 nc[1-4,7-56,61-104,113-156,165-176]
       q1h-40p     up     1:00:00    154    20 nc[1-4,7-56,61-104,113-156,165-176]
             .      .           .      .     .                                   .
             .      .           .      .     .                                   .
             .      .           .      .     .                                   .
```

En la siguiente tabla se da una descripción de los campos que conforman la salida anterior:

|   **Campo**   |   **Descripción** |
|---------------|-------------------|
|   PARTITION   |   Nombre de la partición.|
|   AVAIL       |   Estado de la partición.|
|   TIMELIMIT   |   Tiempo máximo de ejecución para cualquier trabajo.|
|   NODES       |   Número de nodos en la partición.|
|   CPUS        |   Número de CPUs por nodo.|
|   NODELIST    |   Lista de nodos que conforman la partición.|

```admonish note title="NOTA"
El `*` (asterisco) que sigue al nombre de una partición, indica que es la partición 
predeterminada para el envío de trabajos.
```

Para obtener más información de este comando, consulte la página [sinfo](https://slurm.schedmd.com/sinfo.html) 
de la documentación oficial de SLURM.

## Buscar una partición disponible

Para buscar una partición disponible en el clúster, utilice la aplicación `yoltla_pool` 
del módulo *yoltla/beta*. 

Para cargar el módulo *yoltla/beta*, utilice el siguiente comando:
```
module load yoltla/beta
```

Posteriormente, para ejecutar la aplicación `yoltla_pool`, utilice el comando:
```
yoltla_pool
```

A continuación se da un ejemplo de la salida de este comando:
```
    [pepe@yoltla0 ~]$ module load yoltla/beta
    [pepe@yoltla0 ~]$ yoltla_pool
    Particiones por tipo de nodo:
    ===========================================
    NC         TTv1        TTv2       GPU   VGPU
    -------    ---------   ---------  ----  ------
    q1h-20p    tt2d-80p    tt2d-64p   gpus  vgpus
    q1d-20p    tt2d-100p   tt1d-128p
    q4d-20p    tt1d-160p   tt1d-256p
    q7d-20p    tt12h-320p  tt1d-512p
    q1h-40p
    q1d-40p
    q4d-40p
    q4d-80p
    q1h-80p
    q12h-80p
    q1d-80p
    q1h-160p
    q12h-160p
    q1d-160p
    q1h-320p
    q12h-320p
    q1d-320p

    Estado actual:
    =====================================
    TIPO    JOBS_PENDIENTES  NODOS_LIBRES
    ------  ---------------  ------------
    nc      44               15
    ttv1    0                4
    ttv2    1                2
    gpu     2                1
    vgpu    0                2
```

En la parte superior se muestra una tabla  con todas las particiones disponibles en el 
clúster agrupadas por tipo de nodo. Las particiones que se encuentran en la misma 
columna comparten nodos.

En la parte inferior, por tipo de nodo, se muestra una tabla con los trabajos pendientes 
y los nodos libres. Se puede observar que en algunas filas existen trabajos pendientes y 
nodos libres al mismo tiempo, existen dos razones principales para esto:

1.  Los trabajos solicitan una gran cantidad de recursos y están en espera de que estos 
    estén disponibles.

2.  Algunos usuarios han alcanzado el nivel máximo de trabajos corriendo al mismo tiempo.

```admonish note title="NOTA"
La cuota máxima de trabajos corriendo al mismo tiempo es  2,000,000 minutos de CPU por grupo.
```

En este ejemplo, las particiones con nodos tipo TTv1 no tienen ningún trabajo pendiente, 
y además, hay 4 nodos libres de este tipo, por lo que cualquier trabajo que se envíe, 
se ejecutará de manera inmediata, tomando en cuenta las restricciones antes mencionadas.