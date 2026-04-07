*Note: Just make sure the `package com.example.practicalX;` at the very top of the Java files matches your actual Android Studio project package name, otherwise Android Studio will throw an error.*
# MAD Practicals Easy

## Quick Navigation

* [4. TextView and EditText](#4-textview-and-edittext)
* [5. Button, ImageButton and Toggle Button](#5-button-imagebutton-and-toggle-button)
* [6. Checkbox and RadioButton](#6-checkbox-and-radiobutton)
* [7. Progress Bar](#7-progress-bar)
* [8. Login Form](#8-login-form)
* [9. Registration Form with Custom Toast](#9-registration-form-with-custom-toast)
* [12. Calculator](#12-calculator)
* [13. Splash Screen](#13-splash-screen)
* [14. Converter Application](#14-converter-application)
* [15. Countdown Timer](#15-countdown-timer)
* [16. Date Picker](#16-date-picker)
* [17. Time Picker](#17-time-picker)

---
---

### 4. TextView and EditText

**MainActivity.java**
```java
package com.example.practical4;

import android.os.Bundle;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        EditText et = findViewById(R.id.edittext);
        TextView tv = findViewById(R.id.textview);
        
        findViewById(R.id.btn).setOnClickListener(v -> tv.setText("Hello, " + et.getText()));
    }
}
```
**activity_main.xml**
```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent" android:layout_height="match_parent"
    android:orientation="vertical" android:gravity="center" android:padding="16dp">

    <EditText android:id="@+id/edittext" android:layout_width="match_parent" 
        android:layout_height="wrap_content" android:hint="Enter text"/>
    <Button android:id="@+id/btn" android:layout_width="wrap_content" 
        android:layout_height="wrap_content" android:text="Submit"/>
    <TextView android:id="@+id/textview" android:layout_width="wrap_content" 
        android:layout_height="wrap_content" android:textSize="18sp"/>
</LinearLayout>
```

---

### 5. Button, ImageButton and Toggle Button

**MainActivity.java**
```java
package com.example.practical5;

import android.graphics.Color;
import android.os.Bundle;
import android.widget.Button;
import android.widget.ImageButton;
import android.widget.TextView;
import android.widget.Toast;
import android.widget.ToggleButton;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        findViewById(R.id.btnRegular).setOnClickListener(v -> Toast.makeText(this, "Button Clicked!", Toast.LENGTH_SHORT).show());
        findViewById(R.id.imgBtn).setOnClickListener(v -> Toast.makeText(this, "Image Button Pressed", Toast.LENGTH_SHORT).show());

        TextView statusText = findViewById(R.id.tvStatus);
        ((ToggleButton) findViewById(R.id.toggleBtn)).setOnCheckedChangeListener((btn, isChecked) -> {
            statusText.setText(isChecked ? "Toggle is ON" : "Toggle is OFF");
            statusText.setTextColor(isChecked ? Color.BLUE : Color.RED);
        });
    }
}
```
**activity_main.xml**
```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent" android:layout_height="match_parent"
    android:orientation="vertical" android:gravity="center" android:padding="20dp">

    <Button android:id="@+id/btnRegular" android:layout_width="match_parent" android:layout_height="wrap_content" android:text="Click Me!"/>
    <ImageButton android:id="@+id/imgBtn" android:layout_width="80dp" android:layout_height="80dp" android:src="@mipmap/ic_launcher"/>
    <ToggleButton android:id="@+id/toggleBtn" android:layout_width="match_parent" android:layout_height="wrap_content"/>
    <TextView android:id="@+id/tvStatus" android:layout_width="wrap_content" android:layout_height="wrap_content" android:text="Toggle is OFF"/>
</LinearLayout>
```

---

### 6. Checkbox and RadioButton

**MainActivity.java**
```java
package com.example.practical6;

import android.graphics.Color;
import android.os.Bundle;
import android.widget.Button;
import android.widget.CheckBox;
import android.widget.RadioButton;
import android.widget.RadioGroup;
import android.widget.TextView;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        CheckBox cb1 = findViewById(R.id.cb1), cb2 = findViewById(R.id.cb2);
        TextView tv = findViewById(R.id.tvResult);

        findViewById(R.id.btnShow).setOnClickListener(v -> {
            String res = (cb1.isChecked() ? "Reading " : "") + (cb2.isChecked() ? "Gaming" : "");
            tv.setText(res.isEmpty() ? "None selected" : "Selected: " + res);
        });

        ((RadioGroup) findViewById(R.id.rg)).setOnCheckedChangeListener((group, id) -> {
            tv.setTextColor(id == R.id.rbMale ? Color.BLUE : Color.MAGENTA);
        });
    }
}
```
**activity_main.xml**
```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent" android:layout_height="match_parent"
    android:orientation="vertical" android:padding="20dp">

    <CheckBox android:id="@+id/cb1" android:layout_width="wrap_content" android:layout_height="wrap_content" android:text="Reading"/>
    <CheckBox android:id="@+id/cb2" android:layout_width="wrap_content" android:layout_height="wrap_content" android:text="Gaming"/>
    
    <RadioGroup android:id="@+id/rg" android:layout_width="wrap_content" android:layout_height="wrap_content">
        <RadioButton android:id="@+id/rbMale" android:layout_width="wrap_content" android:layout_height="wrap_content" android:text="Male"/>
        <RadioButton android:id="@+id/rbFemale" android:layout_width="wrap_content" android:layout_height="wrap_content" android:text="Female"/>
    </RadioGroup>

    <Button android:id="@+id/btnShow" android:layout_width="match_parent" android:layout_height="wrap_content" android:text="Show Result"/>
    <TextView android:id="@+id/tvResult" android:layout_width="match_parent" android:layout_height="wrap_content" android:textSize="18sp"/>
</LinearLayout>
```

---

### 7. Progress Bar

**MainActivity.java**
```java
package com.example.practical7;

import android.os.Bundle;
import android.widget.Button;
import android.widget.ProgressBar;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        
        ProgressBar pb = findViewById(R.id.progressBar);
        findViewById(R.id.btnStart).setOnClickListener(v -> new Thread(() -> {
            for (int i = 0; i <= 100; i++) {
                int progress = i;
                runOnUiThread(() -> pb.setProgress(progress));
                try { Thread.sleep(50); } catch (Exception e) {}
            }
        }).start());
    }
}
```
**activity_main.xml**
```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent" android:layout_height="match_parent"
    android:gravity="center" android:orientation="vertical">

    <ProgressBar android:id="@+id/progressBar" style="?android:attr/progressBarStyleHorizontal"
        android:layout_width="300dp" android:layout_height="wrap_content" android:max="100"/>
    <Button android:id="@+id/btnStart" android:layout_width="wrap_content" 
        android:layout_height="wrap_content" android:text="Start"/>
</LinearLayout>
```

---

### 8. Login Form

**MainActivity.java**
```java
package com.example.practical8;

import android.os.Bundle;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Toast;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        EditText user = findViewById(R.id.etUser), pass = findViewById(R.id.etPass);
        findViewById(R.id.btnLogin).setOnClickListener(v -> {
            boolean valid = user.getText().toString().equals("admin") && pass.getText().toString().equals("1234");
            Toast.makeText(this, valid ? "Success" : "Invalid", Toast.LENGTH_SHORT).show();
        });
    }
}
```
**activity_main.xml**
```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent" android:layout_height="match_parent"
    android:orientation="vertical" android:gravity="center" android:padding="30dp">

    <EditText android:id="@+id/etUser" android:layout_width="match_parent" android:layout_height="wrap_content" android:hint="Username"/>
    <EditText android:id="@+id/etPass" android:layout_width="match_parent" android:layout_height="wrap_content" android:hint="Password" android:inputType="textPassword"/>
    <Button android:id="@+id/btnLogin" android:layout_width="match_parent" android:layout_height="wrap_content" android:text="Login"/>
</LinearLayout>
```

---

### 9. Registration Form with Custom Toast

**MainActivity.java**
```java
package com.example.practical9;

import android.graphics.Color;
import android.os.Bundle;
import android.widget.Button;
import android.widget.CheckBox;
import android.widget.EditText;
import android.widget.TextView;
import android.widget.Toast;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        EditText name = findViewById(R.id.etName);
        CheckBox terms = findViewById(R.id.cbTerms);

        findViewById(R.id.btnRegister).setOnClickListener(v -> {
            if (!terms.isChecked() || name.getText().toString().isEmpty()) return;
            
            TextView customView = new TextView(this);
            customView.setText("Registered: " + name.getText());
            customView.setBackgroundColor(Color.DKGRAY);
            customView.setTextColor(Color.GREEN);
            customView.setPadding(30, 30, 30, 30);

            Toast t = new Toast(this);
            t.setView(customView);
            t.show();
        });
    }
}
```
**activity_main.xml**
```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent" android:layout_height="match_parent"
    android:orientation="vertical" android:padding="20dp">

    <EditText android:id="@+id/etName" android:layout_width="match_parent" android:layout_height="wrap_content" android:hint="Name"/>
    <CheckBox android:id="@+id/cbTerms" android:layout_width="wrap_content" android:layout_height="wrap_content" android:text="Accept Terms"/>
    <Button android:id="@+id/btnRegister" android:layout_width="match_parent" android:layout_height="wrap_content" android:text="Register"/>
</LinearLayout>
```

---

### 12. Calculator

**MainActivity.java**
```java
package com.example.practical12;

import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {
    EditText res;
    int num1;
    String op;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        res = findViewById(R.id.result);
    }

    public void click(View v) { res.append(((Button)v).getText()); }
    public void operator(View v) { num1 = Integer.parseInt(res.getText().toString()); op = ((Button)v).getText().toString(); res.setText(""); }
    public void equal(View v) {
        int num2 = Integer.parseInt(res.getText().toString());
        res.setText(String.valueOf(op.equals("+") ? num1 + num2 : num1 - num2));
    }
}
```
**activity_main.xml**
```xml
<?xml version="1.0" encoding="utf-8"?>
<GridLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:columnCount="4" android:layout_width="match_parent" android:layout_height="match_parent">
    
    <EditText android:id="@+id/result" android:layout_columnSpan="4" android:layout_width="match_parent" android:layout_height="wrap_content"/>
    <Button android:text="1" android:onClick="click"/> <Button android:text="2" android:onClick="click"/>
    <Button android:text="3" android:onClick="click"/> <Button android:text="+" android:onClick="operator"/>
    <Button android:text="=" android:layout_columnSpan="4" android:layout_width="match_parent" android:onClick="equal"/>
</GridLayout>
```

---

### 13. Splash Screen

**MainActivity.java**
```java
package com.example.practical13;

import android.os.Bundle;
import android.os.Handler;
import android.os.Looper;
import android.view.View;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        findViewById(R.id.logo).animate().alpha(1f).setDuration(2000).start();

        new Handler(Looper.getMainLooper()).postDelayed(() -> {
            findViewById(R.id.splash).setVisibility(View.GONE);
            findViewById(R.id.main).setVisibility(View.VISIBLE);
        }, 3000);
    }
}
```
**activity_main.xml**
```xml
<?xml version="1.0" encoding="utf-8"?>
<FrameLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent" android:layout_height="match_parent">

    <LinearLayout android:id="@+id/splash" android:layout_width="match_parent" android:layout_height="match_parent" android:gravity="center">
        <ImageView android:id="@+id/logo" android:layout_width="100dp" android:layout_height="100dp" android:src="@mipmap/ic_launcher" android:alpha="0"/>
    </LinearLayout>

    <TextView android:id="@+id/main" android:layout_width="match_parent" android:layout_height="match_parent" android:gravity="center" android:text="Main Screen" android:visibility="gone"/>
</FrameLayout>
```

---

### 14. Converter Application

**MainActivity.java**
```java
package com.example.practical14;

import android.os.Bundle;
import android.widget.ArrayAdapter;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Spinner;
import android.widget.TextView;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {
    double[] rates = {1.0, 0.012, 0.011}; // INR, USD, EUR
    String[] curr = {"INR", "USD", "EUR"};

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        Spinner s1 = findViewById(R.id.s1), s2 = findViewById(R.id.s2);
        ArrayAdapter<String> adp = new ArrayAdapter<>(this, android.R.layout.simple_spinner_item, curr);
        s1.setAdapter(adp); s2.setAdapter(adp);

        EditText input = findViewById(R.id.input);
        TextView res = findViewById(R.id.res);

        findViewById(R.id.btn).setOnClickListener(v -> {
            try {
                double amt = Double.parseDouble(input.getText().toString());
                double converted = (amt / rates[s1.getSelectedItemPosition()]) * rates[s2.getSelectedItemPosition()];
                res.setText(String.format("%.2f", converted));
            } catch (Exception e) { res.setText("Invalid"); }
        });
    }
}
```
**activity_main.xml**
```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent" android:layout_height="match_parent" android:orientation="vertical" android:padding="24dp">
    
    <EditText android:id="@+id/input" android:layout_width="match_parent" android:layout_height="wrap_content" android:inputType="numberDecimal"/>
    <Spinner android:id="@+id/s1" android:layout_width="match_parent" android:layout_height="wrap_content"/>
    <Spinner android:id="@+id/s2" android:layout_width="match_parent" android:layout_height="wrap_content"/>
    <Button android:id="@+id/btn" android:layout_width="match_parent" android:layout_height="wrap_content" android:text="Convert"/>
    <TextView android:id="@+id/res" android:layout_width="match_parent" android:layout_height="wrap_content" android:textSize="20sp"/>
</LinearLayout>
```

---

### 15. Countdown Timer

**MainActivity.java**
```java
package com.example.practical15;

import android.os.Bundle;
import android.os.CountDownTimer;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {
    CountDownTimer timer;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        TextView tv = findViewById(R.id.tvCount);
        EditText et = findViewById(R.id.etSecs);
        
        findViewById(R.id.btnStart).setOnClickListener(v -> {
            if(timer != null) timer.cancel();
            long millis = Long.parseLong(et.getText().toString().isEmpty() ? "10" : et.getText().toString()) * 1000;
            
            timer = new CountDownTimer(millis, 1000) {
                public void onTick(long m) { tv.setText(String.valueOf(m / 1000)); }
                public void onFinish() { tv.setText("Done!"); }
            }.start();
        });
    }
}
```
**activity_main.xml**
```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent" android:layout_height="match_parent" android:orientation="vertical" android:gravity="center" android:padding="20dp">

    <TextView android:id="@+id/tvCount" android:layout_width="wrap_content" android:layout_height="wrap_content" android:textSize="60sp" android:text="10"/>
    <EditText android:id="@+id/etSecs" android:layout_width="match_parent" android:layout_height="wrap_content" android:hint="Seconds" android:inputType="number"/>
    <Button android:id="@+id/btnStart" android:layout_width="wrap_content" android:layout_height="wrap_content" android:text="Start Timer"/>
</LinearLayout>
```

---

### 16. Date Picker

**MainActivity.java**
```java
package com.example.practical16;

import android.app.DatePickerDialog;
import android.os.Bundle;
import android.widget.Button;
import android.widget.TextView;
import androidx.appcompat.app.AppCompatActivity;
import java.util.Calendar;

public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        TextView tv = findViewById(R.id.tvDate);
        findViewById(R.id.btn).setOnClickListener(v -> {
            Calendar c = Calendar.getInstance();
            new DatePickerDialog(this, (view, y, m, d) -> tv.setText(d + "/" + (m + 1) + "/" + y), 
                c.get(Calendar.YEAR), c.get(Calendar.MONTH), c.get(Calendar.DAY_OF_MONTH)).show();
        });
    }
}
```
**activity_main.xml**
```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent" android:layout_height="match_parent" android:orientation="vertical" android:gravity="center">
    
    <Button android:id="@+id/btn" android:layout_width="wrap_content" android:layout_height="wrap_content" android:text="Pick Date"/>
    <TextView android:id="@+id/tvDate" android:layout_width="wrap_content" android:layout_height="wrap_content" android:textSize="18sp"/>
</LinearLayout>
```

---

### 17. Time Picker

**MainActivity.java**
```java
package com.example.practical17;

import android.app.TimePickerDialog;
import android.os.Bundle;
import android.widget.Button;
import android.widget.TextView;
import androidx.appcompat.app.AppCompatActivity;
import java.util.Calendar;

public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        TextView tv = findViewById(R.id.tvTime);
        findViewById(R.id.btn).setOnClickListener(v -> {
            Calendar c = Calendar.getInstance();
            new TimePickerDialog(this, (view, h, m) -> tv.setText(h + ":" + String.format("%02d", m)), 
                c.get(Calendar.HOUR_OF_DAY), c.get(Calendar.MINUTE), true).show();
        });
    }
}
```
**activity_main.xml**
```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent" android:layout_height="match_parent" android:orientation="vertical" android:gravity="center">
    
    <Button android:id="@+id/btn" android:layout_width="wrap_content" android:layout_height="wrap_content" android:text="Pick Time"/>
    <TextView android:id="@+id/tvTime" android:layout_width="wrap_content" android:layout_height="wrap_content" android:textSize="18sp"/>
</LinearLayout>
```
