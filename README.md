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

__HashSet<E>__ almacena sus valores en una tabla hash. No podemos predecir nada sobre el orden pero tiene el mejor rendimiento de todas, que se mejora el si se establece una capacidad inicial no muy elevada. Proporciona tiempo constante (O(1)) en las operaciones básicas y permite insertar valores nulos. No es una implementación sincronizada.

Con __LinkedHashSet<E>__ tenemos un rendimiento mejor que TreeSet<E> pero peor que HashSet<E>. Almacena sus valores en una tabla hash con una lista doblemente enlazada, manteniendo el orden de inserción y la posibilidad de almacenar un valor nulo, pero sigue sin estar sincronizada.

__TreeSet<E>__ almacena sus valores en un árbol red-black, manteniendo el orden basado en sus valores pero con peor rendimiento que el resto de opciones. Los elementos deben implementar Comparable y no se permite insertar nulos, además de no ser una implemmentación sincronizada y con rendimiento de O(log(N)) debido a su estructura de árbol.
