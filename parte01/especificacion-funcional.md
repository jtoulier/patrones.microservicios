![Alquicleta](../images/alquicleta.png "Alquicleta")

# Especificación Funcional

## Levantamiento de información

**Alquicleta** es un servicio de alquiler de bicicletas ofrecidos de manera online a través de una página web.

Como parte del levantamiento de información, en nuestra conversación con el dueño del negocio, tuvimos una entrevista y recopilamos las funcionalidades principales.

Queda claro que estamos en las etapas iniciales del proyecto y las notas presentadas aún no están estructuradas ni ordenadas. Hasta es posible que algunas no estén del todo claras.

Los requerimientos han sido divididos en dos grupos iniciamente:
* Requerimientos funcionales
* Requerimientos no funcionales

### Requerimientos funcionales
* El servicio será gratuito, pues es una iniciativa municipal.
* Los usuarios finales, aquellos que se inscriben con el fin de alquilar una bicicleta, serán llamados **cleteros**
* Los *cleteros* podrán autoafiliarse al servicio ingresando sus datos personales como nombres, dirección, DNI, correo electrónico y un número de teléfono celular. Solo el correo electrónico será validado como parte del proceso de darse de alta. En una futura fase deberá validarse el número de teléfono celular mediante un mensaje SMS.
* El usuario administrador del sistema tendrá una opción para crear y mantener:
  * Relación de bicicletas (ID, modelo, color, estado [disponible, reservada, en uso, en revisión, desactivada])
  * Relación de estaciones (nombre, dirección, estado [abierta, cerrada], tiempo de tolerancia de inicio de alquiler)
* Para reservar una bicicleta, el *cletero* ingresará a la página web, colocará como datos obligatorios la estación origen y la hora de inicio de alquiler (no más de 15 minutos de la hora actual, del momento de reserva). Como datos opcionales ingresará la estación destino así como la hora aproximada de entrega. En caso exista una bicicleta **disponible** en dicho momento en la estación origen, dicha bicicleta quedará en estado **reservada**. El *cletero* dispondrá de esta reserva desde ese momento hasta la hora de inicio de alquiler indicada, y tendrá derecho a un tiempo de tolerancia según la estación origen. El sistema le asigna un número de reserva y le envía un correo con el código QR de la reserva.
* El *cletero* llegará a la estación origen, se acercará al encargado de la estación, éste escaneará el código QR mostrado por el *cletero*, y visualizará en el sistema los datos de la reserva. En caso siga siendo válida, busca la bicicleta reservada, revisa el estado delante del *cletero* y en caso todo esté bien, le entrega la bicicleta y ésta pasa al estado **en uso**.
* Cuando el *cletero* llegue a la estación destino, se acercará al encargado, éste escaneará el código QR mostrado por el *cletero* y visualizará en el sistema los datos de la reserva. Verificará que la bicicleta devuelta sea la asignada, revisará el estado de la bicicleta y de estar todo conforme, da por finalizado el alquiler, asigna la bicicleta a la estación y pasa la bicicleta al estado **disponible**.
* En caso una bicicleta esté en mal estado, el encargado de la estación pasa dicha bicicleta al estado **en revisión** indicando las fallas y el sistema le notificará por SMS al administrador del sistema para que tome las medidas correctivas pertinentes. Estas medidas se harán por fuera del sistema.
* En caso una bicicleta sea robada o esté en un estado irrecuperable será pasada al estado **desactivada**.
* Cada alquiler tendrá como duración máxima dos horas, contadas a partir del momento que la bicicleta pasa al estado **en uso**. En caso un *cletero* se exceda este tiempo máximo de alquiler, será sancionado con siete días de deshabilitación. Una segunda ocurrencia de retraso se sanciona con quince días de suspensión. En caso exista una tercera ocurrencia será deshabilitado definitivamente.

### Requerimientos no funcionales
* El sistema será una página web y alojada íntegramente en alguna nube como AWS o Azure. En un futuro podría desarrollarse una app móvil.
* El login será implementado con alguna red social como Google y/o Facebook.
* El código QR debe estar encriptado para evitar que un usuario con intenciones delincuenciales genere códigos QR falsos.

## Referencias
* [Leer código QR en una aplicación web (cambiar qrcode -> qrcodex)](https://www.sitepoint.com/create-qr-code-reader-mobile-website/)
* [Login con Google](https://developers.google.com/identity/sign-in/web/sign-in)
* [Login con Facebook](https://developers.facebook.com/docs/facebook-login/web)

## Navegación
[Volver a índice](../README.md)