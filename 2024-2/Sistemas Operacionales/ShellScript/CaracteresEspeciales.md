# Caracteres Especiales

* Conocidos tambien como metacaracteres
* Los metacaracteres poseen significado especial para el shell
* Existen diversas categorias de acuerdo a la funcionalidad con que esten relacionados
* **Ejemplos**
    
```bash
cd ~/libros
rm *.bck
find / -name a* &
echo El dijo \¨Hola\¨
echo Gecha y hora actual: `date`
echo Hay `wc -l /etc/passwd | awk '{print $1}'` usuarios
```

| Caracter |                                   Significado                                    |
| ------------ | ------------------------------------------------------------------------ |
| ~             | Directorio home                                                               |
| `              | Sustitucion de comando                                                  |
| #             | Comentario                                                                     |
| $             | Valor de variable                                                             |
| &             | Trabajo en background                                                   |
| *              | Estrella de Klenne (Expreciones regulares)                   |
| (              | Inicio de subshell                                                            |
| )              | Fin de subshell                                                                |
| \              | Caracter de Escape                                                        |
| \|             | Pipe                                                                                 |
| ]              | Fin de conjunto de caracteres (Expresiones regulares) |
| {              | Inicio de bloque de comandos                                        |
| }              | FIn de bloque de comandos                                           |
| ;              | Secuenzializar comandos                                               |
| '              | Comilla simple (Strong quote)                                         |
| "              | Comilla dobles (Weak quote)                                          |
| <             | Redirecion entrada                                                          |
| >             | Redirecion salida                                                            |
| /              | Separador de directorios pathname                                |
| ?             | Remplazo de un caracter (Expresiones regulares)        |
| !              | Negacion de pipeline                                                      |


## Archivos , comodines y pathname expansion

* Los archivos ocultos comienza con punto (,), utilzar `ls -la` *(a:all)*

* **Comodines**
    * **`?`** un caracter cualquiera.
    * **`*`** cualquier cadena de caracteres
    * **`[...]`** Cualquier caracter entre los corchetes *(Conjunto)*
    * **`[!...]`** Cualquier caracter no perteneciente al conjunto

* **Conjuntos**
    * **`[abc]`**    a,b o c
    * **`[,.;]`** punto, coma y (punto y coma)
    * **`[a-c]`** a, b o c
    *  **`[a-z]`** Todas las minusculas
    * **`[!0-9]`** Ningun digito
    * **`[0-9!]`** Todos los digitos y el caracter `!`
    * **`[a-zA-Z]`** Todas las letras.
    
* **Expansion de llaves (Brace expasion)**
    * <span style="color:#84E4DD">prefijo {cadenas} sufijo</span>
    * `echo ca{pa,ra,sa}s`
    * capas, caras ,casas
    
## Qouting

* Desabilitar el comportamiento por defecto o imprime textualmente un metacaracter
* Proteger metacaracteres dentro de una cadena a fin de evitar que se reinterpreten o expanda por accion de shell
* Existen tre mecanismos de quoting
    * El caracter de escape `\``(Escape character)
    * Comillas dobles `"` (Double quotes)
    * Comillas simples `'` (Single quotes)
    
### El caracter de escape
    
* Es el caracter `\` (backslash)
* Evita que el siguiente caracter sea interpretado por el shell

### Comillas dobles

* Los caractere encerrados entre comilla dobles preserva su valor literal
* Tambien se conoce como Weak qouting o Partial quoting
* Los caracteres * y @ tiene un significado especia cuando se encierra comillas dobles
* **Excepciones**
    * `$` y `'` siguen mateniendo su significado especial
    * `\` sigue manteniendo su significado especial solo si antecede los caracteres $ , ' ¨ , \ o newline.
    
### Comillas simples

* Los caracteres encerrados entre comillas simples preservan su valor literal
* No se permite la desreferencia de variables entre comillas simples
* No puede aparecer una comilla simple entre dos comillas simples
* Tambien se conice como Stron quoting 

* **Excepcion** \newline

