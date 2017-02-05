

1. JAVA의 주요 특징과 특정 숫자까지 모두 더하기 - BigDecimal

2. 모양 출력하기. if, for문 사용

3. Array와 String, 달팽이 수열

4. 게시판 만들기 

5. 파일 io, nio 와 데이터베이스


참고링크

https://github.com/Teddy-Hong/Java/blob/master/Theory/Weekly1.md

https://github.com/Ekutz/Fast_Campus_JS/blob/ff9c9c378a4b42eb779433a0b74ee29eda39cec8/170119/README.md

https://github.com/reach0328/androidschool/blob/master/Week02/Day06/java.md



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


**3) 코드 작성 규칙**

class HelloWorld {
예약어를 클래스이름으로 쓸 경우  " " 한 칸 띄우고 중괄호 들어가야
	public static void main(String args[]) {
	새로운 블럭 시작할 때는 들여쓰기를 꼭 해야! 공백 4개 (or tab-글자 1칸 커스터마이징도 가능)
		System.out.print("Hello World");
		두번 들어간 들여쓰기. 
	}

}

- 완전한 객체지향 언어는 항상 함수 안에서 로직, 변수 선언이 되어야한다.

- 클래스 안에서 변수 선언은 가능. 연산은 못함.

- 로직은 함수 안에서만 가능. 로직은 줄이 바뀌게 되면 세미콜론으로 그 줄을 종료

**4) 파일을 구별하는 방법 - Magic number**

파일을 0과 1로만 구성된 바이너리 파일로 변환했을 때 맨 앞 4bit의 값인 
504b, 0304 등으로 zip 등의 파일형식을 알 수 있다.



**5) Java 파일의 런타임 컴파일**

- VM을 통한 컴파일 방법은 두 가지가 있다.

  1) JIT(Just In Time) : 실행시 최초 한번 클래스 파일을 기계어로 컴파일. 
  속도 저하. 파일이 호출될 때 실행 ! 실행할 때만 있고 닫으면 번역한 내용을 저장안함

  2) AOT (Ahead Of Time) : 설치 시 최초한번 기계어로 컴파일. 안드로이드처럼 설치가 명확한 구조만 가능 용량을 많이 차지함. 번역된 걸 계속 가지고 있음.

=> VM 컴파일이 필요한 파일을 다운로드 받으면 OS가 알아서 둘 중에 하나를 씀

- pre compile : javac 클래스 만듬

- 자바랑 안드로이드가 다른 이유? 자바의 실행환경은 ART로 작동 

- 클래스 로더의 구조 
  클래스 로더에 온 코드는 Method Area, Heap, Java steak 에 위치한다. 
  Method Area - 항상 있어야 되는 내용 
  Heap - 지금 실행되는 변수 등등이 저장되는 곳 => 가비지 컬렉터가 확인하고 지우는 곳.
  Java steak - 함수 내에 있는 변수들이 들어가는 공간.


++ 수업에 나온 Tip

- new: 공간을 변수보다는 좀 더 크게 주는 것을 의미.. 

- 생성자 : 클래스 명을 다시 한 번 써줌 => 다른 클래스의 함수를 여기서 쓰겠다는 의미.

- 자바는 Pacage 언어..URL 패키지명을 지정함. 객체명을 구분해주기 위해서.
   패키지명이 다른 클래스가 서로 이름이 같으면.. 구분하기가 어려워짐. 
  이름 예시 ) 패키지명. 클래스명() 변수 = new.패키지명. 클래스명();

- 변수와 상수 구별하기. 상수는 한번 정하면 못바꿈~


**6) 기본 자료형 - 퍼포먼스. 길이가 지정되어있음**

- 문자형 : 범위가 지정되어 있음. 2 byte ' 외따옴표 사용. 유니코드

- 문자형2 string : 가장 많이 씀. 기본형은 아님. => 길이 제한이 없음, " 쌍따옴표 사용.

- 기본 자료형 간의 연산

  정수형 : 
  byte + byte = int
  byte + short = int
  char + char = int + int 

  실수형
  일반적인 소수는 모두 더블로 인식
  float
  double


**7) 지수가수 표기법 - 부동 소수점 표기**

	a  = 1.515
	b = 0.0000055

소수점 연산오류 원인
컴퓨터는 기본적으로 0.1을 표현할 수 없다.
0과 1의 정수만 표현가능한데, 소수점 표현을 위해 지수부와 가수부를 구분해서 표시
즉, 위 a, b는 아래와 같이 표시된다. 

	a = 0.1515*10E1
	b = 0.55 * 10E-5

>지수가수 표기법으로 변경 (가수에 할당된 자리수가 7자리일 경우)
>a+b = 0.15150055*10E1 < 1.5150055 (실제 숫자) 
>여기서 이미 0.0000005의 오차가 발생한다.

> 가수부가 3자리로 한정되면 아래와 같이 뒷자리가 절삭된다.
> 자리가 모자라서 없애버리면서 오차 발생!
> a+b = 0.152*10


**8) 부동 소수점 연산의 한계**

- 정확한 수치연산을 위해서 소수점이하 값이 있는 값들(부동소수점)끼리 연산을 못하도록 규정하고 있다.Double 함수에다 int 변수를 계산하면 값을 소수점이하로 내줌.

- 큰 숫자끼리 연산할 일이 생기면 값은 String으로 먼저 받음 -> Double로 파싱 후 계산 -> String으로 변환


**9) 지수가수 표기법 및 연산**



13. 자료형 변환(Type Casting)
    float 랑 연산하는 int byte long 은 모두 float 로 나옴

14. 자료형 변환

숫자를 문자로 변경

파싱 : 문자를 숫자로 변경

15. 연산 우선순위

16. 산술연산자 

17. ! not 연산자
    반대로

18. ~(bit not) 연산자
    0과 1을 바꿔줌.
     인티저. 4바이트. 너무 큰 값을 넣으면 마이너스로 값이 바뀜

19. 쉬프트 연산자 1
    변수값을 2진 비트로 변경하고 입력한 값만큼 비트를 이동시킨다. 
    값을 한번 이동할때  

통째로 한칸씩 옮김 
3칸을 옮겨야 부호가 안바뀜

20 관계연산자

21. 논리연산자
    Short-Circuit 
    if &&, ||에서 앞의 값이 틀리거나 맞으면 
    뒤에거는 계산 안해도 됨

22. 비트논리 연산자

XOR : 둘의 값이 달라야 1

배타적 OR

23. 3항 연산자

boolean pass;
pass = (국어 > 국어)? true:false

24. 증감 연산자

++, -- 가독성때문에 빠지는 추세

a += 3 == a = a+3 

스트링, 인트가 혼합된 값은 string a = null + " " 을 쓸수있음

======================================
/** 지불한 금액 payed에서
실제가격 amount 를 빼고
남은 거스름돈의 개수를 출력하세요.


제약조건
payed  = 10,000원
amount = 3,720원

@param payed
@param amount
public
*/

public void calculate ( int payed, int amount) {

int ft = 0;
//잔돈 중 오천원권의 개수
//계산 후

ft = 1;

System.out.println("오천원:"+ ft +"개"

}


=====================================================


무조건 한 번은 실행시키는 것 do while


break와 continue


//첫글자가 대문자면 클래스

package com.seasompark;
// 이 경로를 따라가서 만듬

import java.math.BigDecimal;

public class HelloWorld {

	public static void main(String[] args) {
		//static 이 있는 함수는 바로 사용 가능. 없으면 메모리에 올려야함 new 연산자가 올려주는 함수.
		
		//Operator oper = new Operator();
		
		// 1. 연산자
		HelloWorld hello = new HelloWorld();
		// 이 객체를 Heap 영역에 올려서 메모리 할당 후 사용할 수 있게됨
		// 변수 타입은 클래스와 같이 가야
		//힙과 메서드를 같이 가리키고 있음
	
		long bigNumber = 333333333333L;
		BigDecimal result = hello.sum2(bigNumber); 
		System.out.println(result.toString());


​		
		//hello.calculate(10000,3720);

		// hello.multiple(33);

​		
		/*
		 * 
		 * 
		 * 	for(int i=1 ; i<=3 ; i++){
			for(int j=1 ; j<=2 ; j++){
				if(i<=2) continue;
				System.out.println(i+" "+j);
			}
			
			System.out.println("end j");
					
		}
		
		for(int i=1 ; i<=3 ; i++){
			for(int j=1 ; j<=2 ; j++){
				if(i<=2) break;
				System.out.println(i+" "+j);
			}
			
			System.out.println("end j");
					
		}


		 * 
		hello.loop1(1, 1000);


		hello.loop();	

​			
		hello.condition();			

		hello.sum333(1, 3333333333L);

​		
​		
		int r = hello.sum(1,2); 
		//1,2는 이제 아규먼트라고 부름
		//포인터와 같은 것. hello는 이제 r을 부름.
		
		hello.print(r);	
		//변수명에 담는 과정
		
		//빼기 호출
		
		hello.print(hello.minus(5,10)); 
				
		// 곱하기 호출 후 결과값 출력


		int c = hello.multiply(10,13); 
		hello.print(c);
				
		//나누기 호출 후 결과 값 출력
		
		hello.print(hello.divide(15,5)); 
		
		*/


	}
​	

	/**
	 * 1부터 max 까지의 합을 구하는데 짝수만 더해보세요
	 * 제약조건 : BigDecimal 을 사용합니다
	 * 
	 * @param max
	 * @return
	 *
	 */
	
	public BigDecimal sumEven(BigDecimal max){
		BigDecimal result = new BigDecimal(0);
		BigDecimal sumtotal = new BigDecimal(max.longValue());
		
		result = result.add(sumtotal);
		result = result.add(new BigDecimal(2));
		
		//max, max-1 나눠서 계산
			
		return result;
				
	}
	
	/*
	public BigDecimal sumEven(BigDecimal max){
		BigDecimal result = new BigDecimal(0);
		BigDecimal sumtotal = new BigDecimal(max.longValue());
		
		if (max.longValue>2){
		if (max.intValue()%2==0){
			result = result.add(sumtotal);
			result = result.add(new BigDecimal(2));
			result = result.divide(new BigDecimal(2));
			result = result.multiply(max.intValue()/2);
			result = result.divide(new BigDecimal(2));		
			
		} else{
			result = result.add(sumtotal);
			result = result.add(new BigDecimal(2));
			result = result.multiply((max.intValue()-1)/2);
			result = result.divide(new BigDecimal(2));
			
		}
		}
					
		result = result.divide(new BigDecimal(2));
		return result;
		
	}
	
	*/
	
	public BigDecimal sum2(long max){
		BigDecimal result = new BigDecimal(0);
		BigDecimal bigMax = new BigDecimal(max);
		
		//(n+1)*n/2
		result = result.add(bigMax);
		result = result.add(new BigDecimal(1));
		result = result.multiply(bigMax);
		result = result.divide(new BigDecimal(2));
		
		/*long count = 1;


		for(count=1; count<=max ;count++){
			BigDecimal current = new BigDecimal(count);
			result.add(current);
		*/
		//result.add(new BigDecimal(count));


		return result;

​		
}
​		
​		
​	


	/** 지불한 금액 payed에서
	실제가격 amount 를 빼고
	남은 거스름돈의 개수를 출력하세요.


	제약조건
	payed  = 10,000원
	amount = 3,720원
	
	@param payed
	@param amount
	public
	*/


	public void calculate(int payed, int amount) {

		int ft = 0;
		//잔돈 중 오천원권의 개수
		//계산 후
		//천원, 오백원 , 백원, 오십원, 십원
		
		int ot = 0;
		int fh = 0;
		int oh = 0;
		int ff = 0;
		int tt = 0;
	
		int rt = payed - amount;
		
		ft = rt/5000;
		ot = (rt-ft*5000)/1000;
		fh = (rt-ft*5000-ot*1000)/500;
		oh = (rt-ft*5000-ot*1000-fh*500)/100;
		ff = (rt-ft*5000-ot*1000-fh*500-oh*100)/50;
		tt = (rt-ft*5000-ot*1000-fh*500-oh*100-ff*50)/10;	
									
		/*
		 * int ft = rt/5000;
		 * 
		   rt = rt-ft*5000;		  
		   int ot = rt/1000;
		   
		   rt = rt-ot*1000;		   
		   int fh = rt/500;
		   
		   rt = rt-fh*500;		   
		   int oh = rt/100;
		   
		   rt = rt-oh*100;
		   int ff = rt/50;
		   
		   rt = ff-f*50;
		   int tt = rt/10;
		
		 * 
		 *  
		 */
		
		System.out.println("오천원:"+ ft +"개");
		System.out.println("천원:"+ ot +"개");
		System.out.println("오백원:"+ fh +"개");
		System.out.println("백원:"+ oh +"개");
		System.out.println("오십원:"+ ff +"개");
		System.out.println("십원:"+ tt +"개");
	
	}
	
	/** 값을 콘솔에 출력하는 변수
	 *@param value - 정수형 입력값


	*/

	// 0. JavaDog : Java
	/**
	 * 
	 * Java 문서를 생성하기 위한 주석
	 * @author
	 * @version 1.0
	 */

​	

	public void print(int value) {
		// value 값을 받아서 출력함
		// 앞으로 system의 print가 아니라 HelloWorld의 print를 사용함
		// print("aa") 했을 떄 출력값이 없음. 이 경우 void
		// sum 쓰려면 string을 int로 써야 


		System.out.println(value);

​		
	}

​	
	//public은 접근 제어자. 안쓰면 그냥 default가 들어감
	  public int     sum       (int a, int b) {
		  //리턴값int //함수명sum // 파라미터들.. 지역 변수가 선언된 것
		  //void는 리턴 타입이 없는 리턴 타입
		  
		/** 입력값 a, b를 더해서 리턴
	 * 
	 * @param a
	 * @param b
	 * @return
	 * */


		  int result;
		  result = a+b;
		  
		  return result;
		  
		  /*int value= a+b;
		  return value;
		  or
		  return a+b;
				  */		  
		  
	  }


​	
	  public int minus (int a, int b) {

		  int result=0;
		  result = a - b;		  
		  return result;
		  
	  }
	
	  public int multiply (int a, int b) {
		  
		  int result=0;
		  result = a*b;		  
		  return result;
		  
	  }
	  
	  public int divide (int a, int b) {

 		int result = 0; //객체는 null. 값 넣을 공간을 미리 넣어주는 게 좋음. =0
 		result = a/b;	  
 		return result;
​	  
	  }

		/** 
		 * 2. 조건문
		 * if
		 * 비교결과가 참인지 거짓인지를 판단하여 해당블럭 내에 있는 로직을 실행한다.
		 * switch
		 * 입력된 값과 어떤 특정값을 비교하여 해당 블러 내에 있는 로직을 실행한다
		 */
		  public void condition() {
			  int a = 15;
			  int b = 20;
			  int c = 15;
			  
			  if(a>b) {
				 System.out.println("a는 b보다 큽니다.");		  
			  } else if(a==b){
			 	 System.out.println("a와 b는 같습니다.");			  
			  } else if(a==b){
				 System.out.println("a와 b보다 작습니다.");
			  }
			  
			  switch(a){		 
			 //case는 if문의 ==와 같은 역할
			  case 1 :
				  System.out.println("a는 1입니다.");
				  break;
			  case 15 :
				  System.out.println("a는 15입니다.");
				  break;
			  case 20 :
				  System.out.println("a는 20입니다.");
				  break;			    			    
			  default : 
				  System.out.println("a는 "+a+"1입니다.");
				  break;			    
			  
			  }
			  
			  //3항 연산자			  
			   c = (a==15) ? 100:0;


		  } 

​	
​		  
​		  
​	
	/**
	 *  3. 반복문
	 *  for
	 *  특정 범위 내의 값만큼 반복하면서 블럭 내의 로직을 실행한다.
	 *  
	 *  while
	 *  특정조건이 만족될 때 블럭 내의 로직을 실행한다
	 *      
	 *  
	 */
		  
		  public void loop() {
		//시작값, 종료값, 증감값
		
			int i = 0; //반복문 시작
			int limit =100; //반복문 종료
	
			for(i=0 ; i<limit ; i++) {				
				System.out.println("i1="+i);
			}
			
			i=0;
			while(i<limit) {
				System.out.println("i2="+i);
				i=i+1;
			}			
			
			int a = 0;
			int a_limit = 10;//


			int b = 0; //  내부 for 문의 시작값
			int b_limit = 10;// 내부 for 문의 종료값
			
			for(a=0;a<a_limit;a++){
				for(b=0;b<b_limit;b++){
					System.out.println("a="+a+",b="+b);		
				}
			}
			System.out.println("after a="+ a);
			
		  }


​	
​	
		public void sum333(long w, long q) {

		  long sum333 = 0;

		  for (long i = w ; i <= q ; i++) {				  
			  sum333=sum333+i;
			}
			  
		  System.out.println(sum333);


	  }

		public void loop1(int n, int m) {

			if (n<=1000 && m<=1000) {

				int s = 0;		
				for(int i=n; i<=m ; i++){
					s=(n+m)*(m-n+1);
				
					if(s%2==0){
						s=s/2;
					} else {					
						s=(s-1)/2 +1;
					}


				}

				System.out.println(s);	

			} else{

				System.out.println("1000을 넘는 숫자는 계산할 수 없습니다");	

			}

		}		

​		
		public void multiple (int n){

			for(int i=1 ; i <=n  ; i++){
				for(int j =1 ; j<n+1 ;j++){
						System.out.print(j+" X "+i+" = "+i*j+"\t");						
					}
				
				System.out.println();
				
				}


			}

​			
​		
​		
​		
}


​		
​		
​			
​	
​	


