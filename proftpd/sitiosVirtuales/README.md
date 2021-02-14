<img src="../../imagenes/MI-LICENCIA88x31.png" style="float: left; margin-right: 10px;" />

# Crear Sitios Virtuales

El término Virtual Host se refiere a hacer funcionar más de un sitio (ftp,web etc ...) como por ejemplo www.servidor1.com y www.servidor2.com en una misma máquina. Los Hosts Virtuales pueden funcionar basándose en "direcciones IP", lo que significa que cada Virtual Host tiene una dirección IP diferente, o basados en "nombres de dominio", lo que significa que con una sola dirección IP están funcionando Virtual Hosts con diferentes nombres de dominio. Este proceso es totalmente transparente para el usuario final.

Con VirtualHosts podemos tener varios servidores FTP en un mismo servidor.

>[Importante]FTP NO ES CAPAZ DE DETECTAR EL NOMBRE DE DOMINIO.
SOLO REDIRECCIONA IP Y PUERTO.

## Pre-coniguración

```bash
echo "Include /etc/proftpd/virtuals.conf" >> /etc/proftpd/proftpd.conf
cp /etc/proftpd/virtuals.conf /etc/proftpd/virtuals.conf.ORIGINAL
```

**Sintaxis y Reiniciar servicio**

```bash
#Sintaxis
proftpd -t
systemctl restart proftpd.service
systemctl status proftpd.service
```

## Crear sitio virtual 1

```bash
mkdir /srv/FTP1
cd /srv/FTP1/
wget https://m.media-amazon.com/images/I/71bylIXR7hL._AC_SL1350_.jpg
touch FTP1-prueba
chown -R ftp:nogroup /srv/
```

*Añadir a `/etc/proftpd/virtuals.conf`*

```conf
<VirtualHost ftp.servera.com>
ServerName              "FTP1"
Port    7000
RequireValidShell       off
DefaultRoot             /srv/FTP1    
</VirtualHost>
```

**ó**

```bash
echo '<VirtualHost ftp.servera.com>' >> /etc/proftpd/virtuals.conf
echo 'ServerName              "FTP1"' >> /etc/proftpd/virtuals.conf
echo 'Port    7000' >> /etc/proftpd/virtuals.conf
echo 'RequireValidShell       off' >> /etc/proftpd/virtuals.conf
echo 'DefaultRoot             /srv/FTP1' >> /etc/proftpd/virtuals.conf
echo '</VirtualHost>' >> /etc/proftpd/virtuals.conf
```

**Sintaxis y Reiniciar servicio**

```bash
#Sintaxis
proftpd -t
systemctl restart proftpd.service
systemctl status proftpd.service
```

## VirtualHosts 2

```bash
mkdir /srv/FTP2
cd /srv/FTP2/
wget https://m.media-amazon.com/images/I/71bylIXR7hL._AC_SL1350_.jpg
touch FTP2-prueba
chown -R ftp:nogroup /srv/
```

*Añadir a `/etc/proftpd/virtuals.conf`*

```conf
<VirtualHost ftp.serverb.com>
ServerName              "FTP2"
Port    7001
RequireValidShell       off
DefaultRoot             /srv/FTP2    
</VirtualHost>
```

**ó**

```bash
echo '<VirtualHost ftp.serverb.com>' >> /etc/proftpd/virtuals.conf
echo 'ServerName              "FTP2"' >> /etc/proftpd/virtuals.conf
echo 'Port    7001' >> /etc/proftpd/virtuals.conf
echo 'RequireValidShell       off' >> /etc/proftpd/virtuals.conf
echo 'DefaultRoot             /srv/FTP2' >> /etc/proftpd/virtuals.conf
echo '</VirtualHost>' >> /etc/proftpd/virtuals.conf
```

![ftpfotos](../../imagenes/sitiosVirtuales.png)

**Sintaxis y Reiniciar servicio**

```bash
#Sintaxis
proftpd -t
systemctl restart proftpd.service
systemctl status proftpd.service
```

_________________________________________________
*[Volver atrás...](../../README.md)*
