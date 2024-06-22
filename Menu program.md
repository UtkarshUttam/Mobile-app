Here’s a simple example of an Android app with a menu. This will include necessary code for both files (`MainActivity.java` and `activity_main.xml`), keeping it as short as possible.

### MainActivity.java

```java
package com.example.menudemo;

import android.os.Bundle;
import android.view.Menu;
import android.view.MenuInflater;
import android.view.MenuItem;
import android.widget.Toast;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }

    @Override
    public boolean onCreateOptionsMenu(Menu menu) {
        MenuInflater inflater = getMenuInflater();
        inflater.inflate(R.menu.menu_main, menu);
        return true;
    }

    @Override
    public boolean onOptionsItemSelected(MenuItem item) {
        switch (item.getItemId()) {
            case R.id.action_settings:
                Toast.makeText(this, "Settings selected", Toast.LENGTH_SHORT).show();
                return true;
            case R.id.action_about:
                Toast.makeText(this, "About selected", Toast.LENGTH_SHORT).show();
                return true;
            default:
                return super.onOptionsItemSelected(item);
        }
    }
}
```

### activity_main.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:padding="16dp">

    <TextView
        android:id="@+id/textView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Hello, World!"
        android:textSize="20sp"/>
</RelativeLayout>
```

### menu_main.xml (Menu Resource)

Create a new XML file under `res/menu/menu_main.xml`.

```xml
<?xml version="1.0" encoding="utf-8"?>
<menu xmlns:android="http://schemas.android.com/apk/res/android">
    <item
        android:id="@+id/action_settings"
        android:title="Settings"/>
    <item
        android:id="@+id/action_about"
        android:title="About"/>
</menu>
```

### Explanation

1. **MainActivity.java**:
   - **onCreateOptionsMenu**: Inflates the menu from `menu_main.xml`.
   - **onOptionsItemSelected**: Handles menu item clicks, showing a Toast message for each item.

2. **activity_main.xml**:
   - A simple layout with a `TextView`.

3. **menu_main.xml**:
   - Defines the menu with two items: "Settings" and "About".

### Output

When the app runs, you will see a "Hello, World!" text. The menu will have two items: "Settings" and "About". Clicking on each item will show a Toast message. 

![Menu Program](https://i.imgur.com/YmXlIij.png)