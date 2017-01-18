
### 자바로 삼각형, 격자 무늬 마름모꼴 출력하기


##삼각형 

#함수 : showTri(7,"X");

숫자값과 문자를 넣으면 다음과 같이 숫자 층을 가진 삼각형이 출력됨.



       X       
      XXX      
     XXXXX     
    XXXXXXX    
   XXXXXXXXX   
  XXXXXXXXXXX  
 XXXXXXXXXXXXX 



# 작성방식

1. 먼저 for문으로 숫자값의 행과 숫자값*2의 열을 만듭니다

2. 정 가운데만 문자를 출력하는 if문을 만듭니다.

3. 매 행마다 2.를 기준으로 문자를 하나씩 더 출력하는 if문 작성 


# 코드

public void showTri(int count, String unit){
		int  i, j;
		for(i=1;i<=count;i++){

			//공백을 출력하는 반복문
		 	for(j=1;j<=count*2+1;j++){
		 		if(j<=(count*2+2)/2+(i-1)&&j>=(count*2+2)/2-(i-1)){
					System.out.print(unit);	
				} else {
					System.out.print(" ");
				}
		    }
		 	System.out.println("");
		}
	}

   

	

##격자 무늬 마름모꼴

#.함수 : showRhombusS(5,"X")

위에서 작성한 삼각형을 토대로 위쪽 부분을 격자 모양인 마름모꼴을 출력

    X     
   X X    
  X X X   
 X X X X  
X X X X X 
 XXXXXXX  
  XXXXX   
   XXX    
    X     


# 작성방식

1. 반복되는 값인 숫자값*2을 변수 k에 넣고 행 for문을 k로 바꿔줍니다.  

2. 숫자값보다 큰 행(아래 반 쪽)을 출력하는 if문 작성

3. 위 반쪽에서 홀수 행은 홀수 열만 짝수 행에서는 짝수 행만 출력하는 if문 작성 


# 코드


	public void showRhombusS(int count, String unit){
		int  i, j;
		int k=count*2;
		
		for(i=1;i<=k-1;i++){
			if(i<=count){
				
				for(j=1;j<=k+1;j++){
					
					if(j<=(k+2)/2+(i-1)&&j>=(k+2)/2-(i-1)){
						if((!(j%2==1||i%2==1))||(j%2==1&&i%2==1)){
							System.out.print(" ");
						} else {							
							System.out.print(unit);
						}					
						
					} else {
	 					System.out.print(" ");
					}
				}
			} else {
		
				for(j=1 ; j<=k+1 ; j++){
			 		if(j<=(k+2)/2+(k-i-1)&&j>=(k+2)/2-(k-i-1)){
						System.out.print(unit);	
					} else {
						System.out.print(" ");
					}
				}
			}

		 	System.out.println("");
		}
	}
	
     