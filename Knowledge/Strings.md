
##문자열 사용하기
	
###1.문자열 비교

String 타입으로 들어간 건 if안에서 ==을 사용하여 비교할 수 없다. 이 경우 '비교할 변수.compareTo(비교할 다른 문자열)' 이나 '문자열.equals(문자열)'을 사용한다. 같으면 true, 다르면 false를 반환한다.
 
 문자열.compareTo(문자열)
 문자열.equals(문자열) 비교하기
 문자열 == 문자열
		
		String a = "231131";
		String b = "12345";
		String c = "231131";
		
		System.out.println(a.compareTo(b)); 
		System.out.println(a.compareTo(c));
		if(a.equals(c)){
			System.out.println("a와 c가 같습니다.");
		}
		
		System.out.println(a.equals(b));
		System.out.println(a.equals(c)); // 두개 문자열이 같으면 true

- 출력값
a와 c가 같습니다. // a와 c가 같으므로 if가 작동하여 print가 작동한다
false // a와 b의 값은 같지않으므로 false
true // a와 c의 값은 같으므로 true


###2. 문자열의 인덱스 값

String 타입의 데이터에서 (괄호)번째 값을 표시한다. 

	String a = "231131";
	System.out.println(a.charAt(2));
		
- 출력값
0 //a에서 2는 가장 첫번째(0)에째있다. 

###3. 문자열 합치기 '+' 사용

	String a = "231131";
	String b = "12345";
	System.out.println(a + b);

- 출력값
23113112345 // a와 b의 문자열을 붙여서 출력한다

###4. 맨 처음 시작하는 문자열(혹은 맨 끝의 문자열)이 내가 원하는 문자가 맞는지 true, false로 반환

	String a = "231131";
	System.out.println(a.startsWith("23"));
	System.out.println(a.endsWith("23"));

- 출력값
true // a의 첫글자는 23으로 시작함
false // a의 마지막 글자는 23으로 시작하지 않는다
 
 
###5. 찾고자하는 문자열이 몇 번째 있는지 알려줌. 함수 String 사용. 가장 먼저 나오는 (괄호)와 똑같은 문자의 위치를 가져와서 숫자로 표시한다. 순서는 0부터 시작. Last 를 붙이면 뒤에서부터 찾음. 찾는 문자열이 없으면 -1 리턴

	String a = "231131";
	System.out.println(a.indexOf("3"));

- 출력값
1 // 3은 a의 값 231131에서 앞에서 두번째(1)번째에 있다

###6. 문자열 길이를 계산

	String a = "231131";
	System.out.println(a.length());

- 출력값
6 // a의 값 231131은 6글자이다
		
###7. 문자열 변경 원하는 문자 하나를 전부 다른 글자로 바꿔준다... replaceAll ("문자열의 패턴 : 정규식","바꿀 문자")

	String a = "231131";
	System.out.println(a.replace("1","X"));
		
- 출력값
23XX3X
// a값 안의 모든 1은 X로 바뀐다
// uppercase - 대문자 소문자 바꿔줌


### 8. 문자열 자르기 
(숫자)까지 자른 나머지 값을 보여준다. (a,b) 인덱스 값 a와 b 사이의 문자를 가져옴. 
이 때 표시된 글자는 0부터 시작되는데 글자 사이사이마다 숫자가 있다고 생각하면 계산이 편함.
범위를 가져올 수도 있음. subString도 비슷한 기능을 한다.

	String a = "231131";
	System.out.println(a.substring(3));
	System.out.println(a.substring(3,4));

- 출력값
131 // a값의 앞에서 3(실재로는 4)번째까지 자르고 남은 문자는 131
1 // a값의 앞에서 3(실재로는 4)번째까지 자르고 4(실재로는 5)번째까지 사이에 있는 문자는 1이다

###9.문자열 분리하기 split.
배열에 저장됨. (괄호)의 문자를 기준으로 값 안에 있는 문자들을 다 각각 잘라서 저장.

	String value = "a/b/cdg/a2223/afefs";
	String values[] = value.split("/");
	for(String item : values) {
	System.out.println(item);
		}

- 출력값
a
b
cdg
a2223
afefs

// a/b/cdg/a2223/afefs를 / 기준으로 잘라서 각각 values[]에 저장된다
// 여기서 사용된 for문은 향상된 for문으로 values[]의 크기만큼 item에 values[]의 각각의 값이 들어가고 item이 매 줄마다 출력된다.
				
###10. 숫자 -> 문자변환 = 숫자+""

	String ccc = 888+"";
		
 - 결과 : ccc에 888이 String으로 들어간다 

###11. 문자 -> 숫자변환 

	int ddd = Integer.parseInt(ccc);
	long eee = Long.parseLong(ccc);

 - 결과 : ccc값인 888이 Integer타입으로 ddd, Long 타입으로 eee에 들어간다 

###12. int -> char 변환 
char 범위보다 큰 값이 입력되면 절삭됨

	char fff = (char)ddd;

 - 결과 : int형식인 ddd의 값 888이 char타입으로 선언된 변수 fff에 char타입으로 들어간다 

###13. 하나의 숫자를 char로 변형 
이유: 문자열String을 사용하는 것보다 효율적일 때가 있다

	int argNum   =  8; // 입력하는 숫자
	int argDigix = 10; // 진법
	char cha = Character.forDigit(argNum, argDigix);

- 결과 : 8이 10진법으로 char로 선언된 cha에 들어감

###14. 문자열 분해
문자열을 한글자씩 char로 분해해서 배열에 삽입

	String target = "8888";
	char arrs[] = target.toCharArray();

 - 결과 : target의 문자가 하나씩 쪼개져서 그 개수만큼 arrs[]이 생성되고 값이 들어감 

###15. 배열 정렬

	Arrays.sort(arrs);

- 결과 : arrs[] 안의 모든 문자가 내림차순으로 모두 정렬되서 내부 배열 순서가 변경된다
		        
