# Condicionales

* Los condicionales en JavaScript son estructuras de control que permite ejecutar bloques de codigo diferentes sugun el resultado de una evaluacion logica o una condicion. Son fundamentales para tomar decisiones en el flujo del programa.

    ## <span style="color:#2168b0">Tipos</span> 
    
    1. `if`
        * El condicional `if` se utiliza para ejecutar un vloque de codigo solo si una condicion es verdadera.
        
        ```javascript
            let edad = 18;

        if (edad >= 18) {
            console.log("Eres mayor de edad.");
        }
        // Salida: "Eres mayor de edad."
        ```
                    
    2. `if...else`
        * Se utiliza cuando necesitamos manejar dos casos: uno cuando la condicion es verdadera y otor cuando es falsa.
        
        ```javascript
        let hora = 15;

        if (hora < 12) {
            console.log("Buenos días.");
        } else {
            console.log("Buenas tardes.");
        }
        // Salida: "Buenas tardes."
        ```
    3. `if...else if...else`
        * Se utiliza para manejar multiples condicionales.
        
        ```javascript
            let calificacion = 85;

        if (calificacion >= 90) {
            console.log("Excelente");
        } else if (calificacion >= 75) {
            console.log("Aprobado");
        } else {
            console.log("Reprobado");
        }
        // Salida: "Aprobado"   
        ```
    4. **Operador Ternario** `condicion ? expr1 : expr2`
       * Es una forma simplificada de escribir un `if...else`
      
        ```javascript
        let esMayor = edad >= 18 ? "Mayor de edad" : "Menor de edad";
        console.log(esMayor);
        // Salida: "Mayor de edad"
        ```
    5. `switch`
        * Es util para evaluar una expresion con multiples posibles valores. En lugar de usar varios `if...else if`, `switch` proporciona una estructura mas limpia.
        
        ```javascript
        let dia = 3;

        switch (dia) {
            case 1:
                console.log("Lunes");
                break;
            case 2:
                console.log("Martes");
                break;
            case 3:
                console.log("Miércoles");
                break;
            default:
                console.log("Día no válido");
        }
        // Salida: "Miércoles"
        ```



            
    