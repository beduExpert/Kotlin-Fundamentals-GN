## Postwork

## 1. Herencia y Polimorfismo

Crea una clase base Animal con un método hacerSonido(). Luego, crea dos clases derivadas Perro y Gato que hereden de Animal y sobrescriban el método hacerSonido(). Finalmente, crea una función que reciba un Animal y llame a su método hacerSonido().

<details>
<summary>Ver solución</summary>
    
```kotlin
open class Animal {
    open fun hacerSonido() {
        println("El animal hace un sonido")
    }
}

class Perro : Animal() {
    override fun hacerSonido() {
        println("El perro ladra")
    }
}

class Gato : Animal() {
    override fun hacerSonido() {
        println("El gato maulla")
    }
}

fun hacerSonar(animal: Animal) {
    animal.hacerSonido()
}

fun main() {
    val perro = Perro()
    val gato = Gato()
    
    hacerSonar(perro) // Imprime: El perro ladra
    hacerSonar(gato)  // Imprime: El gato maulla
}
```
</details>

## 2. Clases Abstractas

Crea una clase abstracta Figura con un método abstracto calcularArea(). Luego, implementa dos clases concretas Circulo y Rectangulo que hereden de Figura e implementen el método calcularArea().

<details>
<summary>Ver solución</summary>
    
```kotlin
abstract class Figura {
    abstract fun calcularArea(): Double
}

class Circulo(private val radio: Double) : Figura() {
    override fun calcularArea(): Double {
        return Math.PI * radio * radio
    }
}

class Rectangulo(private val base: Double, private val altura: Double) : Figura() {
    override fun calcularArea(): Double {
        return base * altura
    }
}

fun main() {
    val circulo = Circulo(5.0)
    val rectangulo = Rectangulo(4.0, 6.0)
    
    println("Área del círculo: ${circulo.calcularArea()}")
    println("Área del rectángulo: ${rectangulo.calcularArea()}")
}
```
</details>

## 3. Interfaces

Crea una interfaz Volador con un método volar(). Luego, implementa esta interfaz en las clases Ave y Avion. Crea una función que reciba un Volador y llame a su método volar().

<details>
<summary>Ver solución</summary>
    
```kotlin
interface Volador {
    fun volar()
}

class Ave : Volador {
    override fun volar() {
        println("El ave vuela moviendo sus alas")
    }
}

class Avion : Volador {
    override fun volar() {
        println("El avión vuela usando motores")
    }
}

fun hacerVolar(volador: Volador) {
    volador.volar()
}

fun main() {
    val ave = Ave()
    val avion = Avion()
    
    hacerVolar(ave)   // Imprime: El ave vuela moviendo sus alas
    hacerVolar(avion) // Imprime: El avión vuela usando motores
}
```
</details>

## 4. Data Classes
Crea una data class Libro con propiedades para título, autor y año de publicación. Luego, crea una lista de libros y utiliza las funciones generadas automáticamente para copiar un libro y comparar dos libros.

<details>
<summary>Ver solución</summary>
    
```kotlin
data class Libro(val titulo: String, val autor: String, val anioPublicacion: Int)

fun main() {
    val libro1 = Libro("1984", "George Orwell", 1949)
    val libro2 = Libro("Cien años de soledad", "Gabriel García Márquez", 1967)
    val libro3 = libro1.copy(titulo = "Rebelión en la granja")
    
    val libros = listOf(libro1, libro2, libro3)
    
    println(libro1 == libro2) // false
    println(libro1 == libro1.copy()) // true
    
    libros.forEach { println(it) }
}
```
</details>

## 5. Companion Object

Crea una clase Contador con un companion object que mantenga un contador global de instancias creadas. Cada vez que se cree una nueva instancia de Contador, el contador global debe incrementarse.

<details>
<summary>Ver solución</summary>
    
```kotlin
class Contador {
    companion object {
        private var contadorGlobal = 0
        
        fun obtenerContadorGlobal(): Int {
            return contadorGlobal
        }
    }
    
    init {
        contadorGlobal++
    }
}

fun main() {
    println(Contador.obtenerContadorGlobal()) // 0
    
    val contador1 = Contador()
    println(Contador.obtenerContadorGlobal()) // 1
    
    val contador2 = Contador()
    val contador3 = Contador()
    println(Contador.obtenerContadorGlobal()) // 3
}
```
</details>

## 6. Herencia Múltiple con Interfaces

Crea dos interfaces Nadador y Corredor con métodos nadar() y correr() respectivamente. Luego, crea una clase Triatleta que implemente ambas interfaces. Finalmente, crea una función que reciba un objeto y verifique si puede nadar, correr o ambos.

<details>
<summary>Ver solución</summary>
    
```kotlin
interface Nadador {
    fun nadar()
}

interface Corredor {
    fun correr()
}

class Triatleta : Nadador, Corredor {
    override fun nadar() {
        println("El triatleta está nadando")
    }
    
    override fun correr() {
        println("El triatleta está corriendo")
    }
}

fun verificarHabilidades(obj: Any) {
    if (obj is Nadador) {
        obj.nadar()
    }
    if (obj is Corredor) {
        obj.correr()
    }
}

fun main() {
    val triatleta = Triatleta()
    verificarHabilidades(triatleta)
}
```
</details>
