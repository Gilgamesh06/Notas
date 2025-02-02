# Inmutabilidad

* La **inmutabilidad** significa que una vez que se crea un objetivo o estructura de datos, no puede ser modificado. Esto es especialmente importante en la programacion funcional, donde se evita cambiar el estado del programa para evitar errores relacionados con efectos secundarios.
* En vez de modificar un objeto. **se crea una copia nueva con los cambios**.

    ## Funcionamiento
    
    * En legueajes mutables (como Python y Java),es comun modificar directamente los valroes de las variables, Sin embargo, en la programacion funcional, una vez que un valor es asignado, permanece constante.
    * Cuando necesita modificar un valor, en lugar de cambiar el objeto original, se genera **un nuevo objeto** que contiene los cambios.
    
    ## Ejemplo: Python
    
    ```python
    # Mutable (modificando el valor original)
    lista = [1, 2, 3]
    lista.append(4)
    print(lista)  # [1, 2, 3, 4]

    # Inmutable (creando una nueva lista)
    lista = [1, 2, 3]
    nueva_lista = lista + [4]
    print(lista)       # [1, 2, 3] (sin cambios)
    print(nueva_lista) # [1, 2, 3, 4]
    ```
    * En el primer caso, la lista es **mutable** proque se modifica directamente.
    * En el segundo caso, la lista es **inmutable**, ya que la lista original no cambia, y se crea una nueva lista con los cambios.
    
    ## Caracteristicas

    |      **Característica**       |                                                     **Descripción**                                                     |
    | ----------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
    | **Evita efectos secundarios** | Los objetos inmutables no cambian de estado, lo que evita errores relacionados con cambios inesperados.                 |
    | **Facilita el debugging**     |                                                                                                                         |
    | **Facilita la concurrencia**  | Los objetos inmutables son seguros para trabajar en entornos multihilo, ya que no hay conflictos de estado.             |
    | **Mayor predictibilidad**     | Los objetos inmutables garantizan que una vez creados, permanecerán iguales, lo que facilita la comprensión del código. |

    ## Ventajas de la Inmutabilidad
    
    1. **Reduccion de errores**
        * Evitar modificar el estado del programa reduce los errores relacionados con variables que cambian inesperadamente.
   
    2. **Codigo mas facil de mantener**
        * El codigo que utiliza inmutabilidad es mas facil de mantener y depurar.
        
   3. **Seguridad en concurrencia**
        * Los objetos inmutables son mas seguros en programas concurrentes o multihilo, ya que no hay riesgo        

