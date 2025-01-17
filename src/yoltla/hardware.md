# Hardware

## Componentes principales del Cluster Yoltla

A continuación se describe detalladamente los componentes principales de
Yoltla.

### Nodo maestro 

El nodo Maestro es el encargado de recibir todas las peticiones de los
usuarios para poder distribuir las tareas a cada uno de los nodos
esclavo. A continuación se resumen las principales características del
nodo maestro:

**Nodo Maestro, Dell, PowerEdge R720**
| **Procesador** | **Memoria** | **Disco Duro** | **Comunicaciones** |
|----------------|-------------|----------------|--------------------|
| 2 x E5-2695 v2 a 2.40GHz | 96 GB en RAM | - 2 HD 15 K RPM SAS 600 GB<br> - 4 HD 7.2 K RPM NL-SAS 1 TB | 2 Tarjetas Mellanox ConnectX-3 VPI, single-port QSFP, FDR 10 IB (40Gb/s) |

### Nodos de acceso 

Los nodos de acceso se utilizarán para que los usuarios accedan al
sistema, transfieran y respalden información; así como la compilación de
aplicaciones. Estos tienen las siguientes características:

**Nodo Login, Dell, PowerEdge R720**
| **Procesador** | **Memoria** | **Disco Duro** | **Comunicaciones** |
|----------------|-------------|----------------|--------------------|
| 2 x E5-2695 v2 a 2.40GHz | 96 GB en RAM | - 2 HD 2.5" 15 K RPM SAS 600 GB<br> - 2 HD 2.5" 7.2 K RPM NL-SAS 1 TB | 2 Tarjetas Mellanox ConnectX-3 VPI, single-port QSFP, FDR 10 IB (40Gb/s) |

### Nodos de cómputo Intel Xeon E5-2670v2 (nodos nc) 

Los nodos de procesamiento son los encargados de ejecutar las
solicitudes del maestro, y están asignados única y exclusivamente al
procesamiento de datos, a continuación se muestran sus principales
características:

**Nodo de Procesamiento, Dell, PowerEdge C6220 II**
| **Procesador** | **Memoria** | **Disco Duro** | **Comunicaciones** |
|----------------|-------------|----------------|--------------------|
| 2 x E5-2670 v2 a 2.50GHz | 64 GB en RAM | - 1 HD 3.5" 7.2 K RPM NL-SAS 1 TB | 1 Tarjeta Mellanox ConnectX-3 VPI, single-port QSFP, FDR 10 IB (40Gb/s) |

### Nodos de cómputo Intel Xeon E5-2660v3 (nodos tt) 

**Nodo de Procesamiento, Dell, PowerEdge FC430**
| **Procesador** | **Memoria** | **Disco Duro** | **Comunicaciones** |
|----------------|-------------|----------------|--------------------|
| 2 x E5-2660 v3 a 2.60GHz | 128 GB en RAM | HD 1.8\* SSD 200 GB | 1 puerto infiniband FDR14 56 Gbps. |


### Nodos de cómputo Intel Xenon E5-2670 v2 (nodos ngk) 
**Nodo de Procesamiento, Dell, PowerEdge C6220 II**
| **Procesador** | **Memoria** | **Disco Duro** | **Comunicaciones** |
|----------------|-------------|----------------|--------------------|
| 2 x Xeon E5-2670 v2 a 2.50GHz | 64 GB en RAM |ST1000NM0033-9ZM HDD 1TB, 7.2k RPM, 6Gb/s. 3.5¨ | 1 Tarjeta Mellanox MT27500 (ConnectX-3) DR/40 GbE | 


### Nodos de cómputo Intel Xenon Gold 6140 (nodos ngv) 
**Nodo de Procesamiento, Supermicro, SYS-1029GQ-TVRT**
| **Procesador** | **Memoria** | **Disco Duro** | **Comunicaciones** |
|----------------|-------------|----------------|--------------------|
| 2 x Xeon Gold 6140 a 2.30GHz | 128 GB en RAM| - MZ7KM240HMHQ0D3 SSD 240GB, 6Gb/s, 2.5¨<br> - ST1000NX0423 HDD 1TB, 7.2k RPM, 6Gb/s, 2.5¨ | 1 Tarjeta Mellanox MT27500 (ConnectX-3) |



### Nodos de cómputo AMD EPYC 7513 (nodos ncz) 

**Nodo de Procesamiento, Dell, PowerEdge C6525**
| **Procesador** | **Memoria** | **Disco Duro** | **Comunicaciones** |
|----------------|-------------|----------------|--------------------|
| 2 x AMD EPYC 7513 a 3.9GHz | 512 GB en RAM | DELLBOSS VD HDD, 500 GB | 1 Tarjeta Mellanox MT28908 (ConnectX-6) |  




## Sistema de almacenamiento Lustre de 96TB 

El sistema Lustre se integra por un servidor MGS, dos servidores MDS y
siete servidores OSS, todos los servidores son del tipo Dell poweredge
R720. Complementa el sistema LUSTRE un arreglo de discos de
almacenamiento Dell PowerVault MD3220. A continuación se describen cada
uno de estos componentes.

### Servidor MGS (Management Server) 

En la siguiente Tabla se muestran las principales características del
Servidor MGS.

**Servidor MGS(Management Server), Dell, PowerEdge R720**
| **Procesador** | **Memoria** | **Disco Duro** | **Comunicaciones** |
|----------------|-------------|----------------|--------------------|
| 2 x E5-2670 v2 a 2.50 GHz | 80 GB en RAM | 2 HD 2.5" 15 K RPM SAS 300 GB | 2 Tarjetas Mellanox ConnectX-3 VPI, single-port QSFP, FDR 10 IB (40Gb/s) |


### Servidores MDS (Meta Data Servers) {#_servidores_mds_meta_data_servers}

En la siguiente Tabla se muestran las principales características del
Servidor MDS.

**Servidor MGS(Management Server), Dell, PowerEdge R720**
| **Procesador** | **Memoria** | **Disco Duro** | **Comunicaciones** |
|----------------|-------------|----------------|--------------------|
| 2 x E5-2670 v2 a 2.50 GHz | 80 Gb en RAM | - 2 HD 2.5" 15 K RPM SAS 300 GB<br> - 2 HD 2.5" 10 K RPM SAS 600 GB | 2 Tarjetas Mellanox ConnectX-3 VPI, single-port QSFP, FDR 10 IB (40Gb/s) |

Los Servidores MDS, están conectadas a un sistema de almacenamiento
MD3220.

```admonish note tittle="NOTA"
El arreglo MD3220 se integra por 24 discos SAS SFF de 300 GB de
capacidad y 15K RPM.
```

**Sistema de Almacenamiento, Dell, PowerVault MD3220**
| **Disco Duro** |
|----------------|
| 24 HD 2.5" 15 K RPM SAS 300 GB                                        |

### Servidores OSS (Object Storage Servers) {#_servidores_oss_object_storage_servers}

En la siguiente Tabla se muestran las principales características de los
servidores OSS.

**Servidor MGS(Management Server), Dell, PowerEdge R720**
| **Procesador** | **Memoria** | **Disco Duro** | **Comunicaciones** |
|----------------|-------------|----------------|--------------------|
| 2 x E5-2670 v2 a 2.50 GHz | 80 GB en RAM | - 2 HD 2.5" 15 K RPM SAS 300 GB<br> - 22 HD 2.5" 15 K RPM SAS 600 GB<br> - 2 HD 2.5 " SSD 100 GB | 1 Tarjeta Mellanox ConnectX-3 VPI, single-port QSFP, FDR 10 IB (40Gb/s) |

## Sistema de comunicaciones de baja latencia infiniband 

Los nodos de Yoltla nc se interconectan utilizando redes Infiniband y
Ethernet. Los requisitos del rendimiento de interconexión son
satisfechos por el Switch Mellanox SX6512. En la siguiente Tabla se
muestran las principales características del Switch.

**Switch Mellanox SX6512**
| **Descripción** |
|-----------------|
| El switch tiene una capacidad de crecimiento de 216 puertos |
| La solución de conectividad tiene 216 puertos en uso        |
| Conectividad punto a punto de 40 Gb/s                       |
| El switch soporta una capacidad de 24.2 Tb/s de rendimiento y con una latencia menor a 1 microsegundo |

Los nodos de Yoltla Nodos tt se interconectan utilizando redes
Infiniband y Ethernet. Los requisitos del rendimiento de interconexión
son satisfechos por 2 switches infiniband marca Mellanox modelo SX6025F.
En la siguiente Tabla se muestran las principales características del
Switch.

**Switch Mellanox SX6025F**
| **Descripción** |
|-----------------|
| Los switches tiene una capacidad de crecimiento de 36 puertos |
| La solución de conectividad tiene 58 puertos utilizables      |
| Conectividad punto a punto de 56 Gb/s                         |
