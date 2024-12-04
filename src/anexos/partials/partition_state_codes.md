+------+---------------------------------------------------------------+
| Es   | Descripción                                                   |
| tado |                                                               |
+======+===============================================================+
| up   | La partición está disponible para su uso. Se pueden enviar y  |
|      | ejecutar trabajos.                                            |
+------+---------------------------------------------------------------+
| down | La partición no está disponible para su uso. Se pueden enviar |
|      | trabajos, pero no se ejecutarán ni se les asignarán recursos. |
|      | Los trabajos que ya se están ejecutando continúan             |
|      | ejecutándose.                                                 |
+------+---------------------------------------------------------------+
| d    | La partición no está disponible para su uso. No se pueden     |
| rain | enviar trabajos, pero los trabajos que ya están en cola       |
|      | podrán solicitar recursos y ejecutarse.                       |
+------+---------------------------------------------------------------+
| i    | La partición se encuentra inactiva. No se pueden enviar       |
| nact | trabajos. Los trabajos que ya están en la cola no se les      |
|      | asignarán recursos ni se ejecutarán.                          |
+------+---------------------------------------------------------------+
