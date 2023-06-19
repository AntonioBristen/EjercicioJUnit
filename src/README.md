# Proyecto StoreWize

# Introducción

El proyecto StoreWize Conforma el Proyecto final del Capstone Proyect, agrupando en el todos los Requerimientos y Criterios de Evaluación del entrenamiento generado en la tercera y cuarta semana.
Los criterios se enlistan en el siguiente contenido. 

# Contenido
- Generación de un módulo propio del proyecto.
- Uso de reflexión para examinar una clase propia del proyecto.
- Creación de un componente Singleton.
- Creación de un componente Prototype.
- Creación de un componente Session.
- Manipulación de un Bean usando ApplicationContext.
- Manipulación de un Bean usando BeanFactory.
- TransactionManager.
- Aplicación de metodos Transactional en un componente Service
- Creación de un filtro HTTP (de tipo seguridad)
- Creación de una operación Mono.
- Creación de una operación Flux.
- Integración con SonarCloud.
- Creación de un pipeline de Jenkins para ejecutar pruebas.
- Uso del patrón de diseño Adapter.
- Uso del patrón de diseño Facade.
- Uso del patrón de diseño Proxy.
- Uso del patrón de arquitectura MVC.
- Uso del patrón de microservicios Chassis.

# Requisitos Para la Arranque del Proyecto

- Java 11 o superior
- Gradle 6.8.3 o superior
- Spring Boot 2.7.12 o superior
- Cliente de peticiones Rest (Postman)

## Antes de empezar 

Se versiona la coleccion JSON en este mismo directorio para poder importarla en su Cliente Rest y así probar el proyecto una vez este corriendo.
Para poder probar todos los endpoint del proyecto primero hay que generar el Bearer Token con la peticion JSON dentro de la carpeta Autenticator, ya que todas pasan por el filtro de segurirdad. el Token sera devuelto en un cabecero de nombre Authorization y el valor de Bearer + el token como lo muestra la imagen 0.0

![image](https://github.com/AntonioBristen/EjercicioJUnit/assets/65436475/bde8bfff-24d2-4891-89c0-252a731e1dd5)

(imagen 0.0)

Cabe señalar que el usuario por default es "username": "wizeantonio"  con un "password": "nolapodranvulnerar" si requiere cambiar este usuario tendria que modificar las constantes USER y PASS, de la clase ConstantsUtil.

# 💻: Desarrollo de Requerimientos y Criterios de Evaluación.
## Presentación del Proyecto: 

 El Proyecto StoreWize es una aplicación de microservicio basado en arquitectura MVC, el cual consume recursos de una API Restfull [Fakes Store](https://fakestoreapi.com/) con la finalidad de abastecer tanto de consumos hacia una API externa para el uso de MVC, como la obtención de datos para su  procesamiento, también implementa conexion hacia la base de datos H2 embebida en Spring para poder realizar CRUD´s  acoplando el TransaccionManager y cumplir con una implementación fiable de un esquema, cuyo objetivo es meramente académico para este proyecto, en la parte de los filtros HTTP cuenta con un filtro de seguridad basado en Oauth y la generación de un Bearer Token, todos los Requerimientos y Criterios a evaluar están agrupados en el mismo proyecto. 

El proyecto cuenta con la siguiente estructura de paquetes:

- beans
- config
- contextbeanfactory
- controllers
- daos
- entities
- exception
- parser
- repository
- services
- utils 

Cuenta tambien con un modulo importado de StoreWizeReflexion para el uso de la reflexión y del modulo indpendiente.

## Generación de un módulo propio del proyecto.

1.- Se genero un modulo independiente al principal con nombre de StoreWizeReflexion.

2.- La funcionalidad de este modulo es realizar la reflexion a los metodos de la clase ReadCategoriesService enviando como parametro de entrada el nombre de uno de los dos metodos que contiene la clase.

3.- Se muestra en la imagen 1.0 el modulo y clases.

![image](https://github.com/AntonioBristen/EjercicioJUnit/assets/65436475/8af4ca57-bdbc-4edc-8fbf-ed2693f0bab1)

(imagen 1.0)

4.- Exportación del modulo module-info.java imagen 1.1

![image](https://github.com/AntonioBristen/EjercicioJUnit/assets/65436475/62dfd179-fe3a-4b97-acda-339ad7e8427d)

(imagen 1.1)

5.- Importación del modulo hacia el proyecto StoreWize module-info.java imagen 1.2

![image](https://github.com/AntonioBristen/EjercicioJUnit/assets/65436475/15a69437-ef82-4ea2-b9d1-94b9b44be6c8)

6.- Codigo de StoreWize module-info.java imagen 1.3

![image](https://github.com/AntonioBristen/EjercicioJUnit/assets/65436475/c6788e9d-f8c4-49e0-943b-2d07d8efcb8c)

7.- Muetra de la importación del modulo en la capa de StoreWizeCategoryReflexionController imagen 1.4 

![image](https://github.com/AntonioBristen/EjercicioJUnit/assets/65436475/d4ae03d1-942c-4c36-9be6-76503f86843b)

8.- Peticiones REST a probar con esta implementación en la imagen 1.5 de la coleccion JSON

![image](https://github.com/AntonioBristen/EjercicioJUnit/assets/65436475/b827285a-6e42-404b-ae9d-d79ac2e66a07)


## Uso de reflexión para examinar una clase propia del proyecto.

1.- La reflexion esta implementada en el modulo antes aborado de StoreWizeReflexion.

2.- Se adjunta imagen 2.0 con la clase implementadora de la reflexion.

![image](https://github.com/AntonioBristen/EjercicioJUnit/assets/65436475/05779332-effb-4ba7-b8a9-d7b2c6d66c62)

(imagen 2.0)

3.- Al igual que en el punto anterior la peticion con la que se prueba esta implementacion es la misma con la peculiaridad de que recive ya sea el uno de los dos nombres de los metodos implementados en la clase, mismos que estan precargados en la tepicion en el cabecero con nombre "x-met"

## Creación de un componente Singleton.

1.- La clase de tipo Singleton explicitamente establecida es ConstantsUtil y es utilizada como proveedora de valores constantes dentro de todo el proyecto.

2.- Se adjunta la clase en la imagen 3.0

![image](https://github.com/AntonioBristen/EjercicioJUnit/assets/65436475/e1c64787-7cc5-4a85-87e4-887bb09c1c07)

(imagen 3.0)

## Creación de un componente Prototype.

1.- La clase de tipo Prototype es GeneralResponseDTO y es utilizada en todas las transacciones ya que  cacha y regresa a su vez una respuesta general para todas las peticiones evitando el estar haciendo una respuesta por cada funcionalidad y cuyo proposito es que se genere una instancia nueva en cada iteración que se requiera.

2.- Se adjunta la clase en la imagen 4.0

![image](https://github.com/AntonioBristen/EjercicioJUnit/assets/65436475/c6bf49e1-1e6f-4f7b-bd04-f7896291b56b)

(imagen 4.0)

## Creación de un componente Session.

1.- La clase de tipo Session es StoreWizeEditionController y es utilizada para recuperar la sesion del usuario y realiza una consulta  ala API [Fakes Store](https://fakestoreapi.com/) retornando como resultado los datos del usuario y el has y id de la sesión.

2.- Se adjunta la clase en la imagen 5.0

![image](https://github.com/AntonioBristen/EjercicioJUnit/assets/65436475/b6f57106-647a-4a83-8cd0-55659305ce2b)

(imagen 5.0)

## Manipulación de un Bean usando ApplicationContext.

1.- La clase donde se implemente el Applicationcontex es el controlador StoreWizeSearchesController cuya funcionalidad es generar por medio de su constructor el contexto de spring y así una de las funcionalidades es que se puede referenciar hacia una clase de tipo service sin necesidad de inyectar explicitamente codigo de ella.

2.- Se adjunta la clase en la imagen 6.0 

![image](https://github.com/AntonioBristen/EjercicioJUnit/assets/65436475/cefd25cb-8c69-49a8-9338-3916be1b6ac0)

(imagen 6.0)

📓: Estos Cuatro Criterios (Singleton, Prototipe, Session y AplicationContext )se pueden comprobar con las peticiones de la carpeta que a continuacion de muestra en la imagen 7.0

![image](https://github.com/AntonioBristen/EjercicioJUnit/assets/65436475/67933ed3-5ae8-41ef-931e-1c8b43352bbe)

(imagen 7.0)

## Manipulación de un Bean usando BeanFactory.

1.- La clase en donde podemos verificar la implementación del BeanFactory es CategoryConfig la cual recae el trabajo de generar un Bean de acuerdo al parametro de ServiceRegistry que sea enviado, pues la funcionalidad de esta es que tambien funga como un proxy y ejecute el servicio de acuerdo a el nombre del service que reciba el ServiceRegistry.

2.- En la imagen 8.0 de muestra la clase mencionada.

![image](https://github.com/AntonioBristen/EjercicioJUnit/assets/65436475/dac145af-b9fb-422f-824b-a2bd5288ef7d)

(imagen 8.0)

3.- Esta implementación se pueden comprobar con la petición de la carpeta que a continuacion de muestra en la imagen 8.1

![image](https://github.com/AntonioBristen/EjercicioJUnit/assets/65436475/240e5fcc-8e34-4731-84d3-11b30492e406)

(imagen 8.1)

## TransactionManager / Aplicación de metodos Transactional en un componente Service. 

1.- El TransactionManager se configuro con un repository apuntando a la base H2 con un key de tipo CartsEntity y su respectivo identificador de tipo Long, cuya funcionalidad recae en el service CartsService y con dos metodos de tipo Transaccional uno de solo lectura que obtiene los carritos cargados en la H2 y otro que nos permite Actualizar los carritos de la H2, tambien se cuenta con un metodo de creación de Carritos para la alimentación de la H2.

2.- En la imagen 9.0 se muestra la clase.

![image](https://github.com/AntonioBristen/EjercicioJUnit/assets/65436475/6d43537b-ba79-4e78-969c-6378961cc7e5)

(imagen 9.0)

3.- Esta implementación se pueden comprobar con las peticiones de la carpeta que a continuacion de muestra en la imagen 9.1

![image](https://github.com/AntonioBristen/EjercicioJUnit/assets/65436475/cfe30519-31d4-4b12-9349-343d56d7cfdc)

(iamgen 9.1)

## Creación de un filtro HTTP (de tipo seguridad).

1.- Para la creación del filtro HTTP de seguridad utilizando Bearer Token se implementaron las siguientes clases con las funcionalidades adelante descritas.

- SecurityConfig (Adaptador de Seguridad donde definiremos las reglas de seguridad a implementar agregando el Filtro de la autenticación como del token) 
- LoginFilter (Esta filtro se encarga de interceptar las peticiones que provengan de /acces y obtener el username y password que vienen en el body de la petición.)
- JwtUtil (Sera la clase encargada de generar el token si la utenticacion del LoginFilter fue exitosa)
- JwtFilter (Por ultimo paso tenemos la validación ahora del Token y la clase encargada para ello es JwtFilter haciendo uso tambien de la clase JwtUtil)

 2.- A continuación en la siguiente imagen 10.0 se muestran todas estas clases del filtro.

![image](https://github.com/AntonioBristen/EjercicioJUnit/assets/65436475/3e62201b-992a-49ad-83c6-57a211fac50d)

(iamgen 10.0) 

3.- Esta implementación se pueden comprobar como lo mencione en un principio del Tema con la peticion de /acces.

## Creación de una operación Mono / Creación de una operación Flux.

1.- Para estas implementaciones recurrimos nuevamente a la clase service CartsService donde se implemento una peticion Mono y una Flux solo que estas no son de tipo Transaccional, la funcionalidad es justamente Crear Crritos de compra por medio de la programacion Reactiva Mono Y Flux Utilizando tambien el Repository de H2.

2.- en la siguiente imagen 11.0 s emuestra un fragmento del codigo de la clase mencionada.

![image](https://github.com/AntonioBristen/EjercicioJUnit/assets/65436475/e463315e-79ab-43df-bc94-2ce33978f7a9)

(imagen 11.0)

3.- Esta implementación se pueden comprobar con las peticiones de la carpeta que a continuacion de muestra en la imagen 11.1

![image](https://github.com/AntonioBristen/EjercicioJUnit/assets/65436475/cfe30519-31d4-4b12-9349-343d56d7cfdc)

(iamgen 11.1)

## Integración con SonarCloud / Creación de un pipeline de Jenkins para ejecutar pruebas.

1.- Para el cumplimiento de este Criterio se adjuntan las siguientes imagenes tanto de SonarCloud como del server de Jenkins al momento de ejecutarse el Pipeline, asi como tambien en el codigo se establecio el archivo Jenkinsfile, la configuracion del sonar en el build.gradle y se deja la url del Repositorio publico [StoreWIze](https://github.com/AntonioBristen/StoreWize.git)

![image](https://github.com/AntonioBristen/EjercicioJUnit/assets/65436475/da6e8798-9216-4230-bbbb-2a1a271c311f)

![image](https://github.com/AntonioBristen/EjercicioJUnit/assets/65436475/4f92f274-b03f-41e4-acba-fbd490f340c2)

![image](https://github.com/AntonioBristen/EjercicioJUnit/assets/65436475/163663ee-5d42-4113-b447-137c489927f0)

![image](https://github.com/AntonioBristen/EjercicioJUnit/assets/65436475/57ca083e-e4af-4d4c-9bce-f3b0e129a725)

![image](https://github.com/AntonioBristen/EjercicioJUnit/assets/65436475/a0097372-e237-4741-9ba7-029fbd6a3bbc)


## Uso del patrón de diseño Adapter / Uso del patrón de diseño Facade / Uso del patrón de diseño Proxy.

1.- El Patron Adapter se emplea en parsear la respuesta de obtener productos en la clase ProductDAO imagen 12.0

![image](https://github.com/AntonioBristen/EjercicioJUnit/assets/65436475/310bebc9-a055-446f-a267-87eab39e18ba)

(imagen 12.0)

2.- El Patron Facade al generar la Interface AdpterSerice para que sea implementada por las tres clases del service categorias imagen 12.1

![image](https://github.com/AntonioBristen/EjercicioJUnit/assets/65436475/de6c56b7-15f0-4c5b-9e96-a0ead3ebaa78)

(imagen 12.1)

3.- El Patron Proxy al generar mi clase ServiceRegistry que devuelve una clase de tipo beanfactory de manera dinamica imagen 12.2 de acuerdo al nombre del path ingresado.

![image](https://github.com/AntonioBristen/EjercicioJUnit/assets/65436475/8d86e1fa-d71b-4639-a307-df2674c15e3d)

(imagen 12.2)

## Uso del patrón de arquitectura MVC.

1.- Se estructura del proyecta ueda consttar como se estan usando las capas de la vista entrando por nuestra API aplicando un filtro de seguridad, y cayendo en nuestra capa de controlador por medio de los RestControllers, y llevando la capa del negocio hacia los services, dejando en un punto independiente a la capa de Modelo.

![image](https://github.com/AntonioBristen/EjercicioJUnit/assets/65436475/d8e162be-e2aa-4e52-947f-cef5f773daf2)

(imagen 13.0)

## Uso del patrón de microservicios Chassis.

2.- Se adjunta la imagen 14.0 reflejando el patrón Chassis empleado en este proyecto así como tambien se visualiza la dependencia MVC de Sping 

![image](https://github.com/AntonioBristen/EjercicioJUnit/assets/65436475/9f1fef8e-1961-45e0-b62b-36189d043cff)

(imagen 14.0)
