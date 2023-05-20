QUE SON LOS PATRONES GOF:

Los patrones GOF son patrones de diseño de software que fueron estudiados por Erich Gamma, Richard Helm, Ralph Johnson y John Vlissides en su libro "Design Patterns"  El objetivo principal de los patrones es facilitar la reutilización de diseños y arquitecturas de software que han tenido éxito capturando la experiencia y haciéndola accesible a los no expertos.

Dentro de los patrones GOF se desarrollan 3 tipos de patrones que son los que se encargan de adaptarse a un contexto diferente depende de el que se use. Estos patrones son:

Patrones de creación -
Patrones estructurales - 
Patrones de comportamiento 

Antes de describir cada uno de los patrones, hay que decir que cada patron tiene sus funcionalidades que lo complementan y que practicamente se pueden denominar como funciones que nos proporciona el patron que estemos utilzando. Podemos empezar a desenvolver cada patron uno por uno y con su respectivo ejemplo.

.

PATRONES DE CREACION

Principalmente unicamente tiene la utilidad de que tratan el tema de la iniciacion y configuracion de clases y objetos. sus funciones son las siguientes;

ABSTRACT FACTORY. Proporciona una interfaz para crear familias de objetos o que dependen entre sí, sin especificar sus clases concretas.

BUILDER. Separa la construcción de un objeto complejo de su representación, de forma que el mismo proceso de construcción pueda crear diferentes representaciones.

FACTORY METHOD Define una interfaz para crear un objeto, pero deja que sean las subclases quienes decidan qué clase instanciar. Permite que una clase delegue en sus subclases la creación de objetos.

PROTOTYPE. Especifica los tipos de objetos a crear por medio de una instancia prototípica, y crear nuevos objetos copiando este prototipo.

SINGLETON. Garantiza que una clase sólo tenga una instancia, y proporciona un punto de acceso global a ella.

Estos patrones tambien funcionan para abstraer y facilitar la creación de instancias de objetos. Permiten tratar las clases a crear de forma genérica y posponer la decisión de qué clase crear o cómo crearla. Esto puede ser útil en situaciones en las que la creación de objetos es compleja o requiere de una lógica específica.

EJEMPLO

Un ejemplo de un patrón de creación GOF es el patrón Singleton. Este patrón garantiza que una clase sólo tenga una instancia y proporciona un punto de acceso global a ella. Esto puede ser útil en situaciones en las que se necesita controlar el acceso a un recurso compartido, como una base de datos o un archivo de configuración


    private Singleton() {}

    public static Singleton getInstance() {
        if (instance == null) {
            instance = new Singleton();
        }
        return instance;
    }


.

PATRONES ESTRUCTURALES 

Estos patrones tratan de desacoplar la interfaz e implementación de clases y objetos. Estos patrones permiten que las clases y objetos trabajen juntos de manera más flexible y que puedan cambiar sin afectar a otras partes del sistema. Como lo mencionaba estos patrones tienen sus respectivas funciones, las funciones de los patrones estructurales son:

ADAPTER. Convierte la interfaz de una clase en otra distinta que es la que esperan los clientes. Permiten que cooperen clases que de otra manera no podrían por tener interfaces incompatibles.

BRIDGE. Desvincula una abstracción de su implementación, de manera que ambas puedan variar de forma independiente.

COMPOSITE. Combina objetos en estructuras de árbol para representar jerarquías de parte-todo. Permite que los clientes traten de manera uniforme a los objetos individuales y a los compuestos.

DECORATOR. Añade dinámicamente nuevas responsabilidades a un objeto, proporcionando una alternativa flexible a la herencia para extender la funcionalidad.

FACADE. Proporciona una interfaz unificada para un conjunto de interfaces de un subsistema. Define una interfaz de alto nivel que hace que el subsistema se más fácil de usar.

FLYWEIGHT. Usa el compartimiento para permitir un gran número de objetos de grano fino de forma eficiente.

PROXY. Proporciona un sustituto o representante de otro objeto para controlar el acceso a éste.

Por ejemplo, el patrón Adapter permite convertir la interfaz de una clase en otra interfaz esperada por los clientes. Esto permite que clases con interfaces incompatibles puedan trabajar juntas



    public void hacerSonido() {
        System.out.println("El juguete hace sonido");
    }

    public JuguetePajaroAdapter(JuguetePajaro juguete) {
        this.juguete = juguete;
    }

    public void volar() {
        juguete.mover();
    }

    public void cantar() {
        juguete.hacerSonido();
    }

.

PATRONES DE COMPORTAMIENTO 

Estos patrones tratan de las interacciones dinámicas entre sociedades de clases y objetos. Estos patrones permiten definir cómo los objetos interactúan y cómo se comunican entre sí. A continuacion estan sus respectivas funciones:

CHAIN OF RESPONSIBILITI. Evita acoplar el emisor de una petición a su receptor, al dar a más de un objeto la posibilidad de responder a la petición. Crea una cadena con los objetos receptores y pasa la petición a través de la cadena hasta que esta sea tratada por algún objeto.

COMMAND. Encapsula una petición en un objeto, permitiendo así parametrizar a los clientes con distintas peticiones, encolar o llevar un registro de las peticiones y poder deshacer la operaciones.

INTERPRETER. Dado un lenguaje, define una representación de su gramática junto con un intérprete que usa dicha representación para interpretar las sentencias del lenguaje.

ITERATOR. Proporciona un modo de acceder secuencialmente a los elementos de un objeto agregado sin exponer su representación interna.

MEDIATOR. Define un objeto que encapsula cómo interactúan un conjunto de objetos. Promueve un bajo acoplamiento al evitar que los objetos se refieran unos a otros explícitamente, y permite variar la interacción entre ellos de forma independiente.

MEMENTO. Representa y externaliza el estado interno de un objeto sin violar la encapsulación, de forma que éste puede volver a dicho estado más tarde.

OBSERVER. Define una dependencia de uno-a-muchos entre objetos, de forma que cuando un objeto cambia de estado se notifica y actualizan automáticamente todos los objetos.

STATE. Permite que un objeto modifique su comportamiento cada vez que cambia su estado interno. Parecerá que cambia la clase del objeto.

STRATEGY. Define una familia de algoritmos, encapsula uno de ellos y los hace intercambiables. Permite que un algoritmo varíe independientemente de los clientes que lo usan.

TEMPLATE METHOD. Define en una operación el esqueleto de un algoritmo, delegando en las subclases algunos de sus pasos. Permite que las subclases redefinan ciertos pasos del algoritmo sin cambiar su estructura.

VISITOR. Representa una operación sobre los elementos de una estructura de objetos. Permite definir una nueva operación sin cambiar las clases de los elementos sobre los que opera.
   			
Un ejemplo de un patrón de comportamiento GOF es el patrón Observer. Este patrón define una dependencia uno-a-muchos entre objetos, de manera que cuando el objeto sujeto cambia de estado, todos sus objetos dependientes son notificados y actualizados automáticamente.



class Subject {
    private List<Observer> observers = new ArrayList<Observer>();
    private String message;

    public void addObserver(Observer observer) {
        observers.add(observer);
    }

    public void removeObserver(Observer observer) {
        observers.remove(observer);
    }

    public void notifyObservers() {
        for (Observer observer : observers) {
            observer.update(message);
        }
    }

    public void setMessage(String message) {
        this.message = message;
        notifyObservers();
    }

    private String name;

    public ConcreteObserver(String name) {
        this.name = name;
    }

    public void update(String message) {
        System.out.println(name + " received: " + message);
    }


