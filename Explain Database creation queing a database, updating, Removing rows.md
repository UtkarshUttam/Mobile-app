### SQLite Database Operations in Android

SQLite is a lightweight database that comes embedded with Android. It allows you to store and manage data in a structured manner. Here's how you can create a database, insert data, update data, and delete data in SQLite in an Android application.

### 1. Database Creation

**Step 1: Create a Database Helper Class**

Create a class that extends `SQLiteOpenHelper`. This class will help manage the creation, updating, and deletion of the database.

```java
package com.example.mydatabaseapp;

import android.content.Context;
import android.database.sqlite.SQLiteDatabase;
import android.database.sqlite.SQLiteOpenHelper;

public class DatabaseHelper extends SQLiteOpenHelper {
    private static final String DATABASE_NAME = "MyDatabase.db";
    private static final int DATABASE_VERSION = 1;

    // Table name
    private static final String TABLE_NAME = "Users";
    // Table columns
    private static final String COLUMN_ID = "id";
    private static final String COLUMN_NAME = "name";
    private static final String COLUMN_AGE = "age";

    // SQL query to create the table
    private static final String CREATE_TABLE = "CREATE TABLE " + TABLE_NAME + " (" +
            COLUMN_ID + " INTEGER PRIMARY KEY AUTOINCREMENT, " +
            COLUMN_NAME + " TEXT, " +
            COLUMN_AGE + " INTEGER);";

    public DatabaseHelper(Context context) {
        super(context, DATABASE_NAME, null, DATABASE_VERSION);
    }

    @Override
    public void onCreate(SQLiteDatabase db) {
        db.execSQL(CREATE_TABLE);
    }

    @Override
    public void onUpgrade(SQLiteDatabase db, int oldVersion, int newVersion) {
        db.execSQL("DROP TABLE IF EXISTS " + TABLE_NAME);
        onCreate(db);
    }
}
```

### 2. Inserting Data

**Step 2: Create Methods to Perform Database Operations**

```java
package com.example.mydatabaseapp;

import android.content.ContentValues;
import android.content.Context;
import android.database.sqlite.SQLiteDatabase;

public class DatabaseManager {
    private DatabaseHelper dbHelper;
    private SQLiteDatabase database;

    public DatabaseManager(Context context) {
        dbHelper = new DatabaseHelper(context);
    }

    public void open() {
        database = dbHelper.getWritableDatabase();
    }

    public void close() {
        dbHelper.close();
    }

    public void insertUser(String name, int age) {
        ContentValues values = new ContentValues();
        values.put("name", name);
        values.put("age", age);
        database.insert("Users", null, values);
    }
}
```

### 3. Updating Data

**Step 3: Add Method for Updating Data**

```java
public void updateUser(int id, String name, int age) {
    ContentValues values = new ContentValues();
    values.put("name", name);
    values.put("age", age);
    database.update("Users", values, "id = ?", new String[]{String.valueOf(id)});
}
```

### 4. Removing Rows

**Step 4: Add Method for Deleting Data**

```java
public void deleteUser(int id) {
    database.delete("Users", "id = ?", new String[]{String.valueOf(id)});
}
```

### Example Usage

**Step 5: Using the DatabaseManager in an Activity**

```java
package com.example.mydatabaseapp;

import android.os.Bundle;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {
    private DatabaseManager dbManager;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        dbManager = new DatabaseManager(this);
        dbManager.open();

        // Insert a user
        dbManager.insertUser("John Doe", 25);

        // Update a user
        dbManager.updateUser(1, "Jane Doe", 26);

        // Delete a user
        dbManager.deleteUser(1);

        dbManager.close();
    }
}
```

### Summary of Key Operations

1. **Creating the Database**:
   - Define a `SQLiteOpenHelper` class to manage database creation and version management.
   - Override `onCreate()` to define the schema of the database.
   - Override `onUpgrade()` to handle database version upgrades.

2. **Inserting Data**:
   - Use `ContentValues` to store key-value pairs representing column names and their respective values.
   - Call `insert()` on the SQLite database instance.

3. **Updating Data**:
   - Use `ContentValues` to store the new data.
   - Call `update()` with the appropriate `WHERE` clause to specify which rows to update.

4. **Deleting Data**:
   - Call `delete()` with the appropriate `WHERE` clause to specify which rows to delete.

By following these steps, you can create, update, and delete data in an SQLite database within your Android application. This code is streamlined to fit within limited space for easy handwritten note-taking.