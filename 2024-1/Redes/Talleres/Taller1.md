<div style=";border:solid; margin:20px; padding:3%">

<h1> Taller <h1>


<h2>Práctica 2 de Capa 3: Enrutamiento Estático</h2>

En esta práctica se configurará un infraestructura sencilla compuesta por dos redes, cada una con su enrutador correspondiente.

![Topologia](vx_images/212635410635112.png)

<br>
Utilice el siguiente segmento de red para la <strong>red A: </strong>

```
192.168.0.0/24
```
Utilice el siguiente segmento de red para la <strong>red B:</strong>

```
192.168.1.0/24
```
Utilice el siguiente segmento de red para la <strong>red R:</strong>

```
192.168.2.0/27
```

<h2>Configurar los PCs </h2>

Para confirgurar el PC de la red A utilizamos los siguientes comandos:


```bash
ip 192.168.0.2 255.255.255.0 192.168.0.1
save
show
```

![PC Red A](vx_images/197547233960863.png)

<br>
Para confirgurar el PC de la red B utilizamos los siguientes comandos:


```bash
ip 192.168.1.2 255.255.255.0 192.168.1.1
save
show
```

![PC Red B](vx_images/73397497909267.png)


<h3>Configurar la Interfaz FastEthernet 0/1 del router A</h3>

Ingrese los siguientes comandos

```bash
enable
configure terminal
interface fastEthernet 0/1
ip add 192.168.0.1 255.255.255.0
no shutdown
exit
```


![Router A FastEthernet 0/1](vx_images/319831974956731.png)

<br>
Puede ver la configuración con el comando

```bash
show int
```

<h3>Configurar la Interfaz FastEthernet 0/0 del router A</h3>

Ingrese los siguientes comandos

```bash
enable
configure terminal
interface fastEthernet 0/0
ip add 192.168.2.1 255.255.255.0
no shutdown
exit
```

![Router A FastEthernet 0/0](vx_images/31526326595909.png)

<br>
Puede ver la configuración con el comando

```bash
show int
```

<h3>Configurar la Interfaz FastEthernet 0/1 del router B</h3>


Ingrese los siguientes comandos

```bash
enable
configure terminal
interface fastEthernet 0/1
ip add 192.168.1.1 255.255.255.0
no shutdown
exit
```

![Router B FastEthernet 0/1 ](vx_images/500081626142387.png)

<br>
Puede ver la configuración con el comando

```bash
show int
```

<h3>Configurar la Interfaz FastEthernet 0/0 del router B</h3>


```bash
enable
configure terminal
interface fastEthernet 0/0
ip add 192.168.2.2 255.255.255.0
no shutdown
exit
```
![Router B FastEthernet 0/0](vx_images/287412484826917.png)

<br>
Puede ver la configuración con el comando

```bash
show int
```

Para guardar la configuracion del Router

Abreviatura de write memory, que guarda la configuración en la memoria no volátil.

```bash
wr
```

Este comando copia la configuración actual (en la memoria RAM) a la configuración de inicio (que se carga al reiniciar el router).

```bash
copy running-config startup-config

```

Configurar las Rutas Estáticas en los Enrutadores


<h2>Ruta Estática del enrutador A</h2>

Esta ruta le indica al enrutador A como llegar a la red B. Para configurar la ruta ingrese los siguientes comandos

```bash
enable
configure terminal
ip route 192.168.1.0 255.255.255.0 fastEthernet 0/0 192.168.2.2
```

![Ruta Estatica del enrutador A](vx_images/298014016921057.png)

<br>
Para ver todas las rutas estáticas salga del modo de configuración y luego utilice el siguiente comando

```bash
show ip route static
```

<h2>Ruta Estática del enrutador B</h2>


Esta ruta le indica al enrutador B como llegar a la red A. Para configurar la ruta
ingrese los siguientes comandos

```bash
enable
configure terminal
ip route 192.168.0.0 255.255.255.0 fastEthernet 0/0 192.168.2.1
```

![Ruta estatica del enrutador B](vx_images/569402912542597.png)

<br>
Para ver todas las rutas estáticas salga del modo de configuración y luego utilice el siguiente comando

```bash
show ip route static
```

Para ver la comunicacion entre el PC de la Red A y el PC de la Red B  usamos el comando <strong>ping</strong>

```bash
ping 192.168.1.2
```
![Ping PC Red A a PC Red B](vx_images/511393624668433.png)

</div>