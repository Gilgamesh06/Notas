<h2>INSTALAR UNA CA PARA GENERAR CERTIFICADOS</h2>

1. <h3> Instalar el software para crear una CA</h3>

```bash     
apt install  easy-rsa
```

2. <h3>Copiar la configuración para generar los certificados</h3>

```bash
cd /root
cp -a /usr/share/easy-rsa/ easy-rsa-example
cd easy-rsa-example
```


3.  <h3>Editar el archivo "vars" y fijar los valores para las siguientes variables</h3>


```bash
set_var EASYRSA_DN		"org"
set_var EASYRSA_REQ_COUNTRY     "CO"
set_var EASYRSA_REQ_PROVINCE    "SD"
set_var EASYRSA_REQ_CITY        "Bucaramanga"
set_var EASYRSA_REQ_ORG         "UIS"
set_var EASYRSA_REQ_EMAIL       "gilberto.diaz@uis.edu.co"
set_var EASYRSA_REQ_OU          "SC3"
set_var EASYRSA_KEY_SIZE        2048
set_var EASYRSA_CA_EXPIRE       3650
set_var EASYRSA_CERT_EXPIRE     3650
```

4.  <h3>Eliminar los certificados previos</h3>

```bash
./easyrsa init-pki
```

5. <h3>Generar el certificado de la CA</h3>

```bash
./easyrsa build-ca 
```

ca key = lain

Seleccione las respuestas según se muestra a continuación. Luego de la configuración del archivo 
anterior, En casi todas las opciones se ingresa ENTER

```bash
#Note: using Easy-RSA configuration from: ./vars
#Generating a 2048 bit RSA private key
#..............................................+++
#......+++
#writing new private key to '/root/easy-rsa-example/pki/private/ca.key.ZCGZKGuZJ8'
#Enter PEM pass phrase: ESCRIBA UNA CONTRASEÑA PARA EL CERTIFICADO DE LA CA
#Verifying - Enter PEM pass phrase: REPITA LA CONTRASEÑA
#-----
#You are about to be asked to enter information that will be incorporated
#into your certificate request.
#What you are about to enter is what is called a Distinguished Name or a DN.
#There are quite a few fields but you can leave some blank
#For some fields there will be a default value,
#If you enter '.', the field will be left blank.
#-----
Country Name (2 letter code) [CO]: ENTER
State or Province Name (full name) [SD]: ENTER
Locality Name (eg, city) [Bucaramanga]: ENTER
Organization Name (eg, company) [UIS]: ENTER
Organizational Unit Name (eg, section) [SC3]: ENTER
Common Name (eg: your user, host, or server name) [Easy-RSA CA]:SC3 CA
Email Address [gilberto.diaz@uis.edu.co]: ENTER

CA creation complete and you may now import and sign cert requests.
Your new CA certificate file for publishing is at:
/root/easy-rsa-example/pki/ca.crt
```

6. <h3>Generar la solicitud y llave del certificado del servidor. Asegúrese que el nombre del servidor sea único</h3>

```bash
./easyrsa gen-req openvpn.uis.edu.co nopass
```

En todas las preguntas se ingresa ENTER como se muestra a continuación

```bash
#Note: using Easy-RSA configuration from: ./vars
#Generating a 2048 bit RSA private key
#........................................................................+++
#................................................................................................+++
#writing new private key to '/root/easy-rsa-example/pki/private/fox1.key.9Jmo96OIh1'
#-----
#You are about to be asked to enter information that will be incorporated
#into your certificate request.
#What you are about to enter is what is called a Distinguished Name or a DN.
#There are quite a few fields but you can leave some blank
#For some fields there will be a default value,
#If you enter '.', the field will be left blank.
#-----

Country Name (2 letter code) [CO]:
State or Province Name (full name) [SD]:
Locality Name (eg, city) [Bucaramanga]:
Organization Name (eg, company) [UIS]:
Organizational Unit Name (eg, section) [SC3]:
Common Name (eg: your user, host, or server name) [fox1]:
Email Address [gilberto.diaz@uis.edu.co]:

Keypair and certificate request completed. Your files are:
req: /root/easy-rsa-example/pki/reqs/fox1.req
key: /root/easy-rsa-example/pki/private/fox1.key
```

7. <h3>Firme el certificado del servidor</h3>

```bash
./easyrsa sign-req server openvpn.uis.edu.co
```

Sólo ingrese la palabra "yes" para confirmar los datos. La salida se verá así

```bash
	#Note: using Easy-RSA configuration from: ./vars


	#You are about to sign the following certificate.
	#Please check over the details shown below for accuracy. Note that this request
	#has not been cryptographically verified. Please be sure it came from a trusted
	#source or that you have verified the request checksum with the sender.

	#Request subject, to be signed as a server certificate for 3650 days:

	#subject=
    	#countryName               = CO
    	#stateOrProvinceName       = SD
    	#localityName              = Bucaramanga
    	#organizationName          = UIS
    	#organizationalUnitName    = SC3
    	#commonName                = fox1
    	#emailAddress              = gilberto.diaz@uis.edu.co


	#Type the word 'yes' to continue, or any other input to abort.
  	
        Confirm request details: yes
	Using configuration from /root/easy-rsa-example/openssl-1.0.cnf
	Enter pass phrase for /root/easy-rsa-example/pki/private/ca.key:
	Check that the request matches the signature
	Signature ok
	The Subject's Distinguished Name is as follows
	countryName           :PRINTABLE:'CO'
	stateOrProvinceName   :ASN.1 12:'SD'
	localityName          :ASN.1 12:'Bucaramanga'
	organizationName      :ASN.1 12:'UIS'
	organizationalUnitName:ASN.1 12:'SC3'
	commonName            :ASN.1 12:'fox1'
	emailAddress          :IA5STRING:'gilberto.diaz@uis.edu.co'
	Certificate is to be certified until Jun  4 14:58:10 2027 GMT (3650 days)

	Write out database with 1 new entries
	Data Base Updated

	Certificate created at: /root/easy-rsa-example/pki/issued/fox1.crt
```

8. <h3>Generar los parámetros Diffie-Hellman del archivo .pem utilizados por el servidor</h3>

```bash
./easyrsa gen-dh
```

9. <h3>Generar el código secreto de autenticación de mensajes basado en Hash. (Hash-based Message  Authentication Code, HMAC)</h3>

```bash
apt install openvpn
openvpn --genkey --secret /root/easy-rsa-example/pki/ta.key
```


11.  <h3>Generar los certificados de los clientes. El nombre del cliente debe ser único</h3>

```bash
./easyrsa build-client-full Lain nopass
```

<h2>CONFIGURAR EL SERVIDOR OPENVPN</h2>

1. <h3>Cree el archivo</h3>

```bash
nano server.conf
```

Y agregar las siguientes líneas


```bash
                                                                                                         
port 80
proto tcp
dev tun0
topology subnet
ca /etc/openvpn/server/certs/ca.crt
cert /etc/openvpn/server/certs/openvpn.uis.edu.co.crt
key /etc/openvpn/server/certs/openvpn.uis.edu.co.key  # This file should be kept secret
dh /etc/openvpn/server/certs/dh.pem
server 10.38.45.0 255.255.255.0
ifconfig-pool-persist ipp.txt
push "dhcp-option DNS 8.8.8.8"
push "dhcp-option DNS 8.8.4.4"
client-to-client
duplicate-cn
keepalive 10 120
tls-auth /etc/openvpn/server/certs/ta.key 0 # This file is secret
#comp-lzo
#user nobody
#group nobody
persist-key
persist-tun
status openvpn-status.log
log-append  /var/log/openvpn.log
verb 3
client-config-dir /etc/openvpn/client

```

2. <h3>Copiar el directorio de los certificados</h3>


Al directorio de configuración de openvpn

```bash
cd server
mkdir certs
cd /root/easy-rsa-example/pki
cp dh.pem /etc/openvpn/server/certs/
cp ca.crt /etc/openvpn/server/certs/
cp ta.key /etc/openvpn/server/certs/
cd private
cp openvpn.uis.edu.co.key /etc/openvpn/server/certs
cd /root/easy-rsa-example/pki/issued
cp openvpn.uis.edu.co.crt  /etc/openvpn/server/certs/
```
3. <h3>Iniciar el servicio</h3>

```bash
systemctl stop openvpn.service
systemctl start openvpn@server.service
systemctl status openvpn@server.service
```

4. <h3>Crear archivo  del cliente<7h3>

```bash
cd /etc/openvpn/client
nano Lain
ifconfig-push 10.38.45.2 255.255.255.0
```


5. <h3>copiar certificados</h3>

```bash

scp -i Wiredkey.pem root@172.210.136.159:/root/easy-rsa-example/pki/issued/Lain.crt .
scp -i Wiredkey.pem root@172.210.136.159:/root/easy-rsa-example/pki/private/Lain.key .
scp -i Wiredkey.pem root@172.210.136.159:/root/easy-rsa-example/pki/ca.crt .
scp -i Wiredkey.pem root@172.210.136.159:/root/easy-rsa-example/pki/ta.key .
cd ~/Documentos/Azure
mkdir Lain
cd Key
mv ca.crt Lain.crt Lain.key ta.key ~/Documentos/Azure/Lain 
cd ..
cd Lain

``` 
6. <h3>Crear archivo configuracion del cliente</h3> 

```bash
nano Lain.ovpn
```

7. <h3>Archivo de configuracion del cliente</h3> 


```bash
client
dev tun0
proto tcp
remote 172.210.136.159 80
resolv-retry infinite
nobind
persist-key
persist-tun
ca ca.crt
cert Lain.crt
key Lain.key
tls-auth ta.key
key-direction 1
remote-cert-tls server
verb 4
#log-append openvpn.log
```

