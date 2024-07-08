# Ejercicios de Kotlin: Funciones, Condicionales, Ciclos y Estructuras de Datos

## Ejercicio 1: Calculadora de volumen de cilindro

Crea una función que calcule el volumen de un cilindro dado su radio y altura.
<details>
<summary>Solución:</summary>

```kotlin
import kotlin.math.PI

fun calcularVolumenCilindro(radio: Double, altura: Double): Double {
    return PI * radio * radio * altura
}

fun main() {
    println("Volumen del cilindro: ${calcularVolumenCilindro(5.0, 10.0)}")
}
```
</details>

## Ejercicio 2: Verificador de número primo

Implementa una función que determine si un número es primo.
<details>
<summary>Solución:</summary>
        
```kotlin
fun esPrimo(numero: Int): Boolean {
    if (numero <= 1) return false
    for (i in 2..Math.sqrt(numero.toDouble()).toInt()) {
        if (numero % i == 0) return false
    }
    return true
}

fun main() {
    println("¿Es 17 primo? ${esPrimo(17)}")
    println("¿Es 24 primo? ${esPrimo(24)}")
}
```
</details>

## Ejercicio 3: Validador de email con función local

Desarrolla una función que valide una dirección de email utilizando una función local.
<details>
<summary>Solución:</summary>
    
```kotlin
    fun validarEmail(email: String): Boolean {
    fun tieneArrobaYPunto(str: String): Boolean {
        return str.contains("@") && str.contains(".")
    }

    return email.isNotEmpty() && tieneArrobaYPunto(email)
}

fun main() {
    println("¿Es válido user@example.com? ${validarEmail("user@example.com")}")
    println("¿Es válido invalid-email? ${validarEmail("invalid-email")}")
}
```
</details>

## Ejercicio 4: Clasificador de edades usando when

Crea una función que clasifique a una persona según su edad utilizando when.
<details>
<summary>Solución:</summary>
    
```kotlin
fun clasificarEdad(edad: Int) {
    when (edad) {
        in 0..12 -> println("Niño")
        in 13..19 -> println("Adolescente")
        in 20..64 -> println("Adulto")
        else -> println("Adulto mayor")
    }
}

fun main() {
    clasificarEdad(8)
    clasificarEdad(15)
    clasificarEdad(35)
    clasificarEdad(70)
}
```
</details>

## Ejercicio 5: Imprimir números pares en un rango

Utiliza un ciclo for para imprimir los números pares en un rango dado.
<details>
<summary>Solución:</summary>
    
```kotlin
fun imprimirPares(inicio: Int, fin: Int) {
    for (i in inicio..fin step 2) {
        if (i % 2 == 0) {
            println(i)
        }
    }
}

fun main() {
    imprimirPares(1, 10)
}
```
</details>

## Ejercicio 6: Contar vocales en una lista de palabras

Usa una lista y un ciclo para contar las vocales en una lista de palabras.
<details>
<summary>Solución:</summary>
    
```kotlin
fun contarVocales(palabras: List<String>): Int {
    val vocales = setOf('a', 'e', 'i', 'o', 'u')
    var totalVocales = 0
    
    for (palabra in palabras) {
        totalVocales += palabra.lowercase().count { it in vocales }
    }
    
    return totalVocales
}

fun main() {
    val listaPalabras = listOf("Hola", "Mundo", "Kotlin")
    println("Total de vocales: ${contarVocales(listaPalabras)}")
}
```
</details>

## Ejercicio 7: Diccionario de sinónimos

Crea un mapa de sinónimos y una función para obtener sinónimos de una palabra.
<details>
<summary>Solución:</summary>
    
```kotlin
val sinonimos = mapOf(
    "feliz" to listOf("contento", "alegre", "dichoso"),
    "triste" to listOf("melancólico", "abatido", "apenado"),
    "enojado" to listOf("furioso", "irritado", "colérico")
)

fun obtenerSinonimos(palabra: String): List<String> {
    return sinonimos[palabra.lowercase()] ?: listOf("No se encontraron sinónimos")
}

fun main() {
    println("Sinónimos de 'feliz': ${obtenerSinonimos("feliz")}")
    println("Sinónimos de 'cansado': ${obtenerSinonimos("cansado")}")
}
```
</details>
