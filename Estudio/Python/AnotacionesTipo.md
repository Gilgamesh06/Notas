# Anotaciones de Tipo

* Las **Anotaciones de tipo en Python** son una forma de agregar informacion sobre los tipos de datos que las variable, funciones y argumentos deben tener. Esto mejopra la legibilidad del codigo y ayuda  a evitar errores al proporcionar pistas sobre el tipo de datos que se espera. Aunque **Python sigue siendo dinamico** y las anotaciones no afectan la ejecucion del codigo, estas son utiles para:
    1. Mejora la documetnacion.
    2. Ayuda a herramientas como linter (`mypy`, `pylint`) a detectar errores antes de ejecutar el programa.
    3. Facilitar el mantenimiento del codigo.
    
    ## <span style="color:#2168b0">Sintaxis de las anotaciones de tipo</span>
    
    1. **Anotaciones de variables**
        * Puedes especificar el tipo de una variable utilizando `:` despues del nombre de la variable.
        
            ```python
            # Sin anotaciones
            x = 10

            # Con anotaciones
            x: int = 10  # x es un entero
            y: str = "Hola"  # y es una cadena
            z: float = 3.14  # z es un número de punto flotante
            ```
    2. **Anotaciones en funciones**
        * Las funciones puede tener anotaciones tanto en los **parametros** como en el **valor de retorno** usando `->`
       
            ```python
            # Función sin anotaciones
            def sumar(a, b):
                return a + b

            # Función con anotaciones de tipo
            def sumar(a: int, b: int) -> int:
                return a + b
            ```
            * `a:int` y  `b:int` indican que los parametros deben ser enteros.
            * `-> int` indica que al funcion debe devolver un entero.
            
   3. **Uso de `Optional` y `Union`**
       * Si un argumento puede ser mas de un tipo, se puede usar `Union` o `Optional`
        * **Union** 
        
            ```python
            from typing import Union

            # La función puede aceptar int o str como argumento
            def procesar_dato(dato: Union[int, str]) -> str:
                return str(dato)
            ```
        * **Optional**
            * `Optional` es un atajo para `Union[None , T]`, lo que significa que el valor puede ser del tipo `T` o `None`.
            
                ```python
                from typing import Optional

                def saludar(nombre: Optional[str] = None) -> str:
                    if nombre:
                        return f"Hola, {nombre}!"
                    return "Hola, mundo!"
                ```
    4. **Anotaciones en lista, tuplas y diccionarios**
        * Para estructuras de datos como Listas, Tuplas y Diccionarios, debes especificar el tipo de los elementos que contiene.
        
            ```python
            from typing import List, Tuple, Dict

            # Lista de enteros
            numeros: List[int] = [1, 2, 3, 4]

            # Tupla con dos enteros
            coordenadas: Tuple[int, int] = (10, 20)

            # Diccionario con claves str y valores float
            precios: Dict[str, float] = {
                "manzana": 1.5,
                "banana": 0.8
            }
            ```
    5. **Anotaciones para funciones que no devuelve valor**
        * Si una funcion no devuelve nada, puede anotarla como `None`

            ```python
            def imprimir_mensaje(mensaje: str) -> None:
                print(mensaje)
            ```
    6. **Anotaciones con funciones lambda**
        * Tambien puede anotar funciones lambda, aunque no es muy comun
        
            ```python
            from typing import Callable

            # Función que acepta una función como parámetro
            def aplicar_funcion(func: Callable[[int, int], int], a: int, b: int) -> int:
                return func(a, b)

            # Llamada a la función
            resultado = aplicar_funcion(lambda x, y: x + y, 3, 4)
            print(resultado)  # Salida: 7
            ```

    7. **Anotaciones para clases y metodos**
        * Tambien puede usar anotaciones de tipo en clases.
       
            ```python
            class Persona:
                def __init__(self, nombre: str, edad: int):
                    self.nombre: str = nombre
                    self.edad: int = edad

                def saludar(self) -> str:
                    return f"Hola, mi nombre es {self.nombre} y tengo {self.edad} años."
            ```

    8. **Anotaciones con generics (parametros genericos)**
    
        ```python
        from typing import TypeVar, Generic

        # Definimos un tipo genérico
        T = TypeVar('T')

        class Caja(Generic[T]):
            def __init__(self, contenido: T):
                self.contenido = contenido

            def obtener_contenido(self) -> T:
                return self.contenido

        # Uso de la clase genérica
        caja_entera = Caja(10)
        print(caja_entera.obtener_contenido())  # Salida: 10

        caja_texto = Caja("Hola")
        print(caja_texto.obtener_contenido())  # Salida: Hola
        ```
        * `TypeVar` define una variable generica y `Generic` la recibe como parametro 
        * `'T'` Es una convecion comun para nobrear estas variables
        

    9. **Listas de lista (List of Lists)**
        * Si tienes una lista que contien otras lista y deseas anotar su tipo, puedes usar, `List[List[T]` donde `T` es el tipo de los elementos dentro de la lista.
       
            ```python
            from typing import List

            # Una lista de listas de enteros
            notas: List[List[int]] = [
                [85, 90, 78],
                [88, 76, 92],
                [90, 91, 89]
            ]
            ```    
        * Si tulista contien diferentes tipos (enteros, cadenas, etc.) Puedes usar `Union`para especifiar los tipos
            
            ```python
            from typing import List, Union

            # Lista de listas que puede contener enteros o cadenas
            datos: List[List[Union[int, str]]] = [
                [1, "Math"],
                [2, "Science"],
                [3, "History"]
            ]
            ```
            
    10. **Diccionario de lista (Dict of Lists)**
        * Si tienes un **diccionario** donde las claves son cadenas y los valores son listas

            ```python
            from typing import Dict, List

            # Diccionario con claves str y valores List[int]
            materias: Dict[str, List[int]] = {
                "Matemáticas": [85, 90, 78],
                "Ciencias": [88, 76, 92],
                "Historia": [90, 91, 89]
            }
            ```
    ## <span style="color:#2168b0">Inyeccion de dependencias en POO</span>
    
    * En **POO**, es comun que una clase reciba una **dependencia** como parametro en el constructor o en un metodo especifico. Esto mejora la flexibilidad del codigo, facilita las pruebas unitarioas y promueve el principio `D` de `SOLID` (Dependency Inversion)
    
        ### <span style="color:#f39921">Ejemplo: Clases Estudiante y Materia</span>

        * Supongamos que tienes una clase `Estudiante`, que recibe una lista de objetos de tipo `Materia` mediante inyección de dependencia.

            ####  Clase `Materia`

            ```python
            class Materia:
                def __init__(self, nombre: str, profesor: str):
                    self.nombre: str = nombre
                    self.profesor: str = profesor

                def __str__(self) -> str:
                    return f"{self.nombre} impartido por {self.profesor}" 
            ```
            ####  Clase `Estudiante` que recibe una lista de `Materia`

            ```python
            from typing import List

            class Estudiante:
                def __init__(self, nombre: str):
                    self.nombre: str = nombre
                    self.materias: List[Materia] = []

                # Método que recibe una lista de objetos Materia
                def agregar_materias(self, materias: List[Materia]) -> None:
                    self.materias.extend(materias)

                def mostrar_materias(self) -> None:
                    print(f"Estudiante: {self.nombre}")
                    for materia in self.materias:
                        print(f"- {materia}") 
            ```


            ####  Uso de las clases

            ```python
            # Crear objetos de tipo Materia
            materia1 = Materia("Matemáticas", "Profesor Pérez")
            materia2 = Materia("Ciencias", "Profesor Gómez")
            # Crear un objeto Estudiante y agregar las materias
            estudiante = Estudiante("Juan")
            estudiante.agregar_materias([materia1, materia2])

            # Mostrar las materias del estudiante
            estudiante.mostrar_materias()
            ```
            ####  Salida esperada

            ```python
            Estudiante: Juan
            - Matemáticas impartido por Profesor Pérez
            - Ciencias impartido por Profesor Gómez
            ```

    
    
    

        

      


    
