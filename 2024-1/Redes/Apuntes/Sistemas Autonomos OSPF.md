<div style=";border:solid; margin:20px; padding:3%">

<h2  style = "color:#066694">Sistemas autonomos</h2>

<div  style = "background-color:#066694; color:white; padding:10px; border-radius: 5px">
<ul>
    <li><strong>Autonomoues System: </strong>Es un conjunto de enrutadores que se encuentran bajo una misma administracion.
    <li>Los distintos protocolos de enrutamiento pueden clasificarse como:
    <ul>
        <li>Protocolos de enrutamiento <strong>interno</strong></li> 
         <li>Protocols de enrutamiento <strong>externo</strong></li>
    </ul>
</ul>
</div>


<h4 style = "color:#066694"> Rutas </h4>

<div  style = "background-color:#066694; color:white; padding:10px; border-radius: 5px">
<ul>
    <li>Una ruta esta conformada por los siguientes elementos:</li>
    <ul>
        <li>La direccion de la red destino.</li>
        <li>La mascara de la red destino.</li>
        <li>La direccion IP del router adyacente.</li>
        <li>El numero de router que hay que atravesar para llegar a la red destino (Saltos).</li>
        <li>La interfaz de red por donde deben retransmitirse los paquetes.</li>
    </ul>
</ul>
</div>

<h4 style = "color:#066694"> Algoritmos de enrutamineto dinamico </h4>

<div  style = "background-color:#066694; color:white; padding:10px; border-radius: 5px">
  <li>Vector distancia.</li>
  <li>Ruta mas corta</li>
  <li>Estado del enlace.</li>
</div>

<h4 style = "color:#066694">Estado de Enlace</h4>

<div  style = "background-color:#066694; color:white; padding:10px; border-radius: 5px">
    <li>Descubrir sus vecinos y aprender sus direcciones de redes.</li>
    <li>Medir la demora de cada enlace.</li>
    <li>Construir un paquete que dice que ya todo esta aprendido.</li>
    <li>Calcular la ruta a cada router.</li>
</div>

<h4 style = "color:#066694">Ruta mas corta</h4>

<div  style = "background-color:#066694; color:white; padding:10px; border-radius: 5px">
 <ul>
    <li>Numero de saltos.</li>
    <li>Distancia en kilometros del enlace.</li>
    <li>La ruta mas corta en los terminos anteriores y mas rapida.</li>
    <li>En general nosotros podemos etiquetar cada arco con un valor que puede ser funcion de:</li>
    <ul>
        <li>Ancho de banda.</li>
        <li>Cantidad de trafico habitual.</li>
        <li>Longitud de colas promedio.</li>
        <li>Demora,etc.</li>
    </ul>
</ul>
</div>

<h4 style = "color:#066694">Open Shortest Path First (OSPF)</h4>

<div  style = "background-color:#066694; color:white; padding:10px; border-radius: 5px">
  <ul>
  <li>Es el protocolo interior mas utilizado y fue el que remplazo a RIP (Vector Distancia). Los diseñadores debiean desarrollar un protocolo que cumpliera con los siguientes requisitos:</li>
        <ul>
            <li>Publicarse en la literatura abierta</li>
            <li>Soporte para multiples metricas:</li>
            <ul>    
                <li>Distancia fisica.</li>
                <li>Demora, etc.</li>
                <li>Tener un algoritmo dinamico que soportara cambios dinamicos de la arquitectura de la red.</li>
                <li>Enrutamiento basado en tipo de servicio.</li>
                <li>Balanceo  de carga sobre multiples enlaces.</li>
                <li>Seguridad.</li>
            </ul>
            <br>
            <li>Este protocolo soplorta tres tipos de redes:</li>
            <ul> 
                <li>Punto a punto.</li>
                <li>Redes de acceso multiple con difusion (broadcast).</li>
                <li>Redes de acceso multiple sin difusion.</li>
            </ul>
        </ul>
        <br>
        <ul>
            <li>Este protocolo trabaja mediante la utilizacion de un grafo:</li>
            <ul>
                <li>Cada nodo es un enrutador</li>
                <li>Cada arco en un enlace al cual se le asigna un (distancia,demora,.etc)</li>
                <li>Cada red de acceso multiple es representada como un nodo.</li>
                <li>Un arcoentre una red y router tiene peso 0.</li>
                <li>Permite organizar cada AS en areas numeradas.</li>
                <li>Cada area representa una red o un grupo de redes continuas.</li>
                <li>Las areas no se pueden solapar.</li>
                <li>Todos los enrutadores deben pertenecer a un area.</li>
                <li>Cada AS debe tener un area troncal (area 0).</li>
            </ul>
        </ul>
        <br>
        <ul>
            <li>Podemos encontrar tres tipos de enrutadores:
            <ul>
                <li>Inter Area</li>
                <li>Intra Area</li>
                <li>Inter AS</li>
            </ul>
        </ul>
</ul>
</div>

</div>


´