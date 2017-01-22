

#Collection과 향상된 for문

## 1.Collection 

ArrayList 등을 사용하여 하나의 객체 안에 변수 여러 개의 값을 통채로 속성으로 저장하는 것. 컬렉션 클래스는 Set인터페이스를 구현했거나 List인터페이스를 구현했거나 Map인터페이스를 구현한 것으로 나눌 수 있다.

**목표 : ArrayList로 nameList에 값을 쌓아서 특정값만 출력하거나 전체를 출력한다.**


### 코드

####ArrayList 
ArrayList : 힙 메모리 영역을 확보하여 주소 번지를 네임리스트에 옮겨줌.
generic: 내부에 추가되는 모든 값의 타입을 지정해줌. <꺽쇠> 안에 원하는 타입을 씀. -<클래스명>이 들어갈 수도 있음
ArrayList <꺽쇠> 배열이름, 배열이름.add() : 입력하면 배열 안에 안에 참조할 변수를 순서대로 쌓아줌(.add). 이렇게 쌓인 변수를 다른 변수에서 꺼내서 사용할 때는 모든 타입이 Object형으로 바뀌기 때문에 타입을 지정해줘야한다. 이걸 한꺼번에 해주는 게 <꺽쇠> 

    1)  String myName = "saesompark";
	String ahChim = "ahchim";
	String saetByul = "saetByul";
	String gaeMee = "gaeMee";
	String daSom = "daSom";
		
    2)  ArrayList<String> nameList = new ArrayList<String>();

    3)  nameList.add(myName);
	nameList.add(ahChim);
	nameList.add(saetByul);
	nameList.add(gaeMee);
	nameList.add(daSom);
	
    4)  System.out.println("2번째사람="+nameList.get(1));
	
    5)  int nameListsize = nameList.size(); 

    6) 		for(int i=0 ; i<nameListsize ; i++){

    7) 			  System.out.println(nameList.get(i));
	}
	
	
1)각 변수를 생성해서 이름을 넣는다.

2)ArrayList 를 호출해서 내용을 저장하는 배열 nameList를 생성한다. <꺽쇠>안이 String으로 설정되었으므로 이 배열에 들어가는 모든 값은 String으로 저장된다.

3)1)에서 저장한 변수들을 모두 nameList에 하나씩 넣는다. 즉, nameList[0]은 myname의 "saesompark"이라는 값을 갖게 되고 이 값은 String으로 저장된다. 만일 myname의 타입과 <꺽쇠> 안이 다를 경우 parse(파싱)해주는 작업이 필요하다.

4)nameList.get() : nameList에 add를 한 순서대로 (괄호)번째 데이터를 가져온다. 0부터 시작하므로 1번째(실제로는 두번째)인 변수 ahChim에 있는 값,
ahchim
이 출력된다.

5)nameList.size() : nameList의 사이즈, 즉, add된 총 개수를 계산한다. 계산한 값을 nameListsize 변수에 넣는다.

6)for문을 사용하여 nameList의 모든 값 출력.nameList.get(i)의 i의 값이 5)에서 얻은 nameListsize 값만큼 반복되면서 7)을 통해 nameList전체, 즉
saesompark
ahChim
saetByul
gaeMee
daSom
을 출력한다.

++ nameList.remove() : (괄호) 번째에 있는 값을 삭제함. 코딩 표준은 반복문에서 동적 배열의 사이즈를 직접 참조해서 사용하지 말라는 권고 사항이 있음(int 값으로 빼와서 사용) nameList.remove(2); 이런 식으로 삭제시킬 경우 쌓인 값의 전체 순서가 바뀌므로..


## 2. 향상된 for문

반복횟수를 따로 i나 j처럼 인수를 for문 안에 선언하지 않고 어떤 변수의 값이나 객체의 크기를 바로 적용해서 반복한다.

**목표 : 향상된 for문을 사용하여 nameList의 모든 값 출력**

### 코드

	1)  for(Object item : nameList){ 

	2)	String temp = item.toString();
	3)	System.out.println(item);
		System.out.println(nameList.indexOf(item));

	  }


1)String이 아닐 경우를 가정
nameList에 add하면서 값은 Object형으로 바뀌므로 object로 name을 선언해준다.) ':'콜론은 참조하라는 의미로 nameList에서 알아서 하나하나씩 add된 것을 꺼낼 수 있다.		

2)nameList에서 꺼낸 값(object)을 item에 String 타입으로 넣어준다

3)현재 item을 출력하고 그 item의 순서를 출력한다.	
출력값
saesompark
0
ahChim
1
saetByul
2
gaeMee
3
daSom
4


#####Tip 객체의 개념?

객체는 원래 코드와 상관없는 것. 설계 단계에 개념화된 앞으로 개발할 대상을 의미 
이걸 코드로 만든 게 클래스 
-> 객체가 실행되고 나서 컴퓨터 내 주기억장치에 올라간 게 instance 개체
