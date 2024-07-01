# Declaración de Variables en Kotlin

## OBJETIVO
* Comprender el concepto de variable
* Aprender a declarar variables de forma implícita y explícita

## REQUISITOS
1. Tener una idea básica de qué es una variable en programación

## DESARROLLO

### Variables
Una variable es un espacio en memoria que almacena un dato. Accedemos a este espacio mediante un identificador para leer o modificar su contenido. En Kotlin, las variables se tratan como objetos, lo que significa que podemos invocar métodos desde una variable (este tema se abordará más adelante).

Existen tres tipos de declaraciones de variables en Kotlin:

* **var:** Variables mutables que pueden cambiar su valor.
* **val:** Variables inmutables cuyo valor no puede modificarse una vez asignado. La asignación puede ocurrir en tiempo de ejecución (*runtime*).
* **const:** Variables inmutables cuyo valor se determina en tiempo de compilación (*compile time*).

### Ejercicio Práctico

Abre un nuevo proyecto y crea un archivo `main.kt` con el siguiente código:

```kotlin
fun main() {
    var number1 = 21
    number1 = 3
    println(number1)

    val number2 = 7
    println(number2)

    // Esta línea causará un error de compilación
    // number2 = 8

    // Declaración correcta de una constante
    println(number3)
}

// Declaración de constante a nivel de archivo
const val number3 = 24
