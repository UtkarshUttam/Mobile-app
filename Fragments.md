### Android Fragments

Fragments are modular sections of an activity in Android that can be used to create more flexible and reusable UI components. Fragments are similar to activities in that they have their own lifecycle, receive their own input events, and can be added or removed while the activity is running.

### Key Features of Fragments:
1. **Modularity**: Fragments allow for building reusable and flexible UIs.
2. **Lifecycle Management**: Fragments have their own lifecycle methods.
3. **Dynamic UI**: Fragments can be added, removed, or replaced dynamically.
4. **Reusable Components**: Fragments can be used in multiple activities.
5. **Support for Different Screen Sizes**: Fragments make it easier to support multiple screen sizes by using different layouts for different device configurations.

### Fragment Lifecycle

The lifecycle of a fragment is similar to that of an activity, but it has additional states. Here are the key lifecycle methods:

1. **onAttach()**: Called when the fragment is first attached to its context.
2. **onCreate()**: Called to initialize the fragment.
3. **onCreateView()**: Called to create the view hierarchy associated with the fragment.
4. **onActivityCreated()**: Called when the activity’s onCreate() method has returned.
5. **onStart()**: Called when the fragment becomes visible.
6. **onResume()**: Called when the fragment is visible and actively running.
7. **onPause()**: Called when the fragment is no longer interacting with the user.
8. **onStop()**: Called when the fragment is no longer visible.
9. **onDestroyView()**: Called to clean up the view hierarchy.
10. **onDestroy()**: Called to do final cleanup of the fragment’s state.
11. **onDetach()**: Called when the fragment is detached from its context.

### Example of Using Fragments

**1. Define a Fragment Class:**

```java
package com.example.fragmentdemo;

import android.os.Bundle;
import android.view.LayoutInflater;
import android.view.View;
import android.view.ViewGroup;
import androidx.fragment.app.Fragment;

public class ExampleFragment extends Fragment {
    @Override
    public View onCreateView(LayoutInflater inflater, ViewGroup container, Bundle savedInstanceState) {
        // Inflate the layout for this fragment
        return inflater.inflate(R.layout.fragment_example, container, false);
    }
}
```

**2. Define the Fragment Layout (fragment_example.xml):**

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="16dp">

    <TextView
        android:id="@+id/textView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Hello from Fragment!"
        android:textSize="20sp"/>
</LinearLayout>
```

**3. Add Fragment to an Activity (activity_main.xml):**

```xml
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <FrameLayout
        android:id="@+id/fragment_container"
        android:layout_width="match_parent"
        android:layout_height="match_parent"/>
</RelativeLayout>
```

**4. Add Fragment to Activity Programmatically (MainActivity.java):**

```java
package com.example.fragmentdemo;

import android.os.Bundle;
import androidx.appcompat.app.AppCompatActivity;
import androidx.fragment.app.Fragment;
import androidx.fragment.app.FragmentManager;
import androidx.fragment.app.FragmentTransaction;

public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // Add fragment to activity
        FragmentManager fragmentManager = getSupportFragmentManager();
        FragmentTransaction fragmentTransaction = fragmentManager.beginTransaction();
        Fragment fragment = new ExampleFragment();
        fragmentTransaction.add(R.id.fragment_container, fragment);
        fragmentTransaction.commit();
    }
}
```

### Summary

- **Fragments**: Reusable UI components with their own lifecycle.
- **Lifecycle Methods**: Manage the lifecycle of fragments with methods like onCreate(), onCreateView(), onStart(), onResume(), onPause(), onStop(), and onDestroyView().
- **Usage**: Define fragment classes, create layouts for fragments, and add fragments to activities either statically through XML or dynamically in Java/Kotlin code.
- **Flexibility**: Fragments support dynamic UI changes and better handling of different screen sizes and orientations.
![[Pasted image 20240622193952.png]]