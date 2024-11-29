# Eficiencia de trabajos

## Consultar el informe de eficiencia

Puede consultar el informe de eficiencia de un trabajo con el comando `seff` seguido 
del ID del trabajo:
```
    seff <ID del trabajo>
```

```admonish note title="NOTA"
No se recomienda el uso del comando `seff` en trabajos fallidos o en ejecución, ya 
que puede reportar información errónea.
```

Por ejemplo, para consultar el informe de eficiencia del trabajo con ID 888872, 
ejecute el comando:
```
[pepe@yoltla0 ~]$ seff 888872
Job ID: 888872
Cluster: yoltla
User/Group: c.553/edra
State: COMPLETED (exit code 0)
Nodes: 1
Cores per node: 20
CPU Utilized: 05:53:51
CPU Efficiency: 99.96% of 05:54:00 core-walltime
Job Wall-clock time: 00:17:42
Memory Utilized: 53.33 GB
Memory Efficiency: 88.89% of 60.00 GB
```
A continuación se da una breve explicación de algunos de los campos de la salida anterior:

-   El tiempo de CPU (*core-walltime*) es la cantidad de tiempo que la CPU dedicó al 
    trabajo. Por ejemplo, si un trabajo se ejecutó durante una 1 hora en 20 CPUs, 
    entonces habrá usado 20 horas de CPU.

-   La eficiencia de CPU (*CPU Efficiency*) es la relación del tiempo de CPU utilizado 
    (*CPU Utilized*) y el tiempo de CPU.

-   La eficiencia de memoria (*Memory Efficiency*) es la relación de la cantidad de 
    memoria utilizada (*Memory Utilized*) y la cantidad de memoria solicitada.

En este este ejemplo, el trabajo se ejecutó durante 17 minutos y 42 segundos en 20 CPUs, 
por lo que su tiempo de CPU es de 5 horas con 54 minutos, pero el tiempo de CPU utilizado 
es de 5 horas con 53 minutos y 51 segundos, por lo tanto, la eficiencia de CPU es del 99.96%. 
La cantidad de memoria solicitada fue de 60.00 GB, pero la cantidad de memoria utilizada 
fue de 53.33 GB, por lo tanto, la eficiencia de memoria es del 88.89%.

```admonish warning title="IMPORTANTE"
Para obtener el informe de la eficiencia de la memoria es necesario utilizar la directiva:

        --mem=#

en su script de SLURM, de lo contrario el valor reportado será el siguiente:

        Memory Efficiency: 0.00% of 0.00 MB (0.00 MB/node)
```