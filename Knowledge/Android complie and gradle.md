# **Android Architecture & Gradle**

### 1. 안드로이드 구조 - 컴파일

##### 1)  Android Runtime(Compile) - 달빅 vs ART

자바의 VM을 통한 실행방법에는 두 가지가 있다.

 [자세히보기 >](https://github.com/somybak/AndroidS/blob/master/Weeklyrecord/1st%20week(editing).md) 의 2-5)Java 파일의 런타임 컴파일 참고 

- Dalvic(JIT) : 실행될 때 한 번만 컴파일을 하기 때문에 성능저하의 우려

- ART(AOT+JIT) : 최초 한 번만 하지만 실행될 때 컴파일 하기도. 효율적이라 현재는 ART 방식을 주로 이용.

##### 2) Architecture

-  Android Runtime Architecture

  안드로이드 오덱스에서 실행시키는 구조에서 아예 리눅스에서 바로 실행시키는 방식으로 바뀜.

  ![Android Runtime Architecture](https://github.com/somybak/AndroidS/tree/master/Weeklyrecord/Dayrecord/upload(blog)/Architecture.png)



- Android Architecture 

  맨 아래 Kernel에 실행에서 중요한 대부분의 것들이 있다....(고 합니다.)

![Android Architecture](https://github.com/somybak/AndroidS/tree/master/Weeklyrecord/Dayrecord/upload(blog)/ArdArchitecture.png)



### **2. Builder gradle - 특징과 장점**

##### 1) Compile - 리눅스와 안드로이드의 차이

- Builder 라는 건 원래 리눅스(C언어)에서 컴파일할 때 소스코드를 기계어로 바꾸고 바꾼 기계어(소스코드)를 다시 라이브러리에 연결(Link)하는 것을 의미한다. 
- 안드로이드의 경우는 컴파일 과정에서 라이브러리와 소스코드가 이미 연결된 Dex파일을 만들기 때문에 기존 Build의 의미와는 약간 다르다.




##### 2) Android Build

- 안드로이드에서는 *소스코드+라이브러리 링크가 컴파일과 동시에 이루어진 덱스파일* 을 만들고 이걸 *스토어에서 다운받아 사용자가 설치할 수 있게끔 설치 파일*까지 만들어서 스토어에 올려놓는 것을 Build라고 한다.

  ​

##### 3) Build Tool과 Gradle의 장점

- Build Tool : Make, Ant, Maven (국내에서 많이 씀, 라이브러리 관리 툴), Ant, Make, Gradle (공식 안드로이드 빌드툴)

- Gradle의 장점

  - 그루비 스타일 지원DSL : 컴파일 없이 문서화도 쉽게 할 수 있있고 고수준(일반언어에 가까운) 언어 DSL로 빌드 가능

  - Wrapper만 실행시키면 실행 모듈없어도 실행가능
  - 빌드 스크립트 자체를 컴포넌트로 해서 재사용 
  - 하나의 파일 안에 프로젝트로 연결연결 및 서브와의 의존관계를 쓸 수 있음
  - 업데이트할 때 하위버전 유지