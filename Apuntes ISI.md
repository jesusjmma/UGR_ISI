# Metodología docente

En las prácticas desarrollaremos un sistema de información y lo desplegaremos.

40% Teoría - Examen final tipo test (mínimo 4 sobre 10)
40% Proyecto - Solo se evalúa la entrega final (mínimo 4 sobre 10)
20% Caso práctico

## Prácticas
- Semana 1: Haremos una propuesta de proyecto en conjunto en el equipo.
- Semana 2: Presupuesto del proyecto

Tanto el proyecto como los casos prácticos se ven en clases de Prácticas. El proyecto es en equipo y los casos prácticos son individuales.

# Tema 1. Introducción al diseño de sistemas de información.

## El proceso de diseño de software.

Nos interesa la estructura del software:
- Firmeza: Que no falle
- Comodidad: Que sea adecuado para aquello para lo que se diseñó
- Deleite: Que sea agradable su uso

Hay que aplicar buenas prácticas en el diseño de un sistema de información.

El diseño se puede descomponer en distintas fases:
- Diagrama Entidad-Relación --> Para modelar los datos
- Diseño arquitectónico --> Para organizar en subsistemas
- Diseño de interfaces
- Diseño de componentes

Algunos consejos:
- El diseño del software comienza considerando los datos (tipo de datos, estructura de los datos, volumen de datos, velocidad de procesamiento, forma de llegada de los datos, etc.).
- Tras tener los datos, se trabaja la estructura.
- Tras establecer la arquitectura, se hacen el resto de tareas de diseño.

Evaluación del diseño:
- Cualquier sistema tiene diferentes requisitos implícitos aparte de los explícitos, los cuales también deben satisfacerse.
- El diseño debe entenderlo todo el mundo que esté implicado.

## Evolución de las técnicas de diseño de software.

Vemos ejemplos generales.

Las técnicas han ido evolucionando y elevando cada vez más los niveles de abstracción. De esta forma podemos centrarnos en soluciones a problemas más complejos sin necesidad de pensar en cosas cosas menos importantes (de más bajo nivel).

## Caso práctico: Aplicaciones de gestión.

# Tema 2. Arquitectura de los sistemas de información.

## Conceptos clave en arquitectura del software.

Nos enfrentamos siempre a ciertas restricciones:
- Ámbito/Características
- Coste/recurso
- Tiempo/calendario
- Calidad
- Personal

Hay que determinar las prioridades del proyecto

El arquitecto es el encargado del diseño del sistema.

El **diseño arquitectónico** es la etapa que conecta el **análisis de requisitos** del sistema con el **diseño software**.

El **modelo de 3 picos** interpreta lo que se quiere resolver

## Vistas: modelo 4+1, puntos de vista y perspectivas.

En lugar de describir el sistema como un único modelo, se utilizan **vistas** para describir las partes clave del sistema y ver si este va a poder cumplir con su objetivo.

Hay diferentes puntos de vista que permiten facilitar la comunicación con ciertas personas dentro del proceso de diseño del software.

Vamos a ver 2 modelos de vista, pero hay muchos más.

### Modelo 4+1

Comprende 4 vistas:
- **Vista lógica**: Clases. Lo que entiende el usuario del sistema desde fuera. Corresponde a un modelo orientado a objetos del sistema.
- **Vista de procesos**: Tareas. Cuál es la concurrencia del sistema y cómo se comunican y sincronizan los procesos.
- **Vista física**: Nodos. Cómo es la arquitectura y qué tiene. El hardware y su distribución.
- **Vista de desarrollo**: Módulos y subsistemas. Cómo organizar internamente la implementación desde el punto de vista del programador. Organización de los módulos para que puedan trabajar varios equipos de forma simultánea.

Cualquier otra cosa relevante para el diseño del sistema que se quede fuera de esas 4 vistas se describe mediante el uso de **escenarios** (pasos y scripts).

### Modelo alternativo

Aquí tenemos 6 vistas (no se necesitan usar todas). Corresponden:
- **Punto de vista Funcional** (equivale al lógico): Se puede usar un diagrama de componentes UML (no de clases, porque estamos describiendo el sistema a grandes rasgos).
- **Punto de vista de Información**: Modelo de datos del sistema (diagramas entidad-relación, diagramas de clases).
- **Punto de vista de Concurrencia**: Se utiliza un diagrama UML añadiéndole *estereotipos* (en las diapositivas, lo que va entre <<>>) o un diagrama de estados.
- **Punto de vista de Desarrollo**: Diagrama de componentes en UML (paquetes). Facilita la organización de los módulos
- **Punto de vista de Despliegue** (equivale al físico): Diagrama de despliegue en UML.
- **Punto de vista Operativo**: No tiene un diagrama UML asociado estándar. Son las instrucciones que le das al administrador del sistema (como actualizarlo, mantenerlo, etc).

Estos puntos de vista se complementan con **perspectivas** (equivalen a los escenarios). Son los requisitos que afectan a nuestro diseño pero que no encajan en los puntos de vista anteriores (p.e.: requisitos no funcionales). Se pone en formato de tabla/cuadrícula

### Beneficios
Las vistas nos ofrecen una serie de beneficios a la hora del diseño de nuestro sistema:
- Nos permite separar diferentes asuntos.
- Nos facilita la comunicación con diferentes grupos de stakeholders de nuestro proyecto.
- Nos permite gestionar la complejidad del sistema, ya que cada vista se puede realizar por separado.
- Nos permite documentar el proyecto.

De igual forma las vistas también conllevan una serie de limitaciones:
- Inconsistencias entre vistas: si no comprobamos que las diferentes vistas tengan sentido entre sí.
- Conjunto de vistas erróneo: si no cogemos las vistas adecuadas para documentar el sistema. No hay que forzar a que estén todas las vistas, solo hay que utilizar las necesarias.
- Fragmentación de la descripción arquitectónica: Se nos puede colar algún aspecto clave del sistema. 

## Patrones arquitectónicos: capas, flujo de datos, pizarra.

### Arquitecturas basadas en capas

Cada sistema complejo lo dividimos en diferentes subsistemas. Ayudan a estructurar sistemas que pueden descomponerse en grupos de subtareas a distintos niveles de abstracción.

La arquitectura basada en capas se puede describir con tarjetas CRC. Las **tarjetas CRC** describen a las diferentes clases del sistema, de qué se encargan y con quien colaboran.

Cada capa puede tener diferentes componentes. La capa $n$ tan solo se comunica con las capas $n-1$ y $n+1$.

A la larga el sistema se va complicando y se hace muy difícil de mantener.

Las arquitecturas basadas en capas se llevan a cabo mediante un refinamiento progresivo, mediante una estrategia descendente en la que se descompone el problema en subproblemas más detallados y concretos:
- Definimos el criterio de abstracción
- Determinamos el número de niveles de abstracción (capas)
- Nombramos las capas
- Asignamos responsabilidades/atribuciones a cada capa
- Especificamos los servicios que ofrece cada capa

Nota: suele ser más adecuado un enfoque ascendente.

Una vez definidas las capas y lo que hacen, hay que diseñarlas:
- Diseñamos la interfaz
- Diseñamos la estructura de cada capa
- Diseñamos el mecanismo de comunicación entre capas
- Desacoplamos las capas adyacentes
- Diseñamos un mecanismo de detección de errores



### Arquitecturas basadas en flujos de datos


### Arquitecturas con pizarra


## Técnicas de validación, p.ej. evaluación mediante escenarios (ATAM & SAAM).

## Caso práctico: Aplicaciones web.

# Tema 3. Acceso a los datos

## Bases de datos relacionales y herramientas de O/R mapping.

## Bases de datos distribuidas: fragmentación, asignación de recursos y replicación de datos.

## Bases de datos NoSQL: key-value stores, wide-column stores, document stores & graph DBMSs.

## Bases de datos multidimensionales: data warehousing.

# Tema 4. Integración de datos

## Sistemas de integración de datos

## Descripción de fuentes de datos: GAV, LAV & GLAV.

## Integración de esquemas [schema matching & mapping].

## Emparejamiento de datos [data matching].

## Wrappers: Construcción manual y automática.

# Tema 5. Middleware y sistemas distribuidos

## Estándares y evolución: sockets, RPC, colas de mensajes...

## Servicios web

## Middleware basado en brokers: CORBA [Common Object Request Broker Architecture].

## Middleware basado en publish/subscribe: DDS [Data Distribution Service]

# Tema 6. Procesamiento de transacciones

## ACIDez de las transacciones.

## Implementación: logs de transacciones & versiones.

## Procesamiento de transacciones distribuidas: 2-phase commit & 3-phase commit.

## El teorema CAP: BASE vs. ACID.

# Tema 7. Seguridad en los sistemas de información

## Fundamentos: Técnicas criptográficas, funciones hash, firmas digitales y certificados.

## Caso práctico: Seguridad en aplicaciones web.
