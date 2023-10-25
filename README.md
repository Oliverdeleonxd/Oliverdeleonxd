## En el Manifest

Agregas estos 3 perminos

```java
<uses-permission android:name="android.permission.MODIFY_AUDIO_SETTINGS" />  
<uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />  
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
```

## En el MainActivity

```java
package com.example.play;  
import androidx.appcompat.app.AppCompatActivity;  
import android.content.Context;  
import android.media.AudioManager;  
import android.os.Bundle;  
import android.view.KeyEvent;  
import android.view.View;  
  
public class MainActivity extends AppCompatActivity {  
    // CRear objeto de la clase AudioManager  
    AudioManager mAudioManager;  
    @Override  
    protected void onCreate(Bundle savedInstanceState) {  
        super.onCreate(savedInstanceState);  
        setContentView(R.layout.activity_main);  
        // inicialixar el Onjeto  
         mAudioManager = (AudioManager) getSystemService(Context.AUDIO_SERVICE);  
    }  
    // Funcion para la reproduccion y pausa  
    public void playPauseMusic(View view) {  
        if (mAudioManager.isMusicActive()) { // si esta reproduciendose  
            // Para pausar la música
            KeyEvent eventPause = new KeyEvent(KeyEvent.ACTION_DOWN, KeyEvent.KEYCODE_MEDIA_PAUSE);
            mAudioManager.dispatchMediaKeyEvent(eventPause);  
        }else { // si no esta reproduciendose  
            // Para reproducir la música
            KeyEvent eventPlay = new KeyEvent(KeyEvent.ACTION_DOWN, KeyEvent.KEYCODE_MEDIA_PLAY);  
            mAudioManager.dispatchMediaKeyEvent(eventPlay);  
        }  
    }// fin de la funcion  
  
}
```

## En el Xml 

```java
<?xml version="1.0" encoding="utf-8"?>  
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"  
    xmlns:app="http://schemas.android.com/apk/res-auto"  
    xmlns:tools="http://schemas.android.com/tools"  
    android:layout_width="match_parent"  
    android:layout_height="match_parent"  
    tools:context=".MainActivity">  
  
    <TextView  
        android:id="@+id/txt"  
        android:layout_width="wrap_content"  
        android:layout_height="wrap_content"  
        android:text="Hello World!"  
        app:layout_constraintBottom_toBottomOf="parent"  
        app:layout_constraintLeft_toLeftOf="parent"  
        app:layout_constraintRight_toRightOf="parent"  
        app:layout_constraintTop_toTopOf="parent" />  
  
    <Button  
        android:id="@+id/play_pause_button"  
        android:layout_width="wrap_content"  
        android:layout_height="wrap_content"  
        android:onClick="playPauseMusic"  
        android:text="Play/Pause"  
        app:layout_constraintBottom_toBottomOf="parent"  
        app:layout_constraintEnd_toEndOf="parent"  
        app:layout_constraintStart_toStartOf="parent"  
        app:layout_constraintTop_toBottomOf="@+id/txt" />  
  
  
</androidx.constraintlayout.widget.ConstraintLayout>
```
