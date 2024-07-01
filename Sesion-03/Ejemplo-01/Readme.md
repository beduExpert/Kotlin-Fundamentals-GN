## Clases y objetos

## Objetivo
- Crear el código para generar una clase.
- Instanciar clases.

## Requisitos
- Leer sobre Programación Orientada a Objetos (POO).

## Desarrollo
La Programación Orientada a Objetos (POO) interpreta problemas y los abstrae en modelos de objetos con atributos y métodos.

Una clase es un modelo abstracto de un objeto, y su representación más básica en Kotlin es la siguiente:

```kotlin
class NombreDeLaClase {
    // Atributos (propiedades) de la clase
    var atributo1: TipoDeDato1
    var atributo2: TipoDeDato2

    // Constructor de la clase
    constructor(atributo1: TipoDeDato1, atributo2: TipoDeDato2) {
        this.atributo1 = atributo1
        this.atributo2 = atributo2
    }

    // Métodos de la clase
    fun metodo1() {
        // Código del método
    }
}
```
Haciendo un repaso, en kotlin todas las variables son tomadas como objetos. Por tanto, incluso los tipos de datos primitivos son envueltos en un objeto para que puedan tener métodos.

```kotlin
val a=20
println("a es igual a 20? ${a.equals(20)}")
```

>a es igual a 20? true

la clase Int contiene un método llamado *equals*, al crear *val a*, estoy creando un objeto e la clase Int.

Para tener una lista donde guardar mi clase, crearemos un *package* llamado **clases**. 

<img src="imgs/01.png" width= "40%"/>

Dentro de ese paquete, vamos a crear nuestra clase, el proceso es similar a cuando creamos el archivo *main.kt* de cada proyecto, pero selecciconando ***Class*** en vez de ***File***. Nombrar a esa clase **Phone**

<img src="imgs/02.png" width= "40%"/>

Dentro de la clase, declararemos ciertos atributos: 

* bandera para saber si el dispositivo está prendido
* nombre de marca


la clase nos queda así

```kotlin
class Phone {

    //atributos
    var isOn = false
    lateinit var model:String   
}
```

Abora vamos a integrarle métodos, que representan accciones que pueden ser llevadas a cabo con el objeto que representa la clase. en este caso vamos a poder prenderlo y apagarlo. También tendremoss otro método para consultar estatus de prendido del teléfono.

```kotlin
class Phone{
...

    //métodos
    fun turnOn(){
        isOn = true
    }

    fun turnOff(){
        isOn = false
    }
    
    fun getTurn(){
        val turnMode = if(isOn) "Encendido" else "Apagado"
        println("el teléfono esta $turnMode")
    }
    
    

}
```
notar que los métodos modifican mi atributo prendido o apagado.


Para instanciar una clase, es decir, para crear un objeto a partir de la clase definida, vamos a declarar una variable que genere la instancia

```kotlin
val myPhone = Phone()
```

Aquí un gif que ejemplifica la declaración:

<img src="imgs/createObject.gif" width= "40%"/>

Ahora vamos a consultar el estado de mi teléfono (definimos como valor por defecto apagado), prenderemos el teléfono y volvemos a consultar su estado:

```kotlin
    myPhone.getTurn()
    myPhone.turnOn()
    myPhone.getTurn()
```

El resultado es el siguiente:

>el teléfono esta Apagado

>el teléfono esta Encendido






