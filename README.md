# Resumen del taller sobre Colecciones en Java

Una colección es un contenedor para un conjunto de elementos de un tipo en una sola unidad, que se utiliza para almacenamiento, recuperación y manipulación de datos. Suelen representar elementos que forman grupos naturales
Disponible como framework desde la versión 2, importandose del paquete java.util

## Framework de Colecciones en Java
Nos ofrece interfaces: tipos de datos, independientes de su representación;
Implementaciones: concreciones de los diferentes tipos;
y algoritmos: métodos para buscar, ordenar, clasificar...

Las ventajas que ofrece son:

* Esfuerzo de programación reducido, aumento de la calidad y velocidad del programa.
* Permite la interoperabilidad con librerías de terceros y reduce el esfuerzo para aprender y usar otras librerías, parte de disminuir el esfuerzo al diseñar nuevas librerías.
* También fomenta la reutilización de software.

## Colecciones
La interfaz de colecciones en Java(Collection<E>) hereda de la interfaz Iterable<E>. A su vez, las interfaces __Set<E>__, __List<E>__ y __Queue<E>__ heredan de Collection<E>, pero __Map__ y sus derivados no. Cabe destacar que permite tener una serie de métodos comunes a (casi) todos los tipos de colecciones, teniendo en cuenta que JDK no ofrece ninguna implementación directa de esta interfaz.

Las principales operaciones a realizar son las siguientes:

- Para tamaño: size y isEmpty
- Para comprobación: contains
- Para añadir y eliminar: add y remove
- Para iterar: iterator
- Para operaciones bulk: containsAll, addAll, removeAll, removeIf, retainAll, clear
- Para transformar en array: toArray
- Para streams: stream, parallelStream

### Set
Se trata de un Collection<E> que no permite duplicados y que se basa en la abstracción del concepto matemático de conjunto.
Set no añade ningún método a los heredados de Collection<E> ni tiene acceso “posicional” (i.e. tercer elemento), pero mejora la implementación de los métodos equals y hashCode con respecto a Collection<E>. En Set se toman dos instancias por iguales si contienen los mismos elementos.

Set se puede implementar como:

- HashSet(Más rápido)
- LinkedHashSet(Ordena según la inserción)
- TreeSet(Ordena según el valor)

__HashSet<E>__ almacena sus valores en una tabla hash. No podemos predecir nada sobre el orden pero tiene el mejor rendimiento de todas, que se mejora si se establece una capacidad inicial no muy elevada. Proporciona tiempo constante (O(1)) en las operaciones básicas y permite insertar valores nulos. No es una implementación sincronizada.

Con __LinkedHashSet<E>__ tenemos un rendimiento mejor que TreeSet<E> pero peor que HashSet<E>. Almacena sus valores en una tabla hash con una lista doblemente enlazada, manteniendo un orden de inserción y la posibilidad de almacenar un valor nulo, pero sigue sin estar sincronizada.

__TreeSet<E>__ almacena sus valores en un árbol red-black, manteniendo un orden basado en sus valores pero con peor rendimiento que el resto de opciones. Los elementos deben implementar Comparable y no se permite insertar nulos, además de no ser una implemmentación sincronizada y con rendimiento de O(log(N)) debido a su estructura de árbol.

### List
Se trata de un Collection<E> que permite duplicados y que añade a las funcionalidades de Collection<E> las siguientes:
Acceso posicional, búsqueda, iteración extendida y operaciones sobre un rango de elementos de la lista.

Las implementaciones de List son:

- ArrayList(Más usual)
- Vector(Sincronizada pero con métodos Legacy; menos recomendable)
- LinkedList(Bastante eficiente en algunas ocasiones)

Destaco ArrayList y LinkedList, por lo siguiente:

__ArrayList__ es la más adecuada en la mayoría de las situaciones. Tiene acceso por índice en O(1) y el tipo de inserción, en media, en O(1), pero tiene menos espacio que LinkedList.

Aunque suele tener peor rendimiento, __LinkedList<E>__ tiene más espacio (debe incluir dos referencias). Posee el acceso por índice en O(n) y en cuanto a inserción/borrado: O(1) extremos, O(n) por índice, O(1) en iteración.
  

### Queue
Se trata, junto con __Deque__, de una interfaz estrachamente relacionada con List. Queue<E> funciona como una cola (FIFO).
  
Las operaciones principales para Queue son:
- Para inserción: add(e), offer(e)
- Para extraer: remove(), poll()
- Para examinar: element(), peek()

Implementaciones:
- PriorityQueue<E>
- ArrayDeque<E>
- LinkedList<E>

__Deque<E>__
Esta interfaz hereda de Queue y puede funcionar como una cola (FIFO) o como una pila (LIFO).
También puede funcionar como una pila doble o una cola doble.

Como cola:
- Para inserción: add(e), addLast(e), offer(e), offerLast(e)
- Para extraer: remove(), removeFirst(), poll(), pollFirst()
- Para examinar: element(), getFirst(), peek(), peekFirst()

Como pila:
- Para inserción: push(e), addFirst(e), offerFirst(e)
- Para extraer: pop(), removeFirst(), pollFirst()
- Para examinar: peek(), getFirst(), peekFirst()

Como cola doble:
- Para inserción: addFirst(e), offerFirst(e), addLast(e), offerLast(e)
- Para extraer: removeFirst(), pollFirst(), removeLast(), pollLast()
- Para examinar: getFirst(), peekFirst(), getLast(), peekLast()

Implementaciones de Deque:
- ArrayDeque<E>
- LinkedList<E>


### Map<K,V>
No hereda de Collection<E> y maneja pares clave,valor habiendo para cada clave, un solo valor. Cada clave puede existir una sola vez en el map, puede haber una clave nula y múltiples valores nulos. En otros lenguajes de programación se le conoce como diccionario.
No puede almacenar tipos primitivos; hay que usar los tipos wrapper en su lugar (int → Integer)

Map.Entry<K,V>
- Clase que permite consultar un par clave,valor de un Map.
- No se pueden utilizar para insertar valores.
- Se puede obtener un Set<Map.Entry<K,V>> a través del método Map.entrySet().

Operaciones con Map
- Para insertar una clave y su valor: put(key, value)
- Para obtener un valor en base a la clave: get(key)
- Para consultar si una clave o un valor están contenidos: containsKey(key) / containsValue(value)
- Para eliminar el par clave, valor: remove(key)
- Para recorrer un Map: forEach(Obtener un Set con las claves, para cada clave, obtener los valores);Usando el lambdas(Método forEach; expresión lambda (Biconsumer))
