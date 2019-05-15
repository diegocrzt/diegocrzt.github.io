# Listado de tareas - NodeJS

Completar la implementación del backend escrito en nodejs que fue dado y descripto en las clases anteriores. El código está disponible en [github](https://github.com/diegocrzt/nodejs-todo-list-starter).

Debes probar el código mínimamente con postman/insomnia, pero la mejor manera de comprobar que todo funcione correctamente una vez hechas todas las modificaciones es: utilizando las tareas precedentes de JS o JQuery pero modificando el archivo `todolist.js` en la línea que contiene la definición de la URL para la API

```js
const API_URL = 'https://task-backend-fpuna.herokuapp.com/tasks';
```

Cambiar por la url del backend nodejs, usualmente sería

```js
const API_URL = 'http://localhost:3000/tasks';
```

Queda a criterio del desarrollador la manera más eficaz de probar el código.

## Código proveído

El [código](https://github.com/diegocrzt/nodejs-todo-list-starter) que se provee ya tiene implementados varios de los métodos requeridos, y algunos controles necesarios, se debe leer detenidamente para completar los métodos y controles faltantes, por ejemplo ya se provee un método para manejar las peticiónes `GET /tasks` en la función `obtenerTareas()` del fichero `routes/tareas.js`, que verfica que se envién las cabeceras correctas y retorna un mensaje de error adecuado en caso de no recibir cabeceras correctas. Esta función puede usarse de ejemplo para terminar las faltantes.

El repositorio tiene su propio `README.md` para saber como instalar las dependencias y ejecutar el proyecto.

Se puede usar la función de `fork` de github para no tener que crear manualmente un repositorio propio.

## Especificaciones

Las especificaciones de este backend son las que ya conocemos y utilizamos a lo largo de los trabajos anteriores, la documentación de los endpoints puede encontrarse en detalle en [este](https://documenter.getpostman.com/view/2543680/S17kyrCZ) enlace, o se puede volver a mirar la definición del trabajo de [JavaScript](https://github.com/diegocrzt/diegocrzt.github.io/blob/master/js-task/problem/Ej_JS.md) para conocer el funcionamiento de los endpoints.

## Objetivos

- ITEM 0: Cada endpoint debe estar implementado según la especificación proveída en el link de postman. son 7 métodos en total, 3 para el path `/tasks` (`OPTIONS`, `GET`, `POST`) y 4 para el path `/tasks/:id` (`OPTIONS`,`GET`,`PUT`,`DELETE`)
- ITEM 1: Todas las funciones deben retornar una respuesta existosa con código 200 y el cuerpo adecuado en caso de que no haya problemas o una respuestas con códigos de error 400 y un mensaje JSON en el cuerpo de la respuesta en caso de error, en el mensaje de respuesta.
- ITEM 2: El método `POST /tasks` debe verificar que se envíen los campos requeridos y enviar una respuesta de error en caso contrario, se pueden ignorar los campos extra no requeridos
- ITEM 3: El método `PUT /tasks/:id` debe verificar que se envien los datos requeridos y que el objeto por actualizar exista, en caso contrario se debe enviar un mensaje de error adecuado.
- _BONUS!_ ITEM 4: Todos los mensajes de error retornaran además del código de error un objeto JSON en la repsuesta que tenga la siguiente estructura:

  ```json
  {
    "details": "Detalle del mensaje de error, ej: El objeto con id 444 no existe",
    "message": "Descripción general del mensaje de error ej: NOT FOUND"
  }
  ```

- _BONUS!_ ITEM 5: En el código proveído se utilizó mongodb como base de datos, que retorna el identificador en el campo `_id`, para que el cliente no se tenga que modificar, debes hacer que la respuesta retorne el identificador en el campo `id`, queda a criterio del desarrollador decidir como implementar esto, las soluciones que retornen ambos campos `_id` e `id` serán aceptadas como válidas.

## Criterios

- El trabajo `PUEDE` realizarse en los mismos grupos de trabajo que se venían manejando, pero cada integrante `DEBE` hacer una entrega por separado.
- El código `DEBE` estar en un repositorio github y la evaluación se hará sobre el mismo.
- El repositorio `DEBE` contener todos los ficheros necesarios para ejecutar la aplicación web, utilizando `npm install` y `npm start`.
- Es responsabilidad del desarrollador, leer, configurar o instalar las herramientas necesarias para el desarrollo. (nodejs, npm, express, express-body, mongoose, Visual Studio Code, etc.)
- La información de los estudiantes junto con el enlace al repositorio `DEBEN` ser enviados a más tardar el `lunes 3 de junio de 2019` a las `23:59:59` por medio del siguiente [formulario](https://forms.gle/ALmE1TjfFaiAJK8t8).

De aquí en más ¡éxitos! ;-)