# 19173054 전채원 캡스톤디자인 기말고사 과제 제출

## 로그인 화면

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

## 메뉴 화면

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
