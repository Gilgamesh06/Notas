
* <h1> Introduccion a Numpy </h1>

<p>
El objeto principal de NumPy es la matriz multidimensional homogénea. Es una tabla de elementos (generalmente números), todos del mismo tipo, indexaos poruna tupla de enteros no negativos. En NumPy, las dimenciones se denomina <strong><i>ejes</i></strong>
<br>
Por ejemplo, la matriz de las corrdenadas de un punto en el espacio 3D, tiene un eje. Ese eje tiene 3 elementos, por lo que decimos Tiene una longitud de 3.En el ejemplo que se muestra a continuación, la matriz tiene 2 Ejes, El primer ejer Tiene una longitud de 2, el segundo eje tiene una longitud de 3. <code>[1,2,3]</code>
</p>

```python
[
    [1. , 2. , 0. ],
    [0. , 1. , 2. ]
]
```
<p>
La clase de matriz de Numpy se llama. Tambíen se le conoce con el alias. Tenga en cuenta que no es lo mismo que el estándar Python Library, que solo maneja unidimensionales y ofrece menos funcionalidad. Los atributos más importantes de un objeto son:
<ul>
    <li>ndarray</li>
    <li>array</li>
    <li>numpy.array</li>
    <li>array.array</li>
    <li>ndarray</li>
</ul>
<ul>
    <li><strong>ndarray.ndim</strong></li>
        <ul>
            <li>El número de ejes (dimensionales) de una matriz.</li>
        </ul>
    <li><strong>ndarray.shape</strong></li>
        <ul>
            <li>Las dimensiones de la matriz. Esta es una tupla de números enteros que indica. El tamaño de la matriz en cada dimensión. Para una matriz. con  n filas y m colimnas, será. La longitud de la tupla es por lo tanto , el numero de ejes. <code> example.shape (n,m) shape dim </code></li>
        </ul>
    <li><strong>ndarray.size</strong></li>
        <ul>
            <li>El numero total de elementos de la matriz.Esto es igual a la producto de los elementos de <code> .shape </code></li>
        </ul>     
    <li><strong>ndarray.dtype</strong></li>
         <ul>
            <li>Objeto que describe el tipo de los elementos de la matriz.Por ejemplo un array de elementos de tipo 8  (=64/8), mientra que uno de tipo 4 (=32/8). Lo equivalente a  <code> .float64  </code>  <code> itemsize </code>  <code> .complex32  </code>  <code> itemsize </code>  <code> ndarray.dtype.itemsize  </code></li>
        </ul>
    <li><strong>ndarray.data</strong></li>
        <ul>
            <li>El búfer que  contiene los elementos reales de la matriz. Normalmente, nonecesitaremos usar este atributo porque accederemos a los elementos de una matriz mediante funciones de indexación</li>
        </ul>
</ul>
</p>

```python
import numpy as np

a = np.arange(15).reshape(3,5)

print(a.shape, "Devuelve una tupla con el numero de filas y columnas")
print(a.ndim ,"Devuelve las dimenciones del arreglo")
print(a.size,"Devuelve el numero de elementos del arreglo")
type(a)

```

* <h3>Creacion de Matrices </h3>

<p>
Hay varias formas de crear matrices.
<br>
Por ejemplo, puede crear una matriz a partir de un lista o tupla normal de Python unsando la función. Se deduce el tipo de matriz resultante del tipo de los elementos de la secuencia . <code>array</code>
</p>

```python
import numpy as np
a = np.array([2.4,3,4])
print(a)
print(a.shape)
print(a.size)
print(a.ndim)
print(a.dtype)
```
Por lo visto np.array si le paso un lista unidimensional el me crea un arreglo vertical es decir por filas.
<br>
<code>array</code> transforma secuencias de secuencias en matrices bidimensionales,secuencias de secuencias de secuencias en matrices tridimencionales y asi sucesivamente.

```python
import numpy as np
a = np.array([ [1,2,3] , [4,5,6] ])
print(a)
print(a.shape)
print(a.size)
print(a.ndim)
print(a.dtype)
```
<code>array</code> recibe tanto tuplas como listas y pueden ser itercaladas. y puede recibir tanto valores numericos como cadenas.
<br>
El tipo de matriz tambien se puede especificar explicitamente en el momento de la creacion:


```python
import numpy as np
c= np.array([ [1,2,3] , [4,5,6] ] , dtype=complex)
print(c)
print(c.shape)
print(c.size)
print(c.ndim)
print(c.dtype)
```

A menudo, los elementos de una matriz son originalmente desconosidos, pero su tamaño es conocido.Por lo tanto, NumPy ofrece varias funciones para crear matrices con contenido de marcador de posicion inicial. Estos minimizan  la necesidad de matrices en crecimiento, una operación costosa.
<br>
La función <code>zeros </code>crea una matriz llena de ceros , la funcion <code>ones</code> crea una una matriz llena de unos. Y la funcion <code>empy</code> crea  una matriz cuyo contenido inicial es aleatorio y depende de el estado de la memoria. D e forma predeterminada, el tipo dtype de la matriz creada es float pero se puede cambiar con <code>dtype = intt64</code>
</p>

```python
import numpy as np

ceros = np.zeros((3,4))
print(ceros)
print(ceros.dtype)
unos = np.ones((2,3,4), dtype = np.int16)
print(unos)
print(unos.dtype)
aleatorio = np.empty((2,3))
print(aleatorio)
```
Para crear secuencias de números,NumPy proporciona la funcion que es análoga a la función incorporada de Python. pero devuelve un arreglo. <code>arange  range</code>


```python
import numpy as np

metodo_arange = np.arange(10,30,5) #Comienza en 10 termina en 30 y va de 5 en 5.
print(metodo_arange)
print(type(metodo_arange))
metodo_arange_float = np.arange(0,2,0.3) #Comienza en 0 va hasta 2 y va de 0.3 en 0.3.
print(metodo_arange_float)

metodo_range = np.range(10,30,5)
print(metodo_range)
print(type(metodo_range))

```

Las diferencias que noto entre <code>arange</code> y <code>range</code> es que uno me devuelve un NumPy array y el otro un lista.
<br>
Cunado se usa con argumentos de coma flotante,generalmente es no es posible predecir el numero de elementos obtenidos, debido a la precisión finita de coma flotante.Por esta ranzón , suele ser mejor para usar la función que recibe como argumento el numero de los elementos que queremos, en lugar del paso : <code>arange linspace</code>

```python
import numpy as np
from numpy import pi
metodo_linspace = np.linspace(0,2,9) # nueve numeros entre 0 y 2
print(metodo_linspace)
x = np.linspace(0,2*pi,100) # evaluar la funcion x en seno
print(x)
f = np.sin(x)
print(f)

```

* <h3>Impresion de Matrices</h3>

<ul>
    <li>Cuando imprime una matriz, NumPy la muestra de manera similar a las matriz anidad listas, pero con              el siguiente diseño:</li>
    <ul>
        <li>El ultimo eje se imprime de izquierda a derecha.</li>
        <li>El penultimo se imprime de arriba a abajo</li>
        <li>el resto tambie se imprime de arriba a abajo, con cada rebanada separada de la siguiente manera por una linea vacia</li>
    </ul> 
    <li>La matriz unidimensionales se imprimen como filas , las bidimensionales como matrices y tridimencionales como lista de matrices.</li>
</ul>

```python
a = np.arange(6)                    # array de una dimension
print(a)
b = np.arange(12).reshape(4, 3)     # array de dos dimensiones
print(b)
c = np.arange(24).reshape(2, 3, 4)  # 3 array de tres dimensiones
print(c)
```

Si  una Matriz es demasiado grande para ser impresa. NumPy omite automaticamente la parete central de la matriz y solo imprime las esquinas:

 
```python
print(np.arange(10000))
print(np.arange(10000).reshape(100,100))
```

Para desactivar este comportamiento y forzar a NumPy a imprimir toda la matriz, puede cambiar las opciones de impresion usando <code>.set_printoptions</code>

```python
np.set_printoptions(threshold=sys.maxsize)  # el modulo sys debe importarse
```

* <h3>Operaciones Basicas</h3>

Los operadores aritméticos de las matrices se aplican a los elementos. Una nueva matriz es creado y rellenado con el resultado.

```python
a = np.array([20,30,40,50])
b = np.arange(4)
print(b)
c = a-b
print(c)
b = b**2
print(b)
seno = 10* np.sin(a)
print(seno)
condicion = a < 35
print(condicion)
```

A diferencia de muchos lenguajes matriciales, el operador de producto <code>*</code> opera elementwise en matrices NumPy. El producto de la matriz se puede realizar utilizando El operador <code>@</code> o el metodo  <code>dot</code>.

```python
A = np.array([[1,1] , [0,1]])
B = np.array( [ [2,0] ,[3,4]])
C = A*B
print(C)
D = A @ B
print(D)

M = A.dot(B)
print(M)
```