
무릇 Music Player 앱을 만들었다고 한다면 일반 사용자로서 나에게는 응당 재생목록과 재생화면은 당연하고, 가사보기, 즐겨찾기, 나만의 리스트, 카테고리별 음악찾기 등등… 을 생각하게 되지만 개발자의 세계 - 라기보단 나 같이 왕초보로 기어가는 코드 타이퍼(ㅠㅠ)의 수준의 - 에서는 고저 목록이 뜨고 재생화면으로 넘어가기만 해도 엄청난 성공인 것이다. 오류가 나지 않는 앱이 모바일 화면에 아이콘으로 존재하는 것..만 해도 정말 쉽지 않다. 이번 주는 계속 리사이클뷰, 카드뷰 와 런파임 퍼미션, 어댑터, 데이터로더 클래스 만들기 등을 학습하고 있는데 이걸 토대로 어제 만들(었어야했)었던 뮤직플레이어의 전체 음악파일 목록 화면에다가 오늘은 진짜 재생화면과 기능을 연결하는 걸 공부해서 정리해보려고 한다. 입이 떡 벌어질 정도로 어느 기능 하나 그냥 되는 게 없다는 걸 구구절절 깨닫는 하루였다.



참고자료
[Recycler 개념도 보기](http://prezi.com/aouqpcrh87xk/?utm_campaign=share&utm_medium=copy)

![리사이클뷰](https://github.com/somybak/AndroidS/tree/master/Weeklyrecord/Dayrecord/upload(blog)/rv.png)





#0. <☆중요> 뮤직플레이어 재생목록 화면 실행

Runtime Permmition(**기존의 모바일 안에 있는** 음악목록, 전화번호부 가져오기 등)을 받을 경우,

**반드시 AndroidManifest.xml에**

####<"uses-permission android:name=“android.permission.READ_EXTERNAL_STORAGE”/>"
   ↑ 
   쌍따옴표 빼고 
   
이 코드를 꼭 넣어주어야 한다. 안 그럼 결코 아예 실행서부터 문제가 생겼다는 메시지 뜨고 기껏 만든 화면 뜨지도 않고 앱이 die… 한 시간 동안 이걸로 수업이…ㅠㅠ 누군가에게 같은 실수가 반복되어선 안되도록 널리널리 알려야 한다 !! 



#1. 곡마다 앨범 이미지 보여주기

**1-1. 일단 데이터를 받아올 곳을 확인**

기존의 모바일에 저장된 음악 파일의 정보를 앱으로 가져오기 위해서는 먼저 **모바일 내부의 어디에서 음악파일 정보가 어디에 저장되어있는지**를 확인해야 한다. 나는 이게 당연히 육안으로 컴퓨터에 연결하면 볼 수 있는 각각의 폴더라고 생각했지만 이제 그건 개발자가 아닌 자의 생각일 뿐! 모바일에 기본적으로 깔려있는 안드로이드 OS에서는 내부에 모든 Media 파일이 생기는 즉시 이 안드로이드 자체가 그 파일의 정보를 한 곳에 모아서 저장한다. 그러니까 모든 안드로이드 폰 개발자라면 어떤 폰을 대상으로 하건 다 똑같은 URI주소를 쓰면 되는 것이다!! (이런 게 정말 어메이징하다 진짜.)

그 주소는 바로 이것!!

  ###**MediaStore.Audio.Media.EXTERNAL_CONTENT_URI;**

원래 음악 파일 정보말고도 모든 파일들에겐 각각을 구별할 수 있는 주소가 있는데 그걸 URI라고 부른다. 즉, 음악파일의 정보 - 파일 이름, 아티스트명, 앨범명 심지어 앨범 이미지(있는 경우) 등등 - 는 그냥 저 URI 주소에서 URI 객체(정보를 담아오는 그릇)를 만들어서 통째로 한번에 가져오면 되는 것이다. 이는 다음과 같다.  

###**Uri uri = MediaStore.Audio.Media.EXTERNAL_CONTENT_URI;**

그러나 컴퓨터는 실제로 정보를 가져올 때 0과 1만 읽는다. 즉, 어떤 데이터든 데이터를 받는 쪽은 이 수많은 0과 1의 정보를 사람이 해석할 수 있게 텍스트로 저장된 0과1은 텍스트로, 이미지는 이미지로 받아야 하는데 이것을 데이터 타입이라고 한다. (물론 이 데이터 타입은 단순히 숫자, 문자 뿐만 아니라 이걸 여러 기능과 조합하여 기존에 만든 걸 활용할 수도 있는데 이걸 ‘참조타입'이라고 한다.) 다시 말해서 위의 URI에서 가져온 수많은 음악 정보데이터 중에서도 곡 이름, 아티스트명 등의 텍스트 정보는 String이라는 문자형 데이터 타입으로 읽어와야 실제로 화면을 보는 사람이 무슨 곡이고 어떤 정보인지 알 수 있게 되는 것이다. 그런데 저 URI에서 통째로 가져온 음악 파일 정보 중에 몇몇 곡은 텍스트 정보 뿐만 아니라 앨범 **이미지**가 있는 경우도 있다. 그럼 이 이미지는 어떤 타입으로 읽어야 화면에 나타낼 수 있을까?



##**1-2. 구체적으로 받아오는 과정**

**※목적 : 곡 정보에 앨범 이미지가 포함되어 있으면 음악파일 목록에서도 같이 보여주자!**

목적은 쉽지만 실제로 코딩을 하기 위해서는 이 모든 과정을 하나하나 쪼개야 하는데 그걸 마치 심부름에 비유하자면 다음과 같다.

##1) 심부름의 이름은 "load(Context context)"
이걸 불러오면 아래와 같은 작업을 진행한다.

###① URI 주소를 가서 '데이터를 받아오(는 심부름을 하)겠다고  객체로 선언.
데이터를 가져올 역할을 하는 Control Resolver 객체 생성.

      ContentResolver resolver = context.getContentResolver();

###② 어디로 가야되는지 메모하기
URI 객체 생성하고 URI 입력. 이를 '데이터 컨텐츠 URI 정의'라고 한다.

      Uri uri = MediaStore.Audio.Media.EXTERNAL_CONTENT_URI;

###③ 가서 뭐 가져올지 적기
URI에 있는 곳에 가서 무슨 무슨 데이터 필요한지 적는다! URI에 가보면 데이터는 엑셀 파일처럼 가로세로의 테이블로 되어있고 컬럼 단위로 가져올 수 있다. (컬럼은 테이블의 세로 길게 한 줄로 각각 다른 내용이 담긴 같은 종류의 데이터를 의미한다. 예를 들면 곡이름1, 곡이름2, 곡이름 3..은 '곡이름' 컬럼이다. )
여기서는 곡의 ID(고유정보), 앨범명, 곡 제목, 아티스트명을 가져올거니까 다음과 같이 원하는 한 컬럼당 한 줄씩 아래와 같이 적어주고 텍스트만 받는 proj를 만들어서  순서대로 넣어준다.

    String proj[] = {
                 MediaStore.Audio.Media._ID,
                 MediaStore.Audio.Media.ALBUM_ID,
                 MediaStore.Audio.Media.TITLE,
                 MediaStore.Audio.Media.ARTIST
         };

이 코드가 실행되고 나면 proj[0]부터 proj[3]까지 각각의 컬럼이 담기게 된다.

###④ 가서 이거이거 가지러 왔다고 요청하고 가방에 담기
①②③을 모두 묶어서 모바일에게 정보를 달라고 요청하는데 이걸 query라고 한다. 그리고  데이터를 받으면 그걸 담을 cursor라는 객체를 선언해서 이 안에 통째로 다 담는다. 단, 이 cursor에는 요청한 데이터 그 자체가 담긴 것은 아니고 요청한 데이터의 위치를 가리키고 있는 것에 가깝다. 하지만 어쨌든 이 cursor를 호출하면 데이터 그 자체를 진짜, 정말로, 드디어, 받아온다.  

    Cursor cursor = resolver.query(uri, proj, null, null, null);

###⑤ 가방에 담아온 데이터를 하나씩 꺼내보자!
일단 ④에서 받아온 cursor가 비어있진 않은지 if로 확인하고 뭔가 있는 게 확인되면 한 줄 한 줄씩 꺼내주는 moveToNext()를 사용해서 꺼내는데 while문으로 확인하면서 그 다음 줄이 없을 때까지, 더 안 나올때까지 계속 꺼낸다. 단, 이 때 꺼내는 데이터는 매 줄을 별개로 꺼내기 때문에 하나의 음악파일에 있는 곡명, 앨범명 등등의 정보가 다 흩어지게 된다. 즉, 우리는 받아온 파일을 **한 세트**로 정리해서 꺼내야 하는 것이다!!  

    if(cursor != null){
             while(cursor.moveToNext()){

        <이 곳이 어떻게 꺼낼지 정리해야하는 곳 1-3.>

      }
           cursor.close();
       }

여기서 중요한 건, cursor는 안 끝내주는 끝도 없이 불러오기 때문에 어떻게든 다 꺼냈으면 닫아줘야 메모리를 낭비하지 않는다. 다음 줄이 없어서 while문을 빠져나가면 바로 close()로 닫으면 된다.




##**1-3. 받아온 데이터를 정리해서 보내기  **

###① 텍스트 정보 꺼내기
하나의 음악 파일에는 하나의 곡 ID, 앨범명, 곡 제목, 아티스트명+앨범 이미지까지가 **한 세트**이다. 하지만 컴퓨터는 그 사실을 알 리가 없으므로 우리는 이걸 '한 세트'로 묶어서 꺼내도록 '데이터 타입'을 정해줘야 한다. 사실 그걸 여기다 다 쓰면 너무 번잡스러우니깐 Music이라는 클래스에서 다음과 같이 변수만 미리 지정해놨다.

    public class Music {
       String id;
       String album_id;
       String artist;
         String title;

       Uri album_image;
       Uri uri;
    }

즉, Music 타입의 music이란 객체를 만들어서 위에 선언한 변수명대로 하나씩 꺼내면 music이란 객체로 다음과 같이 while문 안에서 한 세트씩 묶일 수 있는 것이다. 그리고 각각의 세트는 곡 ID으로 구별한다.

      Music music = new Music();

               int idx = cursor.getColumnIndex(proj[0]);
               music.id = cursor.getString(idx);
               idx = cursor.getColumnIndex(proj[1]);
               music.album_id = cursor.getString(idx);
               idx = cursor.getColumnIndex(proj[2]);
               music.title = cursor.getString(idx);
               idx = cursor.getColumnIndex(proj[3]);
               music.artist = cursor.getString(idx);

###② 앨범 이미지 꺼내기
이미지는 텍스트와 다르게 용량도 크고 복잡하기 때문에 꺼내는 방법을 따로 꼼꼼하게 만들어줘야한다. 단, while문 안에는 함수를 써서 간단하게만 쓴다.

    music.album_image = getAlbumImageBitmap(music.album_id);

친절한 안드로이드씨는 Bitmap이라는 클래스를 제공해서 이 클래스를 데이터 타입으로 지정해주면 가져온 이미지 파일을 담을 수 있다. 그래서 위에 적은 getAlbumImageBitmap를 Bitmap으로 지정해주는 함수를 만든다.

    private static Bitmap getAlbumImageBitmap(Context context, String album_id){

    <이 내부에 파일을 꺼내는 방법이 들어간다>

    }

앨범 이미지를 가져오기 위해서 일단 1-1의 ①②와 방법은 동일하다. 똑같이 URI 객체를 생성해서 혹시라도 놓치는 이미지가 없도록 직접 위치를 지정한다.

       Uri uri = Uri.parse("content://media/external/audio/albumart/" + album_id);

또한  ContentResolver 객체를 만들어서 데이터를 가져오는 것도 동일하다. 단, 여기서부터 Stream을 열어서 빨대로 가져오듯이 이미지를 넣고  

       // 2. 컨텐트 리졸버 가져오기
       ContentResolver resolver = context.getContentResolver();
       try {
           // 3. 리졸버에서 스트림열기
           InputStream is = resolver.openInputStream(uri);
           // 4. BitmapFactory 를 통해 이미지 데이터를 가져온다
           Bitmap image = BitmapFactory.decodeStream(is);
           // 5. 가져온 이미지를 리턴한다
           return image;
       }catch(FileNotFoundException e){
           Logger.print(e.toString(),"로그위치");
       }

###③ 심부름을 재추적해서 특정 곡에 대해서만 정보를 보기 위해 곡ID로 어디서 가져왔는지 주소를 담아줄 수 있다.

               music.uri = getMusicUri(music.id);

     // 음악 id로 uri 를 가져오는 함수
     private static Uri getMusicUri(String music_id){
          Uri content_uri = MediaStore.Audio.Media.EXTERNAL_CONTENT_URI;
         return Uri.withAppendedPath(content_uri, music_id);
     }    

###④ 하나의 파일의 정보가 모두 담긴 music객체를 보낸다

               datas.add(music);

-----------------------------------------------------------------

나머지는 다음에!!





####2. 이미지를 통합해서 관리하는 라이브러리 - glide

####3. Adapter란 무엇인다? 도대체 뭐에 어떻게 쓰(고있었)나?

####4. 본격적으로 재생목록과 재생화면을 붙여보자!!

####5. 선택한 음악파일의 재생화면을 보려면?

####6. 재생 화면에서 재생만 하는 것도 쉽지 않다

####7. 전체 시간 표시하기

####8. 일시정지와 다른 곡 재생

####9. 재생 위치 핸들러(SeekBar)를 움직여 보자

####10. 재생 시간을 표시하기.
