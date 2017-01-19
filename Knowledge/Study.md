String a = "231131";
		String b = "12345";
		String c = "231131";
		
		//1.문자열 비교
		// 문자열.compareTo(문자열)
		// 문자열.equals(문자열) 비교하기
		// 문자열 == 문자열
		
		System.out.println(a.compareTo(b));
		System.out.println(a.compareTo(c));
		if(a.equals(c)){
			System.out.println("a와 b가 같습니다.");
		}
		
		System.out.println(a.equals(b));
		System.out.println(a.equals(c)); // 두개 문자열이 같으면 true
		
		//2. 문자열의 인덱스 값
		// 어떤 문자의 위치를 가져옴. 글자 사이사이마다 숫자가 있음. 범위를 가져올 수도 있음.
		// subString도 비슷
				
		System.out.println(a.charAt(2));
		
		// 3. 문자열 합지기 '+' 사용
		System.out.println(a + b);
		
		// 4. "무엇" 으로 시작하는 문자열인지.. "무엇"으로 끝나는지
		System.out.println(a.startsWith("23"));
		System.out.println(a.endsWith("23"));
		
		// 5. 찾고자하는 문자열리 몇번째 있는지... String 함수 중요
		// 맨 처음에 나오는 거 하나만 가져옴
		// Last 를 붙이면 뒤에서부터 찾음
		// 찾는 문자열이 없으면 -1 리턴
		System.out.println(a.indexOf("3"));
		
		// 6. 문자열 길이
		System.out.println(a.length());
		
		// 7. 문자열 변경
		// 한개만 바뀜... replaceAll ("문자열의 패턴 : 정규식","바꿀 문자")
		//숫자로 시작하는 어떤 문자는 내가 원하는 문자로 바꿔줘
		System.out.println(a.replace("1","X"));
		
		//uppercase - 대문자 소문자 바꿔줌
		//8. 문자열 자르기 (숫자)까지 자름. (a,b) a와 b 사이의 문자를 가져옴
		System.out.println(a.substring(3));
		System.out.println(a.substring(3,4));
		
		//9.문자열 분리하기 split. 배열에 저장됨 (괄호)의 문자를 기준으로 다 짤라서 저장.
		String value = "a/b/cdg/a2223/afefs";
		String values[] = value.split("/");
		for(String item : values) {
			System.out.println(item);
		}		
				
		// 10. 숫자 -> 문자변환 = 숫자""
		String ccc = 888+"";
		
		// 11. 문자 -> 숫자변환
		int ddd = Integer.parseInt(ccc);
		long eee = Long.parseLong(ccc);
		
		//12. int -> char 변환 = char 범위보다 큰 값이 입력되면 절삭됨
		char fff = (char)ddd;
		
		// 13. 하나의 숫자를 char로 변형 = 이유: 문자열보다 효율적
		        int argNum   =  8; // 입력하는 숫자
		        int argDigix = 10; // 진법
		        char cha = Character.forDigit(argNum, argDigix);
		// 14. 문자열을 한글자씩 char로 분해해서 배열에 삽입
		        String target = "8888";
		        char arrs[] = target.toCharArray();
		        
		//15. 배열 정렬
		       Arrays.sort(arrs);
		        //arrs = 정렬 이미 되서 이후로 arrs 쓰면 다 정렬되어 있음
		        

	}