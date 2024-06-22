### Shortest Code for SQLite Database with Employee, Student, and Product Tables

Below is the essential code to create an SQLite database in an Android application with three tables: Employee, Student, and Product. The code includes basic operations such as creating the database and inserting data.

#### DatabaseHelper.java
This class manages database creation and version management.

```java
package com.example.myapp;

import android.content.Context;
import android.database.sqlite.SQLiteDatabase;
import android.database.sqlite.SQLiteOpenHelper;

public class DatabaseHelper extends SQLiteOpenHelper {
    private static final String DATABASE_NAME = "MyDatabase.db";
    private static final int DATABASE_VERSION = 1;

    // Table creation SQL
    private static final String CREATE_EMPLOYEE_TABLE = "CREATE TABLE Employee (id INTEGER PRIMARY KEY AUTOINCREMENT, name TEXT, department TEXT);";
    private static final String CREATE_STUDENT_TABLE = "CREATE TABLE Student (id INTEGER PRIMARY KEY AUTOINCREMENT, name TEXT, course TEXT);";
    private static final String CREATE_PRODUCT_TABLE = "CREATE TABLE Product (id INTEGER PRIMARY KEY AUTOINCREMENT, name TEXT, price REAL);";

    public DatabaseHelper(Context context) {
        super(context, DATABASE_NAME, null, DATABASE_VERSION);
    }

    @Override
    public void onCreate(SQLiteDatabase db) {
        db.execSQL(CREATE_EMPLOYEE_TABLE);
        db.execSQL(CREATE_STUDENT_TABLE);
        db.execSQL(CREATE_PRODUCT_TABLE);
    }

    @Override
    public void onUpgrade(SQLiteDatabase db, int oldVersion, int newVersion) {
        db.execSQL("DROP TABLE IF EXISTS Employee");
        db.execSQL("DROP TABLE IF EXISTS Student");
        db.execSQL("DROP TABLE IF EXISTS Product");
        onCreate(db);
    }
}
```

#### DatabaseManager.java
This class provides methods to insert data into each table.

```java
package com.example.myapp;

import android.content.ContentValues;
import android.content.Context;
import android.database.sqlite.SQLiteDatabase;

public class DatabaseManager {
    private DatabaseHelper dbHelper;
    private SQLiteDatabase database;

    public DatabaseManager(Context context) {
        dbHelper = new DatabaseHelper(context);
        database = dbHelper.getWritableDatabase();
    }

    public void insertEmployee(String name, String department) {
        ContentValues values = new ContentValues();
        values.put("name", name);
        values.put("department", department);
        database.insert("Employee", null, values);
    }

    public void insertStudent(String name, String course) {
        ContentValues values = new ContentValues();
        values.put("name", name);
        values.put("course", course);
        database.insert("Student", null, values);
    }

    public void insertProduct(String name, double price) {
        ContentValues values = new ContentValues();
        values.put("name", name);
        values.put("price", price);
        database.insert("Product", null, values);
    }

    public void close() {
        dbHelper.close();
    }
}
```

#### MainActivity.java
This class demonstrates how to use the `DatabaseManager` to insert data into the database.

```java
package com.example.myapp;

import android.os.Bundle;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {
    private DatabaseManager dbManager;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        dbManager = new DatabaseManager(this);

        // Insert sample data
        dbManager.insertEmployee("Alice", "HR");
        dbManager.insertStudent("Bob", "Engineering");
        dbManager.insertProduct("Laptop", 999.99);

        dbManager.close();
    }
}
```

### Summary of Essential Parts

1. **DatabaseHelper**: Manages database creation and upgrades.
   - Tables: Employee, Student, Product.
   - SQL statements for table creation.

2. **DatabaseManager**: Provides methods to insert data into each table.
   - Methods: `insertEmployee()`, `insertStudent()`, `insertProduct()`.

3. **MainActivity**: Demonstrates database operations.
   - Inserts sample data into each table.

This code covers the essentials for creating an SQLite database with three tables and performing basic insert operations. It is concise and suitable for handwritten notes.