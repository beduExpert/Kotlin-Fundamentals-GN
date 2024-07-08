## Postwork

## Ejercicios de Kotlin: Corrutinas

## Ejercicio 1: Lanzamiento de una corrutina básica

Escribe una función main que lance una corrutina usando GlobalScope.launch. La corrutina debe imprimir "Hola desde la corrutina" después de un retraso de 1 segundo.

<details>
<summary>Ver solución</summary>
 
```kotlin
import kotlinx.coroutines.*

fun main() = runBlocking {
    GlobalScope.launch {
        delay(1000)
        println("Hola desde la corrutina")
    }
    delay(2000) // Esperamos para que la corrutina tenga tiempo de ejecutarse
}
```
Esta solución lanza una corrutina global que imprime un mensaje después de un segundo de retraso.
</details>

## Ejercicio 2: Uso de runBlocking

Modifica el ejercicio anterior para usar runBlocking en lugar de GlobalScope.launch. Elimina la necesidad de esperar explícitamente al final de la función main.

<details>
<summary>Ver solución</summary>
 
```kotlin
import kotlinx.coroutines.*

fun main() = runBlocking {
    launch {
        delay(1000)
        println("Hola desde la corrutina")
    }
}
```
Esta solución utiliza runBlocking para crear un scope de corrutina y launch para iniciar una nueva corrutina dentro de ese scope.
</details>

## Ejercicio 3: Funciones de suspensión

Crea una función de suspensión llamada obtenerDatos que simule la obtención de datos de una API. Debe tomar un tiempo aleatorio entre 500ms y 2000ms, y devolver un String. Luego, usa esta función en la main.

<details>
<summary>Ver solución</summary>
 
```kotlin
import kotlinx.coroutines.*
import kotlin.random.Random

suspend fun obtenerDatos(): String {
    delay(Random.nextLong(500, 2000))
    return "Datos obtenidos"
}

fun main() = runBlocking {
    println("Iniciando obtención de datos...")
    val resultado = obtenerDatos()
    println(resultado)
}
```
Esta solución define una función de suspensión que simula una operación de larga duración y la utiliza en la función main.
</details>

## Ejercicio 4: Manejo de Jobs

Lanza dos corrutinas, una que imprima números del 1 al 5 cada 500ms, y otra que imprima letras de la 'a' a la 'e' cada 750ms. Usa Jobs para esperar a que ambas corrutinas terminen antes de finalizar el programa.

<details>
<summary>Ver solución</summary>
 
```kotlin
import kotlinx.coroutines.*

fun main() = runBlocking {
    val job1 = launch {
        for (i in 1..5) {
            delay(500)
            println(i)
        }
    }
    
    val job2 = launch {
        for (c in 'a'..'e') {
            delay(750)
            println(c)
        }
    }
    
    job1.join()
    job2.join()
    println("Todas las corrutinas han terminado")
}
```
Esta solución lanza dos corrutinas y utiliza join() para esperar a que ambas terminen antes de finalizar el programa.
</details>

## Ejercicio 5: Cancelación de corrutinas

Crea una corrutina que imprima números incrementalmente cada segundo. Después de 5 segundos, cancela la corrutina.

<details>
<summary>Ver solución</summary>
 
```kotlin
import kotlinx.coroutines.*

fun main() = runBlocking {
    val job = launch {
        var i = 1
        while (isActive) {
            println(i++)
            delay(1000)
        }
    }
    
    delay(5000)
    job.cancel()
    println("Corrutina cancelada")
}
```
Esta solución lanza una corrutina que se ejecuta indefinidamente, pero se cancela después de 5 segundos usando job.cancel().
</details>

## Ejercicio 6: Corrutinas en paralelo con async

Crea dos funciones de suspensión que simulen operaciones largas (por ejemplo, obtenerUsuario y obtenerPerfil). Usa async para ejecutarlas en paralelo y combina sus resultados.

<details>
<summary>Ver solución</summary>
 
```kotlin
import kotlinx.coroutines.*

suspend fun obtenerUsuario(): String {
    delay(1000)
    return "Usuario123"
}

suspend fun obtenerPerfil(): String {
    delay(1000)
    return "Perfil de desarrollador"
}

fun main() = runBlocking {
    val usuario = async { obtenerUsuario() }
    val perfil = async { obtenerPerfil() }
    
    println("Usuario: ${usuario.await()}")
    println("Perfil: ${perfil.await()}")
}
```
Esta solución utiliza async para ejecutar dos operaciones en paralelo y luego combina sus resultados usando await().
</details>
