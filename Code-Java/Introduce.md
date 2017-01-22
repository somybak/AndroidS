## 기획의도

주말 내내 게시판 만들기만 혼자 죽어라고 파다가

(하라는 Daily 정리는 다 못 끝내고 Weekly 정리도 못 끝내고ㅜㅜ(이제 다 할거임))

궁금하신 거 없냐는 친절한 조교님을 괴롭;;혀서ㅋㅋㅋ 

클래스, 메서드, 오버로드, 상속의 개념을

어렴풋이나마 드디어 ㅠㅠ 이해하고 

예시로 짜주신 코드를 보고 나만의 무언가를 만들고 싶었던 것이다!

그리하야 게시판에서 배운 걸 응용해서 스스로 프로그램을 짜보았다.



### 설계 

(결코 이 순서대로 하지는 않았지만;;)

1. 부모클래스 Person, 자식클래스 Developer, Designer, Planner 만듬

2. Person 클래스에 이름/직업을 입력받는 interviewYou 메서드 생성
3. 모든 클래스에 introduceMe 메서드 생성
4. 각각 introduceMe 메서드에 출력값 설정  (자식클래스엔 super() 입력)
5. 부모클래스에서 자식클래스의 객체를 각각 생성하고 실행

어쨌든 성공은 했는데 의문이 남는 부분이 몇 개 있음..ㅠ



### 코드

**부모클래스 Person > main() 메서드**

> ​	public static void main(String[] args) {	
>
>        1) Person person1 = new Person(); 
>        2) person1.interviewYou();
>
> ​	}

1) 현재 main() 메서드 안에서 

새로운 Person 클래스의 생성자를 호출하면서 객체를 생성하고

이 객체는 person1이라는 변수로 참조하여 실행할 것임.

2) main이 참조하고 있는 Person 객체 안에 interviewYou() 메소드 호출하여 실행



**부모클래스 Person > interviewYou() 메서드 **

> public void interviewYou(){
>
> 3)Person developer = new Developer(null); 
>    Person designer = new Designer(null); 
>    Person planner = new Planner(null); 
>    Person person = new Person(); 
>
> 4) Scanner scanner1 = new Scanner(System.in);	//Scanner로 입력값을 받음		
>
>     System.out.println("이름을 입력하세요"); 
>     String name = scanner1.nextLine(); // name에 이름을 입력
>     System.out.println("직업을 입력하세요");
>      String job = scanner1.nextLine(); // job에 직업을 입력
>
>
> 5) if (job.equals("개발자")){ developer.introduceMe(name, job);
>
>      } else if (job.equals("디자이너")){designer.introduceMe(name, job);
>
>      } else if (job.equals(기획자")){planner.introduceMe(name, job);
>
>      } else { person.introduceMe(name, job); 
> }



3) 자식 클래스인 Developer, Designer, Planner에 Person을 상속해놓고나서 각각 클래스의 생성자를 호출하는 developer, designer, planner 변수를 만든다. 

+ 이 세 개의 직업이 아닐 경우를 위해 Person을 호출하는 person 변수도 만든다.

4) 입력값을 입력받는 Scanner를 만들고 각각의 값을 받아서 이름은 ‘name’에, 직업은 ‘job’에 담는다.

5) 직업이 개발자인 경우 Developer 클래스의  introduceMe를 실행
직업이 디자이너인 경우 Designer 클래스의  introduceMe를 실행 
직업이 기획자인 경우 Planner 클래스의  introduceMe를 실행
위 세 가지가 아니면 아래 Person 클래스의 introduceMe를 실행 



**부모클래스 Person > introduceMe(String name, String job) 메서드 **

> public void introduceMe(String name, String job){
>
> 6) System.out.println("내 이름은 "+name+"이고 직업은 "+job+"입니다.");
>
> }

6) 직업이 개발자,디자이너,기획자가 모두 아닐 경우 

호출한 곳에서 (argument 1, argument 2) 위치에 각각 String 형식으로

name, job이라는 지역변수에 담아서 입력한 그대로 자기 소개 출력.



**자식클래스 Developer ( 직업을 “개발자”라고 입력했을 경우 실행)**

> 7) public class Developer extends Person {
>
> 8) public Developer(String job){
>
>  super();
>
>    }
>
> 9) @Override
>
> public void introduceMe(String name, String job){
> System.out.println("내 이름은 "+name+"이고 직업은 Fastcampus 출          신"+job+"입니다.");
>
>  }	
>
> }

7) Person 클래스를 상속받음

8) Developer가 호출받을 경우 부모에 있는 job 쓰지말고 현재 Developer 클래스에 있는 걸 쓰라고 super()로 명시

9)  Developer가 호출받아서 introduceMe를 사용할 때는 name, job을 받아서 나의 자기소개를 출력

* 자식클래스 Designer, Planner도 Developer와 식별자만 빼고 코드 동일.



의문점

3) 에서 클래스 호출하는 생성자 변수에 왜  null을 넣어야 하는지?
