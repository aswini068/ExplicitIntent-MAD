## Ex.No:2(b) To create a two screens , first screen will take one number input from user. After click on Factorial button, second screen will open and it should display factorial of the same number using Explicit Intents.


## AIM:

To create a two screens , first screen will take one number input from user. After click on Factorial button, second screen will open and it should display factorial of the same number using Explicit Intents.


## EQUIPMENTS REQUIRED:

Latest Version Android Studio

## ALGORITHM:

Step 1: Start App & Display First Screen
Launch the app.
Show the first screen (MainActivity) with:
EditText for user input (number)
Button labeled “Factorial”

Step 2: Get User Input
User enters a number in the EditText.
When the “Factorial” button is clicked:
Read the number from EditText.
Validate input (check if it’s not empty and is a positive integer).

Step 3: Use Explicit Intent to Open Second Screen
Create an Explicit Intent to start the second activity (ResultActivity).
Intent intent = new Intent(MainActivity.this, ResultActivity.class);
Pass the number to the second screen using Intent extras:
```
intent.putExtra("number", inputNumber);
```

Start the second activity:
startActivity(intent);


Step 4: Second Screen Receives Number
In ResultActivity’s onCreate() method:
Get the number from Intent:
```
int num = getIntent().getIntExtra("number", 0);
```

Step 5: Calculate Factorial

Initialize factorial = 1.
Loop from 1 to num:
```
for (int i = 1; i <= num; i++) {
    factorial *= i;
}
```
Or use BigInteger if large numbers.

Step 6: Display Result
Show the factorial in a TextView on the second screen.

Step 7: Optional Enhancements
Handle invalid inputs (empty or negative numbers) with a Toast message.
Use ScrollView if the factorial result is large.
Use BigInteger for very large numbers to prevent overflow.



## PROGRAM:
```
/*
Program to print the text “ExplicitIntent”.
Developed by: Aswini M
Registeration Number : 212223220010
*/
```
ACTIVITY MAIN.XML
```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:gravity="center"
    android:background="#0D0D1A"
    android:padding="20dp">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Factorial Calculator"
        android:textSize="24sp"
        android:textColor="#A020F0"
        android:layout_marginBottom="20dp"/>

    <EditText
        android:id="@+id/edtNumber"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter a Number"
        android:inputType="number"
        android:padding="12dp"
        android:background="@android:drawable/edit_text"
        android:textColor="#000000"
        android:textColorHint="#888888"/>

    <Button
        android:id="@+id/btnFactorial"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Factorial"
        android:layout_marginTop="20dp"
        android:backgroundTint="#00C2A8"
        android:textColor="#FFFFFF"/>
</LinearLayout>
```
MAINACTIVITY JAVA
```
package com.example.myfact;

import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    EditText edtNumber;
    Button btnFactorial;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        edtNumber = findViewById(R.id.edtNumber);
        btnFactorial = findViewById(R.id.btnFactorial);

        btnFactorial.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {

                String numStr = edtNumber.getText().toString().trim();

                if (!numStr.isEmpty()) {
                    int number = Integer.parseInt(numStr);

                    int factorial = 1;
                    for (int i = 1; i <= number; i++) {
                        factorial *= i;
                    }

                    Intent intent = new Intent(MainActivity.this, MainActivity2.class);
                    intent.putExtra("number", number);
                    intent.putExtra("result", factorial);
                    startActivity(intent);
                }
            }
        });
    }
}
```
ACITIVITY2 MAIN.XML
```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:gravity="center"
    android:orientation="vertical"
    android:background="#0D0D1A">

    <TextView
        android:id="@+id/txtResult"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Result"
        android:textSize="22sp"
        android:textColor="#FFFF00"/>
</LinearLayout>
```
MAINACTIVITY2 JAVA
```
package com.example.myfact;

import android.os.Bundle;
import android.widget.TextView;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity2 extends AppCompatActivity {

    TextView txtResult;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main2);

        txtResult = findViewById(R.id.txtResult);

        int number = getIntent().getIntExtra("number", 0);
        int result = getIntent().getIntExtra("result", 0);

        txtResult.setText(number + "! = " + result);
    }
}
```
## OUTPUT

<img width="1723" height="950" alt="Screenshot 2025-09-16 105210" src="https://github.com/user-attachments/assets/13b75527-9de2-4500-847b-b2d5a0b2ad79" />


<img width="1919" height="1076" alt="Screenshot 2025-09-16 105225" src="https://github.com/user-attachments/assets/65b1bf13-7a8c-428d-ae09-487bbeeb85ec" />


<img width="1918" height="1078" alt="Untitled design (8)" src="https://github.com/user-attachments/assets/86a45e63-db9c-4441-be77-3d686db2315e" />


<img width="1918" height="1078" alt="Untitled design (10)" src="https://github.com/user-attachments/assets/f7a84459-4764-41cd-8c29-f0fc2984d3a5" />


<img width="1918" height="1078" alt="Untitled design (11)" src="https://github.com/user-attachments/assets/ad04b50c-e0a1-44c1-838a-16627d7392d9" />



## RESULT
Thus a Simple Android Application create a Explicit Intents using Android Studio is developed and executed successfully.


