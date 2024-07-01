# Funciones en Kotlin

## 1. Introducción a las funciones en Kotlin
Las funciones en Kotlin son bloques de código reutilizables que realizan una tarea específica. Nos ayudan a modularizar nuestro código, haciéndolo más organizado y fácil de mantener.

## 2. Sintaxis básica de funciones
La estructura básica de una función en Kotlin es:

```kotlin
fun nombreDeLaFuncion(parametro1: TipoDeDato1, parametro2: TipoDeDato2): TipoDeRetorno {
    // Código de la función
    return resultadoDeLaFuncion
}
```
## Ejemplo:

```kotlin
fun circleArea(radius: Float): Float {
    return PI * radius * radius
}
```
Nota: PI es una constante que deberías definir previamente, por ejemplo: const val PI = 3.1416f

## 3. Tipos de retorno y Unit
Las funciones pueden retornar un valor específico o no retornar nada (Unit).
Unit es el equivalente a void en otros lenguajes.

Ejemplos:

```kotlin
Copiar código
// Función que retorna un valor
fun suma(a: Int, b: Int): Int {
    return a + b
}

// Función que no retorna valor (Unit)
fun imprimirSaludo(nombre: String) {
    println("Hola, $nombre!")
}

// Unit puede omitirse
fun imprimirDespedida(nombre: String): Unit {
    println("Adiós, $nombre!")
}
```

## 4. Funciones locales
Las funciones locales son funciones definidas dentro de otras funciones.

Ejemplo:

``` kotlin

fun login(user: String, password: String): Boolean {
    fun validate(input: String): Boolean {
        return input.isNotEmpty()
    }
    
    val userValidated = validate(user)
    val passValidated = validate(password)
    
    return userValidated && passValidated
}
```
Consejo: Las funciones locales son útiles para encapsular lógica que solo se usa dentro de una función específica.

## 5. Argumentos por defecto y argumentos nombrados
Kotlin permite establecer valores por defecto para los parámetros y usar argumentos nombrados al llamar a las funciones.

``` kotlin

fun rectangleArea(base: Double = 20.0, height: Double = 30.0): Double {
    return base * height
}

// Uso:
println(rectangleArea())  // Usa valores por defecto
println(rectangleArea(10.0))  // Base = 10.0, altura por defecto
println(rectangleArea(height = 15.0))  // Base por defecto, altura = 15.0
println(rectangleArea(height = 5.0, base = 2.0))  // Usando argumentos nombrados
```

## 6. Ejercicios prácticos
Crea una función que calcule el volumen de un cilindro.
Implementa una función que determine si un número es primo.
Desarrolla una función local dentro de otra función que valide una dirección de email.
Desafío: Intenta resolver estos ejercicios por tu cuenta y luego compara tus soluciones con las de un compañero o mentor.
