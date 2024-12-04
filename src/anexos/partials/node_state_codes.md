+-------+--------------------------------------------------------------+
| E     | Descripción                                                  |
| stado |                                                              |
+=======+==============================================================+
| \*    | El nodo no responde. No se le asignarán nuevos trabajos.     |
+-------+--------------------------------------------------------------+
| allo  | El nodo tiene asignado uno o más trabajos.                   |
| cated |                                                              |
+-------+--------------------------------------------------------------+
| compl | Todos los trabajos asociados con este nodo están en proceso  |
| eting | de finalización.                                             |
+-------+--------------------------------------------------------------+
| down  | El nodo no está disponible para su uso. SLURM puede colocar  |
|       | automáticamente los nodos en este estado si ocurre alguna    |
|       | falla.                                                       |
+-------+--------------------------------------------------------------+
| dr    | El nodo no está disponible para su uso por solicitud del     |
| ained | administrador del sistema.                                   |
+-------+--------------------------------------------------------------+
| dra   | El nodo está ejecutando un trabajo actualmente, pero no se   |
| ining | le asignarán nuevos trabajos. El estado del nodo cambiará a  |
|       | *drained* cuando se complete el último trabajo.              |
+-------+--------------------------------------------------------------+
| idle  | El nodo no tiene ningún trabajo asignado y está disponible   |
|       | para su uso.                                                 |
+-------+--------------------------------------------------------------+
| mixed | El nodo tiene algunos recursos disponibles para su uso y     |
|       | otros asignados a uno o más trabajos.                        |
+-------+--------------------------------------------------------------+
