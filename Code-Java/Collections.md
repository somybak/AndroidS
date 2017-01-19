String myName = "saesompark";
		String ahChim = "ahChim";
		String saetByul = "saetByul";
		String gaeMee = "gaeMee";
		String daSom = "daSom";
				
		//객체는 원래 코드와 상관없는 것. 설계 단계에 개념화된 앞으로 개발할 대상을 의미 
		//-> 이걸 코드로 만든 게 클래스 -> 실행시키고 나서 컴퓨터 내 주기억장치에 올라간 게 instance 개체
		
		int num = 57;
		
		ArrayList<String> nameList = new ArrayList<String>();
		//generic: 내부에 추가되는 모든 값의 타입을 지정해줌. <꺽쇠> 안에 원하는 타입을 씀. 
		//ArrayList : 힙 메모리 영역을 확보하여 주소 번지를 네임리스트에 옮겨줌.
		
		//입력하면 하나하나 쌓아줌
		nameList.add(myName);
		nameList.add(ahChim);
		nameList.add(saetByul);
		nameList.add(gaeMee);
		nameList.add(daSom);
		
	//	System.out.println("2번째사람="+nameList.get(0));
	// .get() : add를 한 순서대로 (괄호)번째 데이터를 가져온다. 0부터 시작  
	
//		//동시에 찍어보기
//		int i=0;
//		int nameListsize = nameList.size(); 
//		for(i=0 ; i<nameListsize ; i++){
//			System.out.println(nameList.get(i));
//			//
//			//코딩 표준 : 반복문에서 동적 배열의 사이즈는 사용하지 말라는 권고 사할이 있음. intㄴ로 사용
//			//nameList.remove(2); 삭제시킬 경우 순서가 바뀌므로..
//			
			
		//향상된 for문
		// nameList.add(new Integer(num));
		
		
		// for(Object name : nameList) {
			//String temp = item.toString();
			// System.out.println(item);
			// System.out.println(nameList.indexOf(item));
		// }
		// ':'콜론 - 참조하라는 의미. 알아서 하나하나씩 네임을 꺼낼 수가 있음.
		// for(String name : nameList) <= nameList에 add하면서 Object형으로 바꿔짐.  