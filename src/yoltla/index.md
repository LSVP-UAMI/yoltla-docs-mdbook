El cluster Yoltla se integra por 1 nodo maestro, 2 nodos de acceso, 292
nodos de procesamiento, 1 sistema de almacenamiento tipo Lustre de 96TB
y comunicaciones de alta velocidad Infiniband FDR10/FDR. Los nodos de
procesamiento están basados en arquitectura Intel Xeon, se cuenta con
3760 núcleos de procesamiento tipo Intel Xeon Processor E5-2670 v2 de
2.5 Ghz distribuidos en 188 nodos de procesamiento con 12.032 TB de
memoria RAM distribuida. 1160 núcleos de procesamiento tipo Intel Xeon
Processor E5-2660 v3 de 2.6 Ghz distribuidos en 58 nodos de
procesamiento con 7.424 TB de memoria RAM distribuida. En 2016 se han
agregado 1432 núcleos de procesamiento tipo Intel Xeon Processor
E5-2683v4 de 2.1GHz distribuidos en 46 nodos de procesamiento con 11.776
TB de memoria RAM distribuida.\
El sistema operativo instalado en Yoltla está basado en Linux Enterprise
6 y Linux Enterprise 7.

+-----------------+-------------+------+-------------------------------+
| Tipo            | Nombre      | Cant | Descripción                   |
|                 |             | idad |                               |
+=================+=============+======+===============================+
| Nodo de cómputo | nc\[1-4,    | 154  | 20 CPUs Intel Xeón E5-2670v2, |
| nc              | 7-56,       |      | 64GB RAM                      |
|                 | 61-104,     |      |                               |
|                 | 113-156,    |      |                               |
|                 | 165-176\]   |      |                               |
+-----------------+-------------+------+-------------------------------+
| Nodo de cómputo | nc\[5, 6,   | 22   | 20 CPUs Intel Xeón E5-2670v2, |
| nc con GPU      | 57-60,      |      | 64GB RAM\                     |
|                 | 105-112,    |      | - 2 nodos con 8 GPUs K20\     |
|                 | 157-164\]   |      | - 4 nodos con 4 GPUs K20\     |
|                 |             |      | - 16 nodos con 2 GPUs K20\    |
+-----------------+-------------+------+-------------------------------+
| Nodo de cómputo | nc          | 3    | 36 CPUs\                      |
| nc con VGPU     | \[177-179\] |      | - 2 nodos con 2 GPUs, 128GB   |
|                 |             |      | RAM\                          |
|                 |             |      | - 1 nodo con 4 GPUs, 256GB    |
|                 |             |      | RAM                           |
+-----------------+-------------+------+-------------------------------+
| Nodo de cómputo | tt\[1-58\]  | 58   | 20 CPUs Intel Xeón E5-2660v3, |
| tt              |             |      | 128GB RAM                     |
+-----------------+-------------+------+-------------------------------+
| Nodo de cómputo | t           | 46   | 32 CPUs Intel Xeon E5-2683v4, |
| tt v4           | t\[59-104\] |      | 256GB RAM                     |
+-----------------+-------------+------+-------------------------------+

: Nodos del clúster Yoltla
