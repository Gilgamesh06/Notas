<h2> BGP </h2>


### ¿Qué es BGP?

**BGP**, o **Border Gateway Protocol**, es el protocolo estándar de enrutamiento utilizado para intercambiar información de enrutamiento entre sistemas autónomos (AS) en Internet. Un sistema autónomo es un grupo de redes IP bajo una única administración que presenta una política de enrutamiento común al Internet.


### Capa del Modelo TCP/IP donde Funciona BGP

BGP opera en la **Capa de Aplicación** del modelo TCP/IP. Aunque se encarga del enrutamiento entre sistemas autónomos, que es una función de red, se considera parte de la capa de aplicación porque utiliza un protocolo de transporte (TCP) para gestionar las sesiones y el intercambio de mensajes.

### Formato de los Mensajes BGP

Los mensajes BGP tienen un formato específico que incluye las siguientes partes:

- **`Cabecera`**: Incluye un marcador, el tamaño total del mensaje y el tipo de mensaje (OPEN, UPDATE, NOTIFICATION, KEEPALIVE).

- **`Mensaje OPEN`**: Establece una sesión entre dos pares BGP e intercambia parámetros básicos como la versión de BGP, el AS del emisor, el tiempo de espera y el identificador BGP.

- **`Mensaje UPDATE`**: Anuncia nuevas rutas o retira rutas previamente anunciadas. Contiene listas de rutas accesibles junto con sus atributos.

- **`Mensaje KEEPALIVE`**: Mantiene la sesión abierta entre pares BGP y confirma que la conexión está activa.

- **`Mensaje NOTIFICATION`**: Se envía cuando hay un error en la sesión BGP. Contiene un código de error y un mensaje descriptivo.

Cada mensaje tiene su propósito y estructura para asegurar una comunicación eficiente y confiable entre pares BGP.

### ¿Para qué sirve BGP?

BGP es fundamental para la operación de Internet. Permite a los routers de diferentes sistemas autónomos comunicarse entre sí, compartiendo información sobre las rutas disponibles y tomando decisiones inteligentes sobre el mejor camino para enviar paquetes de datos. Aquí hay algunas funciones clave de BGP:

- **`Interconexión de Sistemas Autónomos`**: BGP permite que la red de un AS se conecte y comunique con otras redes AS.

- **`Políticas de Enrutamiento`**: Los administradores de red pueden definir políticas para controlar el flujo del tráfico basándose en necesidades empresariales o acuerdos de nivel de servicio.

- **`Escalabilidad`**: BGP puede manejar grandes cantidades de rutas y es capaz de escalar para soportar el crecimiento de la infraestructura de Internet.

- **`Resiliencia y Estabilidad`**: BGP puede reaccionar a cambios en la topología de la red, como fallas en las conexiones, y recalcula las rutas para asegurar la continuidad del servicio.

- **`Selección de Ruta Óptima`**: BGP selecciona la mejor ruta posible basándose en varios factores, incluyendo la política del AS, la distancia, y la estabilidad del camino.

BGP es un protocolo complejo con muchas características avanzadas que permiten a Internet funcionar como una red interconectada y resiliente.

<hr>

- `configure terminal`: Este comando te lleva al modo de configuración global, donde puedes realizar cambios en la configuración del router.

- `router bgp 100`: Inicia la configuración del Border Gateway Protocol (BGP) con un número de sistema autónomo (AS) de 100.

- `neighbor 160.223.145.18 remote-as 200`: Establece un vecino BGP en la dirección IP 160.223.145.18 que pertenece a otro AS, específicamente el AS 200.

- `redistribute ospf 1`: Toma las rutas aprendidas por el protocolo OSPF (Open Shortest Path First) en la instancia 1 y las redistribuye en BGP, permitiendo que otras redes conozcan estas rutas.

- `router ospf 1`: Inicia la configuración de OSPF para la instancia 1.

- `redistribute bgp 100 subnets`: Redistribuye las rutas aprendidas por BGP en OSPF, incluyendo todas las subredes.

- `end`: Sale del modo de configuración global y regresa al modo EXEC privilegiado.

- `wr`: Guarda la configuración actual en la memoria no volátil para que persista después de un reinicio.

<hr>

### Verificar BGP

Este comando te muestra un resumen del estado de BGP, incluyendo la lista de vecinos BGP, el estado de la sesión (si está establecida o no), el número de prefijos recibidos de cada vecino y más información útil para el diagnóstico.

```bash
show ip bgp summary
# Para IPv6
show bgp ipv6 unicast
show bgp ipv6 unicast summary
```
<hr>


### Implementacion en IPv6

- `router bgp 100:` Este comando configura el proceso BGP (Border Gateway Protocol) en el router con el número de sistema autónomo (AS) 100.
- `address-family ipv6:` Aquí se especifica que estamos trabajando con direcciones IPv6 en el contexto del BGP.
- `redistribute connected metric 1:` Este comando redistribuye las rutas conectadas (interfaces directamente conectadas) en el proceso BGP con una métrica de 1.
- `neighbor FEC0:242:0:6::2 remote-as 200:` Define un vecino BGP con la dirección IPv6 FEC0:242:0:6::2 y el número de sistema autónomo (AS) 200.
- `neighbor FEC0:242:0:6::2 activate:` Activa la relación BGP con el vecino especificado.
- `redistribute ospf 1:` Redistribuye las rutas aprendidas a través del protocolo OSPF (Open Shortest Path First) en el proceso BGP.
- `exit-address-family:` Sale del contexto de la familia de direcciones IPv6.
- `exit:` Sale del modo de configuración BGP.
- `ipv6 router ospf 1:` Configura el proceso OSPF con el número de proceso 1 para IPv6.
- `redistribute bgp 100 metric-type 1:` Redistribuye las rutas aprendidas a través del BGP en el proceso OSPF con una métrica tipo 1.
- `redistribute connected metric-type 1:` Redistribuye las rutas conectadas en el proceso OSPF con una métrica tipo 1.
- `end:` Finaliza la configuración.
- `wr:` Guarda la configuración en la memoria permanente (equivalente a write memory).