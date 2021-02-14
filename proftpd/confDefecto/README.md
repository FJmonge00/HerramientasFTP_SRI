<img src="../../imagenes/MI-LICENCIA88x31.png" style="float: left; margin-right: 10px;" />

# Configuración por defecto

## Fichero por defecto:/etc/proftpd/proftpd.conf


|Directiva  |Función  |
|:---------:|---------|
|ServerName|Nombre del servidor que aparecerá en programa cliente.|
|DeferWelcome|Para activar o desactivar el mensaje de bienvenida al servidor.|
|ShowSymlinks|Para que nos muestre los links para saltar entre las carpetas.|
|TimeoutIdle|El número de segundos que puede estar el cliente sin actividad (Sin hacer nada). Si llega a ese tiempo lo expulsa.|
|Port|Puerto. Lo podríamos modificar.|
|MaxInstances|El número de conexiones simultáneas al servidor.|
|User|Usuario por defecto. del servidor|
|Group|Grupo por defecto.|
|Umask|Para establecer los permisos por defecto de los archivos que se creen en el servidor ftp.|
|xferlog|Dónde se guarda los logs de las transferencias. --> tail -n 15 /var/log/proftpd/xferlog|
|SystemLog|Dónde se guardan las respuestas del servidor. --> cat /var/log/proftpd/proftpd.log|

## Modificaciones
### Modificar el ServerName

```bash
apt-get install proftpd-doc -y
```

### Directiva de bienvenida al servidor

```conf
ServerName			"FTP Informatica Rodrigo Caro"
```

![ftpfotos](../../imagenes/directivaBienvenida.jpg)

### Directiva de mensaje conexion y error de conexión

```conf
AccessGrantMSG "Bienvenido al servidor FTP de Informatica RC"
AccessDenyMSG "Error, en el acceso al servidor FTP"
```

![ftpfotos](../../imagenes/mensajesAccesoAlServidor.jpg)

** Sintaxis y Reiniciar servicio**

```bash
#Sintaxis
proftpd -t
systemctl restart proftpd.service
systemctl status proftpd.service
```

#### Comprobaciones de acceso

![ftpfotos](../../imagenes/mensajeBienvenida.jpg)
![ftpfotos](../../imagenes/mensajeError.jpg)

## Enjaular usuarios

```conf
DefaultRoot			~
```
![ftpfotos](../../imagenes/enjaularUsuarios.jpg)

```bash
#Sintaxis
proftpd -t
systemctl restart proftpd.service
systemctl status proftpd.service
```

## Cambiar permisos por defecto (Umask)

```conf
Umask				066  077
```

```bash
#Sintaxis
proftpd -t
systemctl restart proftpd.service
systemctl status proftpd.service
```

![ftpfotos](../../imagenes/umask.jpg)

## Cambiar permisos por defecto (Umask)

```conf
Umask				066  077
```

![ftpfotos](../../imagenes/umask.jpg)

** Sintaxis y Reiniciar servicio**

```bash
#Sintaxis
proftpd -t
systemctl restart proftpd.service
systemctl status proftpd.service
```
![ftpfotos](../../imagenes/pruebasPermisos.jpg)

_________________________________________________
*[Volver atrás...](../../README.md)*