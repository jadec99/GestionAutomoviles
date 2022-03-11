# GestionAutomoviles
Proyecto final Liceo la Paz

Javier Debén Chacón

## Resumen
Como su nombre indica, el proyecto es un gestor de automóviles por el cual se organizan vehículos según su modelo o propietario. Permite **añadir**, **editar** o **eliminar** datos añadidos de cada vehículo o cliente. 
Se incluye información como marcas, modelos, año de lanzamiento, gastos que produce el vehículo (litros, taller...). Se puede comenzar desde clientes o marcas, los cuales desplegarán
información relacionada a estos y una opción para añadir más datos. Estos dos apartados sirven como el comienzo de una guía según se va profundizando en la información (por ejemplo 
desde marcas se mostrarán un listado de estas, tras clicar en una mostrará los modelos registrados y la opción de añadir, modificar o eliminar uno de estos).

Es una manera sencilla de **organizar vehículos** y sus gastos y comparar estos con otros automóviles. También puede ser usado como una agenda, para controlar los gastos de cada cliente
y que puedan autoregularlos a su voluntad.



## Objetivos del proyecto
Con el desarrollo de esta aplicación web se busca cumplir con una serie de objetivos:

- Crear una herramienta **sencilla de utilizar** por el usuario, accesible e
intuitiva, con funcionalidades que generen sensación de utilidad, comodidad y buena
experiencia de uso.

- Buscar una **diferenciación en el mercado** al compararse con otras aplicaciones similares. El poder administrar cualquier marca de automóviles (pudiendo añadirse en cualquier en momento) es una gran ventaja en el
mundo cambiante actual (y el auge de las nuevas marcas incipientes de vehículos electrificados). A pesar de no tener porque contener una información completa en un
principio, se podrían ir añadiendo en el futuro por los usuarios. El que sea una aplicación web, permite que el acceso a ella sea totalmente transparente,
cómodo y sencillo, pudiendo entrar desde cualquier lugar en el que se encuentre el usuario siendo únicamente necesario que disponga de un dispositivo con un browser o navegador
web y una conexión a Internet. Esto nos da una amplitud de posibilidades bastante elevada, ya que abarca opciones como
puede ser un smartphone (teléfono inteligente), tablet, ordenadores portátiles o de
sobremesa, incluso en la actualidad, aunque más incómodos, navegadores integrados en
los televisores. Simplemente se necesita una **conectividad a Internet.**

- Facilidad del usuario para **registrar gastos**. El ejemplo más claro serían los repostajes, permitiendo guardarlos en el momento en el que se producen, y por tanto posteriormente se listarán todos
esos registros para poder realizar análisis reales de los gastos de su vehículo. Este enfoque es mucho más versátil que lo que nos puede ofrecer una aplicación de
escritorio clásica, donde solo podríamos interactuar con ella a través del equipo en el que estuviese instalada y que probablemente el usuario no lleve encima cuando se producen
los gastos asociados al vehículo, y en caso de llevarla (un ordenador portátil) sería incómodo encenderla y registrar en ese momento el citado gasto o intervención.



## Requisitos para la integración del proyecto

Los pasos aquí detallados son necesarios para la realización del trabajo de programación de la aplicación detallada en este proyecto. Algunas de estas instrucciones son comunes y
necesarias igualmente para la instalación en el equipo en el que se vaya a desplegar. Se explicitará cuales son comunes y cuales especificas para el desarrollo inicial.


Tanto para desarrollar como para ejecutar nuestro proyecto necesitamos un software sobre el que ejecutar el proyecto de gestión de coches. En primer lugar se necesita instalar el
intérprete de ***PHP***, ya que es el lenguaje de programación en el que se desarrolla la aplicación web, y el ***Composer***, como gestor de paquetes de *PHP* para posteriormente
obtener ***Symfony***, los cuales podemos ***descargar desde las páginas web oficiales***. Así mismo necesitamos una base de datos en la que almacenar el contenido de nuestra aplicación
web y para ello vamos a usar la integrada en el paquete ***XAMPP***, la cual es una *MySQL*.


Una vez tenemos este software básico instalado *(PHP, Composer y XAMPP)*, procederemos a instalar el framework de Symfony. Para ello necesitamos tener PHP en las variables de
entorno y teclearemos en una consola (cmd) lo siguiente:


        c:\> php -r "readfile('http://symfony.com/installer');" > symfony
        
        
Hasta aquí sería la parte necesaria para la instalación del paquete de software en cualquier equipo que se quisiese ejecutar y desplegar la aplicación. Para el desarrollo además
necesitamos ejecutar y configurar lo siguiente:

- Necesitamos instalar ***Doctrine***, para que nos ayude a crear tanto entidades como
repositorios de forma sencilla. A continuación las tablas en la BBDD a partir de las
entidades y la realización del mapeo de forma automática y coherente, para lo cual teclearemos:


        composer require symfony/orm-pack composer require --dev symfony/maker-bundle


- Una vez tenemos todo el software instalado vamos a crear nuestro proyecto. Estos
comandos son solo necesarios para la creación inicial (del proyecto y de entidades). Para
ello teclearemos:


        symfony new --full gestionCoches
        
        
- Abrimos el proyecto con el Visual Studio y editamos el archivo .env para configurar el
acceso a la BBDD (la cual tendremos que tener lanzada y configurada desde XAMPP). Este
archivo se entregará ya configurado en el proyecto finalizado:


        DATABASE_URL="mysql://root:1234@127.0.0.1:3306/gestionCoches?serverVersion=5.7"
        
        
- También se puede crear la base de datos directamente con Doctrine con el siguiente comando:


        php bin/console doctrine:database:create
        
        
- Tras esto, se pueden añadir migraciones y "fields" dentro de la base de datos con el
siguiente comando:


        php bin/console make:entity
        
        
- Una vez tenemos creada la entidad, podemos hacer que sea el propio Symfony quien nos
cree la tabla correspondiente en la base de datos o nos actualice la existente si la hemos
modificado. Para ello, hemos de teclear lo indicado al terminar de crear la entidad:


        php bin/console make:migration
        
> Nota
> 
> Tras este comando, el cmd te proporcionará la opción de realizar el *migrations:migrate* para realizar la migración.

- Finalmente, después de introducir toda la información necesaria, podemos crear el
controller, que nos da las operaciones básicas del CRUD (Create, Read, Update, Delete), por
medio del comando:


        php bin/console make:controller “Nombre”Controller
        
        
Con esto tendríamos el esqueleto del proyecto creado, tras eso tendríamos que trabajar
editando y creando código de forma manual.
En la entrega del proyecto, se proporcionará una imagen de la base de datos (poblada con
datos iniciales sobre marcas de coches, modelos y colores), que simplemente será
necesario importar en el MySQL instalado en la máquina sobre la que se vaya a realizar el
despliegue.

### Ejecución de la aplicación

Para ejecutar y desplegar la aplicación simplemente hay que abrir una consola de
comandos en la carpeta donde está el proyecto y ejecutar la siguiente instrucción:


        Symfony server:start
        
        
## Listado de tecnologías utilizadas


| Tecnología | Ámbito | Explicación | 
| ---- | ---- | ---- |
| HTML | Lenguaje de marcas | Utilizado para definir la estructura y los contenidos visualizados en el navegador web por el usuario. Con este lenguaje se define como se estructuran sin influir en su diseño lo cual actualmente se realiza mediante la siguiente tecnología. |
| CSS | Lenguaje de estilos | Usado para darle formato visual a los contenidos mostrados en el navegador. Nos referimos tales como formato visual a cuestiones como colores y tamaños de tipografía, colores de fondo y de los diversos componentes, enlaces (pulsados y sin pulsar)... Simplemente cambiando esta hoja de estilos se podría modificar el diseño visual del contenido desplegado. |
| PHP | Lenguaje de programación | Es el lenguaje utilizado en el proyecto para realizar nuestro *core* o **backend**, es decir, toda la operativa de nuestro proyecto. Es el lenguaje a través del cual realizamos las operaciones necesarias para el funcionamiento del gestor, esto es, la recuperación de datos solicitados por el usuario y que serán mostrados en la *vista* o **frontend**, el guardado de las nuevas entradas del proyecto con sus correspondientes comprobaciones necesarias. |
| Symfony | Framework web | Framework web basado en PHP que implementa el patrón Modelo-Vista-Controlador **MVC**. Nos ayuda y facilita en las tareas de escuchar los diferentes endpoints (urls) y mapearlas a los correspondientes métodos que realizan las funciones que implementan el comportamiento buscado para esa operación y que están escritas en PHP. Tambíen nos ayuda a trabajar con las entidades que representan los datos almacenados en nuestra BBDD, así como los repositorios que nos permiten acceder y consultarlos de forma sencilla. |
| Twig | Motor de plantillas | Es el motor por defecto utilizado por Symfony y que nos ayuda a generar el HTML de forma dinámica para ser enviado a la vista. El contenido de este HTML va a ser función de la consulta que nos devuelva la BBDD. En esta plantilla se define un esqueleto del HTML que será rellenado en cada ejecución con los datos correspondientes enviados por el controlador despues de consultar al modelo. |

