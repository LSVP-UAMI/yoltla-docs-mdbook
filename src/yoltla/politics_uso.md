Con el propósito de organizar jerárquicamente las cuentas de los
usuarios existen tres tipos de cuentas:

1.  **Usuario investigador**: Usuario responsable de hacer la petición a
    la comisión de supercómputo para acceder a Yoltla.

2.  **Usuario colaborador**: usuario con permisos para acceder a Yoltla
    a petición del usuario investigador. Ejemplos de usuario
    colaborador: postdocs, o investigadores de otras instituciones.

3.  **Usuario alumno**: este tipo de usuario se asignará a los
    estudiantes que trabajan con un usuario Investigador el cual tendrá
    acceso a Yoltla a petición del usuario investigador.

Los usuarios colaboradores y alumnos, tienen asignado su directorio HOME
dentro del directorio de trabajo del usuario investigador. El usuario
investigador tiene permisos para acceder/modificar la información de sus
alumnos y colaboradores.

Las cuotas son un mecanismo que permite administrar el almacenamiento,
establece límites en la cantidad de información almacenada por usuario o
grupo de usuarios. Estos límites son determinados por número de archivos
(*inodos*) y espacio utilizado (*Kilobytes*).

La capacidad de nuestro de sistema de almacenamiento Lustre es finito
por lo que se establecen **cuotas** por grupo. Un grupo está integrado
por un usuario investigador, sus *alumnos* y *colaboradores*.

+-------------+-------------+-------------+-------------+-------------+
| Descripción | Elementos   | Directorio  | Tamaño      | Número de   |
|             | del grupo   |             |             | archivos    |
+-------------+-------------+-------------+-------------+-------------+
| Cuota por   | Usuario:    | HOME        | 2 TB        | 2           |
| grupo en    | In          |             |             | 000,000/por |
| home de     | vestigador, |             |             | grupo       |
| Lustre      | Alumnos y   |             |             |             |
|             | Co          |             |             |             |
|             | laboradores |             |             |             |
+-------------+-------------+-------------+-------------+-------------+
| Cuota por   | Usuario     | \~/tmp      | \-          | \-          |
| usuario en  |             |             |             |             |
| \~/tmp de   |             |             |             |             |
| Lustre      |             |             |             |             |
+-------------+-------------+-------------+-------------+-------------+

La información almacenada en el *\~/tmp*, tendrá un periodo de vida de
60 días, pasado ese tiempo, los archivos serán eliminados.

Si requiere más de 30 minutos para compilar sus aplicaciones en los
nodos de acceso comuníquese con el personal del LSVP. Scripts,
compilaciones y/o aplicaciones que requieran capacidades multi-threads
serán eliminados sin previo aviso.

Es importante recordar que "**cada usuario es responsable de su
información**", se han implementando mecanismos para apoyar a los
usuarios en el respaldo de su información. La infraestructura de
almacenamiento Lustre de Yoltla está compuesta de elementos RAID de
niveles 6 y 10 para tolerar fallas, aunque esto no es garantía de no
sufrir percances.

Se recomienda respaldar los resultados de cada ejecución de forma
periódica. Recuerde que la información en el \~/tmp tiene un tiempo de
vida de 60 días. El directorio de trabajo de todos los usuarios se
encuentra en un subdirectorio de la base /LUSTRE/home, en esta ruta no
se tiene un tiempo de vida establecido, pero se recomienda respaldar su
información a través de los nodos de acceso. Cuando considere que la
información que va a respaldar es "demasiada" o el tiempo de
transferencia es largo, informe a los administradores del LSVP para
obtener ayuda.

Se cuenta con el nodo de acceso yoltla1 para realizar tareas de
respaldo. Se recomienda utilizar el comando *rsync* para transferencias,
también puede hacer uso de *scp* y *sftp*. Para mejorar la velocidad de
transferencia empaquete sus archivos con la herramienta *tar* o el
compresor *gzip*.

Para obtener soporte relacionado con apertura de cuentas, modificación
de características de usuarios en el uso de la infraestructura de
Supercómputo y almacenamiento, dudas en políticas de uso de la
Infraestructura y validación de aplicaciones, dirigirse con el
coordinador académico del LSVP, Dr. Joel Ireta Moreno (correo
electrónico: <iret@xanum.uam>).

Para obtener soporte relacionado con ejecución, instalación y errores de
aplicaciones, respaldo y transferencia de archivos y/o información,
conectividad, acceso, problemas con infraestructura física o atención
personalizada, envíe un correo a <soporte.lsvp@gmail.com>.
