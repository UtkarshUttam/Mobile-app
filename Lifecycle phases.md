### Key Transitions

- **onCreate()** -> **onStart()** -> **onResume()**: The activity moves to the foreground.
- **onPause()** -> **onResume()**: The activity is temporarily paused.
- **onStop()** -> **onRestart()** -> **onStart()**: The activity is stopped and then restarted.
- **onStop()** -> **onDestroy()**: The activity is completely destroyed.

### Explanation

- **onCreate()**: Initial setup, UI inflation.
- **onStart()**: Activity is becoming visible.
- **onResume()**: Activity is in the foreground, interactive.
- **onPause()**: Activity is partially obscured, but still visible.
- **onStop()**: Activity is completely hidden.
- **onDestroy()**: Cleanup before activity is destroyed.
- **onRestart()**: Restart activity from stopped state.
![ActivityLifecycle](https://media.geeksforgeeks.org/wp-content/uploads/20210303165235/ActivityLifecycleinAndroid-601x660.jpg)