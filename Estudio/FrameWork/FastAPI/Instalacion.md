# Instalacion

* Pasos para la instalacion de **FastAPI**

    ## <span style="color:#2168b0">Crear un entorno virtual</span>
    
    1. **Paso 1: Instalar Python y venv**
        * Primero tenemos que tener Python y el modulo `venv`instalados
    
            ```bash
            sudo apt update
            sudo apt install python3 python3-venv python3-pip
            ```
    2. **Paso 2: Crear el entorno vitual**
        * creamos una carpeta e ingresamos en esta
        
            ```bash
            mkdir my_fastapi_project
            python3 -m venv my_fastapi_project
            cd my_fastapi_project
            ```
    3. **Activar el entorno virtual**
    
        ```bash
        source bin/activate
        ```
        * se ingresa al entorno virtual.
   
    ## <span style="color:#2168b0">Instalar FasAPI y dependecias necesarias</span>
    
    1. **Paso 1: Instalar FastAPI**
        * Usa `pip` para instalar FastAPI dentro del entorno virtual.
        
            ```bash
            pip install fastapi
            ```
    2. **Paso 2: Instalar un servidor ASGI (como Uvicorn)**
        * FastAPI necesita un servidor ASGI para ejecutarse. Uvicorn es una opcion recomendada.
       
            ```bash
            pip install uvicorn
            ```  
    3. **Paso 3: Instalar herramientas adicionales**
        * Dependiendo de tu poryecto, podrias necesitar:
            * `pydantic`  Para validacion y serializacion de datos (ya viene incluido con FastAPI).
            * `python-dotenv` Para manejar variables de entorno.
            * `httpx` Para realizar solicitudes HTTP.   
            
                ```bash
                pip install sqlalchemy python-dotenv httpx
                ```

    4. **Paso 4: Generar un archivo `requurements.txt`**
        * Es una buena practica mantener un archivo con las dependecioas del proyecto. 
        
            ```bash
            pip freeze > requirements.txt
            ```
    ## <span style="color:#2168b0">Ejecutar el servidor FastAPI</span>
    
    1. **Paso 1: Crear un archivo `main.py`**
        * Crear un archivo llamado `main.py` con el siguient contenido
        
            ```python
            from fastapi import FastAPI

            app = FastAPI() 

            @app.get("/")
            async def read_root():
                return {"Mensaje":"Hello, FastAPI"}
            ```   
    2. **Paso 2: Ejecutar el servidor**
        * Ejecutar el servidor con Uvicorn
        
            ```bash
            uvicorn main:app --reload
            ```
            * Accede a la aplicacion en `http://127.0.0.1:8000`
            * La documentacion interactiva estara disponible en `http://127.0.0.1:8000/docs`

                   
                      


