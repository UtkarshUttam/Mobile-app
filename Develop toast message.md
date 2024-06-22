# `MainActivity.java`
```java
package com.example.toastdemo;

import android.os.Bundle;
import android.view.View;
import android.widget.Toast;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        findViewById(R.id.buttonShowToast).setOnClickListener(v -> 
            Toast.makeText(MainActivity.this, "Hello, Toast!", Toast.LENGTH_SHORT).show()
        );
    }
}
```

# `activity_main.xml`
```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:gravity="center"
    android:padding="16dp">

    <Button
        android:id="@+id/buttonShowToast"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Show Toast"/>
</LinearLayout>

```