## MainActivity.java
```java
package com.example.registrationform;

import android.os.Bundle;
import android.view.View;
import android.widget.EditText;
import android.widget.RadioButton;
import android.widget.Spinner;
import android.widget.TextView;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity{
EditText name, password, address, age;
RadioButton male, female;
Spinner state;
TextView result;

@Override
protected void onCreate(Bundle savedInstanceState){
super.onCreate(savedInstanceState);
setContentView(R.layout.activity_main);

name = findViewById(R.id.editTextName);
password = findViewById(R.id.editTextPassword);
address = findViewById(R.id.editTextAddress);
age = findViewById(R.id.editTextAge);
male = findViewById(R.id.radioButtonMale);
female = findViewById(R.id.iradioButtonFemale);
state = findViewById(R.id.spinnerState);
result = findViewById(r.id.textViewResult);

findViewById(R.id.buttonSubmit).setOnClickListener(v -> {
String gender = male.isChecked() ? "Male":"Female";
result.setText("Name:" + name.getText().toString() +
			  "\nPassword: " + password.getText().toString() + 
			  "\nAddress: " + address.getText().toString() +
			  "\nGender: " + gender +
			  "\nAge: " + age.getText().toString() +
			  "\nState: " + state.getSelectedItem().toString());
		});
	}
}

```

## activity_main.xml
```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
			  android:layout_width = "match_parent"
			  android:layout_height = "match_parent"
			  android:orientation = "vertical"
			  android:padding="16dp">
			<EditText
				android:id="@+id/editTextName"
				android:layout_width = "match_parent"
				android:layout_height = "wrap_content"
				android:hint="User Name"/>

			<EditText
				android:id="@+id/editTextPassword"
				android:layout_width="match_parent"
				android:layout_height="wrap_content"
				android:hint="Password"
				android:inputType="textPassword"/>

			<EditText
				android:id="@+id/editTextAddress"
				android:layout_width="match_parent"
				android:layout_height="wrap_content"
				android:hint="Address"/>

			<RadioGroup
				android:layout_width="match_parent"
				android:layout_height="wrap_content">
				<RadioButton
					android:id="@+id/radioButtonMale"
					android:layout_width="wrap_content"
					android:layout_height="wrap_content"
					android:text="Male"/>
				<RadioButton
					android:id="@+id/radioButtonFemale"
					android:layout_width="wrap_content"
					android:layout_height="wrap_content"
					android:text="Female"/>
			</RadioGroup>

			<EditText
				android:id="@+id/editTextAge"
				android:layout_width="match_parent"
				android:layout_height="wrap_content"
				android:hint="Age"
				android:inputType="number"/>
			<Spinner
				android:id="@+id/spinnerState"
				android:layout_width="match_parent"
				android:layout_height="wrap_content"				
				android:entries="@array/state_array"/>

			<Button
				android:id="@+id/buttonSubmit"
				android:layout_width="match_parent"
				android:layout_height="wrap_content"
				android:text="Submit"/>
			<TextView
				android:id="@+id/textViewResult"
				android:layout_width="match_parent"
				android:layout_height="wrap_content"
				android:paddingTop="16dp"/>
</LinearLayout>
```