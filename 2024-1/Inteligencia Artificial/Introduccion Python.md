<div style =" padding:3%; border: solid ; border-color: black">

<h1 style= "color:#D3D300 ">Introduccion Python</h1>



<strong>Python</strong> es un lenguaje de programación de propósito general y multiparadigma tipado dinámicamente de alto nivel. El uso principal en este curso es para computación científica, lo que permite un entorno potente y el uso de algunas bibliotecas populares como numpy, scipy y matplotlib.

<strong>Jupyter notebook</strong> es una aplicación web para crear y compartir documentos dinámicos con código, ecuaciones, texto y visualización.

<strong>Numpy</strong> es una biblioteca científica que proporciona un objeto de matriz multidimensional de alto rendimiento y herramientas para trabajar con estas matrices.

<h2>Fundamentos de Python</h2>

<h3 style="color:#3AA942">1) Tipos de datos python</h3>

Python maneja tipos de datos 

<strong>Enteros :</strong> <span style = " color:red">int </span>
<strong>Flotantes:</strong> <span style = " color:red">float </span>
<strong>Cadena de caracteres:</strong>  <span style = " color:red">str </span>
<strong>Boleanos :</strong> <span style = " color:red">bool </span>

<h3 style="color:#3AA942">2) Operadores en python</h3>

<h4>2.1) Operadores Aritméticos</h4>

Realizan operaciones matemáticas como suma, resta, multiplicación, etc.

```python
a = 7
b = 2
suma = a + b  # Suma
resta = a - b  # Resta
multiplicacion = a * b  # Multiplicación
division = a / b  # División
modulo = a % b  # Módulo (resto)
potencia = a ** b  # Potencia
```

<h4 style="color:#83B979">2.2) Operadores de Asignación</h4>

* Se utilizan para asignar valores a variables.

```python
x = 5  # Asigna 5 a x
```
<h4 style="color:#83B979">2.3)Operadores de Comparación:</h4>

* Comparan dos valores y devuelven un resultado booleano <strong>(Verdadero o Falso).</strong>

```python
a = 5
b = 2
igual = a == b  # ¿a es igual a b?
diferente = a != b  # ¿a es diferente de b?
mayor = a > b  # ¿a es mayor que b?
menor = a < b  # ¿a es menor que b?
mayor_igual = a >= b  # ¿a es mayor o igual que b?
menor_igual = a <= b  # ¿a es menor o igual que b?
```

<h4 style="color:#83B979">2.4) Operadores Lógicos</h4>

* Realizan operaciones lógicas como “y”, “o” y “no”.


```python
p = True
q = False
y = p and q  # "y" lógico (p y q)
o = p or q  # "o" lógico (p o q)
no_q = not q  # "no" lógico (no q)
```

<h3 style="color:#3AA942">3) Estructuras de datos en python</h3>

Python tiene varias estructuras de datos

<h4 style="color:#83B979">3.1) Listas</h4>

* Una lista es una colección ordenada de elementos.

```python
mi_lista = [ 1 , 2 , 3 , 4 , 5 ]
```
* Se define con corchetes [ ] y puede contener cualquier tipo de dato.

```python
cualquier_tipo = [ 1, 2,  3.1416, "Hola",  [ 1 , 2 , 3 , 4 , 5 ]  ]
```
* Como se denota en el ejemplo una lista puede contener otras listas <strong>(cualquier otra estrucura de datos).</strong>

* <h5 style="color:#3FB25B"> 3.1.1) Puedes acceder a elementos por índice.</h5>

```python
primer_elemento = mi_lista[0]  # Accede al primer elemento (1)
tercer_elemento = mi_lista[2]  # Accede al tercer elemento ('j')
```
*  <h5 style="color:#3FB25B"> 3.1.2) Actualización de elementos por índice</h5>
    * Puedes modificar el valor de un elemento utilizando su índice.

    ```python    
    mi_lista[2] = 'kiwi'  # Cambia 'pera' por 'kiwi'
    ```

*  <h5 style="color:#3FB25B"> 3.1.3) Manipulación de listas:</h5>
    
    * Agregar elementos:
    
    ```python
    lista.append(x): #Agrega un elemento al final de la lista.
    lista.insert(pos, x): #Inserta un elemento en una posición específica.
    ```
    * Eliminar elementos:
     
    ```python
    lista.remove(x): #Elimina la primera ocurrencia de un elemento.
    lista.pop(pos): #Elimina y devuelve el elemento en una posición dada.
    ```
    * Otros métodos útiles:
    
    ```python
    len(lista): Devuelve la cantidad de elementos en la lista.
    index(x): Devuelve el índice del primer elemento con valor x.
    sort(): Ordena los elementos de la lista.
    reverse(): Invierte los elementos de la lista.
    sum(): suma los valores de la lista.
    ```   
    * Ejemplo completo

    ```python
    demarcaciones = ['delantero', 'defensa', 'portero', 'centrocampista']
    demarcaciones.append('extremo')  # Agrega 'extremo' al final
    demarcaciones.remove('portero')  # Elimina 'portero'
    demarcaciones.sort()  # Ordena alfabéticamente
    ```
* <h5 style="color:#3FB25B"> 3.1.4) Creación de sub-listas utilizando índices</h5> 
    * Puedes extraer una porción de la lista original utilizando la notación de slicing.
    * Los índices se especifican como [inicio:fin], donde inicio es inclusivo y fin es exclusivo.
   
    ```python
    mi_lista = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
    sub_lista = mi_lista[1:4]  # Extrae elementos desde el índice 1 hasta el 3 (no incluido)
    Resultado: [2, 3, 4]
    ```
    
* <h5 style="color:#3FB25B"> 3.1.5) Creación de sub-listas utilizando saltos</h5>
    * Puedes especificar un tercer valor en el slicing para definir el salto entre elementos.

    ```python
    mi_lista = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
    sub_lista_saltos = mi_lista[1:8:2]  # Extrae elementos desde el índice 1 hasta el 7 con un salto de 2
    Resultado: [2, 4, 6, 8]
    ```
* <h5 style="color:#3FB25B"> 3.1.6) Creación de sub-listas utilizando índices negativos</h5>
    * Puedes utilizar índices negativos para contar desde el final de la lista.
    
    ```python
    mi_lista = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
    sub_lista_negativa = mi_lista[-5:-2]  # Extrae elementos desde el quinto elemento desde el final hasta el tercero desde el final
    Resultado: [6, 7, 8]
    ```

<h4 style="color:#83B979">3.2) Tuplas</h4>

* Similar a las listas, pero inmutables <strong>(no se pueden modificar después de creadas).</strong>
* Se definen con paréntesis ().

```python
mi_tupla = (10, 20, 30, "pera")
```

<h4 style="color:#83B979">3.3) Diccionarios</h4>

* Almacenan pares clave-valor.
* Se definen con llaves {}.

```python
mi_diccionario = {"nombre": "Juan", "edad": 25, "ciudad": "Bogotá"}
```
* <h5 style="color:#3FB25B"> 3.3.1) Creación de diccionarios: </h5>

    * Puedes crear un diccionario utilizando llaves { } y separando cada par clave: valor con comas.

    ```python
    mi_diccionario = {"Nombre": "Sara", "Edad": 27, "Documento": 1003882}
    ```
    
* <h5 style="color:#3FB25B"> 3.3.2) Acceso y modificación de elementos</h5>
    * Puedes acceder a los valores utilizando la clave (key)

    ```python
    nombre = mi_diccionario["Nombre"]  # Accede al valor de la clave "Nombre"
    ```
    
    * También puedes usar el método get():

    ```python
    nombre = mi_diccionario.get("Nombre")
    ```
    * Para modificar un valor, simplemente asigna un nuevo valor a la clave.

    ```python
    mi_diccionario["Nombre"] = "Laura"  # Cambia el nombre a "Laura"
    ```
    * Si la clave no existe, se añade automáticamente:

    ```python
    mi_diccionario["Direccion"] = "Calle 123"  # Añade una nueva clave "Direccion"
    ```
* <h5 style="color:#3FB25B"> 3.2.3) Iterar sobre un diccionario</h5>
    * Puedes iterar sobre las claves o los valores:

    ```python
    # Imprime las claves
    for clave in mi_diccionario:
        print(clave)
    # Imprime los valores
    for clave in mi_diccionario:
        print(mi_diccionario[clave])
    # Imprime claves y valores
    for clave, valor in mi_diccionario.items():
        print(clave, valor)
    ```

* <h5 style="color:#3FB25B"> 3.3.4) Diccionarios anidados</h5>
    * Puedes tener diccionarios dentro de otros diccionarios:

    ```python
    anidado1 = {"a": 1, "b": 2}
    anidado2 = {"a": 1, "b": 2}
    diccionario_anidado = {"anidado1": anidado1, "anidado2": anidado2}
    Código generado por IA. Revisar y usar cuidadosamente. Más información sobre preguntas frecuentes.
        ```
* <h5 style="color:#3FB25B"> 3.3.5) Métodos útiles</h5>

    ```python
    clear(): Elimina todos los elementos del diccionario.
    keys(): Devuelve una lista con las claves.
    values(): Devuelve una lista con los valores.
    ```

<h3 style="color:#3AA942">4) Condicionales</h3>    

* <h4 style="color:#83B979"> 4.1) Sentencia if </h4>
    
    * La sentencia if ejecuta un bloque de código si una condición es verdadera.

    ```python
    edad = 18
    if edad >= 18:
        print("Es mayor de edad")
    ```

* <h4 style="color:#83B979"> 4.2) Sentencia else </h4>
    
    * La sentencia else se ejecuta si la condición del if no se cumple.

    ```python
    dinero = 20
    if dinero >= 25:
        print("Puedes comprar el libro")
    else:
        print("Ve por más dinero")
    ```

* <h4 style="color:#83B979"> 4.3) Sentencia elif</h4>
    
    * La sentencia elif <strong>(abreviatura de “else if”)</strong> se utiliza para evaluar múltiples condiciones.

    ```python
    nota = 75
    if nota >= 90:
        print("Aprobado con A")
    elif nota >= 80:
        print("Aprobado con B")
    else:
        print("Reprobado")
    ```

* <h4 style="color:#83B979"> 4.4) Operadores lógicos</h4>
    
    * Puedes combinar condiciones con operadores lógicos como and, or y not.

    ```python
    temperatura = 28
    if temperatura > 30 and temperatura < 40:
        print("Hace calor")
    ```
    
<h3 style="color:#3AA942">5) Ciclos iterativos</h3>    
    
* <h4 style="color:#83B979"> 5.1) Ciclo for</h4>
    * El ciclo for se utiliza para iterar sobre una secuencia (como listas, tuplas o diccionarios) y ejecutar un bloque de código para cada elemento.

    ```python
    # Iterar sobre una lista
    numeros = [1, 2, 3, 4, 5]
    for numero in numeros:
        print(numero)
    ```
    
    * También puedes usar range() para generar una secuencia de números:

    ```python
    # Imprimir números del 0 al 9
    for i in range(10):
        print(i)
    ```
    
    * Iterar sobre un diccionario:

    ```python
    frutas = {'manzana': 'roja', 'banana': 'amarilla', 'uva': 'morada'}
    for nombre, color in frutas.items():
        print(f"{nombre} es de color {color}")
    ```
    
* <h4 style="color:#83B979"> 5.1) Ciclo while</h4>
    * El ciclo while se ejecuta mientras se cumpla una condición dada.

    ```python
    # Imprimir números del 0 al 9 usando while
    numero = 0
    while numero < 10:
        print(numero)
        numero += 1
    ```
<h3 style="color:#3AA942">6) Funciones</h3>    

* Una función se define con la palabra clave def, seguida de un nombre de función y parámetros entre paréntesis.
La sintaxis básica es la siguiente:
    
    ```python
    def mi_funcion(parametro1, parametro2):
        # Bloque de código
        return resultado
    ```
    * Función sin parámetros ni valor de retorno:

    ```python
    def di_hola():
        print("¡Hola!")
    di_hola()  # Llamada a la función: muestra "¡Hola!" en la consola
    ```

    * Función con parámetros:

    ```python
    def hola_con_nombre(nombre):
        print("¡Hola, " + nombre + "!")
    hola_con_nombre("Ada")  # Llamada a la función: muestra "¡Hola Ada!" en la consola
    ```

    * Función con múltiples parámetros y valor de retorno:

    ```python
    def multiplica(valor1, valor2):
        return valor1 * valor2
    resultado = multiplica(3, 5)  # Muestra 15 en la consola
    ```
    * Valores predeterminados para parámetros: Puedes asignar valores predeterminados a los parámetros:

    ```python
    def suma(a, b=3):
        return a + b
    resultado1 = suma(1)  # Resultado: 4
    resultado2 = suma(b=2, a=2)  # Resultado: 4
    ```
    
    * Funciones como objetos: Puedes asignar una función a una variable y usarla como tal:

    ```python
    def suma(a, b):
        return a + b
    s = suma
    resultado = s(1, 2)  # Resultado: 3
    ```
</div>