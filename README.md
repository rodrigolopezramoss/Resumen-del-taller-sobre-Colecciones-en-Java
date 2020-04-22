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

La interfaz de colecciones en Java(Collection<E>) hereda de la interfaz Iterable<E>. A su vez, las interfaces Set<E>, List<E> y Queue<E> heredan de Collection<E>, pero Map y sus derivados no. Cabe destacar que permite tener una serie de métodos comunes a (casi) todos los tipos de colecciones, teniendo en cuenta que JDK no ofrece ninguna implementación directa de esta interfaz.

Las principales operaciones a realizar son las siguientes:

- Para tamaño: size y isEmpty
- Para comprobación: contains
- Para añadir y eliminar: add y remove
- Para iterar: iterator
- Para operaciones bulk: containsAll, addAll, removeAll, removeIf, retainAll, clear
- Para transformar en array: toArray
- Para streams: stream, parallelStream
