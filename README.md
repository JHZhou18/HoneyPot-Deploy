# HoneyPot-Deploy
Proyecto final para la Microcredencial en fundamentos de la ciberseguridad, ofrecida por la Universidad de Cantabria. 
El proyecto consiste en el despliegue de un honeypot y el posterior analisis de los datos obtenidos para la compresión del estado actual de la seguridad informática y su importancia.

# Tecnologías y Requisitos
## Virtualización
Se utilizó **VirtualBox** para desplegar una maquina basada en el sistema operativo **Linux Ubuntu 24.04.1 Live Server**. A la maquina se le asignaron los siguientes recursos: **8192 MB** de RAM, **4** núcleos y **50 GB** de disco virtual.
## Honeypot
Para el honeypot se uso el proyecto de codigo abierto [**T-POT**](https://github.com/telekom-security/tpotce) que incluye una gran cantidad de **honeypots** junto a herramientas de analisis de datos como **Kibana** y **Attack Map**.

# Seguridad
Se estableció el honeypot en la **DMZ** del router para que los ataque no afectaran a la red privada. Se comprobó que la IP era accesible desde internet a través de [Shodan](shodan.io).

# Monitorizacion
T-POT muestra los resultados de los ataques a través de una **interfaz web** accesible desde el puerto 64297 del servidor, con autenticacion mediante usuario y contraseña.
## Kibana
Muestra multiples **gráficos** con la información recopilada. El dato más relevante que expone son los **CVE** que más comúnmente son explotados por los atacantes.
## Attack Map
Muestra un **mapa** con el origen de los ataques en tiempo real.

# Resultados
Los resultados destacados son:
- **Principales puertos objetivo**: 23 (**telnet**), 22 (**ssh**), 80 (**http**), 2054 (**weblogin**) y 2056 (**omnisky**)
- **Sistema operativo del atacante**: La mayoría proceden de sistemas **Linux** seguidos por **Windows**.
- **Credenciales más probadas**: Para el _username_: **root**, **admin**, **guest**, **123456**, **test1234**, **admin1234**, **sa**. La contraseña que más se ha probado ha sido dejar el campo vacio.
- **Vulnerabilidades más explotadas**: **CVE-2001-0414** (bufferoverflow) y **CVE-2024-6387**
