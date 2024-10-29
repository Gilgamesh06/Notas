# Variables

* El uso de variables permite crear script flexibles y depurables
* Una variable tiene un **nombre** y un valor `$nombre`
* Para permitir concatenacion  `${variable}` cadena
* Bash es case sensitive
* Bas es un lenguaje NO fuertemente tipado
* Con el shell se puede crear, asignar y borrar variables
    * Creacion: `var1 = 10`
    * Asignacion `var2 = $var1`
    * Borrado `unset var1`
* El nombre de la variable pued econtener solo letras numeros o guion bajo y comienza con una letra o _ 
* Las variabes con nombres "numericos" estan reservadas
*  No se advierte sobreescrituras

* Es posible almacenar en una variable el resultado de la ejecucion de un comando
    * **Con acentos graves**
        * lista_de_archivos= `ls`
    * **Con $(...) anidable**
        * lista_de_archivos = $(ls)
        * lista_de_archivos = $(ls $(cat directorios.txt)) 
        
* Referencia indirecta Sie el vcalor de una variable es el nombre de una segunda podemos recuperar el valor de la seguna a traves de la primera
   
```bash
dosmil = numero
numero = 2000
echo $dosmil  # Referencia directa
# numero
eval echo \$$dosmil # Referencia indirecta
# 2000
```

## Variables de shell y entorno

*  **Variables Locales**
    * Presentes en la instancia actual del shell
    * No disponibles para programas iniciados desde el shell (no exportadas)
    
* **Variables de Entorno**
    * Disponibles por todo proceso hijo del shell
    * Muy utiles para la escritura de scripts y programas 
    * Pueden visualizarce mendiante el comando `env`
    * Se pueden agregar variables al entrono mendiante `export` 
    * Nombre en mayusculas por convencion
   
* **Variables de Shell**
    * Establecidas y utilizadas por el shell para su funcionamiento
    * Algunas son variables de entronos otras son locales
    * Pueden visualizarse mendiante el comando `set`
    * Convencionalmente tiene  nombre sen mayuscula
    
## Parametros pocisionales o argumentos

* Son aquellas variables cuyos nombres son numeros.
* Estas referencia a los argumentso de los comandos

*  **Variables argumento especiales**
    * `$#` Cantidad de argumentos pasados al comando
    * `"$*"` todos los argumentos en una sola palabra
    * `"$@"` todos los argumentos sepradas por ''
    * `$_` comando previo
    * `-` flags pasadas al script
    * `$$` pip del proceso shell
    * `$!` pip del ultimo trabajo ejecutandose en background
    * `$?` exit status
   
## Variables enteras

*  Las variables enteras en Bash son enteros con signo (32 bits)
* Posibilidad de overflow
* Bash por si mismo no comprende la aritmetica de punto flotante.
* Bash considera a los numeros punto decimal como cadenas
* utilizar el lenguaje bc en los  scripts si es necesario realizar calculos de punto flotante o emplear funciones amtematicas de bliliotecas

## Arrays

*  Un array es una seri de casillas, cada un contien un valor
* Casilla = elemento , los elementos se acceden mediante indices
* Los indices comienzan en 0 hasta mas de 5 mill billones
* En bash son unicamente uni-direcionales
* **Asignacion**
```bash
colores[0]=rojo
colores[2]=verde
colores[1]=amarillo
colores=([2]=verde [0]=rojo [1]=amarillo)
colores=(rojo amarillo verde)
```
* Los arrays se pueden declarar vacios explicitamente mediante
    * `declarate -a colores`
   
* Los atributos establecidos para el array (read-only) aplican a todos los elementos
* Para referencia un elemento: `${array[i]}`
* Para referenciar todo los elementos: `${array[*]}`

## Comando `getopts`

* Bash provee getopts para tratar con opciones multiples y complejas 
* Puede utiliza como una condicion en un bucle **while**, dada la especificacion del formato de opciones (validez y argumentos), en el cuerpo del `while` se procesan
* **sintaxis**
    * getopts cadena variable
        * cadena coneien letras y argumentso
        * variable cque almacena el argumento de la opcion que esta anamizando
      
