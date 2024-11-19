# Hack_REACT_FLASK_CRUD

     Carpetas a crear Hack_REACT_FLASK_CRUD_AWS_TOTAL

     Rutas en el trabajo:
          
          Repo:
          C:\Users\mhernandez.FOSPUCA\Documents\cursos\Ciclo08\Practica\hack\React\Hack_REACT_FLASK_CRUD_AWS_TOTAL\my-project
     Rutas en casa:
          Repo:
          C:\Users\Magahr\Documents\cursos\socialOplesk\socialOplesk\Ciclo08\Practicas\hacks\Hack_REACT_CRUD\Hack_REACT_FLASK_CRUD_AWS_TOTAL
         

# Paso 1.- Clone el repo
    git clone  https://github.com/magahr/Hack_REACT_FLASK_CRUD_AWS_TOTAL.git

# Paso 2.-Entre en le directorio de repo 
   cd my-project

# Paso 3: crear el virtual en el backend
    Con Bach:
        python  -m venv .venv
    
# Paso 4: activar el virtual env ubicando nuestra carpeta del virtual env creada anteriormente, en mi caso fue "venv" en el backend
    Desde la consola Bach:
        # source .venv/Scripts/activate
    Desde la consola de Cmder
        .venv\Scripts\activate
   
# Paso 5.-Cree (o colocar de otro proyecto del mismo lenguaje) el .gitignore y cloque a:
   # Environments
    .env
    .venv
    env/
    venv/
    ENV/
    env.bak/
    venv.bak/  

# crear la variable de entorno .env
   DB_USER=postgres
   DB_PASSWORD=postgres
   DB_HOST=formulariosrds.chwqcma4ef8n.us-east-2.rds.amazonaws.com
   DB_PORT=5432
   DB_NAME=formularios
    
# Paso 6.- Salir de Visual CODE

# Paso 7.- Entrar a la carpeta del repo

# Paso 8.- Abrir Visual Code desde la carpeta del repo para que se vea .venv ignorado

# Paso 9.- instalar flsk con pip, en caso que no este instaldo
     pip install Flask
     pip list
 
# Paso 10.- instalar las librerias necesaria para conectar flask con una base de datos.
     ORM:
       Flask-SQAIchemy (extension que facilita el uso de SQLAIchemy con Flask)
       
     POSTGRESS: (Adaptador de Postgress para python):
       
     Comando con pip, instalar los dos:
        pip install Flask-SQLAlchemy
        pip install psycopg2 (desde la consola de cmder)
        pip install flask-cors  
        pip install python-dotenv

     Comando para verificar que se instalo:
        pip list

# Paso 11: instalar o crear uno nuevo las dependencias necesarias las cuales dejare en un archivo requirements.txt
    Si ya esta creado, para actualizar una ves que ya se ha bajado el repo:
       # pip install -r requeriments.txt

    Si no está creado, o se quiere actualizar:
       # pip freeze > requeriments.txt

# Paso 12: Crear una nueva rama para trabajar desde alli
     git checkout -b feature/flask-con-base-de-datos

# Paso 13 : Levantar el servidor con el siguiente comando
    Con una aplicación:
    # flask --app hello run
    Con debug:
      flask run --debug

# Paso 14 : Creacion de una BASE DE DATOS
    -Entrar en la consola de postgres
       psql -U postgres (usuario)
          password postgres
       \l (lista la BD)
    -Crear la BASE DE DATOS
       CREATE DATABASE estudiantes_grupo_8;

 

# Paso 15: Configuración de la Base de Datos
   - Importar los modulos correspondientes
     from flask import Flask, jsonify, request
     from flask_sqlalchemy import SQLAlchemy
     from sqlalchemy import text
     
   - buscar la configuracion del servidor en pgadmin,
    sobre el servidor boton derecho - ajustas de conexion,
    URL y seleccionar la url la palabra que va despues de
    jdbc..(no lo consegui ver video clase30 0:48:50)

   - #app.config['SQLALCHEMY_DATABASE_URI'] = 'postgresql://myuser:mypassword@localhost:5432/mydatabase'

    Variables :
      app.config['SQLALCHEMY_DATABASE_URI'] = 'postgresql://postgres:postgres@localhost:5432/estudiantes_grupo_8'

      app.config['SQLALCHEMY_TRACK_MODIFICATIONS'] = False

      db = SQLAlchemy(app)

     Definición del modelo de datos (modelo=tabla de bd):
     modelo de estudiante.
     
     class student(db.Model):

# Paso 17 - guardar los curl 
     
     curl -X GET http://localhost:5000/students
     curl -X POST http://localhost:5000/create-student \

     curl -X GET http://localhost:5000/students/1

     curl -X PATCH http://localhost:5000/patch-student/1   \

     curl -X DELETE "http//localhost:5000/delete-student?name=Juan"

     -H "Content-Type: application/json" \
     -d '{"name": "Juan", "age": 20, "major" : "Ingenieria"}'


# Paso 16: Probar algunos de los endpoints ya creados, los cuales puedes conseguir yendo directamente al archivo hello.py 



Control de cambio

1.- git commit -m "18-11-2024 - Starting my project"
1.- git commit -m "18-11-2024 - Updating my project"


asi estaba:

  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
   "start": "concurrently \"source .venv/bin/activate && flask run\" \"npm start --prefix frontend\"",
            "frontend": "cd frontend && npm start",
            "backend": "source .venv/bin/activate && flask run",
            "setup": "python -m venv .venv && source .venv/bin/activate && pip install -r requeriments.txt"
  }, 

este es el nuevo:
"scripts": {
      "dev": "npm run setup && npm start",
      "frontend": "cd frontend && npm start",
      "backend": "source .venv/bin/activate && flask run",
      "setup": "python -m venv .venv && source .venv/bin/activate && pip install -r requeriments.txt"
},
