# SR-Topologias  
## Miembros del grupo  
Álvaro Cerdá Pulla  
Juan Manuel Palacios Navas  

## Proceso de arranque y prueba  
Para arrancar los dispositivos, debemos hacer levaltar las máquinas y posteriormente acceder a la máquina que queramos (web-server, pc1, router) mediante ssh, lo podemos hacer de la siguiente manera:
```
   vagrant up
   vagrant ssh web-server
   vagrant ssh router
   vagrannt ssh pc1
```
Una vez llegados este punto, podemos probar los servicios que hemos desarrollado.  

### Servidor Web  
Una vez tengamos las máquinas levantadas, desde el pc1, podemos realizar un comando de comprobación, para ver que el servicio web está disponible.   
```
   curl alvaroYJuanmaSR.com
   curl www.alvaroYJuanmaSR.com
```
Se puede añadir la opción -I después del curl, para ver solo las cabeceras.  

### DHCP y DNS  
Podemos ver que el dnsmasq está configurado correctamente de varias maneras. Realizando el comando que hemos descrito antes, vemos como el DNS funciona perfectamente, ya que redirecciona el nombre a la IP que le corresponde.  
Para el DHCP, podremos ver la IP del pc1 (al que le da un rango 192.167.0.1 - 192.167.0.254).  
```
ip addr
```  

### Proxy 
Realizaremos el acceso al servicio web pero desde la IP del proxy.  

```
curl -x 192.168.0.251:3128 -I alvaroYJuanmaSR.com
```  

## Finalidad de cada uno de los ficheros  
Tenemos varios ficheros nuevos:  
- dnsmasq.conf: Aquí estará la configuración para el servidor DNS y DHCP y cómo debe funcionar.  
- hosts: Sirve para que nuestro DNS pueda resolver los nombres e IPs de nuestra red.  
- nginx.config: Configuración del servicio web.  
- resolv.conf: Dirección del servidor donde se buscará.  
- squid.conf: Configuración del proxy con las IPs permitidas y puertos seguros.  

## Enlace al vídeo explicativo  
https://web.microsoftstream.com/video/f30e5b73-3743-49d9-bc69-3292470c74cc  
