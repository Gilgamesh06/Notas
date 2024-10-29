# Generalidades

* **Shell**
    1. Interprete de comandos
    2. Lenguaje de programacion
   
* **Entorno de trabajo**
    * Case sensitive
    * Si un programa no esta en el **PATH** `./nombre_programa`
    * Prompts
        * **$** Usuario normal
        * **#** Usuario administrador o superusuario *(root)*
       
* **Comandos** sintaxis: <span style="color:#fe456e">comandos</span>  <span style="color:#84E4DD">opciones</span> <span style="color:#a9fe91">argumentos</span>
    * Ubicaciones:
        * **`/bin`** Comandos estandar parta todos los usuarios (`ls`,`cat`,`cp`,`mv`)
        * **`/sbin`** Comandos estandar para root (`shutdown`,`mkfs`)
        * **`/usr/bin`** Comandos para todos los usuarios no presentes en todo sistema **UNIX**
        * **`/usr/sbin`** Comandos para root no presentes en todo sistema **UNIX**
        
* **Scripts**
    * Lista de comandos **UNIX** reunidos en un archivo. Reutilizacion de codigo.
    * Un script es un nuevo comando
        * Filosofia **UNIX** crear comandos complejos a partir de comandos simples
        

## Historia de los shell de `UNIX`

* El shell es independiente del SO  $\rightarrow$ generacion de docenas de shells
* **Bourne shell** *(Steven Bourne, UNIX Version 7, 1979)*, conocido como **sh**
* Principal alternatiuca a **sh** fu el **C shell** 
* **Bourne Again Shell** *(Brian Fox, Chet Ramey, 1988-1993)* **bash**
    * Creado para su uso en el proyecto **GNU** 
    * Shell estandar utilizado ampliamente en los sitemas UNIX e incluido en Linux
    

# Introduccion

## Caracteristicas de bash

* <span style="color:#ffbd80">{Bourne Shell} </span>< {Bourne shell Again} <span style="color:#ffbd80">= { C Shell } U {Korn Shell}</span>

* **Caracteristicas propias de C-shell incorporadas**
    * Manipulacion de directorios.
    * Control de trabajos
    * Expansion de llavas, para la generacion de cadenas arbitrarias.
    * Caracter tilde (`~`), manera de referencia al directorio home.
    * Alias, que permite referencia mas convenientemente comanos y sus opciones.
    * Historico de comandos, que posibilita reutilizar conados previamente tipeados.
    
* **Caracteristicas propias**
    * Edicion de linea de comandos, permite usar comandos al estilo `vi` 
    * Configuracion de teclas (key bindings) permite establecer secuencias de teclas de ediccion personalizadas.
    * Caracteristicas de programacion integrada: la funcionalidad de comandos **UNIX** (`test`, `expr`, `getopt`,`echo`) se integraron en el shell, permitiendo que tareas comunes de programacion sean realizadas mas clara y eficientemente.
    * Estructuras de control, especialmente el select para la generacion sencilla de menus.
    * Opciones y variables nuevas permiten personalizar mas el entorno.
    * Arrays uni-dimenisonales que permite facil acceso a lista de datos.
    
```bash
#!/bin/bash
#Primer script
echo "Hola mundo"
```

## Alias

* A veces la sisntaxis de los comandos es dificil de recordar, especialmente si se utiliza con varias opciones y argumentos.
* Alias = sinonimo enriquecido
* Los alias pueden definir en linea de comandos, en el archivo de configuracion `.bashrc` mendiante:
    * `alias [name=comand]`
* **Notas**
    * Se permite definir un alias de un alias
    * No estan permitido alias recursivos `$ alias ls='ls -la'`
    
* **Implicancias**
    * Brevedad 
    * Constumbre
    * Proteccion
    * Personalizacion
    
## Opciones

* Los alias permiten definir nombres convenientes para los comandos pero no cambian realmente el comportamiento del shell
*  Una opcion de shell se establece como **activa/inactiva** (`on`/`off`) y cambia efectivamente el comportamiento del shell
* Sintaxis basica (Contraintuitiva)
    * set +o opcion off
    * set -o opcion on
* Para visualizar el estado de las opciones `set -o`
* La mayoria de los nombre de opciones tiene asociado ua letra para abreviarlas , `set -o noglob -> set -f`