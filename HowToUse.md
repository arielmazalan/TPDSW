## Cómo Utilizarlo por Primera Vez
1.  Entrar a la carpeta de la proposal, ahí encontrarás ambos links para el repositorio de backend como el de frontend. Dentro de cada uno de los repositorios, en la sección de *releases*, habrá una llamada **Lanzamiento para aprobacion directa**. Descargar esa versión de cada uno de los repositorios.

2. **Configuración Técnica Inicial:** Dado que el proyecto requiere bases de datos, tener los datos cargados y claves de API externas, por favor dirígete al **[repositorio backend](https://github.com/TomasRibotta20/BackEnd_Fantasy/)** y sigue estrictamente sus "Pasos de Ejecución" para levantar el contenedor, cargar el `.sql`, configurar las variables de entorno (`.env`) e instalar los requisitos minimos de ejecución. Realiza la misma configuración en el repositorio **[frontend](https://github.com/TomasRibotta20/FrontEnd_fantasy)** siguiendo su propio manual.
BackEnd_Fantasy
3. Una vez con el backend y el frontend descargados y configurados, abre una terminal en cada carpeta y realiza un `pnpm install` en ambos para descargar las dependencias necesarias en el proyecto.

4. Correr el backend con el comando `pnpm run start:dev` y el frontend con el comando `pnpm run dev` al mismo tiempo. Realizando esto, se le abrirá en un navegador la página principal del login en el puerto `5173`. A partir de aquí podrá realizar lo que desee, hay ciertas recomendaciones indicadas abajo.

---

## Recomendaciones de Uso

### Si deseas loguearte como Administrador

Utilizar las siguientes credenciales:
> **Email:** `admin@admin.com`
> **Contraseña:** `admin123`

Dentro de la aplicación ya van a estar precargados los datos de los partidos, jornadas, clubes y jugadores, y va a estar preseteada como jornada activa la jornada 1. Dentro del lado de administrador podrás acceder a todos los CRUDs disponibles, así como al control de jornadas donde podrás elegir la jornada que está activa, habilitar y deshabilitar las modificaciones (lo cual permite o no que los usuarios puedan cambiar su equipo) y procesar jornadas (lo cual trae todos los datos para una jornada de cada uno de los jugadores que participaron de una API externa y calcula los puntajes para cada uno) y además se podrá actualizar los mercados de todos los torneos. Pero, para no tener que hacer todo manualmente, el administrador también podrá activar el modo automatico que permite que se ejecuten las actualizaciones de mercados y procesamientos de jornadas automaticamente sin necesidad de un admin presente (esta propiedad debe activarse, por primera vez, si o si cuando la app se encuentre con la primer jornada activada). Además de esto hay una vista que permite cargar datos de la liga argentina, pero de otro año (si la API lo permite), trayendo nuevos partidos, jornadas, clubes y jugadores (hay que tener en cuenta al ejecutar esta función la base de datos es borrada y creada desde cero).

### Para loguearte como Usuario

Realizar el registro a través de la aplicación y luego hacer un login con las credenciales introducidas previamente.

Dentro del lado del usuario, lo primero que debemos realizar es crear un torneo, dandole un nombre, una descripcion (opcional), un cupo maximo de jugadores (existe un maximo de 5 jugadores por torneo) y el nombre de su equipo para ese torneo. Luego el torneo pasará a estar en modo espera hasta que el creador del mismo decida iniciarlo. Antes de iniciar el torneo el creador tendrá un codigo de acceso único para ese torneo que podrá compartir con sus amigos para que ellos mismos se unan al torneo.
El creador del torneo tiene la capacidad de vetar usuarios mientras el torneo está en espera. Si un usuario es vetado este último no podrá volver a unirse a ese torneo con esa cuenta.
Cuando el torneo es iniciado todos los usuarios con su respectivo equipo recibirán una cantidad de 15 jugadores aleatorios (11 jugadores titulares y 4 suplentes) y recibirán un presupuesto de equipo con el cual podrán realizar las transacciones permitidas, como por ejemplo, vender un jugador de su equipo por el valor de mercado, podrán realizar pujas por jugadores que aparecieron en el mercado, podrán enviar ofertas a sus amigos de ese torneo por jugadores que tengan en su equipo, o por el contrario pordrán efectuar un clausulazo pagando la clausula del jugador sin necesidad de ofertar y por último podrán gastar saldo subiendo la clausula de uno o varios de los jugadores de sus equipos.
El creador del torneo puede expulsar a usuarios de un torneo ya iniciado. Haciendo esto el usuario es borrado del toreno y no podrá volver a unirse. Ningún usuario puede unirse a un torneo ya iniciado.
Luego, en la sección de **Mi Equipo**, el ususario podrá modificar la alineación y jugadores a su gusto, clickeando un jugador y cambiándolo por un suplente. Luego, en la sección **Jornadas**, se podrá ver el resultado de nuestro equipo en las jornadas en las que participó (es decir, en las jornadas donde ya existía el equipo antes de que el administrador procesara los datos de la misma).

### Flujo Básico

Crear varios usuarios, uno por cada amigo que quiera jugar, y elegir los jugadores para que jueguen esa jornada. Luego, antes de que la jornada comience en la vida real, el que ejecute el rol de administrador deberá deshabilitar las modificaciones. Una vez la jornada en la vida real terminó, el admin deberá procesar la jornada (lo cual tarda bastante tiempo por el número de peticiones que se pueden realizar a la API por minuto) y luego volver a habilitar las modificaciones.

Luego, del lado del usuario, cada una de las personas participantes podrán ver sus puntuaciones, comparar quién obtuvo mayor puntaje y prepararse para la siguiente jornada.
