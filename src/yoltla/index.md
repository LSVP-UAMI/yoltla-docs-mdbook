
# Yoltla

El cluster Yoltla se integra por 1 nodo maestro, 2 nodos de acceso, 292
nodos de procesamiento, 1 sistema de almacenamiento tipo Lustre de 96TB
y comunicaciones de alta velocidad Infiniband FDR10/FDR. 

- **2014**
    * Ampliación de capacidad: Adquisición de 1600 núcleos de procesamiento 
    y 64 coprocesadores gráficos.

    * Capacidad total: 152 TF de procesamiento.

    * Innovación: Incorporación de GPGPU, permitiendo abordar problemas 
    complejos gracias a su arquitectura.

- **2015**
    * Incremento de potencia: Añadidos 48.2 TF Rmax a la capacidad de 
    procesamiento.

    * Nueva tecnología: Introducción de estándares de alta densidad 
    (4 nodos de procesamiento por unidad de rack).

    * Componentes:

        * 3760 núcleos Intel Xeon E5-2670 v2 (2.5 GHz) en 188 nodos, 
        con 12.032 TB de RAM distribuida.

        * 1160 núcleos Intel Xeon E5-2660 v3 (2.6 GHz) en 58 nodos, 
        con 7.424 TB de RAM distribuida.

- **2016**
    * 1432 núcleos Intel Xeon E5-2683 v4 (2.1 GHz) en 46 nodos, con 
    11.776 TB de RAM distribuida.
    
- **20__**
    * 1728 núcleos AMD EPYC 7513 32-Core (2.59 GHz) en 27 nodos, con 
    13.5 TB de RAM distribuida.

<!--
Los nodos de
procesamiento están basados en arquitectura Intel Xeon, se cuenta con
3760 núcleos de procesamiento tipo Intel Xeon Processor E5-2670 v2 de
2.5 Ghz distribuidos en 188 nodos de procesamiento con 12.032 TB de
memoria RAM distribuida. 1160 núcleos de procesamiento tipo Intel Xeon
Processor E5-2660 v3 de 2.6 Ghz distribuidos en 58 nodos de
procesamiento con 7.424 TB de memoria RAM distribuida. En 2016 se han
agregado 1432 núcleos de procesamiento tipo Intel Xeon Processor
E5-2683v4 de 2.1GHz distribuidos en 46 nodos de procesamiento con 11.776
TB de memoria RAM distribuida.
-->

El sistema operativo instalado en Yoltla está basado en Linux Enterprise
6 y Linux Enterprise 7.

***Tabla 1. Nodos del clúster Yoltla***
| **Tipo** | **Nombre** | **Cantidad** | **Descripción** | 
|:--------:|:----------:|:------------:|-----------------|
| Nodo de cómputo nc | nc[1-120] | 120 | 20 CPUs Intel Xeón E5-2670v2, 64GB RAM | 
| Nodo de cómputo ngk | ngk[1-24] | 24 | 20 CPUs Intel Xeon E5-2670 v2, 64GB RAM|
| Nodo de cómputo nvg | ngv[1-3] | 3 | 36 CPUs Intel Xeon Gold 6140, 128GB RAM  |
| Nodo de cómputo tt | tt[1-58] | 58 | 20 CPUs Intel Xenón E5-2660v3, 128GB RAM | 
| Nodo de cómputo tt | tt[59-96] | 38 | 32 CPUs Intel Xenón E5-2660v4, 128GB RAM | 
| Nodo de cómputo ncz | ncz[1-27] | 27 | 64 CPUs AMD EPYC 7513 32-Core, 512GB RAM |



***Tabla 1. Nodos del clúster Yoltla***
| **Tipo** | **Nombre** | **Cantidad** | **Descripción** | 
|:--------:|:----------:|:------------:|-----------------|
| Nodo de cómputo nc | nc[1-4, 7-56, 61-104, 113-156, 165-176] | 154  | 20 CPUs Intel Xeón E5-2670v2, 64GB RAM |
| Nodo de cómputo nc con GPU | nc[5, 6, 57-60,<br> 105-112, 157-164] | 22 | 20 CPUs Intel Xeón E5-2670v2, 64GB RAM<br><br> - 2 nodos con 8 GPUs K20<br> - 4 nodos con 4 GPUs K20<br> - 16 nodos con 2 GPUs |K20\ |
| Nodo de cómputo nc con VGPU | nc[177-179] | 3 | 36 CPUs <br><br> - 2 nodos con 2 GPUs, 128GB RAM<br> - 1 nodo con 4 GPUs, 256GB RAM |
| Nodo de cómputo tt | tt[1-58] | 58 | 20 CPUs Intel Xenón E5-2660v3, 128GB RAM | 
| Nodo de cómputo tt v4 | tt[59-104] | 46 | 32 CPUs Intel Xeon E5-2683v4, 256GB RAM |
| Nodo de cómputo ncz | ncz[1-27] | 27 | 64 CPUs AMD EPYC 7513 32-Core, 512GB RAM |



