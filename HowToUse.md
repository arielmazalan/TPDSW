## Cómo Utilizarlo por Primera Vez
1.  Entrar a la carpeta de la proposal, ahí encontrarás ambos links para el repositorio de backend como el de frontend. Dentro de cada uno de los repositorios, en la sección de *releases*, habrá una llamada **Lanzamiento para regularidad**. Descargar esa versión de cada uno de los repositorios.

2. **Configuración Técnica Inicial:** Dado que el proyecto requiere bases de datos, datos precargados y claves de API externas, por favor dirígete al **[repositorio backend](https://github.com/TomasRibotta20/FrontEnd_fantasy)** y sigue estrictamente sus "Pasos de Ejecución" para levantar el contenedor, cargar el `.sql` y configurar las variables de entorno (`.env`). Realiza la misma configuración de variables en el repositorio **[Frontend](https://github.com/TomasRibotta20/BackEnd_Fantasy)** siguiendo su propio manual.

3. Una vez con el backend y el frontend descargados y configurados, abre una terminal en cada carpeta y realiza un `pnpm install` en ambos para descargar las dependencias necesarias en el proyecto.

4. Correr el backend con el comando `pnpm run start:dev` y el frontend con el comando `pnpm run dev` al mismo tiempo. Realizando esto, se le abrirá en un navegador la página principal del login en el puerto `5173`. A partir de aquí podrá realizar lo que desee, hay ciertas recomendaciones indicadas abajo.

---

## Recomendaciones de Uso

### Si deseas loguearte como Administrador

Utilizar las siguientes credenciales:
> **Email:** `admin@admin.com`
> **Contraseña:** `admin123`

Dentro de la aplicación ya van a estar precargados los datos de los partidos, jornadas,clubes y jugadores, y va a estar preseteada como jornada activa la jornada 1. Dentro del lado de administrador podrás acceder a todos los CRUDs disponibles, así como al control de jornadas donde podrás elegir la jornada que está activa, habilitar y deshabilitar las modificaciones (lo cual permite o no que los usuarios puedan cambiar su equipo) y procesar jornadas (lo cual trae todos los datos para una jornada de cada uno de los jugadores que participaron de una API externa y calcula los puntajes para cada uno). El administrador también podrá activar el modo automatico que permite que se ejecuten los cambios de mercados y procesamientos de jornadas automaticamente sin necesidad de un admin presente (debe hacese para la primer jornada). Además de esto hay una vista que permite cargar datos de otro año (si la API lo permite), trayendo nuevos partidos, jornadas, clubes y jugadores (hay que tener en cuenta al ejecutar esta función la base de datos es borrada y creada desde cero).

### Para loguearte como Usuario

Realizar el registro a través de la aplicación y luego hacer un login con las credenciales introducidas previamente.

Dentro del lado del usuario, lo primero que debemos realizar es darle un nombre a nuestro equipo y se creará un equipo aleatoriamente con 11 jugadores titulares y 4 suplentes. Luego, en nuestra sección de **Mi Equipo**, podremos modificar la alineación y jugadores a nuestro gusto, clickeando un jugador y cambiándolo por un suplente o por algún jugador obtenido a través del listado de jugadores con filtro que aparece en la pantalla. Luego, podremos también en la sección **Jornadas** ver el resultado de nuestro equipo en las jornadas en las que participó (es decir, en las jornadas donde ya existía el equipo antes de que el administrador procesara los datos de la misma).

### Flujo Básico

Crear varios usuarios, uno por cada amigo que quiera jugar, y elegir los jugadores para que jueguen esa jornada. Luego, antes de que la jornada comience en la vida real, el que ejecute el rol de administrador deberá deshabilitar las modificaciones. Una vez la jornada en la vida real terminó, el admin deberá procesar la jornada (lo cual tarda bastante tiempo por el número de peticiones que se pueden realizar a la API por minuto) y luego volver a habilitar las modificaciones.

Luego, del lado del usuario, cada una de las personas participantes podrán ver sus puntuaciones, comparar quién obtuvo mayor puntaje y prepararse para la siguiente jornada.
