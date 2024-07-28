<h2> Punto flotante </h2>


Numero reales en coma flotante 

<h3>Procedimiento</h3>

* **Paso 1:**  Convetir al sistema binario.
* **Paso 2:** Escribir en notacion cientifica.
* **Paso 3:** Calcular el bias.
* **Paso 4:** Combertir el exponete a binario.
* **Paso 5:** Remplazar.

Dado el numero 82.25

<h4>Paso 1</h4>

 Convetir al sistema binario.

| numero | dividos | residuo |
| ---------- | --------- | ---------- |
| 82         | 2          | 0           |
| 41         | 2          | 1           |
| 20         | 2          | 0           |
| 10         | 2          | 0           |
| 5           | 2          | 1           |
| 2           | 2          | 0           |
| 1           | 2          | 1           |

$$ 82.25    $$
$$ 0.25 * 2 = 0.5    =>  0 $$
$$ 0.5 * 2 = 1.0    =>  1 $$

$$ (1010010.01)_{2} $$


<h4>Paso 2</h4>

Escribir en notacion cientifica.

$$ 1.01001001* 2^{6} $$


<h4>Paso 3</h4>

Calcular el bias. 

El bias se calcula por medio de la formula 

$$ 2^{n-1} -1   $$

Donde en es el tamño de la catidad de bits que se permiten para el exponente

en este caso trabajaremso con el formato IEE 754 estandar donde  n = 8, es decir

$$  2^{8-1} -1  = 127 $$

Es decir el exponete nuestro es igual a la suma de la cantidad de pasos que dimos mas el bias 

$$ 127 + 6 = 133 $$

<h4>Paso 4</h4>

Pasar a binario el exponente. 

$$ 1000101_{2} $$


<h4>Paso 5</h4>

Remplazamos.

| signo | exponente |                   mantisa                   |
| ------- | -------------- | ---------------------------------------- |
| 0        | 10000101  | 010010010000000000000000 |


