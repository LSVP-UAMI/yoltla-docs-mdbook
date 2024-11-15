# Componentes principales del Cluster Yoltla {#_componentes_principales_del_cluster_yoltla}

A continuación se describe detalladamente los componentes principales de
Yoltla.

## Nodo maestro {#_nodo_maestro}

El nodo Maestro es el encargado de recibir todas las peticiones de los
usuarios para poder distribuir las tareas a cada uno de los nodos
esclavo. A continuación se resumen las principales características del
nodo maestro:

**Nodo Maestro, Dell, PowerEdge R720**

+-----------------------------------------------------------------------+
| Procesador                                                            |
+-----------------------------------------------------------------------+
| Memoria                                                               |
+-----------------------------------------------------------------------+
| Disco Duro                                                            |
+-----------------------------------------------------------------------+
| Comunicaciones                                                        |
+-----------------------------------------------------------------------+
| 2 x E5-2695 v2 a 2.40GHz                                              |
+-----------------------------------------------------------------------+
| 96 GB en RAM                                                          |
+-----------------------------------------------------------------------+
| 2 HD 15 K RPM SAS 600 GB\                                             |
| 4 HD 7.2 K RPM NL-SAS 1 TB                                            |
+-----------------------------------------------------------------------+
| 2 Tarjetas Mellanox ConnectX-3 VPI, single-port QSFP, FDR 10 IB       |
| (40Gb/s)                                                              |
+-----------------------------------------------------------------------+

## Nodos de acceso {#_nodos_de_acceso}

Los nodos de acceso se utilizarán para que los usuarios accedan al
sistema, transfieran y respalden información; así como la compilación de
aplicaciones. Estos tienen las siguientes características:

**Nodo Login, Dell, PowerEdge R720**

+-----------------------------------------------------------------------+
| Procesador                                                            |
+-----------------------------------------------------------------------+
| Memoria                                                               |
+-----------------------------------------------------------------------+
| Disco Duro                                                            |
+-----------------------------------------------------------------------+
| Comunicaciones                                                        |
+-----------------------------------------------------------------------+
| 2 x E5-2695 v2 a 2.40GHz                                              |
+-----------------------------------------------------------------------+
| 96 GB en RAM                                                          |
+-----------------------------------------------------------------------+
| 2 HD 2.5" 15 K RPM SAS 600 GB\                                        |
| 2 HD 2.5" 7.2 K RPM NL-SAS 1 TB                                       |
+-----------------------------------------------------------------------+
| 2 Tarjetas Mellanox ConnectX-3 VPI, single-port QSFP, FDR 10 IB       |
| (40Gb/s)                                                              |
+-----------------------------------------------------------------------+

## Nodos de cómputo Intel Xeon E5-2670v2 (nodos nc) {#_nodos_de_cómputo_intel_xeon_e5_2670v2_nodos_nc}

Los nodos de procesamiento son los encargados de ejecutar las
solicitudes del maestro, y están asignados única y exclusivamente al
procesamiento de datos, a continuación se muestran sus principales
características:

**Nodo de Procesamiento, Dell, PowerEdge C6220 II**

+-----------------------------------------------------------------------+
| Procesador                                                            |
+-----------------------------------------------------------------------+
| Memoria                                                               |
+-----------------------------------------------------------------------+
| Disco Duro                                                            |
+-----------------------------------------------------------------------+
| Comunicaciones                                                        |
+-----------------------------------------------------------------------+
| 2 x E5-2670 v2 a 2.50GHz                                              |
+-----------------------------------------------------------------------+
| 64 GB en RAM                                                          |
+-----------------------------------------------------------------------+
| 1 HD 3.5" 7.2 K RPM NL-SAS 1 TB                                       |
+-----------------------------------------------------------------------+
| 1 Tarjeta Mellanox ConnectX-3 VPI, single-port QSFP, FDR 10 IB        |
| (40Gb/s)                                                              |
+-----------------------------------------------------------------------+

## Nodos de cómputo Intel Xeon E5-2660v3 (nodos tt) {#_nodos_de_cómputo_intel_xeon_e5_2660v3_nodos_tt}

**Nodo de Procesamiento, Dell, PowerEdge FC430**

+-----------------------------------------------------------------------+
| Procesador                                                            |
+-----------------------------------------------------------------------+
| Memoria                                                               |
+-----------------------------------------------------------------------+
| Disco Duro                                                            |
+-----------------------------------------------------------------------+
| Comunicaciones                                                        |
+-----------------------------------------------------------------------+
| 2 x E5-2660 v3 a 2.60GHz                                              |
+-----------------------------------------------------------------------+
| 128 GB en RAM                                                         |
+-----------------------------------------------------------------------+
| HD 1.8\* SSD 200 GB                                                   |
+-----------------------------------------------------------------------+
| 1 puerto infiniband FDR14 56 Gbps.                                    |
+-----------------------------------------------------------------------+

# Sistema de almacenamiento Lustre de 96TB {#_sistema_de_almacenamiento_lustre_de_96tb}

El sistema Lustre se integra por un servidor MGS, dos servidores MDS y
siete servidores OSS, todos los servidores son del tipo Dell poweredge
R720. Complementa el sistema LUSTRE un arreglo de discos de
almacenamiento Dell PowerVault MD3220. A continuación se describen cada
uno de estos componentes.

## Servidor MGS (Management Server) {#_servidor_mgs_management_server}

En la siguiente Tabla se muestran las principales características del
Servidor MGS.

**Servidor MGS(Management Server), Dell, PowerEdge R720**

+-----------------------------------------------------------------------+
| Procesador                                                            |
+-----------------------------------------------------------------------+
| Memoria                                                               |
+-----------------------------------------------------------------------+
| Disco Duro                                                            |
+-----------------------------------------------------------------------+
| Comunicaciones                                                        |
+-----------------------------------------------------------------------+
| 2 x E5-2670 v2 a 2.50 GHz                                             |
+-----------------------------------------------------------------------+
| 80 GB en RAM                                                          |
+-----------------------------------------------------------------------+
| 2 HD 2.5" 15 K RPM SAS 300 GB                                         |
+-----------------------------------------------------------------------+
| 2 Tarjetas Mellanox ConnectX-3 VPI, single-port QSFP, FDR 10 IB       |
| (40Gb/s)                                                              |
+-----------------------------------------------------------------------+

## Servidores MDS (Meta Data Servers) {#_servidores_mds_meta_data_servers}

En la siguiente Tabla se muestran las principales características del
Servidor MDS.

**Servidor MGS(Management Server), Dell, PowerEdge R720**

+-----------------------------------------------------------------------+
| Procesador                                                            |
+-----------------------------------------------------------------------+
| Memoria                                                               |
+-----------------------------------------------------------------------+
| Disco Duro                                                            |
+-----------------------------------------------------------------------+
| Comunicaciones                                                        |
+-----------------------------------------------------------------------+
| 2 x E5-2670 v2 a 2.50 GHz                                             |
+-----------------------------------------------------------------------+
| 80 GB en RAM                                                          |
+-----------------------------------------------------------------------+
| 2 HD 2.5" 15 K RPM SAS 300 GB\                                        |
| 2 HD 2.5" 10 K RPM SAS 600 GB                                         |
+-----------------------------------------------------------------------+
| 2 Tarjetas Mellanox ConnectX-3 VPI, single-port QSFP, FDR 10 IB       |
| (40Gb/s)                                                              |
+-----------------------------------------------------------------------+

Los Servidores MDS, están conectadas a un sistema de almacenamiento
MD3220.

:::: note
::: title
:::

El arreglo MD3220 se integra por 24 discos SAS SFF de 300 GB de
capacidad y 15K RPM.
::::

**Sistema de Almacenamiento, Dell, PowerVault MD3220**

+-----------------------------------------------------------------------+
| Disco Duro                                                            |
+-----------------------------------------------------------------------+
| 24 HD 2.5" 15 K RPM SAS 300 GB                                        |
+-----------------------------------------------------------------------+

## Servidores OSS (Object Storage Servers) {#_servidores_oss_object_storage_servers}

En la siguiente Tabla se muestran las principales características de los
servidores OSS.

**Servidor MGS(Management Server), Dell, PowerEdge R720**

+-----------------------------------------------------------------------+
| Procesador                                                            |
+-----------------------------------------------------------------------+
| Memoria                                                               |
+-----------------------------------------------------------------------+
| Disco Duro                                                            |
+-----------------------------------------------------------------------+
| Comunicaciones                                                        |
+-----------------------------------------------------------------------+
| 2 x E5-2670 v2 a 2.50 GHz                                             |
+-----------------------------------------------------------------------+
| 80 GB en RAM                                                          |
+-----------------------------------------------------------------------+
| 2 HD 2.5" 15 K RPM SAS 300 GB\                                        |
| 22 HD 2.5" 15 K RPM SAS 600 GB\                                       |
| 2 HD 2.5 " SSD 100 GB                                                 |
+-----------------------------------------------------------------------+
| 1 Tarjeta Mellanox ConnectX-3 VPI, single-port QSFP, FDR 10 IB        |
| (40Gb/s)                                                              |
+-----------------------------------------------------------------------+

# Sistema de comunicaciones de baja latencia infiniband {#_sistema_de_comunicaciones_de_baja_latencia_infiniband}

Los nodos de Yoltla nc se interconectan utilizando redes Infiniband y
Ethernet. Los requisitos del rendimiento de interconexión son
satisfechos por el Switch Mellanox SX6512. En la siguiente Tabla se
muestran las principales características del Switch.

**Switch Mellanox SX6512**

+-----------------------------------------------------------------------+
| Descripción                                                           |
+-----------------------------------------------------------------------+
| El switch tiene una capacidad de crecimiento de 216 puertos           |
+-----------------------------------------------------------------------+
| La solución de conectividad tiene 216 puertos en uso                  |
+-----------------------------------------------------------------------+
| Conectividad punto a punto de 40 Gb/s                                 |
+-----------------------------------------------------------------------+
| El switch soporta una capacidad de 24.2 Tb/s de rendimiento y con una |
| latencia menor a 1 microsegundo                                       |
+-----------------------------------------------------------------------+

Los nodos de Yoltla Nodos tt se interconectan utilizando redes
Infiniband y Ethernet. Los requisitos del rendimiento de interconexión
son satisfechos por 2 switches infiniband marca Mellanox modelo SX6025F.
En la siguiente Tabla se muestran las principales características del
Switch.

**Switch Mellanox SX6025F**

+-----------------------------------------------------------------------+
| Descripción                                                           |
+-----------------------------------------------------------------------+
| Los switches tiene una capacidad de crecimiento de 36 puertos         |
+-----------------------------------------------------------------------+
| La solución de conectividad tiene 58 puertos utilizables              |
+-----------------------------------------------------------------------+
| Conectividad punto a punto de 56 Gb/s                                 |
+-----------------------------------------------------------------------+
