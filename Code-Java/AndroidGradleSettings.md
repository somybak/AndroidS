

## 3. Gradle 사용하기

##### 1) Layout-(activity_settings.xml 클래스명)

- MVC Model view controller 방식  : 웹 기반 환경으로 적용, 뷰랑 컨트롤러가 같이 들어가있음

- 왼쪽에서 컴포넌트를 눌러서 모바일 화면으로 드래그(맨 왼쪽은 클래스 선택)

- 오른쪽에서 컴포넌트별로 변수값 지정 가능(안되면 직접 입력)

  ![안드로이드 그래들 실행화면](https://github.com/somybak/AndroidS/blob/master/Weeklyrecord/Dayrecord/upload(blog)/ArdScreen.png)

##### 2) Button, Textview, Listner(SettingsActivity.java)

```
import android.support.v7.app.AppCompatActivity;
import android.os.Bundle; 
import android.view.View; //뷰 화면 
import android.widget.Button; //버튼 기능
import android.widget.TextView; //텍스트뷰 기능

public class SettingsActivity extends AppCompatActivity implements View.OnClickListener { 
기위한 View.OnClickListener 를 implements 한다.

    Button btn; 
    TextView tv;
    // 레이아웃에서 Button, TextView으로 변수값 넣은 컴포넌트를 
    // 각각 btn, tv으로 선언

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_settings);

        btn = (Button) findViewById(R.id.button);
        tv = (TextView) findViewById(R.id.textView);
        
        // 버튼과 텍스트 뷰를 설정해줌. 둘다 뷰를 찾아서 버튼을 찾는데
        // 앞에 각각 (Button)와 (TextView)를 써서 
        // 강제로 최상위 뷰 클래스를 받아 오브젝트끼리 연결

        btn.setOnClickListener(this);
        //버튼 위치에 터치를 대기하고 읽어옴
    }


    @Override
    public void onClick(View view) {
        switch (view.getId()) {
            case R.id.button: //case는 콜론!!
                tv.setText(BuildConfig.MyURL);
                //터치해서 눌렀을 때 나오는 기능
                
        }
    }
```

 

##### 3) app 설정 및 배포용/개발자용 버전 각각 생성하기 (app.iml

```
//모듈의 용도 : 라이브러리 application, library
apply plugin: 'com.android.application'

//안드로이드 앱 관련 설정
android {
    //컴파일(class 파일 생성)러 버전.. 버전별로 컴파일러가 많음..
    compileSdkVersion 25

    //빌드(설치를 위한 apk 생성) 툴의 버전
    buildToolsVersion "25.0.1"
    defaultConfig {

        applicationId "com.example.somy.settings_saesompark"
        // 앱의 고유 ID. 앱의 root package명을 사용
        minSdkVersion 15   
        // API 레벨.. 개발자만 보는 버젼. 최하위 안드로이드 버전 - 수정가능
        targetSdkVersion 25 // 
        컴파일과 빌드의 목표가 되는 버젼 . -수정가능
        versionCode 1       // 내부적으로 관리되는 버전(정수)
        versionName "1.0"   // 외부적으로 알려지는 앱 버전
        testInstrumentationRunner "android.support.test.runner.AndroidJUnitRunner" // 테스트 환경
    }

    lintOptions{
        abortOnError false
    }

    signingConfigs {
        release {
            storeFile file("../keystore/keystone.jks")
            storePassword "qwertpoiuy"
            keyAlias "testKey"
            keyPassword "qwertpoiuy"
        }
    }

    buildTypes {
        // 원래 매니페스트에 있던 것을 가져온 것
        // 빌드타입을 설정을 해두면 그래들로 여러 버전이 한번에 생성됨
        release {
            signingConfig signingConfigs.release
            buildConfigField("String", "MyURL","\"배포용 버전\"");
            minifyEnabled false
            proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
        }
        debug{
            //디버그용이랑 배포버전이랑 다르게 생성
            buildConfigField("String", "MyURL","\"개발용 버전\"");
            // 상수형태로 가져갈 수 있음
        }
    }

    productFlavors {
        google {
            versionName "1.0-google"
        }
        onestore {
            versionName "1.0-onestore"
        }
        samsung {
            versionName "1.0-samsung"
        }
    }

}

//라이브러리 - 대신 다운받아서 그래들을 관리해줌~
dependencies {
    //

    compile fileTree(dir: 'libs', include: ['*.jar'])
    //화면테스트용 라이브러리,
    androidTestCompile('com.android.support.test.espresso:espresso-core:2.2.2', {
        exclude group: 'com.android.support', module: 'support-annotations'
    })
    //하위버전 호환성을 위한 라이브러리
    compile 'com.android.support:appcompat-v7:25.1.0'

    //소스코드 테스트용 라이브러리
    testCompile 'junit:junit:4.12'
}
```



##### 4) Keystore - (app.iml)

- exe 같은 것. 실제 실행해서 사용자 기기에 설치하기 위한 파일로 패스워드를 입력해야만 생성될 수 있다.(보안)


- keystore 설정 메뉴

![Keystore 진입 메뉴](https://github.com/somybak/AndroidS/blob/master/Weeklyrecord/Dayrecord/upload(blog)/keyStore.png)

- app.iml 안에 패스워드 기억해서 입력해야함. 하고 실행 돌리면 

      signingConfigs {
      release {
          storeFile file("../keystore/keystone.jks")
          storePassword "qwertpoiuy"
          keyAlias "testKey"
          keyPassword "qwertpoiuy"
      }
      }
    
    - 
    
- 아래 경로로 keystone.jks 파일 생성C:\Users\Somy\AndroidStudioProjects\Settings-Saesompark(프로젝트명)\keystore\



##### 5) 한번에 여러 스토어에 배포용/개발자용 생성(app.iml)

      productFlavors {
        google {
            versionName "1.0-google"
        }
        onestore {
            versionName "1.0-onestore"
        }
        samsung {
            versionName "1.0-samsung"
        }
      }


- Terminal에서 gradlew build 입력

##### 6) .gitignore 설정하기

이 파일에 아래와 같이 입력한 파일들은 git에 올라가지 않는다.

```
*.iml
.gradle
/local.properties
/.idea/workspace.xml
/.idea/libraries
.DS_Store
/build
/captures
.externalNativeBuild
```



## 4. Lint - Builder gradle에서 코드 검사하기 

##### 1) 의미 

- 보푸라기 등을 의미하는데 코드 내에 오류를 미리 찾아서 수정해주는 역할을 한다.

  ​

##### 2) 사용방법(추후 보강)

- 아래와 같은 코드를 app.iml에 입력

```
lintOptions{
    abortOnError false
}
```

