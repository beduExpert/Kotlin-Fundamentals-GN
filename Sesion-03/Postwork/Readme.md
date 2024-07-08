## Postwork

# Ejercicios de Kotlin: Clases, Objetos y Constructores

## Ejercicio 1: Clase Libro

Crea una clase `Libro` con los atributos `titulo`, `autor` y `añoPublicacion`. Incluye un constructor primario y un método para imprimir la información del libro.

<details>
<summary>Ver solución</summary>

```kotlin
class Libro(val titulo: String, val autor: String, val añoPublicacion: Int) {
    fun imprimirInfo() {
        println("'$titulo' por $autor ($añoPublicacion)")
    }
}

fun main() {
    val miLibro = Libro("1984", "George Orwell", 1949)
    miLibro.imprimirInfo()
}
```
</details>

## Ejercicio 2: Clase Cuenta Bancaria

Diseña una clase CuentaBancaria con un atributo privado saldo. Incluye métodos para depositar, retirar y consultar saldo.

<details>
<summary>Ver solución</summary>
    
```kotlin
class CuentaBancaria(saldoInicial: Double) {
    private var saldo = saldoInicial

    fun depositar(monto: Double) {
        saldo += monto
        println("Depósito de $monto realizado. Nuevo saldo: $saldo")
    }

    fun retirar(monto: Double) {
        if (monto <= saldo) {
            saldo -= monto
            println("Retiro de $monto realizado. Nuevo saldo: $saldo")
        } else {
            println("Saldo insuficiente")
        }
    }

    fun consultarSaldo() = println("Saldo actual: $saldo")
}

fun main() {
    val cuenta = CuentaBancaria(100.0)
    cuenta.depositar(50.0)
    cuenta.retirar(30.0)
    cuenta.consultarSaldo()
}
```
</details>

## Ejercicio 3: Clase con Constructor Secundario

Crea una clase Rectangulo con atributos ancho y alto. Incluye un constructor primario y un constructor secundario que inicialice ambos valores con el mismo número.

<details>
<summary>Ver solución</summary>

```kotlin
    class Rectangulo(val ancho: Double, val alto: Double) {
    constructor(lado: Double) : this(lado, lado)

    fun calcularArea() = ancho * alto
}

fun main() {
    val rectangulo1 = Rectangulo(5.0, 3.0)
    val cuadrado = Rectangulo(4.0)

    println("Área del rectángulo: ${rectangulo1.calcularArea()}")
    println("Área del cuadrado: ${cuadrado.calcularArea()}")
}
```
</details>

## Ejercicio 4: Getters y Setters Personalizados

Implementa una clase Temperatura con un atributo en Celsius. Incluye getters y setters personalizados para obtener y establecer la temperatura en Fahrenheit.

<details>
<summary>Ver solución</summary>
    
```kotlin
    class Temperatura(celsius: Double) {
    var celsius = celsius
        set(value) {
            field = value
            println("Temperatura establecida a $value°C")
        }

    var fahrenheit: Double
        get() = celsius * 9/5 + 32
        set(value) {
            celsius = (value - 32) * 5/9
            println("Temperatura establecida a $value°F")
        }
}

fun main() {
    val temp = Temperatura(25.0)
    println("En Fahrenheit: ${temp.fahrenheit}°F")
    temp.fahrenheit = 68.0
    println("En Celsius: ${temp.celsius}°C")
}
```
</details>

## Ejercicio 5: Clase con Propiedades Lazy
Crea una clase Calculadora con una propiedad pi que se inicialice de manera perezosa (lazy) y un método para calcular el área de un círculo.

<details>
<summary>Ver solución</summary>
    
```kotlin
class Calculadora {
    val pi: Double by lazy {
        println("Calculando pi...")
        3.14159265359
    }

    fun areaCirculo(radio: Double): Double {
        return pi * radio * radio
    }
}

fun main() {
    val calc = Calculadora()
    println("Área de un círculo con radio 5: ${calc.areaCirculo(5.0)}")
    println("Área de un círculo con radio 3: ${calc.areaCirculo(3.0)}")
}
```
</details>

## Ejercicio 6: Clase con Métodos de Extensión

Define una clase Persona con propiedades nombre y edad. Luego, crea un método de extensión para imprimir un saludo personalizado.

<details>
<summary>Ver solución</summary>
    
```kotlin
class Persona(val nombre: String, val edad: Int)

fun Persona.saludar() {
    println("Hola, mi nombre es $nombre y tengo $edad años.")
}

fun main() {
    val persona = Persona("Ana", 28)
    persona.saludar()
}
```
</details>
