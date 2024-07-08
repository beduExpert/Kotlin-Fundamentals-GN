## Postwork

## Ejercicios de Kotlin: Null Safety, Excepciones y Casting

## Ejercicio 1: Null Safety

Dado el siguiente código:
```kotlin
var nombre: String? = "Juan"
```

¿Cuál es la forma correcta de obtener la longitud del nombre si no es nulo, o devolver 0 si es nulo?

<details>
<summary>Ver solución</summary>
    
```kotlin
val longitud = nombre?.length ?: 0
```
Esta solución utiliza el operador de llamada segura ?. y el operador Elvis ?: para manejar el caso nulo de manera concisa.
</details>

## Ejercicio 2: Manejo de Excepciones

Escribe una función que tome un String y lo convierta a un Int. Si la conversión falla, la función debe devolver null. Usa un bloque try-catch para manejar la excepción.

<details>
<summary>Ver solución</summary>
    
```kotlin
fun convertirAEntero(str: String): Int? {
    return try {
        str.toInt()
    } catch (e: NumberFormatException) {
        null
    }
}
```
Esta función intenta convertir el String a Int y devuelve null si ocurre una NumberFormatException.
</details>

## Ejercicio 3: Smart Casting

Dada la siguiente clase sellada:

```kotlin
sealed class Resultado
class Exito(val mensaje: String) : Resultado()
class Error(val codigo: Int) : Resultado()
```
Escribe una función que tome un Resultado y devuelva un String describiendo el resultado.

<details>
<summary>Ver solución</summary>
    
```kotlin
fun describirResultado(resultado: Resultado): String {
    return when (resultado) {
        is Exito -> "Éxito: ${resultado.mensaje}"
        is Error -> "Error: Código ${resultado.codigo}"
    }
}
```
Esta función utiliza smart casting para acceder a las propiedades específicas de cada subclase de Resultado.

</details>

## Ejercicio 4: Safe Cast

Escribe una función que tome un Any y lo convierta de manera segura a un List<String>. Si la conversión no es posible, debe devolver una lista vacía.

<details>
<summary>Ver solución</summary>
    
```kotlin
fun convertirAListaDeStrings(objeto: Any): List<String> {
    return (objeto as? List<*>)?.filterIsInstance<String>() ?: emptyList()
}
```
Esta función utiliza safe cast as? y filterIsInstance para realizar una conversión segura.
</details>

## Ejercicio 5: Manejo de Null con Let
Dada una variable nullable usuario: Usuario?, escribe un código que imprima el nombre del usuario si existe, o "Usuario desconocido" si es null. Usa la función let.

<details>
<summary>Ver solución</summary>
    
```kotlin
usuario?.let { 
    println(it.nombre) 
} ?: println("Usuario desconocido")
```
Esta solución utiliza let para ejecutar un bloque de código solo si usuario no es null, y el operador Elvis para manejar el caso nulo.
</details>

## Ejercicio 6: Lanzamiento de Excepciones Personalizadas

Crea una función dividir que tome dos enteros y devuelva su división. Si el segundo número es cero, debe lanzar una excepción personalizada llamada DivisionPorCeroException.

<details>
<summary>Ver solución</summary>
    
```kotlin
class DivisionPorCeroException : Exception("No se puede dividir por cero")

fun dividir(a: Int, b: Int): Int {
    if (b == 0) {
        throw DivisionPorCeroException()
    }
    return a / b
}
```
Esta función verifica si el divisor es cero y lanza una excepción personalizada en ese caso.
</details>
