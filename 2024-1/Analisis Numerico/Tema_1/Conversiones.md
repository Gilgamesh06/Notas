<h2>Conversiones numeros decimales y binarios</h2>

Para convertir un numero binario es decir un numero en base 2 a un numero decimal es decir en base 10 sumamos cada valor multipllicado por  2^(n)  donde n es la posicion del numero:

$$ 1010010_{(2)} = 1*2^{6} + 0*2^{5} +1*2^{4} +0*2^{3}+ 0*2^{2} + 1*2^{1}+ 0 *2^{0} $$
$$ 1010010_{(2)} = 82 $$

Para convertir un numero de decimal a binario procedemos dividiendo el numero por dos hasta obtener uno y inveritomos la cadena de residuos obtenida

| numero | dividos | residuo |
| ---------- | --------- | ---------- |
| 82         | 2          | 0           |
| 41         | 2          | 1           |
| 20         | 2          | 0           |
| 10         | 2          | 0           |
| 5           | 2          | 1           |
| 2           | 2          | 0           |
| 1           | 2          | 1           |


y luego volteamos el numero

$$ 1010010_{(2)} $$


Para convertir un numero decimal fracionario tenemos que dividir la tarea por partes la parte entera la realizamos con el metodo de division y la parte fracionario la hacemos realizanod multiplicaciones por dos hasta de la forma 

$$ 82.25    $$
$$ 0.25 * 2 = 0.5    =>  0 $$
$$ 0.5 * 2 = 1.0    =>  1 $$

es decir nuestro numero binario seria:

$$ 1010010.01 $$
$$ 1010010_{(2)} = 1*2^{6} + 0*2^{5} +1*2^{4} +0*2^{3}+ 0*2^{2} + 1*2^{1}+ 0 *2^{0} $ = 82 $$
$$ 0.01_{(2)} = 0*2^{(-1)} + 1*2^{(-2)}  =  0.25 $$
 

