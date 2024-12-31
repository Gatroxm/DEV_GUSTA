# Cuestionario Técnico

Este cuestionario está diseñado para evaluar conocimientos y habilidades técnicas en desarrollo de software. Está organizado por categorías y niveles de dificultad.

---

## **Sección 1: Conocimientos Generales**

1. **¿Cuál es la diferencia entre Git y GitHub, y cómo se complementan en el desarrollo de software?**
   _Dificultad: Básico_
   **RESPUESTA:**
   La diferencia radica en sus fuenciones y propositos en el desarrollo de software
   git: es un sistea de control de versiones el cual nos permite a los desarrolladores realizar cambios crear y gestionar ramas de desarrollo etc.
   gitHub: es una plataforma para alojar repositorios de Git
   ***

3. **¿Qué es TypeScript y cuáles son las ventajas de su uso?**  
   _Dificultad: Básico_
   **RESPUESTA:**  
 es un lenguaje de programación que extiende de javascript, que mejora la calidad de código y la productividad en proyectos grandes y colavorativos 
ventajas:
Tipado estatico, Mantenimiento, compatibilidad, soporte Es6+

   ***

5. **Explica qué es CORS (Cross-Origin Resource Sharing) y cómo se maneja en una aplicación web.**  
   _Dificultad: Intermedio_
   **RESPUESTA:**  
  es un mecanismo de seguridad que los navegadores implementan para controlar como un recurso alojado en un dominio puede ser accedido desde otro
el el servidor
### servidor 
´´´
const express = require('express');
const cors = require('cors');
const app = express();

app.use(cors());

appp.use(cors({
    origin: 'http://localhost:3000',    
    credentials: true,
    methods: 'GET, POST, PUT, DELETE, OPTIONS, HEAD',
    allowedHeaders: 'Content-Type, Authorization',
}));
app.listen(3000, () => {
    console.log('Server is running on port 3000');
});
´´´
### Cliente
´´´
fetch('http://localhost:3000/api/v1/users', {
    method: 'POST',
    headers: {
        'Content-Type': 'application/json',
        'Authorization': 'Bearer token'
    },
    body: JSON.stringify({
        name: 'John Doe',
        email: 'johndoe@example.com',
        password: 'password123'
    })
})
.then(res => res.json())
.then(data => console.log(data))
.catch(err => console.error(err));

´´´
   ***

---

## **Sección 2: Desarrollo Frontend**

4. **¿Qué es el Virtual DOM y cómo mejora el rendimiento de React?**  
   _Dificultad: Intermedio_
   **RESPUESTA:**  
 El virtual DOM permite actualizar más rapidas y eficientes asegurando que solo se modifique las partes del DOM necesarias, lo que mejora significativa mente el rendimiento en aplicaciones react, tengamos en cuenta que es tamnbien una representación en mejoria ligera del DOM real el cual o utiliza React para mejorar el rendimiento para las catualizaciones de la interfaz de usuario.

   ***

5. **Escribe un componente en React que renderice una lista de elementos a partir de un array de datos.**  
   _Dificultad: Intermedio_
   **RESPUESTA:**
  ´´´
import React from 'react';

const ItemList = () => {
    const items = ['manzana', 'chocolate', 'pizza', 'ice cream', 'burger', 'fries'];

    return(
        <div>
            <h1>Listado de productos</h1>
            <ul>
                {items.map(item => (
                    <li key={item}>{item}</li>
                ))}
            </ul>
        </div>
    );
};

export default ItemList;
´´´  

   ***

7. **¿Cómo manejarías el estado global en una aplicación React?**  
   _Dificultad: Avanzado_
   **RESPUESTA:**  
   Depende de la magnitud del proyecto, si es un pequeño usaría Context API por que es facíl de manejar y no requiere intalación de librerías, pero si es un proyecto robusto usaría Redux ya que es muy bueno para manejar estadoss complejos y es compatible con herramientas como Redux DevTools

   ***

---

## **Sección 3: Desarrollo Backend**

7. **Explica el concepto de middleware en Express.js y proporciona ejemplos de su uso.**  
   _Dificultad: Intermedio_
   **RESPUESTA:**  
es una función  que tiene accesso al objeto solicitud ´´´ req ´´´, al objeto respuesta ´´´ res ´´´, y la función ´´´ next ´´´ en el ciclo solicitud-respuesta
* aplicación: se ejecuta en toda la aplicación
* enrutador: se ejecuta en rutas espesificas
* incomporados: este ya esta incluido en Espress.js como ´´´ express.json() ´´´
* de terceros: Paquetes como (cors, morgan)

   ***

9. **¿Qué es NestJS y qué lo hace diferente de otros frameworks de backend?**  
   _Dificultad: Básico_
   **RESPUESTA:**  
es un fremework de backend para construir aplicaciones de lado del servidor utilizando TypeScript.
Diferncias:
* usa express por defecto.
* fomenta una arquitectura basada en modulos y patrones bien definidos.
* incluye un sistema de Dependency inyection que mejora la modularidad y facilita las pruebas.

   ***

10. **Explica el concepto de inyección de dependencias en NestJS.**  
   _Dificultad: Avanzado_
   **RESPUESTA:**  
es un patron de diseño que facilita la gestión de dependencias en una palicación al proporcionar objetps a las clases del exterior usando decoradores como ´´´ @Inject() ´´´ o ´´´ @Injectable ´´´
   ***

11. **Diseña una API REST para gestionar tareas (CRUD) utilizando NestJS. Registra las tareas en un archivo de texto.**  
    _Dificultad: Avanzado_
    **RESPUESTA:**

estucytura de carpetas 
´´´
src/
|-- app.module.ts
|-- tasks/
|   |--tasks.controller.ts
|   |--tasks.service.ts
|   |--tasks.model.ts
|   |--tasks.module.ts

tasks.model.ts
export class Tasks {
  id: string;
  title: string;
  description: string;
  status: "pending" | "in-progress" | "completed";
}


tasks.controller.ts
import {
  Controller,
  Get,
  Post,
  Body,
  Patch,
  Param,
  Delete,
} from "@nestjs/common";
import { TasksService } from "./tasks.service";
import { Tasks } from "./tasks.model";

@Controller("tasks")
export class TasksController {
  constructor(private readonly tasksService: TasksService) {}

  @Get()
  getAllTasks() {
    return this.tasksService.getAllTasks();
  }

  @Get(":id")
  getTaskById(@Param("id") id: string) {
    return this.tasksService.getTaskById(id);
  }

  @Post()
  createTask(@Body() task: Tasks) {
    return this.tasksService.createTask(task);
  }

  @Patch(":id")
  updateTask(@Param("id") id: string, @Body() task: Tasks) {
    return this.tasksService.updateTask(task);
  }

  @Delete(":id")
  deleteTask(@Param("id") id: string) {
    return this.tasksService.deleteTask(id);
  }
}

tasks.service.ts
import { Injectable } from "@nextjs/common";
import { Tasks } from "./tasks.model";
import { writeFileSynk, readFileSync, exixstsSync } from "../utils/file.utils";

const TASKS_FILE = "tasks.json";

@Injectable()
export class TasksService {
  private tasks: Tasks[] = [];

  constructor() {
    if (exixstsSync(TASKS_FILE)) {
      this.tasks = JSON.parse(readFileSync(TASKS_FILE));
    }
  }

  private saveToFile() {
    writeFileSynk(TASKS_FILE, JSON.stringify(this.tasks, null, 2));
  }

  getAllTasks(): Tasks[] {
    return this.tasks;
  }

  getTaskById(id: string): Tasks | undefined {
    return this.tasks.find((task) => task.id === id);
  }

  createTask(task: Tasks) {
    this.tasks.push(task);
    this.saveToFile();
    return task;
  }

  updateTask(task: Tasks) {
    const index = this.tasks.findIndex((t) => t.id === task.id);
    if (index > -1) {
      this.tasks[index] = task;
      this.saveToFile();
    }
  }

  deleteTask(id: string) {
    const index = this.tasks.findIndex((t) => t.id === id);
    if (index > -1) {
      this.tasks.splice(index, 1);
      this.saveToFile();
    }
  }
}

tasks.module.ts
import { Module } from "@nestjs/common";
import { TasksController } from "./tasks.controller";
import { TasksService } from "./tasks.service";

@Module({
  controllers: [TasksController],
  providers: [TasksService],
})
export class TasksModule {}

app.module.ts

import { Module } from "@nestjs/common";
import { TasksModule } from "./tasks/tasks.module";

@Module({
  imports: [TasksModule],
})
export class AppModule {}

´´´
    ***

---

## **Sección 4: Infraestructura y DevOps**

11. **¿Cómo configurarías un pipeline CI/CD para una aplicación usando React y NestJS?**  
    _Dificultad: Avanzado_
    **RESPUESTA:**  
   es un conjunto aautomatizado  de procesos que permiten a los desarrolladores realizar cambios en el código, ejecutar pruebas y desplegar la aplicación de manera rápida y eficiente 
    ***

13. **¿Qué es Docker y cómo lo usarías para empaquetar una aplicación Node.js?**  
    _Dificultad: Intermedio_
    **RESPUESTA:**  

no tengo conocimientos con docker
    ***

15. **Diseña una solución tecnológica (a nivel de arquitectura) para captura de datos en campo, garantizando sincronización online/offline.**  
    _Dificultad: Avanzado_
    **RESPUESTA:**  
 1. componentes claves
    * aplicación movil (cliente)
    * backend (API Restful)
    * base de datos local (Dispositivo)
    * mecanismo de sincronización
   
2. Detalles de arquitectura
   * FrontEnd (App móvil)
     * tecnologías: React native, Fluter, Ionic.
     * base de datos local: SQLite o IndexedDb
     * sincronización de datos: la app movil almacena los datos en una base de datos local y tiene un sistema de cola para almacenar las solicitudes que no se puedan enviar
   * BackEnd (API Restful)
      * tecnoligías: Node.js con express, nestJS
      * Base de datos: MongoDB
      * Endpoints:
        * POST/data
        * GET/data
        * PATCH/data/{id}
      * autenticador: Auth2 o JWT
   * Sincronización Datos:
     * La app se sincronizzará de manera inteligente al backend apenas tenga serviciode red
       * cuando el dispositivo este offline, los datos seran guardados localmente
       * cuando el dispositivo este online, los datos de  sincronizarán automaticamente  
---

## **Sección 5: Bases de Datos**

14. **¿Qué es una migración en bases de datos y por qué es importante?**  
    _Dificultad: Básico_
    **RESPUESTA:**  
es un proceso de cambiar o actualizar la estructura de una BD a lo largo de el timpo
por que es importante:
* evolución del modelo de datos
* versionamiento y control
* seguridad y recuperación
* facilidad de desplieges automaticos


    ***

16. **Explica la diferencia entre bases de datos relacionales y no relacionales.**  
    _Dificultad: Básico_
    **RESPUESTA:**  
 la principal diferencia es en como almacenan y estructuran los datos, asi como su flexibilidad y escalabilidad

    ***

18. **Escribe un ejemplo de cómo realizarías una consulta básica a una base de datos con un ORM en NestJS.**  
    _Dificultad: Intermedio_
    **RESPUESTA:**
    ´´´
      const data = await this.dataRepository.find()
    const data = await this.dataRepository.findOne(id)
´´´
    ***

---

## **Sección 6: Algoritmos y Resolución de Problemas**

17. **Escribe un algoritmo en Python que busque duplicados en un array.**  
    _Dificultad: Intermedio_
    **RESPUESTA:**  
 no tengo conocimientos en python

    ***

18. **Tienes un archivo JSON llamado `data.json` que contiene información sobre ventas de una empresa. Diseña un algoritmo en Python que:**  
    _Dificultad: Intermedio_

    - Calcule la suma total de ventas por categoría.
    - Devuelva el resultado en un formato legible como un diccionario Python.
    - Opción adicional: Guarde el resultado en un nuevo archivo JSON llamado `category_sales.json`.

    **RESPUESTA:**  
no tengo conocimientos en python
    ***

20. **Diseña una arquitectura básica para una aplicación de e-commerce usando React, NestJS y PostgreSQL.**
    **RESPUESTA:**
    FrontEnd
       * Librerias principales
          * React
          * React Router
          * Redux Toolkit
          * Axios
          * Boostrap
      * componentes principales
        * Home
        * product
        * cart
        * checkout
        * profile
        * adminpanel
    BackEnd
       * modulos principales
         * auth
         * user
         * products
         * cart
         * order
         * admin
      * Endpoints
        * usuarios
        * prooductos
        * carrito
        * pedidos
      * Autenticación
        * JWT
        * Midelware
      * Modelo BD
        * usuarios
        * productos
        * carrito
        * pedidos
        * Detalle de pedido 
        
    ***
