# Casts en Kotlin

## Objetivo

El objetivo de esta sección es aprender a utilizar los distintos tipos de casting de datos en Kotlin, así como a manejar los errores que pueden surgir durante el proceso de conversión de tipos.

## Requisitos

- Haber leído los ejercicios 1 y 2 de esta unidad para familiarizarse con los conceptos básicos.

## Desarrollo

En Kotlin, el casting o conversión de tipos permite cambiar el tipo de una variable a otro tipo compatible. Existen diferentes formas de hacer casting en Kotlin, cada una con sus propias características y usos. A continuación, exploraremos los conceptos clave de los casts en Kotlin: **Smart Casts**, **Unsafe Casts** y **Safe Casts**.

### 1. **Smart Casts y el Operador `is`**

El operador `is` se usa para verificar el tipo de un objeto en tiempo de ejecución. Si el objeto cumple con el tipo especificado en la condición, Kotlin realiza automáticamente un **Smart Cast**.

**Ejemplo: Uso del Operador `is`**

```kotlin
fun verificarTipo(obj: Any) {
    if (obj is String) {
        println("El objeto es una String de longitud ${obj.length}")
    } else {
        println("El objeto no es una String")
    }
}

verificarTipo("Hola, Kotlin")  // Output: El objeto es una String de longitud 12
verificarTipo(42)              // Output: El objeto no es una String
```
En el ejemplo, obj is String verifica si obj es una instancia de String. Si es así, Kotlin automáticamente convierte obj al tipo String dentro del bloque if.

Ejemplo: Smart Casts en when

```kotlin

fun imprimirNumerico(x: Any) {
    when (x) {
        is Int -> println(x + 1)                  // Si x es Int, incrementa en 1
        is String -> println(x.length + 1)      // Si x es String, imprime la longitud más 1
        is IntArray -> println(x.sum())         // Si x es IntArray, imprime la suma de sus elementos
        else -> println("Tipo no soportado")    // Para cualquier otro tipo
    }
}

imprimirNumerico(20)            // Output: 21
imprimirNumerico("asereje")    // Output: 9
imprimirNumerico(intArrayOf(2, 4, 6))  // Output: 12
```
En el ejemplo, when usa Smart Casts para manejar diferentes tipos de datos en base a su tipo real.

## 2. Unsafe Cast
Un Unsafe Cast es una conversión forzada que puede causar una excepción en tiempo de ejecución si el tipo no es compatible.

Ejemplo: Unsafe Cast

```kotlin

val obj2: Any? = null
val str: String = obj2 as String  // Esto lanzará una excepción en tiempo de ejecución
```
Error Esperado:

```graphql

Exception in thread "main" kotlin.TypeCastException: null cannot be cast to non-null type kotlin.String
```
En este caso, intentamos convertir un valor null a String, lo que genera una excepción TypeCastException.

## 3. Safe Cast
El Safe Cast permite convertir un objeto a otro tipo de manera segura. Si el cast falla, en lugar de lanzar una excepción, asigna null al resultado.

Ejemplo: Safe Cast

```kotlin

val obj2: Any? = null
val str: String? = obj2 as? String  // Safe cast que resultará en null
println(str)  // Output: null
```
En este ejemplo, obj2 as? String intenta convertir obj2 a String de forma segura. Si obj2 no es una instancia de String, str se convierte en null sin lanzar una excepción.

## 4. Comparación de Casting en Kotlin
A continuación, se muestra una tabla comparativa entre los diferentes tipos de casting en Kotlin:

| Tipo de Cast   | Descripción                                                                | Ejemplo                                         |
|----------------|----------------------------------------------------------------------------|-------------------------------------------------|
| **Smart Cast** | Conversión automática basada en una verificación de tipo en tiempo de ejecución. | `if (obj is String) { println(obj.length) }`   |
| **Unsafe Cast**| Conversión forzada que puede lanzar una excepción si los tipos no coinciden. | `val str: String = obj as String`              |
| **Safe Cast**  | Conversión segura que devuelve `null` si el tipo no es compatible.         | `val str: String? = obj as? String`            |

## 5. Resumen
En Kotlin, el manejo de tipos y el casting son fundamentales para escribir código seguro y eficiente. Usar Smart Casts facilita el trabajo con tipos, mientras que los Safe Casts previenen errores potenciales al trabajar con tipos nulos. Los Unsafe Casts deben ser usados con precaución, ya que pueden causar errores en tiempo de ejecución.

Adoptar estos métodos de casting te ayudará a escribir código más robusto y libre de errores en Kotlin.
