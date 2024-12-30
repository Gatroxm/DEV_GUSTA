# Cuestionario Técnico

Este cuestionario está diseñado para evaluar conocimientos y habilidades técnicas en desarrollo de software. Está organizado por categorías y niveles de dificultad.

---

## **Sección 1: Conocimientos Generales**

1. **¿Cuál es la diferencia entre Git y GitHub, y cómo se complementan en el desarrollo de software?**
   _Dificultad: Básico_
   **RESPUESTA:**  
  GIT: Es una herramienta que nos permite mediente comando realizar despluegies a reposiorios, compartir codigo fuente y adicional gestionar librerias o paquetes de desarrolladores que colaboran con nosotros.
  GitHub: Es una plataforma de uso gratuito o pago para respaldar el codigo fuente de los proyectos, permitiendo la colaboracion de multiples desarrolladores sobre el mismo proyecto.

   ***

3. **¿Qué es TypeScript y cuáles son las ventajas de su uso?**  
   _Dificultad: Básico_
   **RESPUESTA:**  
   Es una lenguaje de progrmacion usado habitualmente en Angular, que tiene una estructura definida, lo cual es su mayor ventaja ya que permite que diferentes desarrolladores puedna colaborar de un proyecto a otro permitiendo asi que en caso de cambiar de recursos asignados a un proyecto sea mas agil y sencillo continuar con el desarrollo o la mejora que se estaba desarrollado.   

   ***

4. **Explica qué es CORS (Cross-Origin Resource Sharing) y cómo se maneja en una aplicación web.**  
   _Dificultad: Intermedio_
   **RESPUESTA:**  
   Los Cors es un protocolo y se usa para permitir o no el acceso a un servicio que estemos generando, adicional brinda seguridad ya que evita que nuestras API's aun que esten expuestas no se tenga acceso a ellas facilmente si el usuario consumidor del servicio no esta en el listado de usuarios permitidos.

   ***

---

## **Sección 2: Desarrollo Frontend**

4. **¿Qué es el Virtual DOM y cómo mejora el rendimiento de React?**  
   _Dificultad: Intermedio_
   **RESPUESTA:**  
  El Virtual DOM es el espacio donde se visualiza la aplicacion, la fomra de mejorar el rendimiento es generar componentes independientes que se comuniquen entre si para que solo sean cargados al DOM cuando estos son requeridos por el usuario que esta haciendo uso de la herramienta.

   ***

5. **Escribe un componente en React que renderice una lista de elementos a partir de un array de datos.**  
   _Dificultad: Intermedio_
   **RESPUESTA:**
   const palabras ['UNO','DOS', 'TRES', 'CUATRO', 'CINCO'];
   const componente = palabras.map( (palabra) => <li> {palabra} </li> );   

   ***

7. **¿Cómo manejarías el estado global en una aplicación React?**  
   _Dificultad: Avanzado_
   **RESPUESTA:**  
   Para manejar un estado global declararia la constante de manera global usando la palabra "export" y usaria el "state" para alterar el valor de esta variable.

   ***

---

## **Sección 3: Desarrollo Backend**

7. **Explica el concepto de middleware en Express.js y proporciona ejemplos de su uso.**  
   _Dificultad: Intermedio_
   **RESPUESTA:**  
   Los middleware se usan para intervenir los procesos de las aplicaciones, tales como:
   JWT, este middleware nos sirve para controlar el acceso a los diferentes servicios que se han desarrollado, es decir, esto nos permite tener seguridad de acceso a los datos.
   Podemos tambien generar nuestros propios middleware, para evitar repetir codigo de funciones que podrian formar parte del core de negocio, por ejemplo una operacion que sea siempre tenida en cuenta para calcular el margen de participacion de un material especifico.

   ***

9. **¿Qué es NestJS y qué lo hace diferente de otros frameworks de backend?**  
   _Dificultad: Básico_
   **RESPUESTA:**  
   Es un Framework de node, que usa typescript para mantener un desarrollo de apliaciones facilmente escalables lo que permite ademas cambiar de desarrollador facilmente.
   Lo que lo hace diferente es que usa TypeScript en lujar de JavaScript. 

   ***

11. **Explica el concepto de inyección de dependencias en NestJS.**  
   _Dificultad: Avanzado_
   **RESPUESTA:**  
    Las inyecciones en NestJS se usan para implementar clases de manera recursiva, es decir que se pueden desarrollar funciones en modulos independientes y esto hara que se puedan reimplementar sin tener que replicar el codigo.

   ***

11. **Diseña una API REST para gestionar tareas (CRUD) utilizando NestJS. Registra las tareas en un archivo de texto.**  
    _Dificultad: Avanzado_
    **RESPUESTA:**

Cambio de NestJS a Laravel

    class crud (){

      function Usuarios(){
         $usuario =Usuario.all();
         
      }
    
       function Crear($request request){
         $usuario = new Usuario();
            $usuario->nombre = isset($request->nombre): $request->nombre ? '';
            $usuario->correo = isset($request->correo): $request->correo ? '';
            $usuario->telefono = isset($request->telefono): $request->telefono ? '';
            $usuario->direccion = isset($request->direccion): $request->direccion ? '';
         $usurio->save();
       }
    
       function Actualizar($request request){
         $usuario = new Usuario();
            $usuario->nombre = isset($request->nombre): $request->nombre ? $usuario->nombre;
            $usuario->correo = isset($request->correo): $request->correo ? $usuario->correo;
            $usuario->telefono = isset($request->telefono): $request->telefono ? $usuario->telefono;
            $usuario->direccion = isset($request->direccion): $request->direccion ? $usuario->direccion;
         $usurio->save();
       }
    
       function eliminar($request request){
         $usuario = Usuario.find($request->id);
         $usuario->delete();
       }
    }

    ***

---

## **Sección 4: Infraestructura y DevOps**

11. **¿Cómo configurarías un pipeline CI/CD para una aplicación usando React y NestJS?**  
    _Dificultad: Avanzado_
    **RESPUESTA:**  
    Para genear los Pipeline de integracion y despliegue continuo se siguen los siguientes pasos:
    1. Se genera la conexion a la suscripcion.
    2. Se genera la conexion al repositorio.
    3. Se escriben los comandos para la instalacion de librerias (npm i).
    4. Se genera el paquete de empaquetado que se usara para el despliegue de la apliacion (npm build).
    5. Se generar el Artefacto (ZIP con el codigo fuente generado).
    6. Se generar el despliegue el artefacto.
    7. Se genera la instruccion de descomprencion del artefacto.
    8. Se inicia el servidor (npm star).

    ***

13. **¿Qué es Docker y cómo lo usarías para empaquetar una aplicación Node.js?**  
    _Dificultad: Intermedio_
    **RESPUESTA:**  
    Docker es una herramienta para facilitar la implemtacion de aplicaciones en ambientes de tecnologias modernas que nos permite controlar y conservar versiones de aplicaciones que se encuentren funcionando y desplegadas. para empaquetar una aplicacion de node usaria el siguiente procedimiento:
    1. docker attach container (Para generar el contenedor con el codigo que se usara para el despliegue de la aplicacion)
    2. docker wait container (Bloqueamos el contenedor para prevenir cambios sobre el mismo)
    3. docker push
    4. docker restart
Con estos comandos queda desplegada la aplicacion y si funcionamiento estara bajo un infraestructura que no cambiar y que se puede restablecer o poner en marcha facilmente.

    ***

15. **Diseña una solución tecnológica (a nivel de arquitectura) para captura de datos en campo, garantizando sincronización online/offline.**  
    _Dificultad: Avanzado_
    **RESPUESTA:**  
    ![image](https://github.com/user-attachments/assets/559e6df8-f9b9-4662-802d-3d5fee384379)
    ***

---

## **Sección 5: Bases de Datos**

14. **¿Qué es una migración en bases de datos y por qué es importante?**  
    _Dificultad: Básico_
    **RESPUESTA:**  
    Las migraciones de bases de datos pueden ser de differentes tipos, por ejemplo podemos cambiar de motor, ya sea de MySql a MSSQL y visceversa.
    Son importantes porque permiten reindizar y comprobar los sectores de la base de datos a los que no se accede habitualmente ya que algunos datos a diferencia de otros no son accedidos con la misma frecuencia.

    ***

16. **Explica la diferencia entre bases de datos relacionales y no relacionales.**  
    _Dificultad: Básico_
    **RESPUESTA:**  
    Las bases de datos relacionales manejan los datos en tablas separadas permitiendo que se pueda conservar un orden de los datos mas ordenado y estructurado.
    Las base de datos no relacionales, permiten acceder a los datos de manera muy rapida, su uso esta mas orientado a procesos transaccionales de consulta de grandes volumenes de informacion.

    ***

18. **Escribe un ejemplo de cómo realizarías una consulta básica a una base de datos con un ORM en NestJS.**  
    _Dificultad: Intermedio_
    **RESPUESTA:**  

    async obtenerAlumno(): Promise<Estudiante[]> {
       return this.alumno.find({ 
           where: { 
               edad: MoreThan(14) 
           } 
    });


    ***

---

## **Sección 6: Algoritmos y Resolución de Problemas**

17. **Escribe un algoritmo en Python que busque duplicados en un array.**  
    _Dificultad: Intermedio_
    **RESPUESTA:**  
       names = ['James', "Bob", "James", "Mark", "Kate", "Sarah", "Kate"]
      print(list(set(names)))

    ***

18. **Tienes un archivo JSON llamado `data.json` que contiene información sobre ventas de una empresa. Diseña un algoritmo en Python que:**  
    _Dificultad: Intermedio_

    - Calcule la suma total de ventas por categoría.
    - Devuelva el resultado en un formato legible como un diccionario Python.
    - Opción adicional: Guarde el resultado en un nuevo archivo JSON llamado `category_sales.json`.

    **RESPUESTA:**  
    
    def calcular_ventas_por_categoria(data):
    ventas_por_categoria = {}
    for item in data:
        categoria = item['category']
        ventas = item['sales']
        if categoria not in ventas_por_categoria:
            ventas_por_categoria[categoria] = 0
        ventas_por_categoria[categoria] += ventas
    return ventas_por_categoria 

   def guardar_resultados_en_json(datos, nombre_archivo):
       with open(nombre_archivo, 'w') as archivo:
           json.dump(datos, archivo, indent=4)
    ***

20. **Diseña una arquitectura básica para una aplicación de e-commerce usando React, NestJS y PostgreSQL.**
    - Backend (NestJS):
    - Modelo básico de base de datos: Productos, usuarios y carritos en PostgreSQL.
    - Endpoints esenciales:
    - CRUD de productos.
    - Autenticación básica (registro/login con JWT).
    - Carrito de compras: agregar y listar productos.
    - Frontend (React):
    - Página inicial con listado de productos (simples).
    - Página de detalles de producto (mostrar información de un producto).
    - Carrito de compras básico (mostrar productos agregados).
    - Integración con los endpoints del backend.
    ***
