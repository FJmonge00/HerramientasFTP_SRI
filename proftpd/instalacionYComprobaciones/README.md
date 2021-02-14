<img src="../../imagenes/MI-LICENCIA88x31.png" style="float: left; margin-right: 10px;" />

# Instalación proftpd

```bash
apt-get install proftpd-basic -y``
```

*(Opcional) Instalamos documentación de proftpd*

``apt-get install proftpd-doc -y``

## Versión de apache instalada

``proftpd -v``

![estadoServicio](/imagenes/proftpd/version.jpg)

## Estado del servicio

``systemctl enable proftpd.service``

## Estado del servicio

```bash
systemctl status proftpd.service
```

**ó**

```bash
/etc/init.d/proftpd status
```

![estadoServicio](/imagenes/proftpd/estadoServicio.jpg)

## Usuarios creados

Se crea usuario ftp y proftpd

```bash
getent passwd
```

## Usuarios con acceso denegado

```bash
cat /etc/ftpusers
```

## Configuración por defecto

```bash
cat /etc/proftpd/proftpd.conf | grep -v "^#\|^$"
```

### Instalacion de Cliente FTP Shell

```bash
apt-get install ftp -y
```

![DocumentacionLocal](/imagenes/proftpd/documentacionLocal.jpg)

_________________________________________________
*[Volver atrás...](../../README.md)*