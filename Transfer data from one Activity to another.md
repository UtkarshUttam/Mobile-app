```kotlin
MainActivity (Sends data) ----> SecondActivity (Receives data)
```

# MainActivity.java
```java
package com.example.transferdata;

import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        EditText editText = findViewById(R.id.editTextData);
        Button button = findViewById(R.id.buttonSend);

        button.setOnClickListener(v -> {
            String data = editText.getText().toString();
            Intent intent = new Intent(MainActivity.this, SecondActivity.class);
            intent.putExtra("EXTRA_DATA", data);
            startActivity(intent);
        });
    }
}
```

# SecondActivity.java
```java
package com.example.transferdata;

import android.os.Bundle;
import android.widget.TextView;
import androidx.appcompat.app.AppCompatActivity;

public class SecondActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_second);

        TextView textView = findViewById(R.id.textViewData);
        String data = getIntent().getStringExtra("EXTRA_DATA");
        textView.setText(data);
    }
}
```
# activity_main.xml
```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:gravity="center"
    android:padding="16dp">

    <EditText
        android:id="@+id/editTextData"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:hint="Enter Data"/>

    <Button
        android:id="@+id/buttonSend"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Send Data"/>
</LinearLayout>
```

# activity_second.xml
```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:gravity="center"
    android:padding="16dp">

    <TextView
        android:id="@+id/textViewData"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"/>
</LinearLayout>
```