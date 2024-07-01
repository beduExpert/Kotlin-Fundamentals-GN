# Operaciones Funcionales en Kotlin

## Objetivo

El objetivo de esta sección es aprender a utilizar funciones implementadas en Kotlin para el tratamiento de información, aplicando conceptos de programación funcional.

## Requisitos

- Tener experiencia previa con colecciones en Kotlin.
- Conocer los conceptos básicos de programación funcional.

## Desarrollo

En Kotlin, las operaciones funcionales son técnicas que nos permiten trabajar con colecciones de manera más declarativa y eficiente. A continuación, exploraremos algunas de las funciones más importantes que puedes utilizar para manipular datos en colecciones.

### 1. **Filter**

La función `filter` es una **función de orden superior** que se usa para seleccionar elementos de una colección que cumplen con un criterio específico. Esta función toma una lambda que evalúa cada elemento y devuelve solo aquellos que cumplen con el predicado.

**Ejemplo: Filtrar Calificaciones**

Supongamos que tienes una lista de calificaciones y quieres filtrar solo aquellas que son mayores o iguales a 6, que es el mínimo aprobatorio:

```kotlin
val calificaciones = listOf(10, 8, 9, 5, 3, 2, 5, 1, 7, 6, 9, 4, 10, 3, 6, 2, 6, 5)

// Aproximación imperativa
val aprobados = mutableListOf<Int>()
for (calificacion in calificaciones) {
    if (calificacion >= 6) {
        aprobados.add(calificacion)
    }
}
println(aprobados)  // Output: [10, 8, 9, 7, 6, 9, 10, 6, 6]
La versión funcional usando filter es mucho más concisa y expresiva:

```kotlin

// Aproximación funcional
val aprobados = calificaciones.filter { it >= 6 }
println(aprobados)  // Output: [10, 8, 9, 7, 6, 9, 10, 6, 6]
```
Además, puedes usar filter en mapas para seleccionar pares clave-valor basados en una condición:

```kotlin

val notasAlumnos = mapOf("Lorenza" to 6, "Juan" to 4, "Martina" to 8, "David" to 7)
val porNombre = notasAlumnos.filter { (key, value) -> key == "David" }
println(porNombre)  // Output: {David=7}
```
## 2. Partition
La función partition divide una colección en dos listas según un predicado. La primera lista contiene los elementos que cumplen con el predicado, y la segunda lista contiene los elementos que no lo cumplen.

Ejemplo: Separar Calificaciones

```kotlin

val (notasAprobadas, notasReprobadas) = calificaciones.partition { it >= 6 }
println(notasAprobadas)  // Output: [10, 8, 9, 7, 6, 9, 10, 6, 6]
println(notasReprobadas)  // Output: [5, 3, 2, 5, 1, 4, 3, 2, 5]
```
### 3. Map
La función map transforma cada elemento de una colección aplicando una función lambda. El resultado es una nueva colección con los elementos transformados.

Ejemplo: Aplicar IVA a Precios

Si tienes una colección de precios y necesitas agregar el IVA, puedes hacerlo así:

```kotlin

val preciosLibres = setOf(1024.0, 2408.5, 8224.33)
val preciosFinales = preciosLibres.map { it * 1.16 }
println(preciosFinales)  // Output: [1188.64, 2795.86, 9548.63]
```

### 4. Other Useful Functional Functions
Además de filter, partition, y map, Kotlin ofrece otras funciones funcionales útiles:

forEach: Ejecuta una acción para cada elemento de la colección.

```kotlin

calificaciones.forEach { println(it) }
reduce: Acumula un resultado usando una función de acumulación.
```

```kotlin

val sumaTotal = calificaciones.reduce { acc, calificacion -> acc + calificacion }
println(sumaTotal)  // Output: 88
```
flatMap: Aplica una función a cada elemento y luego aplana el resultado en una sola colección.

```kotlin

val listasDeNumeros = listOf(listOf(1, 2), listOf(3, 4))
val numeros = listasDeNumeros.flatMap { it }
println(numeros)  // Output: [1, 2, 3, 4]
```
