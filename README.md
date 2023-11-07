# Tugas UTS pemrograman mobile

# nama : Malik aziz

# nim : 312210130

# kelas : TI.22.B1

<br>

# tugas menampilkan toast dan fibonaci

<br>
* toast.xml untuk membuat design pada user interface

```
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:orientation="vertical"
        android:gravity="center"

        android:background="@color/yellow"
        android:paddingLeft="40dp"
        android:paddingRight="40dp">

        <TextView
            android:id="@+id/textView"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginTop="10dp"
            android:fontFamily="sans-serif-light"
            android:text="Increment"
            android:textColor="@color/white"
            android:textAlignment="center"
            android:textSize="30sp"/>

        <TextView
            android:id="@+id/textView2"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginTop="10dp"
            android:text="0"
            android:textColor="@color/white"
            android:textAlignment="center"
            android:textSize="28sp"/>

        <TextView
            android:id="@+id/textView3"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginTop="10dp"
            android:text="Fibonacci"
            android:textColor="@color/white"
            android:textAlignment="center"
            android:textSize="30sp"/>

        <TextView
            android:id="@+id/textView4"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginTop="10dp"
            android:text="0"
            android:textColor="@color/white"
            android:textAlignment="center"
            android:textFontWeight="600"
            android:textSize="28sp"/>


    </LinearLayout>

    <Button
        android:id="@+id/button_toast"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_alignParentLeft="true"
        android:layout_alignParentBottom="true"
        android:layout_marginLeft="20dp"
        android:layout_marginBottom="15dp"
        android:backgroundTint="@color/blue"
        android:textColor="@color/white"
        android:text="Toast"/>
    <Button
        android:id="@+id/button_reset"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Reset"
        android:layout_marginTop="20dp"
        android:backgroundTint="@color/Red"
        android:textColor="@color/white"
        android:layout_marginLeft="10dp"
        android:textAlignment="center"/>

    <Button
        android:id="@+id/button_hitung"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Hitung"
        android:layout_marginBottom="15dp"
        android:layout_alignParentBottom="true"
        android:layout_alignParentRight="true"
        android:layout_marginRight="20dp"
        android:backgroundTint="@color/blue"
        android:textColor="@color/white"/>
</RelativeLayout>
```

<br>

- kemudian string untuk membuat text

```
<resources>
    <string name="app_name">fibonacci</string>
    <string name="button_label_toast">Toast</string>
    <string name="button_label_hitung">Hitung</string>
    <string name="hitung_initial_value">0</string>
    <string name="toast_pesan">Berhasil DiKlik</string>

</resources>
```

<br>

- untuk pewarnaan bisa di di lakukan di layout bagian color.
- kemudian untuk logic nya kita menggunakan java sebagai berikut
  <br>

```
package com.co.id.fibonacci;

import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.TextView;
import android.widget.Toast;

public class MainActivity extends AppCompatActivity {
    private int mCount = 0;
    private int mCountFibo = 0;
    private TextView mShowCount;
    private TextView mShowCountFibo;
    private Button buttonToast;
    private Button buttonHitung;
    private Button buttonReset;


    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.toast_activity);
        mShowCount = (TextView) findViewById(R.id.textView2);
        mShowCountFibo = (TextView) findViewById(R.id.textView4);
        buttonToast = (Button) findViewById(R.id.button_toast);
        buttonHitung = (Button) findViewById(R.id.button_hitung);
        buttonReset = (Button) findViewById(R.id.button_reset);

        buttonHitung.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) { hitungIncrement(view);}

        });
        buttonToast.setOnClickListener(new View.OnClickListener(){
            @Override
            public void onClick(View view) {showToast(view);}
        });
        buttonReset.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) { resetCountDanFibbo(view);}
        });
        // class di atas di gunakan untuk melakukan reset pada tombol reset.
    }


    public void showToast(View view){
        Toast toast = Toast.makeText(this, "Berhasil DiKlik",Toast.LENGTH_SHORT);
        toast.show();
    }

    public void hitungIncrement(View view){
        mCount++;
        int fibo = hitungFibonacci(mCount);
        mCountFibo =fibo;
        if(mShowCount != null && mShowCountFibo != null){
            mShowCount.setText(Integer.toString(mCount));
            mShowCountFibo.setText(Integer.toString(mCountFibo));
        }
    }

    public int hitungFibonacci(int n){  // untuk code ini di gunakan untuk membuat angka fibbo nya

        if(n <= 1){
            return n;
        }
        int prev = 0;
        int current = 1;
        for(int i = 2; i <= n; i++){
            int next = prev + current;
            prev = current;
            current = next;
        }
        return current;
    }
    public void resetCountDanFibbo(View view){
        mCount = 0;
        mCountFibo = 0;
        mShowCount.setText(Integer.toString(mCount));
        mShowCountFibo.setText(Integer.toString(mCountFibo));

    }
}
```

<br>

- Hasil

![img](<img/Screenshot%20(51).png>)
<br>

- berikut link youtub untuk video lebiih lanjut :
