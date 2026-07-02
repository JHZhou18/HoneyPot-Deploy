# HoneyPot-Deploy
Proyecto final para la Microcredencial en Fundamentos de la Ciberseguridad, ofrecida por la Universidad de Cantabria. 
El proyecto consiste en el despliegue de un honeypot y el posterior análisis de los datos obtenidos para la comprensión del estado actual de la seguridad informática y su importancia.

# Tecnologías y Requisitos
## Virtualización
Se utilizó **VirtualBox** para desplegar una máquina basada en el sistema operativo **Linux Ubuntu 24.04.1 Live Server**. A la máquina se le asignaron los siguientes recursos: **8192 MB** de RAM, **4** núcleos y **50 GB** de disco virtual.

## Honeypot
Para el honeypot se usó el proyecto de código abierto [**T-Pot**](https://github.com/telekom-security/tpotce) que incluye una gran cantidad de honeypots junto a herramientas de análisis de datos como **Kibana** y **Attack Map**.

# Seguridad
Se estableció el honeypot en la **DMZ** del router para que los ataques no afectaran a la red privada. Se comprobó que la IP era accesible desde internet a través de [Shodan](https://shodan.io).

# Monitorización
T-Pot muestra los resultados de los ataques a través de una **interfaz web** accesible desde el puerto 64297 del servidor, con autenticación mediante usuario y contraseña.

## Kibana
Muestra múltiples **gráficos** con la información recopilada. El dato más relevante que expone son los **CVE** que más comúnmente son explotados por los atacantes.
<img width="512" height="245" alt="image" src="https://github.com/user-attachments/assets/43904299-6be8-4483-9140-8c6f5951c5f9" />
## Attack Map
Muestra un **mapa** con el origen de los ataques en tiempo real.
<img width="512" height="276" alt="image" src="https://github.com/user-attachments/assets/343ca53b-e455-4405-aedc-b77ff2875fb5" />
# Resultados
Los resultados destacados son:
- **Principales puertos objetivo**: 23 (**telnet**), 22 (**ssh**), 80 (**http**), 2054 (**weblogin**) y 2056 (**omnisky**).
- **Sistema operativo del atacante**: La mayoría proceden de sistemas **Linux**, seguidos por **Windows**.
- **Credenciales más probadas**: Para el _username_: **root**, **admin**, **guest**, **123456**, **test1234**, **admin1234** y **sa**. La contraseña que más se ha probado ha sido dejar el campo vacío.
- **Vulnerabilidades más explotadas**: **CVE-2001-0414** (buffer overflow) y **CVE-2024-6387**.
