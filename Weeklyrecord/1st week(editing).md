## 0116 Java 기본 지식

#### 1. Java의 특징

-객체지향
-캡슐화
-상속
-다형성
-가비지컬렉션
-플랫폼독립

[자세히 보기 > ](https://github.com/somybak/AndroidS/blob/master/Knowledge/What%20is%20Java.md)    

#### 2. Java 파일의 컴파일 순서

Java로 만든 프로그램은 두번의 컴파일로 실행된다.

**1) Java ㅊ(사람이 쓰는 언어) -> class**

- 여기서 Java는 Java Virtual Machine을 쓰기 때문에 어떤 플랫폼에서든 작동이 가능하다. 

**2) class -> 기계어(0과1)**

- 모든 프로그램은 class로 시작하고 실제 메모리에 올라가는 진입점(Entry pount)은 main 메서드로 시작한다. 그리고 이 main 메서드 안에 다른 메서드를 불러서 사용한다. 단, 다른 클래스에서 정해져 있는 함수는 그 함수가 속한 클래스도 같이 써줘야한다. 예를 들면 print는 system 의 out 클래스에 속해있다. 또한 이런 메서드들은 

-main 함수는 형식을 정해줘야 : main(String args[])