## Postwork

## Ejercicios de Interoperabilidad Kotlin-Java

## 1. Uso de Clases Java en Kotlin

Crea una clase Java llamada Persona con propiedades nombre y edad, y sus respectivos getters y setters. Luego, en Kotlin, crea una instancia de esta clase y modifica sus propiedades.

<details>
<summary>Ver solución</summary>
    
```java
    // Persona.java
public class Persona {
    private String nombre;
    private int edad;

    public String getNombre() { return nombre; }
    public void setNombre(String nombre) { this.nombre = nombre; }
    public int getEdad() { return edad; }
    public void setEdad(int edad) { this.edad = edad; }
}
kotlinCopy// main.kt
fun main() {
    val persona = Persona()
    persona.nombre = "Juan"
    persona.edad = 25
    println("Nombre: ${persona.nombre}, Edad: ${persona.edad}")
}
```
</details>

## 2. Uso de Clases Kotlin en Java

Crea una clase Kotlin llamada Producto con propiedades nombre y precio. Luego, en Java, crea una instancia de esta clase y accede a sus propiedades.

<details>
<summary>Ver solución</summary>
    
```kotlin
// Producto.kt
class Producto(var nombre: String, var precio: Double)
javaCopy// Main.java
public class Main {
    public static void main(String[] args) {
        Producto producto = new Producto("Laptop", 999.99);
        System.out.println("Nombre: " + producto.getNombre() + ", Precio: " + producto.getPrecio());
    }
}
```
</details>

## 3. Miembros Estáticos de Java en Kotlin

Crea una clase Java con un método estático y una constante estática. Luego, accede a estos miembros desde Kotlin.

<details>
<summary>Ver solución</summary>
    
```java
// Util.java
public class Util {
    public static final String VERSION = "1.0";
    public static int sumar(int a, int b) {
        return a + b;
    }
}
```

```kotlin
// main.kt
fun main() {
    println("Versión: ${Util.VERSION}")
    println("Suma: ${Util.sumar(5, 3)}")
}
```
</details>

## 4. Companion Object de Kotlin en Java

Crea una clase Kotlin con un companion object que contenga un método y una propiedad. Luego, accede a estos miembros desde Java.

<details>
<summary>Ver solución</summary>
    
```kotlin
// Calculadora.kt
class Calculadora {
    companion object {
        const val PI = 3.14159
        fun cuadrado(n: Int): Int = n * n
    }
}
```

```java
// Main.java
public class Main {
    public static void main(String[] args) {
        System.out.println("PI: " + Calculadora.PI);
        System.out.println("Cuadrado de 5: " + Calculadora.Companion.cuadrado(5));
    }
}
```
</details>

## 5. Uso de Keywords de Kotlin como Identificadores en Java

Crea una clase Java con métodos cuyos nombres sean palabras clave en Kotlin (por ejemplo, when, is, object). Luego, llama a estos métodos desde Kotlin.

<details>
<summary>Ver solución</summary>
    
```java
// Keywords.java
public class Keywords {
    public static void when() {
        System.out.println("Método when");
    }
    
    public static void is() {
        System.out.println("Método is");
    }
    
    public static void object() {
        System.out.println("Método object");
    }
}
```

```kotlin
// main.kt
fun main() {
    Keywords.`when`()
    Keywords.`is`()
    Keywords.`object`()
}
```
</details>

## 6. Propiedades Kotlin con Nombres Especiales en Java

Crea una clase Kotlin con propiedades cuyos nombres requieran un tratamiento especial en Java (por ejemplo, is para un booleano). Luego, accede a estas propiedades desde Java.

<details>
<summary>Ver solución</summary>
    
```kotlin
// EstadoObjeto.kt
class EstadoObjeto {
    var isActivo: Boolean = false
    var hasValor: Int = 0
}
```

```java
// Main.java
public class Main {
    public static void main(String[] args) {
        EstadoObjeto estado = new EstadoObjeto();
        estado.setActivo(true);
        estado.setHasValor(10);
        System.out.println("Activo: " + estado.isActivo());
        System.out.println("Valor: " + estado.getHasValor());
    }
}
```
</details>
