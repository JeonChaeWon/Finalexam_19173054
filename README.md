# 19173054 전채원 캡스톤디자인 기말고사 과제 제출

## 로그인 화면

### activity_login.xml

<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent" >

    <RelativeLayout
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_margin="10dp"
        android:layout_centerInParent="true"
        android:background="#aaffffff"
        >
        <LinearLayout
            android:orientation="vertical"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_alignParentLeft="true"
            android:layout_toLeftOf="@+id/loginButton"
            android:layout_margin="4dp"
            >
            <LinearLayout
                android:orientation="horizontal"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:layout_margin="4dp"
                >
                <TextView
                    android:id="@+id/usernameLabel"
                    android:text="사용자명 : "
                    android:textColor="#ff222222"
                    android:textSize="16dp"
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    />

                <EditText
                    android:id="@+id/usernameInput"
                    android:layout_width="170dp"
                    android:layout_height="wrap_content"
                    android:layout_alignBaseline="@id/usernameLabel" />
            </LinearLayout>
            <LinearLayout
                android:orientation="horizontal"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:layout_margin="4dp"
                >
                <TextView
                    android:id="@+id/passwordLabel"
                    android:text="비밀번호 : "
                    android:textColor="#ff222222"
                    android:textSize="16dp"
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    />

                <EditText
                    android:id="@+id/passwordInput"
                    android:layout_width="170dp"
                    android:layout_height="wrap_content"
                    android:layout_alignBaseline="@id/passwordLabel"
                    android:layout_below="@+id/usernameInput"
                    android:inputType="textPassword" />
            </LinearLayout>
        </LinearLayout>
        <Button
            android:id="@+id/loginButton"
            android:layout_width="100dp"
            android:layout_height="100dp"
            android:layout_alignParentRight="true"
            android:layout_centerVertical="true"
            android:layout_marginRight="4dp"
            android:text="로그인"
            />
    </RelativeLayout>

</RelativeLayout>

### LoginActivity.java

    package com.example.finalexam_19173054;

    import android.content.Intent;
    import android.os.Bundle;
    import android.view.View;
    import android.widget.Button;
    import android.widget.EditText;
    import android.widget.Toast;

    import androidx.appcompat.app.AppCompatActivity;


    public class LoginActivity extends AppCompatActivity {
        public static final int REQUEST_CODE_MENU = 101;

        EditText usernameInput;
        EditText passwordInput;

        @Override
        protected void onCreate(Bundle savedInstanceState) {
            super.onCreate(savedInstanceState);
            setContentView(R.layout.activity_login);

            Button loginButton = findViewById(R.id.loginButton);
            loginButton.setOnClickListener(new View.OnClickListener() {
                public void onClick(View v) {
                    String username = usernameInput.getText().toString();
                    String password = passwordInput.getText().toString();

                    Intent intent = new Intent(getApplicationContext(), MenuActivity.class);
                    intent.putExtra("username", username);
                    intent.putExtra("password", password);

                    startActivityForResult(intent, REQUEST_CODE_MENU);
                }
            });

            usernameInput = findViewById(R.id.usernameInput);
            passwordInput = findViewById(R.id.passwordInput);

        }

        protected void onActivityResult(int requestCode, int resultCode, Intent intent) {
            super.onActivityResult(requestCode, resultCode, intent);

            if (requestCode == REQUEST_CODE_MENU) {
                if (intent != null) {
                    String menu = intent.getStringExtra("menu");
                    String message = intent.getStringExtra("message");

                    Toast toast = Toast.makeText(getBaseContext(), "result code : " + resultCode + ", menu : " + menu + ", message : " + message, Toast.LENGTH_LONG);
                    toast.show();
                }
            }

        }

    }

## 메뉴 화면

### activity_menu.xml

<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent" >

    <LinearLayout
        android:orientation="vertical"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_margin="20dp"
        android:padding="20dp"
        android:layout_centerInParent="true"
        android:background="#aaffffff"
        >
        <TextView
            android:id="@+id/titleText"
            android:layout_width="180dp"
            android:layout_height="wrap_content"
            android:gravity="center_horizontal"
            android:text="메뉴"
            android:textSize="18dp"
            android:textStyle="bold"
            android:textColor="#ff333333"
            />
        <Button
            android:id="@+id/menu01Button"
            android:layout_width="180dp"
            android:layout_height="wrap_content"
            android:layout_marginTop="30dp"
            android:text="일별 박스오피스"
            android:textSize="18dp"
            android:textStyle="bold"
            />

        <Button
            android:id="@+id/backButton"
            android:layout_width="180dp"
            android:layout_height="wrap_content"
            android:layout_marginTop="30dp"
            android:text="로그인 화면"
            android:textSize="18dp"
            android:textStyle="bold"
            />
    </LinearLayout>

</RelativeLayout>

### MenuActivity.java

    package com.example.finalexam_19173054;

    import android.app.Activity;
    import android.content.Intent;
    import android.os.Bundle;
    import android.view.View;
    import android.view.View.OnClickListener;
    import android.widget.Button;
    import android.widget.Toast;

    import androidx.appcompat.app.AppCompatActivity;


    public class MenuActivity extends AppCompatActivity {
        public static final int REQUEST_CODE_CLICK = 201;

        @Override
        protected void onCreate(Bundle savedInstanceState) {
            super.onCreate(savedInstanceState);
            setContentView(R.layout.activity_menu);

            // process received intent
            Intent receivedIntent = getIntent();
            String username = receivedIntent.getStringExtra("username");
            String password = receivedIntent.getStringExtra("password");

            Toast.makeText(this, "username : " + username + ", password : " + password, Toast.LENGTH_LONG).show();

            Button backButton = findViewById(R.id.backButton);
            backButton.setOnClickListener(new OnClickListener() {
                public void onClick(View v) {
                    Intent resultIntent = new Intent();
                    resultIntent.putExtra("message", "result message is OK!");

                    setResult(Activity.RESULT_OK, resultIntent);
                    finish();
                }
            });

            Button menu01Button = findViewById(R.id.menu01Button);
            menu01Button.setOnClickListener(new OnClickListener() {
                public void onClick(View v) {
                    Intent intent = new Intent(getApplicationContext(), ClickActivity.class);
                    intent.putExtra("titleMsg", "일별 박스오피스 화면");

                    startActivityForResult(intent, REQUEST_CODE_CLICK);
                }
            });
        }

        protected void onActivityResult(int requestCode, int resultCode, Intent intent) {
            super.onActivityResult(requestCode, resultCode, intent);

            if (intent != null) {
                if (requestCode == REQUEST_CODE_CLICK) {
                    String message = intent.getStringExtra("message");

                    if (message != null) {
                        Toast toast = Toast.makeText(getBaseContext(), "일별 박스오피스 응답, result code : " + resultCode + ", message : " + message, Toast.LENGTH_LONG);
                        toast.show();
                    }
                }
            }
        }
    }

## 일별 박스오피스 화면

### activity_click.xml

<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical" >

    <EditText
        android:id="@+id/editText"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:ems="10"
        android:inputType="text"
        android:text="http://www.kobis.or.kr/kobisopenapi/webservice/rest/boxoffice/searchDailyBoxOfficeList.json?key=54e7011955ae20f9c72174d2064b3a56&#38;targetDt=20120101" />

    <Button
        android:id="@+id/button"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="요청하기" />

    <androidx.recyclerview.widget.RecyclerView
        android:id="@+id/recyclerView"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:layout_marginBottom="10dp"/>

</LinearLayout>

### activity_movie.xml

<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:orientation="vertical">

    <androidx.cardview.widget.CardView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginLeft="8dp"
        android:layout_marginRight="8dp"
        android:layout_marginTop="4dp"
        android:layout_marginBottom="4dp"
        app:cardBackgroundColor="#FFFFFFFF"
        app:cardCornerRadius="10dp"
        app:cardElevation="5dp" >

        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="horizontal">

            <ImageView
                android:id="@+id/imageView"
                android:layout_width="80dp"
                android:layout_height="80dp"
                android:padding="5dp"
                app:srcCompat="@drawable/movie" />

            <LinearLayout
                android:layout_width="match_parent"
                android:layout_height="match_parent"
                android:layout_margin="5dp"
                android:layout_weight="1"
                android:orientation="vertical">

                <TextView
                    android:id="@+id/textView"
                    android:layout_width="match_parent"
                    android:layout_height="wrap_content"
                    android:text="제목"
                    android:textSize="22sp"
                    android:maxLines="1"/>

                <TextView
                    android:id="@+id/textView2"
                    android:layout_width="match_parent"
                    android:layout_height="wrap_content"
                    android:layout_marginTop="10dp"
                    android:paddingRight="10dp"
                    android:gravity="right"
                    android:text="관객수"
                    android:textColor="#FF0000FF"
                    android:textSize="16sp" />
            </LinearLayout>

        </LinearLayout>

    </androidx.cardview.widget.CardView>

</LinearLayout>

### ClickActivity.java

    package com.example.finalexam_19173054;

    import androidx.appcompat.app.AppCompatActivity;

    import android.os.Bundle;
    import android.util.Log;
    import android.view.View;
    import android.widget.Button;
    import android.widget.EditText;
    import android.widget.TextView;

    import androidx.recyclerview.widget.LinearLayoutManager;
    import androidx.recyclerview.widget.RecyclerView;

    import com.android.volley.Request;
    import com.android.volley.RequestQueue;
    import com.android.volley.Response;
    import com.android.volley.VolleyError;
    import com.android.volley.toolbox.StringRequest;
    import com.android.volley.toolbox.Volley;
    import com.google.gson.Gson;

    import java.util.HashMap;
    import java.util.Map;

    public class ClickActivity extends AppCompatActivity {
        EditText editText;
        TextView textView;

        Button button;

        static RequestQueue requestQueue;

        RecyclerView recyclerView;
        MovieAdapter adapter;

        @Override
        protected void onCreate(Bundle savedInstanceState) {
            super.onCreate(savedInstanceState);
            setContentView(R.layout.activity_click);

            editText = findViewById(R.id.editText);
            textView = findViewById(R.id.textView);

            button = findViewById(R.id.button);
            button.setOnClickListener(new View.OnClickListener() {
                @Override
                public void onClick(View view) {
                    makeRequest();
                }
            });

            if (requestQueue == null) {
                requestQueue = Volley.newRequestQueue(getApplicationContext());
            }

            recyclerView = findViewById(R.id.recyclerView);

            LinearLayoutManager layoutManager = new LinearLayoutManager(this, LinearLayoutManager.VERTICAL, false);
            recyclerView.setLayoutManager(layoutManager);

            adapter = new MovieAdapter();
            recyclerView.setAdapter(adapter);

        }

        public void makeRequest() {
            String url = editText.getText().toString();

            StringRequest request = new StringRequest(
                    Request.Method.GET,
                    url,
                    new Response.Listener<String>() {
                        @Override
                        public void onResponse(String response) {
                            printIn("응답 -> " + response);
                            processResponse(response);
                        }
                    },
                    new Response.ErrorListener() {
                        @Override
                        public void onErrorResponse(VolleyError error) {
                            printIn("에러 -> " + error.getMessage());
                        }
                    }
            ) {
                @Override
                protected Map<String, String> getParams() throws AbstractMethodError {
                    Map<String, String> params = new HashMap<String, String>();

                    return params;
                }
            };

            request.setShouldCache(false);
            requestQueue.add(request);
            printIn("요청함.");
        }

        public void printIn(String data) {
            Log.d("ClickActivity", data);
        }

        public void processResponse(String response) {
            Gson gson = new Gson();
            MovieList movieList = gson.fromJson(response, MovieList.class);
            printIn("영화 정보의 수 : " + movieList.boxOfficeResult.dailyBoxOfficeList.size());

            for (int i = 0; i < movieList.boxOfficeResult.dailyBoxOfficeList.size(); i++) {
                Movie movie = movieList.boxOfficeResult.dailyBoxOfficeList.get(i);

                adapter.addItem(movie);
            }

            adapter.notifyDataSetChanged();

        }

    }
