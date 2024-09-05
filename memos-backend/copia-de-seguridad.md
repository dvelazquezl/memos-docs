# Copias de seguridad
Las copias de seguridad de la base de datos se realizan cada viernes a las 19:00 Hs.

### Cada copia de seguridad será guardada en 2 ubicaciones:
1. En el mismo servidor donde está instalada la base de datos, se guardará esta ubicación: /home/$USER/backups. 
2. En el servidor de NextCloud, en una carpeta de backups.
La generación de la copia de seguridad es realizada a través de un cronjob que se encarga de ejecutar un [script](https://bitbucket.org/tfg-workspace/memos-backend/src/develop/backup-db.sh) configurado de la siguiente manera: `0 19 * * 5 ./var/www/<carpeta-de-la-api>/backup-db.sh` (la direccion del archivo backup-db.sh puede ser modificada)

> Antes de ejecutar una copia de seguridad se debe de asegurar que existan las carpetas backups tanto dentro del servidor donde se aloja la base de datos, asi como tambien dentro de la cuenta de NextCloud que se utilizará para almacenar las copias de seguridad.