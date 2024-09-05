# NextCloud
Se utilizo el producto [NextCloud Files](https://nextcloud.com/files), para el almacenamiento de los archivos PDF, imagenes de periodos y archivos de copias de seguridad de la base de datos.

## Requisitos
* Ubuntu Server >= 20 
* Docker

### Instalacion
Seguir los pasos de las instrucciones detalladas en su [Repositorio](https://github.com/nextcloud/all-in-one).

### Configuracion
Una vez instalado se debe ir a la pagina de configuracion inicial http://ip.de.este.server:8080, donde se creara el usuario administrador con el cual se podra crear la cuenta que necesita el sistema de memorandos.
Una vez creada la cuenta e iniciado sesion como administrador, se deben seguir los siguientes pasos:
* Crear la cuenta para el sistema, que debe de tener como nombre de usuario: **memos**
* Ir a la seccion de apps, buscar e instalar la app **WebAppPassword**, luego de instalarlo se debe de ir a la seccion de configuraciones de administracion y buscar por **WebAppPassword**, y en el campo **Allowed origins for webdav** agregar la direccion del frontend (ej. https://tfg-memos.netlify.app, http://localhost:3001 para desarrollo, todos separados por coma) y guardar los cambios.
* Luego, cerrar sesion de administrador e iniciar con la cuenta **memos** para generar una contraseña de acceso para el frontend. Debes ir a la seccion de Seguridad en la configuracion de la cuenta, al final de la pagina en Dispositivos y sesiones se debe generar un nuevo registro en donde se especifica el nombre de la app (ej. memos-app), una vez generado debes de copiar la contraseña generada automaticamente para agregarlo como variable de entorno en el frontend rellenando el campo **NEXTCLOUD_APP_PASSWORD** del archivo .env.local o .env.production.
* Por ultimo volviendo a la pagina principal se debe de crear la estructura de carpetas que necesita el sistema:
  * **attachments**: carpeta donde se guardaran los adjuntos. Dentro de esta carpeta debes de crear la misma cantidad de carpetas que oficinas existan en el sistema utilizando el id de cada oficina para diferenciarlos, siguiendo este patron: office-1, office-2, office-3 y asi sucesivamente.
  * **backups**: carpeta para las copias de seguridad automaticas.
  * **page-layout**: carpeta para el almacenamiento de las imagenes del encabezado y pie de pagina del memorando.