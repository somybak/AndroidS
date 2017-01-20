
String & Foreach & Array 사용 Google 예제


## 1. 숫자개수 구하기

### 문제 1~10000까지 8이란 숫자의 개수는?

### 설계

- String으로 받은 숫자(10000)를 int로 바꿔서 변수 n에 저장 

- 반복문의 반복횟수를 n으로 두고 반복하는 각각의 숫자는 모두 String으로 바꿈

- Split으로 바꾼 숫자에서 if로 8의 개수를 세서 count에 넣음

- count 출력

/**	

	public void countEight(String sum) {
		int n = Integer.parseInt(sum); //  string을 int로 바꿔줌
		int count = 0;
		
		for(int i = 1 ; i<=n ; i++ ){
			
			String value = i+"" ; // int를 string으로 바꿔줌
			String values[] = value.split(""); 
			for(String count_8 : values){
				if(count_8.equals("8")){  //문자열 비교는 euqals로!
					count=count+1;
					
				}
			}	
		}
		
		System.out.println(count);
		
	}
	
	
	*/
	
## 2. 문자열 뒤집기 

입력값을 문자열 n으로 받은 후, 
해당 문자열을 거꾸로 뒤집은 후 출력하는 프로그램을 작성


anything -> gnihtyna

입력값 n = "was it a cat i saw?"



### 설계 1


- array[] 생성하여 입력값의 문자 하나하나를 집어넣음

- 변수 n 생성하여 array에 저장된 입력값의 총 글자개수를 세서 저장 
( input을 직접 가져오기보다 변환한 array[] 길이를 가져오는게 좋음. 잘못 참조하면 꼬여서 input이 바뀜!)

- i를 n-1에서 0까지 --로 돌리는 for문 작성 

- for문 안에 현재 array[i] 값을 저장할 terp 변수 생성

- for문 반복만큼 terp 출력 (i값이 역순이므로 입력값의 반대로 나옴)


	/**
	public void reverseString(String input){

		char array[] = input.toCharArray(); // 캐릭터 각각을 배열로 변환 
   
	
		int n = array.length; 



    	for (int i = n-1 ; i>=0 ; i--){

			char terp = array[i];
			System.out.print(terp);
			
		}
