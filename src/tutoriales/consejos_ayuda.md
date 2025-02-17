# Cómo escribir buenas solicitudes de soporte

Redactar solicitudes de soporte de manera adecuada no solo beneficia al 
equipo de soporte, sino también a usted. Dado que los equipos de administración 
reciben numerosas solicitudes de ayuda, el tiempo disponible para comprender 
cada problema es limitado. Cuanto más clara y detallada sea su solicitud, más 
rápido podremos asistirle.

A continuación, se presentan algunas buenas prácticas a considerar:


## Envíe sus solicitudes de soporte a través de los canales adecuados

Es importante enviar las solicitudes de soporte a la dirección de correo 
correspondiente (<soporte.lsvp@gmail.com>), ya que de esta manera 
los miembros del personal podrán gestionarlas de manera eficiente. Tenga 
en cuenta que algunos miembros del equipo pueden estar disponibles para 
brindar soporte solo de manera parcial. Al utilizar el canal principal, 
se asegura de que su solicitud sea atendida oportunamente.


## Investigue antes de enviar una solicitud

Antes de contactar al equipo de soporte, considere realizar una búsqueda 
en línea utilizando el mensaje de error exacto y el nombre de la aplicación 
en la que experimentó el problema. Es posible que otros usuarios ya hayan 
enfrentado una situación similar y encontrado una solución.


## Utilice un asunto descriptivo

Es recomendable que la línea de asunto de su correo electrónico sea clara
y específica. Por ejemplo, un asunto como “Problema en el Clúster” es 
demasiado general, ya que podría aplicarse a casi cualquier solicitud de 
soporte que recibimos. Tenga en cuenta que el equipo de soporte trabaja 
de manera colaborativa, y la línea de asunto es lo primero que vemos. 
Utilizar un asunto preciso nos ayuda a clasificar y priorizar las 
solicitudes de manera más eficiente, incluso antes de abrir el correo 
electrónico.


## Incluya comandos y mensajes de error exactos

Este punto se detalla más adelante, pero su importancia justifica mencionarlo
aquí: asegúrese de incluir el comando exacto que ejecutó y el mensaje de 
error completo. La mejor forma de hacerlo es copiar y pegar el texto directamente 
en el correo electrónico.

Le pedimos amablemente que evite enviar capturas de pantalla de su terminal SSH 
(en formatos como jpg, png, tiff, etc.), ya que no podemos copiar ni pegar comandos 
ni mensajes de error desde una imagen. Esto dificulta y retrasa innecesariamente 
el proceso de análisis y solución del problema. No se preocupe por el formato 
estético del texto; lo importante es que podamos trabajar con la información de 
manera eficiente.


## Cree un nuevo correo electrónico para cada problema

Por favor, no responda a correos electrónicos de problemas anteriores para reportar
un nuevo inconveniente, especialmente si no están relacionados. Cada problema tiene 
un número de identificación único que aparece en la línea de asunto. Si responde 
en un hilo no relacionado, su solicitud podría archivarse incorrectamente, lo que 
incrementa el riesgo de que pase desapercibida.


## Evite el problema XY

El problema XY ocurre cuando se solicita ayuda para una solución (Y) sin explicar 
el problema original (X) que se desea resolver. Esto puede llevar a malentendidos y a 
una pérdida de tiempo significativa.

En términos sencillos (según lo descrito en el Problema XY):

* Usted desea lograr X.

* No sabe cómo hacerlo, pero cree que podría resolverlo si logra hacer Y.

* Tiene dificultades con Y y solicita ayuda para Y, sin mencionar X.

* Las personas intentan ayudarle con Y, pero resulta confuso porque Y no parece 
un problema relevante.

* Después de mucha interacción, finalmente se descubre que el objetivo real era X, 
y que Y no era la mejor manera de lograrlo.
    
Para evitar esta situación, explique siempre su objetivo final (X), incluso si 
necesita ayuda con un paso intermedio (Y). Esto nos permitirá proporcionarle una 
solución más adecuada y efectiva.


## Informe también sobre lo que ha funcionado

Es de gran ayuda que nos proporcione contexto sobre lo que ha funcionado hasta el 
momento. Por ejemplo, si informa que “X no funciona en dos nodos”, sería útil saber 
si funcionó en un solo nodo, en un solo núcleo o si este es su primer intento de 
ejecución. Esta información nos ayuda a identificar el origen del problema y a evitar 
un intercambio extenso de correos electrónicos para obtener detalles adicionales.

Agradecemos su colaboración al proporcionarnos esta información detallada, ya que 
nos permite brindarle un soporte más ágil y efectivo.


## Especifique su entorno

Para ayudarnos a diagnosticar su problema de manera eficiente, es importante que 
proporcione detalles sobre su entorno de trabajo. Por ejemplo, ¿usted o alguien 
de su equipo compiló el código? ¿Qué módulos se cargaron durante la ejecución?

Si utiliza módulos que no son los predeterminados o que usted mismo ha definido, 
asegúrese de informarlo en su solicitud. Si esta información no se incluye, 
podríamos estar intentando reproducir el problema en un entorno diferente, lo 
que retrasaría el proceso de solución.


## Casos simples: Sea específico, incluya comandos y mensajes de error

Para facilitar la resolución de su problema, evite descripciones vagas como 
“X no funcionó”. En su lugar, proporcione detalles precisos:

* Indique exactamente los comandos que ejecutó.

* Describa el entorno en el que se ejecutaron (véase el punto anterior).

* Incluya el mensaje de error completo.

Los mensajes de error son fundamentales para el diagnóstico. Siempre que sea 
posible, copie y pegue toda la salida en texto en lugar de resumirla. Cuanto 
más clara y detallada sea su descripción, menos preguntas adicionales 
necesitaremos hacer, lo que agilizará la respuesta.

En muchos casos, con solo ver el mensaje de error real, podemos proporcionarle 
una solución inmediata. Para problemas más complejos, es recomendable asegurarse 
de que el problema pueda reproducirse de manera consistente.


## Casos complejos: Cree un ejemplo reproducible

Si su problema es más avanzado, intente proporcionar un ejemplo mínimo que 
podamos ejecutar directamente para replicarlo. De lo contrario, el equipo de 
soporte tendría que interpretar su descripción y generar archivos de entrada 
o scripts desde cero, lo que podría generar demoras.

Le recomendamos compartir un ejemplo que podamos copiar, pegar y ejecutar 
fácilmente. No accederemos a archivos protegidos sin su permiso, por lo que
cualquier información relevante debe ser proporcionada explícitamente.


## Haga el ejemplo lo más pequeño y rápido posible

Si el problema ocurre en un cálculo que tarda una semana en fallar, le 
sugerimos intentar reducir el caso antes de enviar la solicitud de soporte. 
A menudo, es posible reproducir el problema utilizando un ejemplo más pequeño, 
como un sistema reducido o una configuración simplificada.

Esto tiene múltiples ventajas:

* Facilita y acelera el proceso de diagnóstico y solución.

* Permite realizar pruebas más rápidas, ya que el problema se reproduce 
en menos tiempo.

Si bien entendemos que esto puede requerir un esfuerzo adicional, le agradecemos 
su colaboración, ya que permite crear una solicitud de soporte más útil y 
eficiente. Además, al aislar el problema, es posible que identifique la causa 
o solución antes de enviar la solicitud.

[HPCWIKI: How to write good support requests](https://hpc-wiki.info/hpc/How_to_write_good_support_requests)