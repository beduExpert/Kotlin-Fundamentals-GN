
## Postwork

## Ejercicios de Programación Funcional en Kotlin
## 1. Expresiones Lambda

Crea una expresión lambda que tome dos números enteros y devuelva el mayor de ellos. Luego, usa esta lambda para encontrar el número más grande en una lista de enteros.

<details>
<summary>Ver solución</summary>
  
```kotlin
val obtenerMayor: (Int, Int) -> Int = { a, b -> if (a > b) a else b }

fun main() {
    val numeros = listOf(5, 2, 10, 8, 3, 1)
    val maximo = numeros.reduce(obtenerMayor)
    println("El número más grande es: $maximo")
}
```
</details>

## 2. Funciones de Orden Superior

Crea una función de orden superior llamada operacion que tome dos números enteros y una función como parámetros. Esta función debe aplicar la función recibida a los dos números. Luego, utiliza esta función de orden superior para realizar suma, resta y multiplicación.

<details>
<summary>Ver solución</summary>
  
```kotlin
fun operacion(a: Int, b: Int, func: (Int, Int) -> Int): Int {
    return func(a, b)
}

fun main() {
    val suma = { x: Int, y: Int -> x + y }
    val resta = { x: Int, y: Int -> x - y }
    val multiplicacion = { x: Int, y: Int -> x * y }

    println("Suma: ${operacion(5, 3, suma)}")
    println("Resta: ${operacion(5, 3, resta)}")
    println("Multiplicación: ${operacion(5, 3, multiplicacion)}")
}
```
</details>

## 3. Inline Functions

Crea una función inline que tome una lambda como parámetro y la ejecute dentro de un bloque try-catch. Luego, usa esta función para ejecutar una operación que podría lanzar una excepción.

<details>
<summary>Ver solución</summary>
  
```kotlin
inline fun ejecutarSeguro(operacion: () -> Unit) {
    try {
        operacion()
    } catch (e: Exception) {
        println("Se produjo una excepción: ${e.message}")
    }
}

fun main() {
    ejecutarSeguro {
        val resultado = 10 / 0
        println(resultado)
    }
    
    ejecutarSeguro {
        println("Esta operación es segura")
    }
}
```
</details>

## 4. Filter y Map

Dada una lista de palabras, utiliza filter para obtener solo las palabras que tengan más de 5 letras, y luego usa map para convertir estas palabras a mayúsculas.

<details>
<summary>Ver solución</summary>
  
```kotlin
fun main() {
    val palabras = listOf("gato", "perro", "elefante", "ratón", "hipopótamo")
    
    val resultado = palabras
        .filter { it.length > 5 }
        .map { it.uppercase() }
    
    println(resultado)
}
```
</details>

## 5. Partition y FlatMap

Dada una lista de números, usa partition para separar los números pares e impares. Luego, usa flatMap para crear una nueva lista que contenga el cuadrado de los números pares y el cubo de los números impares.

<details>
<summary>Ver solución</summary>
  
```kotlin
fun main() {
    val numeros = listOf(1, 2, 3, 4, 5, 6, 7, 8, 9, 10)
    
    val (pares, impares) = numeros.partition { it % 2 == 0 }
    
    val resultado = listOf(pares, impares).flatMap { lista ->
        lista.map { numero ->
            if (numero % 2 == 0) numero * numero
            else numero * numero * numero
        }
    }
    
    println(resultado)
}
```
</details>

## 6. Reduce y ForEach

Crea una lista de números decimales que representen precios. Utiliza reduce para calcular el total de los precios. Luego, usa forEach para imprimir cada precio con un formato específico (por ejemplo, con dos decimales y el símbolo de moneda).

<details>
<summary>Ver solución</summary>
  
```kotlin
fun main() {
    val precios = listOf(19.99, 24.50, 9.95, 4.20, 99.99)
    
    val total = precios.reduce { acc, precio -> acc + precio }
    
    println("Total: ${"%.2f".format(total)}")
    
    precios.forEach { precio ->
        println("${"$%.2f".format(precio)}")
    }
}
```
</details>
