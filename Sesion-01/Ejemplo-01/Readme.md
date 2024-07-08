# Android Studio: Primeros pasos y Hola Mundo

## OBJETIVO
* Instalar y configurar Android Studio
* Utilizar las herramientas básicas que nos proporciona el entorno de desarrollo
* Crear nuestro primer programa con Kotlin en Android Studio

## REQUISITOS
1. Tener suficiente espacio en la memoria para instalar Android Studio

## DESARROLLO

### Instalación de Android Studio

1. Visita el sitio web oficial de Android Developers para descargar Android Studio: https://developer.android.com/studio

2. Descarga el archivo de instalación correspondiente a tu sistema operativo.

3. Ejecuta el archivo descargado e instala Android Studio siguiendo las instrucciones del asistente de instalación.

### Nuestro primer proyecto

1. Abre Android Studio. Aparecerá la pantalla de bienvenida.

2. Haz clic en "New Project" (Nuevo Proyecto).

3. En la ventana "New Project", selecciona "Empty Activity" (Actividad vacía) y haz clic en "Next".

4. Configura tu proyecto:
   - Name: HelloWorld
   - Package name: com.example.helloworld
   - Save location: Elige una ubicación para tu proyecto
   - Language: Kotlin
   - Minimum SDK: Selecciona la versión mínima de Android que deseas soportar

5. Haz clic en "Finish" para crear el proyecto.

6. Android Studio generará automáticamente la estructura del proyecto y los archivos necesarios.

7. Abre el archivo MainActivity.kt en la carpeta app > java > com.example.helloworld.

8. Reemplaza el contenido del archivo con el siguiente código:

```kotlin
package com.example.helloworld

import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.widget.TextView

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val textView = findViewById<TextView>(R.id.textView)
        textView.text = "¡Hola Bedu!"
    }
}
```

9. Abre el archivo activity_main.xml en la carpeta app > res > layout y reemplaza su contenido con:
```kotlin
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout 
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <TextView
        android:id="@+id/textView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Hello World!"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

</androidx.constraintlayout.widget.ConstraintLayout>
```

10. Para ejecutar la aplicación, haz clic en el botón "Run" (triángulo verde) en la barra de herramientas superior o presiona Shift + F10.
Selecciona un emulador o conecta un dispositivo Android para ver la aplicación en ejecución.

11. La aplicación debería mostrar el mensaje "¡Hola Bedu!" en el centro de la pantalla.

