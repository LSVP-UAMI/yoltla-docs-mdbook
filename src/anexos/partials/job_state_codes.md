
| **Código** | **Estado** | **Descripción** |
|------------|------------|-----------------|
| CA | CANCELLED | El trabajo fue cancelado explícitamente por el usuario o el administrador del sistema. El trabajo puede haberse iniciado o no. |
| CD | COMPLETED | El trabajo ha terminado todos los procesos en todos los nodos. |
| CF | CONFIGURING | Se han asignado recursos al trabajo, pero aún no están listos para su uso. |
| CG | COMPLETING | El trabajo está en proceso de finalización. Es posible que algunos procesos en algunos nodos aún estén activos. |
| F | FAILED | El trabajo terminó con una condición de falla. |
| NF | NODE_FAIL |El trabajo terminó debido a la falla de uno o más nodos asignados. |
| PD | PENDING | El trabajo está esperando la asignación de recursos. |
| R | RUNNING | El trabajo se está ejecutando. |
| TO | TIMEOUT | El trabajo finalizó al alcanzar su límite de tiempo. |
