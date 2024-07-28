
<h1> Parcial 1</h1>

<h2> Redes por definir </h2>

* Network: 160.223.144.0/20
    * **Red A:** 221
    * **Red B:** 17
    * **Red C:** 112
    * **Red D:** 98
    * **Red E:** 245
    * **Red F:** 84
    * **Red G:** 27
    * **Red H:** 192


160.223.144.0/20

| CIDR | Máscara de Subred | Máscara Comodín | # de Direcciones IP | # de Direcciones IP Utilizables |
| -------- | -------------------------- | ------------------------- | -------------------------- | ----------------------------------------- |
| /32     | 255.255.255.255      | 0.0.0.0                    | 1                              | 1                                                |
| /31     | 255.255.255.254      | 0.0.0.1                    | 2                              | 2*                                              |
| /30     | 255.255.255.252      | 0.0.0.3                    | 4                              | 2                                                |
| /29     | 255.255.255.248      | 0.0.0.7                    | 8                              | 6                                                |
| /28     | 255.255.255.240      | 0.0.0.15                  | 16                            | 14                                              |
| /27     | 255.255.255.224      | 0.0.0.31                  | 32                            | 30                                              |
| /26     | 255.255.255.192      | 0.0.0.63                  | 64                            | 62                                              |
| /25     | 255.255.255.128      | 0.0.0.127                | 128                          | 126                                            |
| /24     | 255.255.255.0          | 0.0.0.255                | 256                          | 254                                            |
| /23     | 255.255.254.0          | 0.0.1.255                | 512                          | 510                                            |
| /22     | 255.255.252.0          | 0.0.3.255                | 1,024                       | 1,022                                         |
| /21     | 255.255.248.0          | 0.0.7.255                | 2,048                       | 2,046                                         |
| /20     | 255.255.240.0          | 0.0.15.255              | 4,096                       | 4,094                                         |


 | Red  | Solicitud de Host  | Host Encontrados  | Direccion de Red  | Mask  | Mascara  | Primera IP utilizable  | Ultima IP utilizable  | Direccion de Broadcast |
|---|---|---|---|---|---|---|---|---|
| E | 245  | 254  | 160.223.144.0  | /24  | 255.255.255.0  | 160.223.144.1  | 160.223.144.254  | 160.223.144.255   |
| A | 221  | 254  | 160.223.145.0  | /24  | 255.255.255.0  | 160.223.145.1  | 160.223.145.254  | 160.223.145.255   |
| H | 192  | 254  | 160.223.146.0  | /24  | 255.255.255.0  | 160.223.146.1  | 160.223.146.254  | 160.223.146.255   |
| C | 112  | 126  | 160.223.147.0  | /25  | 255.255.255.128  | 160.223.147.1 | 160.223.147.126 |  160.223.147.127  |    
| D | 98 | 126  |  160.223.147.128 | /25  | 255.255.255.128  | 160.223.147.129  | 160.223.147.254  | 160.223.147.255 |
| F | 84 | 126  | 160.223.148.0  | /25  | 255.255.255.128  | 160.223.148.1  | 160.223.148.126  |  160.223.148.127 |
| G | 27 | 30  | 160.223.148.128  | /27   | 255.255.255.224  | 160.223.148.129  | 160.223.148.158  | 160.223.148.159   |
| B | 17 | 30  | 160.223.148.160  | /27  | 255.255.255.224  | 160.223.148.161  | 160.223.148.190  | 160.223.148.191  |
| Enlace A | 2 | 2  | 160.223.148.192  | /30  | 255.255.252  | 160.223.148.193  | 160.223.148.194 | 160.223.148.195  |
| Enlace B | 2 | 2  | 160.223.148.196 | /30  | 255.255.252  | 160.223.148.197  | 160.223.148.198  | 160.223.148.199  |
| Enlace C | 2 | 2  | 160.223.148.200  | /30 | 255.255.252  | 160.223.148.201  | 160.223.148.202  | 160.223.148.203  |
| Enlace D | 2 | 2  | 160.223.148.204  | /30  | 255.255.252   | 160.223.148.205 | 160.223.148.206  | 160.223.148.207 |
| Enlace E | 2 | 2  | 160.223.148.208  | /30  | 255.255.252  | 160.223.148.209   | 160.223.148.210  | 160.223.148.211 |
| Enlace F | 2 | 2  | 160.223.148.212  | /30  | 255.255.252  | 160.223.148.213   | 160.223.148.214  | 160.223.148.215 |
| Enlace G | 2 | 2  | 160.223.148.216  | /30  | 255.255.252  | 160.223.148.217  | 160.223.148.218  | 160.223.148.219  |
| Enlace H | 2 | 2  | 160.223.148.220  | /30  | 255.255.252  | 160.223.148.221   | 160.223.148.222  | 160.223.148.223  |
| Enlace 1 | 2 | 2  | 160.223.148.224  | /30  | 255.255.252  | 160.223.148.225   | 160.223.148.226  | 160.223.148.227  |
| Enlace 2 | 2 | 2  | 160.223.148.228  | /30  | 255.255.252  | 160.223.148.229   | 160.223.148.230   | 160.223.148.231 |
| Enlace 3 | 2 | 2  | 160.223.148.232  | /30  | 255.255.252  | 160.223.148.233  | 160.223.148.234  |  160.223.148.235  |
| Enlace 4 | 2 | 2  | 160.223.148.236  | /30  | 255.255.252  | 160.223.148.237  | 160.223.148.238  |  160.223.148.239  |
| Enlace  | 2 | 2  | 160.223.148.240  | /30  | 255.255.252  | 160.223.148.241  | 160.223.148.242  |  160.223.148.243  |
| PC  | 2 | 2  | 160.223.148.244  | /30  | 255.255.252  | 160.223.148.245  | 160.223.148.246  |  160.223.148.247  |
 



![](vx_images/218914533960954.png)

<h3>1) Configuración De Los PCs</h3>


Primero Asignamos las ip a los PCs de cada red:

* PC Red A

```bash
ip 160.223.145.2 255.255.255.0 160.223.145.1
save 
show
```
* PC Red B

```bash
ip 160.223.148.162 255.255.255.224 160.223.148.161
save 
show
```
* PC Red C

```bash
ip 160.223.147.2 255.255.255.128 160.223.147.1
save 
show
```

* PC Red D

```bash
ip 160.223.147.130 255.255.255.128 160.223.147.129
save 
show
```
* PC Red E

```bash
ip  160.223.144.2 255.255.255.0 160.223.144.1
save 
show
```
* PC Red F

```bash
ip 160.223.148.2 255.255.255.128 160.223.148.1
save 
show
```

* PC Red G

```bash
ip  160.223.148.130 255.255.255.224  160.223.148.129
save 
show
```
* PC Red H

```bash
ip 160.223.146.2 255.255.255.0 160.223.146.1
save 
show
```

<h3>2.1) Configuración Del Enrutador 1</h3>

Para configurar el router 1 ejecute los siguientes comandos en la cónsola del mismo

```bash
enable
configure terminal
interface FastEthernet 0/1
ip address 160.223.148.193  255.255.255.252
no shutdown
exit
interface fastEthernet 0/0
ip address 160.223.145.1 255.255.255.0
no shutdown
exit
end
wr
show ip interface brief
```

<h3>2.2) Configuración Del Enrutador 2</h3>

Para configurar el router 2 ejecute los siguientes comandos en la cónsola del mismo

```bash
enable
configure terminal
interface FastEthernet 0/1
ip address 160.223.148.197 255.255.255.252
no shutdown
exit
interface fastEthernet 0/0
ip address 160.223.148.161 255.255.255.224
no shutdown
exit
end
wr
show ip interface brief
```

<h3>2.3) Configuración Del Enrutador 3</h3>

Para configurar el router 3 ejecute los siguientes comandos en la cónsola del mismo

```bash
enable
configure terminal

interface fastEthernet 0/0
ip address 160.223.148.238 255.255.255.252
no shutdown
exit
interface FastEthernet 0/1
ip address 160.223.148.225 255.255.255.252
no shutdown
exit
interface FastEthernet 1/0
ip address 160.223.148.194 255.255.255.252
no switchport
no shutdown
exit
interface fastEthernet 1/1
no switchport
ip address 160.223.148.198  255.255.255.252
no shutdown
exit
end
wr
show ip interface brief
```

<h3>2.4) Configuración Del Enrutador 4</h3>

Para configurar el router 4 ejecute los siguientes comandos en la cónsola del mismo

```bash
enable
configure terminal
interface FastEthernet 0/1
ip address 160.223.148.201  255.255.255.252
no shutdown
exit
interface fastEthernet 0/0
ip address 160.223.147.1 255.255.255.128
no shutdown
exit
end
wr
show ip interface brief
```

<h3>2.5) Configuración Del Enrutador 5</h3>

Para configurar el router 5 ejecute los siguientes comandos en la cónsola del mismo

```bash
enable
configure terminal
interface FastEthernet 0/1
ip address 160.223.148.205  255.255.255.252
no shutdown
exit
interface fastEthernet 0/0
ip address 160.223.147.129 255.255.255.128
no shutdown
exit
end
wr
show ip interface brief
```

<h3>2.6) Configuración Del Enrutador 6</h3>

Para configurar el router 6 ejecute los siguientes comandos en la cónsola del mismo

```bash
enable
configure terminal

interface fastEthernet 0/0
ip address 160.223.148.229 255.255.255.252
no shutdown
exit
interface FastEthernet 0/1
ip address 160.223.148.226 255.255.255.252
no shutdown
exit
interface FastEthernet 1/0
ip address 160.223.148.202 255.255.255.252
no switchport
no shutdown
exit
interface fastEthernet 1/1
no switchport
ip address 160.223.148.206  255.255.255.252
no shutdown
exit
end
wr
show ip interface brief
```
<h3>2.7) Configuración Del Enrutador 7</h3>

Para configurar el router 7 ejecute los siguientes comandos en la cónsola del mismo

```bash
enable
configure terminal

interface fastEthernet 0/0
ip address 160.223.148.237 255.255.255.252
no shutdown
exit
interface FastEthernet 0/1
ip address 160.223.148.234 255.255.255.252
no shutdown
exit
interface FastEthernet 1/0
ip address 160.223.148.210 255.255.255.252
no switchport
no shutdown
exit
interface fastEthernet 1/1
no switchport
ip address 160.223.148.214  255.255.255.252
no shutdown
exit
end
wr
show ip interface brief
```

<h3>2.8) Configuración Del Enrutador 8</h3>

Para configurar el router 8 ejecute los siguientes comandos en la cónsola del mismo

```bash
enable
configure terminal
interface FastEthernet 0/1
ip address 160.223.148.209  255.255.255.252
no shutdown
exit
interface fastEthernet 0/0
ip address  160.223.144.1 255.255.255.0
no shutdown
exit
end
wr
show ip interface brief
```

<h3>2.9) Configuración Del Enrutador 9</h3>

Para configurar el router 9 ejecute los siguientes comandos en la cónsola del mismo

```bash
enable
configure terminal
interface FastEthernet 0/0
ip address 160.223.148.1  255.255.255.128
no shutdown
exit
interface fastEthernet 0/1
ip address  160.223.148.213 255.255.255.252
no shutdown
exit
end
wr
show ip interface brief
```

<h3>2.10) Configuración Del Enrutador 10</h3>

Para configurar el router 10 ejecute los siguientes comandos en la cónsola del mismo

```bash
enable
configure terminal

interface fastEthernet 0/0
ip address 160.223.148.230 255.255.255.252
no shutdown
exit
interface FastEthernet 0/1
ip address 160.223.148.233 255.255.255.252
no shutdown
exit
interface FastEthernet 1/0
ip address 160.223.148.218 255.255.255.252
no switchport
no shutdown
exit
interface fastEthernet 1/1
no switchport
ip address 160.223.148.222  255.255.255.252
no shutdown
exit
end
wr
show ip interface brief
```

<h3>2.11) Configuración Del Enrutador 11</h3>

Para configurar el router 11 ejecute los siguientes comandos en la cónsola del mismo

```bash
enable
configure terminal
interface FastEthernet 0/1
ip address 160.223.148.217  255.255.255.252
no shutdown
exit
interface fastEthernet 0/0
ip address  160.223.148.129 255.255.255.224 
no shutdown
exit
end
wr
show ip interface brief
```

<h3>2.12) Configuración Del Enrutador 12</h3>

Para configurar el router 12 ejecute los siguientes comandos en la cónsola del mismo

```bash
enable
configure terminal
interface FastEthernet 0/1
ip address 160.223.148.221 255.255.255.252
no shutdown
exit
interface fastEthernet 0/0
ip address  160.223.146.1 255.255.255.0
no shutdown
exit
end
wr
show ip interface brief
```
* <h3>3) Configuración del Protocolo OSPF</h3>

    * <h4>3.1) Configuración del Enrutador 1</h4>

    Ejecute los siguientes comandos en el enrutador 1


    ```bash
    configure terminal
    router ospf 1
    network 160.223.148.192  0.0.0.3 area 1
    network 160.223.145.0 0.0.0.255 area 1
    end
    ```
   * <h4>3.2) Configuración del Enrutador 2</h4>

    Ejecute los siguientes comandos en el enrutador 2


    ```bash
    configure terminal
    router ospf 1
    network 160.223.148.196   0.0.0.3 area 1
    network 160.223.148.160   0.0.0.31 area 1
    end
    ```

    * <h3>3.3) Configuración del Router 3</h3>

    Ejecute los siguientes comandos en el enrutador 3


    ```bash
    configure terminal
    router ospf 1
    network 160.223.148.192 0.0.0.3 area 1
    network 160.223.148.196  0.0.0.3 area 1
    network 160.223.148.236 0.0.0.3 area 0
    network 160.223.148.224 0.0.0.3 area 0
    end
    ```

    * <h4>3.4) Configuración del Enrutador 4</h4>

    Ejecute los siguientes comandos en el enrutador 4


    ```bash
    configure terminal
    router ospf 1
    network 160.223.148.200 0.0.0.3 area 2
    network 160.223.147.0  0.0.0.127 area 2
    end
    ```

     * <h4>3.5) Configuración del Enrutador 5</h4>

    Ejecute los siguientes comandos en el enrutador 5


    ```bash
    configure terminal
    router ospf 1
    network 160.223.147.128 0.0.0.3 area 2
    network 160.223.148.204  0.0.0.127 area 2
    end
    ```

    * <h3>3.6) Configuración del Router 6</h3>

    Ejecute los siguientes comandos en el enrutador 6


    ```bash
    configure terminal
    router ospf 1
    network 160.223.148.200 0.0.0.3 area 2
    network 160.223.148.204  0.0.0.3 area 2
    network 160.223.148.224 0.0.0.3 area 0
    network 160.223.148.228 0.0.0.3 area 0
    end
    ```

   
    * <h3>3.7) Configuración del Router 7</h3>

    Ejecute los siguientes comandos en el enrutador 7


    ```bash
    configure terminal
    router ospf 1
    network 160.223.148.236 0.0.0.3 area 0
    network 160.223.148.232  0.0.0.3 area 0
    network 160.223.148.208 0.0.0.3 area 3
    network 160.223.148.212 0.0.0.3 area 3
    end
    ```

     * <h4>3.8) Configuración del Enrutador 8</h4>

    Ejecute los siguientes comandos en el enrutador 8


    ```bash
    configure terminal
    router ospf 1
    network 160.223.148.208 0.0.0.3 area 3
    network  160.223.144.0  0.0.0.255 area 3
    end
    ```

     * <h4>3.9) Configuración del Enrutador 9</h4>

    Ejecute los siguientes comandos en el enrutador 9


    ```bash
    configure terminal
    router ospf 1
    network 160.223.148.212 0.0.0.3 area 3
    network  160.223.148.0  0.0.0.127 area 3
    end
    ```

    * <h3>3.10) Configuración del Router 10</h3>

    Ejecute los siguientes comandos en el enrutador 10


    ```bash
    configure terminal
    router ospf 1
    network 160.223.148.232 0.0.0.3 area 0
    network 160.223.148.228  0.0.0.3 area 0
    network 160.223.148.216 0.0.0.3 area 4
    network 160.223.148.220 0.0.0.3 area 4
    end
    ```

     * <h4>3.11) Configuración del Enrutador 11</h4>

    Ejecute los siguientes comandos en el enrutador 11


    ```bash
    configure terminal
    router ospf 1
    network 160.223.148.216 0.0.0.3 area 4
    network  160.223.148.128  0.0.0.31 area 4
    end
    ```


   * <h4>3.12) Configuración del Enrutador 12</h4>

    Ejecute los siguientes comandos en el enrutador 12


    ```bash
    configure terminal
    router ospf 1
    network 160.223.148.220 0.0.0.3 area 4
    network  160.223.146.0  0.0.0.255 area 4
    end
    ```

* <h3> 4) Verificación de las conexiones </h3>
Para verificar el funcionamiento de la topología y la creación de las rutas dinámicas podemos ejecutar los siguientes comandos

```bash
show ip ospf
show ip route
```

