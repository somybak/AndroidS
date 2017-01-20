

#Collection과 향상된 for문

## 1.Collection 

ArrayList 등을 사용하여 하나의 객체 안에 변수 여러 개의 값을 통채로 속성으로 저장하는 것. 컬렉션 클래스는 Set인터페이스를 구현했거나 List인터페이스를 구현했거나 Map인터페이스를 구현한 것으로 나눌 수 있다.

* 목표 : ArrayList로 nameList에 값을 쌓아서 특정값만 출력하거나 전체를 출력한다.



### 출력값

ahChim //특정값

saesompark //전체 출력
ahChim
saetByul
gaeMee
daSom


### 코드



		String myName = "saesompark";
		String ahChim = "ahChim";
		String saetByul = "saetByul";
		String gaeMee = "gaeMee";
		String daSom = "daSom";
		
		ArrayList<String> nameList = new ArrayList<String>();

- ArrayList : 힙 메모리 영역을 확보하여 주소 번지를 네임리스트에 옮겨줌.
- generic: 내부에 추가되는 모든 값의 타입을 지정해줌. <꺽쇠> 안에 원하는 타입을 씀. -<클래스명>이 들어갈 수도 있음

	
		nameList.add(myName);
		nameList.add(ahChim);
		nameList.add(saetByul);
		nameList.add(gaeMee);
		nameList.add(daSom);


- nameList.add() : 입력하면 nameList 안에 참조할 변수를 순서대로 쌓아줌. 이렇게 쌓인 변수를 다른 변수에서 꺼내서 사용할 때는 모든 타입이 Object형으로 바뀌기 때문에 타입을 지정해줘야한다. 이걸 한꺼번에 해주는 게 <꺽쇠>   
		
System.out.println("2번째사람="+nameList.get(0));
	
- nameList.get() : nameList에 add를 한 순서대로 (괄호)번째 데이터를 가져온다. 0부터 시작  

int nameListsize = nameList.size(); 

- nameList.size() : nameList의 사이즈를 계산한다. 계산한 값을 선언한 nameListsize 변수에 넣음.

- nameList.remove() : (괄호) 번째에 있는 값을 삭제함. 코딩 표준은 반복문에서 동적 배열의 사이즈를 직접 참조해서 사용하지 말라는 권고 사항이 있음(int 값으로 빼와서 사용) nameList.remove(2); 이런 식으로 삭제시킬 경우 쌓인 값의 전체 순서가 바뀌므로..


 for(int i=0 ; i<nameListsize ; i++){

 System.out.println(nameList.get(i));

}

- for문을 사용하여 nameList의 모든 값 출력


## 2. 향상된 for문

반복횟수를 따로 i나 j처럼 인수를 for문 안에 선언하지 않고 어떤 변수의 값이나 객체의 크기를 바로 적용

* 목표 : 향상된 for문을 사용하여 nameList의 모든 값 출력

### 출력값

saesompark //전체 출력
ahChim
saetByul
gaeMee
daSom		

### 코드

		
		 for(Object name : nameList) {  /
  
			String temp = item.toString();
			System.out.println(item);
			System.out.println(nameList.indexOf(item));

		  }

- nameList에 add하면서 Object형으로 바뀜. 
		
- ':'콜론 - 참조하라는 의미. 알아서 하나하나씩 네임을 꺼낼 수가 있음.
	 for(String name : nameList)


Tip 객체의 개념?

객체는 원래 코드와 상관없는 것. 설계 단계에 개념화된 앞으로 개발할 대상을 의미 
이걸 코드로 만든 게 클래스 
-> 객체가 실행되고 나서 컴퓨터 내 주기억장치에 올라간 게 instance 개체
