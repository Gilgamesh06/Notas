<h2>Práctica: Virtual Local Area Networks (VLAN) Con Truncamiento</h2>

1. <h3>Construir el diseño de la red</h3>
Construya el siguiente diseño en el simulador

![](vx_images/490211992846203.png)

2. <h3>Configurar los IPs de los PCs</h3>
Hago click derecho sobre el PC1, seleccione la opcion <strong>Edit Config</strong> y asigne la IP 192.168.1.2

```bash
#This the configration for PC1
#Uncomment the following line to enable DHCP
#dhcp
#or the line below to manually setup an IP address and subnet mask 
#ip 192.168.1.1 255.0.0.0
set pcname PC1
ip 192.168.1.2/24
```

Repita la operación para el resto de las PCs con los siguientes valores

|  PC  |         IP         |
| ------ | ---------------- |
| PC1 | 192.168.1.2 |
| PC2 | 192.168.1.3 |
| PC3 | 10.0.0.2       |
| PC4 | 10.0.0.3       |
| PC5 | 192.168.1.4 |
| PC6 | 192.168.1.4 |
| PC7 | 10.0.0.4       |
| PC8 | 10.0.0.5       |

3. <h3>Conectar los PCs al Switch 1</h3>

Conecte los PCs con los puertos del switch 1  en el siguiente orden

|  PC  |       IP        |
| ------ | ------------- |
| PC1 | Ethernet0 |
| PC2 | Ethernet1 |
| PC3 | Ethernet2 |
| PC4 | Ethernet3 |

4. <h3>Conectar los PCs al Switch 2</h3>

Conecte los PCs con los puertos del switch 2  en el siguiente orden

|  PC  |       IP        |
| ------ | ------------- |
| PC5 | Ethernet0 |
| PC6 | Ethernet1 |
| PC7 | Ethernet2 |
| PC8 | Ethernet3 |


5. <h3>Conectar los Switches</h3>

Interconecte los dos switches utilizando el puerto Ethernet4 en ambos.


6. <h3>Configurar las VLANs en el Switch 1</h3>

Encienda el switch 1, abra una consola y ejecute los siguientes comandos

```bash
enable 
configure terminal
vlan 10
name students
vlan 20
name professors
exit
```

7. <h3>Asignar los puertos de la VLAN 10</h3>

```bash
configure terminal
interface GigabitEthernet 0/0
switchport mode access
switchport access vlan 10
exit
interface GigabitEthernet 0/1
switchport mode access
switchport access vlan 10
exit

```
8. <h3>Asignar los puertos de la VLAN 20</h3>


```bash
configure terminal
interface GigabitEthernet 0/2
switchport mode access
switchport access vlan 20
exit
interface GigabitEthernet 0/3
switchport mode access
switchport access vlan 20
exit

```

9. <h3>Configurar las VLANs en el Switch 2</h3>

Encienda el switch 2, abra una consola y ejecute los siguientes comandos

```bash
enable 
configure terminal
vlan 10
name students
vlan 20
name professors
exit
```

10. <h3>Asignar los puertos de la VLAN 10</h3>

```bash
configure terminal
interface GigabitEthernet 0/0
switchport mode access
switchport access vlan 10
exit
interface GigabitEthernet 0/1
switchport mode access
switchport access vlan 10
exit

```
11. <h3>Asignar los puertos de la VLAN 20</h3>


```bash
configure terminal
interface GigabitEthernet 0/2
switchport mode access
switchport access vlan 20
exit
interface GigabitEthernet 0/3
switchport mode access
switchport access vlan 20
exit

```

12. <h3>Configurar el Canal Trunk del Switch 1</h3>

Ejecute los siguientes comandos en el switch 1

```bash
configure terminal
interface GigabitEthernet 1/0
switchport trunk encapsulation dot1q
switchport mode trunk
switchport trunk allowed vlan add 10,20
end
```

Verifica que la interfaz está en modo trunk

```bash
show interfaces GigabitEthernet 1/0 switchport
```


13. <h3>Configurar el Canal Trunk del Switch 2</h3>

Ejecute los siguientes comandos en el switch 2

```bash
configure terminal
interface GigabitEthernet 1/0
switchport trunk encapsulation dot1q
switchport mode trunk
switchport trunk allowed vlan add 10,20
end
```

Verifica que la interfaz está en modo trunk

```bash
show interfaces GigabitEthernet 1/0 switchport
```