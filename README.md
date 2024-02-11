# GPA_shahs31_Calculator

//...........MainActivity.java



package com.example.gpa_shahs31_project;


import android.graphics.Color;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;

import androidx.appcompat.app.AppCompatActivity;
import androidx.constraintlayout.widget.ConstraintLayout;




public class MainActivity extends AppCompatActivity {
    Button button, textview7 ;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        final EditText grade1 = findViewById(R.id.editTextNumber);
        final EditText grade2 = findViewById(R.id.editTextNumber2);
        final EditText grade3 = findViewById(R.id.editTextNumber3);
        final EditText grade4 = findViewById(R.id.editTextNumber4);
        final EditText grade5 = findViewById(R.id.editTextNumber5);
        Button calculateButton = findViewById(R.id.button);
        final TextView gpaResult = findViewById(R.id.textview7);
        final ConstraintLayout backgroundLayout = findViewById(R.id.mainLayot); // Assuming your root layout has the id mainLayout

        calculateButton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                double gpa = calculateGPA(new EditText[]{grade1, grade2, grade3, grade4, grade5});
                gpaResult.setText(String.format("Your GPA is: %.2f", gpa));
                changeBackgroundColor(gpa, backgroundLayout);
                calculateButton.setText("Clear Form");
            }
        });
    }

    private double calculateGPA(EditText[] grades) {
        double sum = 0;
        for (EditText grade : grades) {
            double value = Double.parseDouble(grade.getText().toString());
            sum += getGradePoint(value);
        }
        return sum / grades.length;
    }

    private double getGradePoint(double grade) {
        if (grade >= 90) return grade;
        if (grade >= 80) return grade;
        if (grade >= 70) return grade;
        if (grade >= 60) return grade;
        return 0.0;
    }

    private void changeBackgroundColor(double gpa, ConstraintLayout layout) {
        if (gpa >= 80.0) { // Equivalent to 80-100
            layout.setBackgroundColor(Color.GREEN);
        } else if (gpa >= 61.0 && gpa < 79.0) { // Equivalent to 61-79
            layout.setBackgroundColor(Color.YELLOW);
        } else { // Less than 60
            layout.setBackgroundColor(Color.RED);
        }
    }
    protected void onResume() {
        super.onResume();

        button.setText("Compute GPA");
        textview7.setBackgroundColor(getResources().getColor(android.R.color.transparent));
    }
}






//..........activity_main.xml





<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    tools:context=".MainActivity"
    android:configChanges="orientation|screenSize"
    android:id="@+id/mainLayot"
    android:padding="16dp">


    <TextView
        android:id="@+id/textView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="5dp"
        android:layout_marginBottom="53dp"
        android:text="gpa_calculator"
        app:layout_constraintBottom_toTopOf="@+id/editTextNumber"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <TextView
        android:id="@+id/textView2"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="55dp"
        android:layout_marginTop="60dp"
        android:layout_marginEnd="10dp"
        android:layout_marginBottom="16dp"
        android:text="subject1"
        app:layout_constraintBottom_toTopOf="@+id/textView3"
        app:layout_constraintEnd_toStartOf="@+id/editTextNumber"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/textView" />

    <EditText
        android:id="@+id/editTextNumber"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="55dp"
        android:layout_marginTop="5dp"
        android:layout_marginEnd="73dp"
        android:ems="10"

        android:hint="Enter Grade"
        android:imeOptions="actionDone"
        android:inputType="number"
        app:layout_constraintBottom_toTopOf="@+id/editTextNumber2"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toEndOf="@+id/textView2"
        app:layout_constraintTop_toBottomOf="@+id/textView" />

    <TextView
        android:id="@+id/textView3"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="10dp"
        android:layout_marginTop="20dp"
        android:layout_marginEnd="35dp"
        android:layout_marginBottom="15dp"
        android:text="Subject2"
        app:layout_constraintBottom_toTopOf="@+id/textView4"
        app:layout_constraintEnd_toStartOf="@+id/editTextNumber3"
        app:layout_constraintHorizontal_bias="0.0"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/textView2" />

    <EditText
        android:id="@+id/editTextNumber2"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="30dp"
        android:layout_marginEnd="10dp"
        android:ems="10"
        android:hint="Enter Grade"
        android:imeOptions="actionDone"
        android:inputType="number"
        app:layout_constraintBottom_toTopOf="@+id/editTextNumber3"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toEndOf="@+id/textView3"
        app:layout_constraintTop_toBottomOf="@+id/editTextNumber" />

    <TextView
        android:id="@+id/textView4"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="40dp"
        android:layout_marginTop="23dp"
        android:layout_marginEnd="34dp"
        android:layout_marginBottom="66dp"
        android:text="Subject3"
        app:layout_constraintBottom_toTopOf="@+id/textView5"
        app:layout_constraintEnd_toStartOf="@+id/editTextNumber3"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/textView3" />

    <EditText
        android:id="@+id/editTextNumber3"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="34dp"
        android:layout_marginTop="5dp"
        android:layout_marginEnd="73dp"
        android:ems="10"
        android:hint="Enter Grade"
        android:imeOptions="actionDone"
        android:inputType="number"
        app:layout_constraintBottom_toTopOf="@+id/editTextNumber4"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toEndOf="@+id/textView4"
        app:layout_constraintTop_toBottomOf="@+id/editTextNumber2" />

    <TextView
        android:id="@+id/textView5"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="40dp"
        android:layout_marginTop="20dp"
        android:layout_marginEnd="33dp"
        android:text="Subject4"
        app:layout_constraintEnd_toStartOf="@+id/editTextNumber4"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/textView4" />

    <TextView
        android:id="@+id/textView6"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="40dp"
        android:layout_marginTop="20dp"
        android:layout_marginEnd="33dp"
        android:text="Subject5"
        app:layout_constraintEnd_toStartOf="@+id/editTextNumber5"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/textView5" />

    <EditText
        android:id="@+id/editTextNumber4"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="33dp"
        android:layout_marginTop="5dp"
        android:layout_marginEnd="73dp"
        android:ems="10"
        android:hint="Enter_grade"
        android:imeOptions="actionDone"
        android:inputType="number"
        app:layout_constraintBottom_toTopOf="@+id/editTextNumber5"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toEndOf="@+id/textView5"
        app:layout_constraintTop_toBottomOf="@+id/editTextNumber3" />

    <EditText
        android:id="@+id/editTextNumber5"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="33dp"
        android:layout_marginTop="5dp"
        android:layout_marginEnd="73dp"
        android:ems="10"
        android:hint="Enter Grade"
        android:imeOptions="actionDone"
        android:inputType="number"
        app:layout_constraintBottom_toTopOf="@+id/button"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toEndOf="@+id/textView6"
        app:layout_constraintTop_toBottomOf="@+id/editTextNumber4" />

    <Button
        android:id="@+id/button"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="63dp"
        android:text="Compute Gpa"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/editTextNumber5" />

    <TextView
        android:id="@+id/textview7"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="156dp"
        android:text="Result"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/editTextNumber5" />

</androidx.constraintlayout.widget.ConstraintLayout>
