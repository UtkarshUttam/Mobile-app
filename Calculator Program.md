MainActivity.java

```java
Java package com.example.calculator;

import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {
    EditText display;
    double val1, val2;
    boolean add, sub, mul, div;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        display = findViewById(R.id.display);

        Button[] numButtons = new Button[10];
        for (int i = 0; i < 10; i++) {
            int resID = getResources().getIdentifier("button" + i, "id", getPackageName());
            numButtons[i] = findViewById(resID);
            final int index = i;
            numButtons[i].setOnClickListener(v -> display.append(String.valueOf(index)));
        }

        findViewById(R.id.buttonAdd).setOnClickListener(v -> { val1 = getVal(); add = true; clear(); });
        findViewById(R.id.buttonSub).setOnClickListener(v -> { val1 = getVal(); sub = true; clear(); });
        findViewById(R.id.buttonMul).setOnClickListener(v -> { val1 = getVal(); mul = true; clear(); });
        findViewById(R.id.buttonDiv).setOnClickListener(v -> { val1 = getVal(); div = true; clear(); });
        findViewById(R.id.buttonEqual).setOnClickListener(v -> calculate());
    }

    double getVal() { return Double.parseDouble(display.getText().toString()); }
    void clear() { display.setText(""); }
    void calculate() {
        val2 = getVal();
        if (add) display.setText(String.valueOf(val1 + val2));
        if (sub) display.setText(String.valueOf(val1 - val2));
        if (mul) display.setText(String.valueOf(val1 * val2));
        if (div) display.setText(String.valueOf(val1 / val2));
        add = sub = mul = div = false;
    }
}
```




ActivityMain.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="16dp">

    <EditText
        android:id="@+id/display"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:inputType="numberDecimal"
        android:gravity="end"
        android:textSize="24sp"/>

    <GridLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:columnCount="4">
        
        <Button android:id="@+id/button0" android:text="0"/>
        <Button android:id="@+id/button1" android:text="1"/>
        <Button android:id="@+id/button2" android:text="2"/>
        <Button android:id="@+id/button3" android:text="3"/>
        <Button android:id="@+id/button4" android:text="4"/>
        <Button android:id="@+id/button5" android:text="5"/>
        <Button android:id="@+id/button6" android:text="6"/>
        <Button android:id="@+id/button7" android:text="7"/>
        <Button android:id="@+id/button8" android:text="8"/>
        <Button android:id="@+id/button9" android:text="9"/>
        <Button android:id="@+id/buttonAdd" android:text="+"/>
        <Button android:id="@+id/buttonSub" android:text="-"/>
        <Button android:id="@+id/buttonMul" android:text="*"/>
        <Button android:id="@+id/buttonDiv" android:text="/"/>
        <Button android:id="@+id/buttonEqual" android:text="="/>
    </GridLayout>
</LinearLayout>

```
