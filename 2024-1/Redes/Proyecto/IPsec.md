<h2> IPsec  (Internet Protocol Security) </h2>

<p  style="background-color:#184756; padding:10px; border-radius: 5px ; color:white " >
Es un conjunto de protocolos de seguridad para la red que protege las comunicaciones de datos a través de redes <strong>IP</strong> mediante procesos de autenticación y cifrado. Su objetivo es garantizar la confidencialidad, integridad y autenticación de los datos que se envían entre dos puntos en una red.
<br>
<strong>IPsec</strong> se utiliza comúnmente para establecer <strong>VPNs</strong> <i>(Redes Privadas Virtuales)</i>, permitiendo una conexión segura entre dos puntos a través de una red pública como Internet. Proporciona un medio seguro para que las empresas y los usuarios transmitan información sensible y mantengan la privacidad de sus comunicaciones.
</p>


### Capa del Modelo TCP/IP donde Funciona IPsec

IPsec opera en la **Capa de Red** del modelo TCP/IP. Su función principal es proporcionar seguridad a nivel de paquete durante la transmisión de datos a través de redes IP, lo que incluye servicios como la autenticación y el cifrado.

### Formato de los Mensajes IPsec

IPsec utiliza dos protocolos principales para asegurar las comunicaciones: **AH (Authentication Header)** y **ESP (Encapsulating Security Payload)**. Cada uno tiene un formato diferente para sus mensajes:

- **`AH`**: Proporciona autenticación e integridad de los datos. El formato del mensaje incluye campos como el índice de seguridad, la secuencia de números y los datos de autenticación.

- **`ESP`**: Proporciona confidencialidad (cifrado de datos), así como autenticación e integridad. El formato del mensaje incluye un encabezado ESP, seguido por los datos cifrados y luego un tráiler ESP que contiene información necesaria para el proceso de descifrado.

Ambos protocolos pueden operar en dos modos: **Modo Transporte**, que protege la carga útil del paquete IP, y **Modo Túnel**, que cifra todo el paquete original y lo encapsula en un nuevo paquete IP.

IPsec es una parte esencial de la seguridad en redes modernas, protegiendo la comunicación entre dispositivos en una variedad de aplicaciones.

<hr>

- `enable`: Entra al modo EXEC privilegiado.
- `configure terminal`: Accede al modo de configuración global.
- `access-list 100 permit ip any any`: Permite tráfico IP que pasa por las interfaces definiadas.
- `crypto ipsec transform-set MY_ENCRYP esp-aes esp-sha-hmac`: Define un conjunto de transformaciones para IPsec.
- `crypto map WIRED 10 ipsec-isakmp`: Crea un mapa criptográfico para asociaciones de seguridad dinámicas.
- `set peer 160.223.145.2`: Especifica la dirección IP del otro extremo del túnel VPN.
- `set transform-set MY_ENCRYP`: Asocia el conjunto de transformaciones con el mapa criptográfico.
- `match address 100`: Asocia una ACL con el mapa criptográfico para definir el tráfico protegido.
- `crypto isakmp policy 10`: Crea una política ISAKMP con prioridad.
- `encryption aes`: Utiliza AES para cifrar los datos en ISAKMP.
- `hash sha`: Utiliza SHA para la integridad de datos en ISAKMP.
- `authentication pre-share`: Usa una clave precompartida para autenticación en ISAKMP.
- `group 2`: Usa el grupo Diffie-Hellman 2 para el intercambio de claves.
- `lifetime 86400`: Establece la duración de la asociación ISAKMP (24 horas).
- `crypto isakmp key PASSWORD address 160.223.145.2`: Configura una clave precompartida para un peer específico.
- `interface fastEthernet 0/1`: Accede a la configuración de una interfaz específica.
- `crypto map WIRED`: Aplica el mapa criptográfico a la interfaz seleccionada.
- `end`: Sale del modo de configuración global.

<hr>

- **Conjunto de Transformaciones *(Transform Set)***: Es un conjunto de algoritmos y claves que se utilizan para proteger el flujo de datos en una VPN IPsec. Incluye algoritmos de cifrado y hash para garantizar la confidencialidad e integridad de los datos.
    - **`esp-aes`**: Es un algoritmo de cifrado utilizado en el protocolo **ESP** *(Encapsulating Security Payload)* de IPsec. **AES** *(Advanced Encryption Standard)* es un algoritmo de cifrado simétrico que proporciona una fuerte seguridad para los datos.

    - **`esp-sha-hmac`**: Es una combinación de algoritmos utilizados para la autenticación e integridad de los datos en el protocolo **ESP** de IPsec. **SHA** *(Secure Hash Algorithm)* es un conjunto de funciones hash criptográficas diseñadas por la NSA. **HMAC** *(Hash-based Message Authentication Code)* es un tipo de código de autenticación de mensajes que utiliza una función hash criptográfica junto con una clave secreta.


- **ISAKMP *(Internet Security Association and Key Management Protocol)***: Es un protocolo utilizado para establecer, negociar y gestionar las claves y asociaciones de seguridad para la protección de comunicaciones en una red IP. **ISAKMP** es parte del conjunto de protocolos **IPsec**.

- **ACL *(Access Control List)***: Es una lista que se utiliza para proporcionar seguridad al controlar el tráfico que entra y sale de una red. Las ACL permiten o deniegan el paso de paquetes de datos basándose en una serie de reglas definidas por el administrador de la red.

- **SHA *(Secure Hash Algorithm)*:** Es un conjunto de funciones hash criptográficas que convierten los datos de entrada *(como un mensaje)* en una cadena de longitud fija, que se conoce como valor hash o resumen del mensaje. Este proceso es unidireccional, lo que significa que a partir del valor hash no se puede recuperar el mensaje original. El propósito principal de **SHA** y otras funciones hash es garantizar la integridad de los datos. Se utiliza para verificar que los datos no hayan sido alterados durante la transmisión o el almacenamiento. En el contexto de **IPsec** y otras aplicaciones de seguridad, **SHA** se utiliza para crear un **HMAC**, que proporciona tanto integridad de datos como autenticación de mensajes.

- **Mapa Criptográfico *(Crypto Map)*:** Es una característica utilizada en `routers` y `firewalls` para implementar políticas de seguridad para **VPNs IPsec**. Un mapa criptográfico asocia varias configuraciones y parámetros de seguridad, como conjuntos de transformaciones, listas de acceso *(ACLs)*, y peers **VPN**, con una interfaz de red específica. Los mapas criptográficos permiten que el tráfico que pasa por la interfaz sea cifrado y autenticado según las políticas definidas, asegurando así una comunicación segura entre los puntos finales de la **VPN**. Son esenciales para la configuración y el mantenimiento de túneles **VPN IPsec**.

<hr>

## Comandos para verificar que la conexion del IPsec 

**Verifica las Listas de Acceso:**

* Asegúrate de que las listas de acceso (ACLs) estén correctamente configuradas para el tráfico que deseas proteger.

```bash
show access-lists
```
**Verifica las Interfaces:**


* Asegúrate de que las interfaces a las que se aplica el crypto map estén correctamente configuradas y activas.

```bash
show ip interface brief
```
**Verifica el Estado del Crypto Map**

* Asegúrate de que el crypto map esté aplicado a la interfaz correcta.

```bash
show crypto map
```
**Verifica la Configuración de ISAKMP**

```bash
show running-config | include crypto isakmp
```

**Verifica la Configuración de IPsec**

```bash
show running-config | include crypto ipsec
```

**Verifica la Configuración del Crypto Map**

```bash
show running-config | include crypto map
```

**Verifica la Aplicación del Crypto Map a la Interfaz**

```bash
show running-config interface fastEthernet 0/1
```