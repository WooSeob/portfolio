## 변우섭: BackendDeveloper

안녕하세요.

개발을 좋아하며 클린코드의 꿈을 꾸는 예비 주니어 개발자 변우섭 입니다.

자발적인 필요성에 의해 즐겁게 공부하며

배운것을 적용시켜 기존의것을 개선하는것을 좋아합니다.

부족한점이 많지만 코드 한줄한줄에 깊은 고민을 담아내는 개발자가 되고 싶습니다.



## :computer:프로젝트 이력

### 1. [Web Catchmind](http://catchm1nd.herokuapp.com)(개인) - Fullstack 

1. 개요

   - '[캐치마인드](https://cmind.netmarble.net/main.asp)'라는 게임을 node.js와 Angular, socket.io를 통해서 웹 버전으로 구현했습니다. 웹서버 프레임워크는 Express를 사용했으며 데이터베이스는 mongoDB를, ODM은 mongoose를 사용했습니다. 객체지향적 특징을 더 잘 활용할 수 있도록 백엔드 또한 TypeScript로 구현했습니다. 

   - DB server는 mongoDB atlas cloud를 사용했으며 프로덕트는 heroku에 배포중입니다.

     ![캐치마인드](https://user-images.githubusercontent.com/23726218/118633998-08ffce80-b80d-11eb-8ca1-3850dd3572b7.png)

     > 자기 차례에 해당하는 유저는 제시어에 대해 그림을 그리고 나머지 유저들은 그림을 통해 제시어를 추측하는 게임입니다.

2. 특징

   - MAP 자료구조를 통한 방 관리

     서버에서 방을 관리하기 위해서 방 id를 키로 하고 방 객체를 값으로 하는 Map을 사용하고 방 찾기 요청이 들어오면 존재하는 방 중 참여인원이 가장 작은방의 id를 반환하거나 새로 방을 생성하고 방의 id를 반환하도록 구현했습니다.

   -  스테이트 패턴과 템플릿 메서드 패턴을 통한 게임 진행 로직 구현

      설정된 게임 시간과 라운드 수에 따라 게임은 자동적으로 진행되어야 하고 각 상황마다 유저들이 행할 수 있는 행동이 다르기 때문에 스테이트 패턴을 사용해 게임 진행 로직을 구성했습니다. 또한 스테이트가 바뀔 때마다 클라이언트 모두 스테이트를 동기화하고 필요한 정보를 송신해야 했기 때문에 템플릿 메서드 패턴을 사용했습니다.

   -  스트래티지 패턴을 통한 그리기 모드 구현

      클라이언트에서 유저가 그림을 그릴 때 펜 모드 인지 지우개 모드인지에 따라 다르게 작동할 수 있도록, 더욱이 다른 그리기 도구가 추가될 가능성을 염두에 두어 스트래티지 패턴을 통해 그림 그리기를 구현했습니다. 

[Repository(server)](https://github.com/WooSeob/web-catchmind-server)

[Repository(client)](https://github.com/WooSeob/web-catchmind-client)



### 2. Tutor2Tutee(팀) - Backend

1. 개요

   - 한경대학교에서 주관하는 튜터링 프로그램에서 튜터와 튜티의 매칭을 통해 참여를 더욱 증진시킬 수 있도록 하는 웹 서비스를 개발했습니다.

2. 기여 내용

   - Node.js, Express, mongoDB, mongoose, socket.io를 사용했으며 아래와 같은기능을 개발했습니다.
     1. mongoDB 스키마 설계
     2. HTTP API (회원 가입, 인증, 튜터링 개설, 참가, 출석, 강의 검색) 를 제공하는 백엔드
     3. 채팅방을 위한 socket.io 서버 개발
     4. 데모 시연을 위한 더미 데이터 생성툴을 개발했습니다.

3. 협업 방법

   ![google docs를 통한 협업](https://user-images.githubusercontent.com/23726218/118573518-ae8b5180-b7bd-11eb-9c27-ee547f1f72a2.png)

   [google docs](https://docs.google.com/spreadsheets/d/1Pe2ZcPZiRUYBfrYW3ZOcvmtuUUuG0Yn3Lkc-9folDto/edit#gid=0) 와 [github](https://github.com/WooSeob/pbl3-server-side)을 통해 다른 팀원들과 작업을 분담해서 진행했습니다.

[데모 동영상](https://www.youtube.com/watch?v=X0MH60IjdQc&t=493s)



### 3. 임베디드 시계, 날씨 프로그램(개인) - Embedded

1. 개요

   - ARM 프로세서 기반에 임베디드 리눅스에서 7-segment에 현재 시각 또는 타이머를 표시하고, 현재 날씨 정보를 받아와 8x8 도트 매트릭스 상에 이모티콘으로 재생하는 프로그램을 개발했습니다. 

     ![demo](https://user-images.githubusercontent.com/23726218/118643217-394c6a80-b817-11eb-9ae3-a52bfb01e81b.png)

2. 특징

   - 날씨 정보 받아오기

     임베디드 리눅스에 있던 WGET을 통해 기상청에서 제공하는 날씨 XML을 다운로드하고 파싱을 통해 날씨 정보를 추출해 냈습니다. 장치의 입력을 계속해서 감지하고 도트매트릭스 또는 7-segment로 계속 출력해야 했기 때문에 날씨정보 다운로드 및 파싱을 자식 프로세스를 통해서 동시에 진행할 수 있도록 했습니다.

   - 도트 매트릭스

     어떤 LED가 켜질지는 장치 쓰기 하는 바이너리 값에 달려 있었기 때문에 이모티콘의 바이너리를 직접 계산해서 상수로 정의할 수도 있었지만 수작업으로 진행해야 하고 수정에 취약하다는 점에서 너무 비효율적이라는 생각이 들었습니다. 

     따라서 메인 로직과 그래픽 관련 로직을 분리해서 점들의 집합, 직선, 원을 표현하는 구조체를 정의하고 이러한 구조체들을 원형 리스트에 담아서 보내기만 하면 각 도형의 좌표들을 계산하고 바이너리 값을 계산해서 8x8 매트릭스 디바이스 쓰기 작업을 통해서 실제로 불이 들어오도록 만들었습니다.

     ```c
     // emoticon.c
     void playEmoticon(int Weather)
     {
         int EmoticonOffset = (Weather - 1) * 2;
         Drawable dFrame_1 = {.type = TYPE_Points, .Points = &EMOTICONS[EmoticonOffset]};
         Drawable dFrame_2 = {.type = TYPE_Points, .Points = &EMOTICONS[EmoticonOffset + 1]};
     
         RenderQueue Frame1, Frame2;
     
         Initialize(&Frame1);
         Initialize(&Frame2);
     
         InsertFront(&Frame1, &dFrame_1);
         InsertFront(&Frame2, &dFrame_2);
     
         if (AnimationFrame % 2 == 0){
             DOT_Draw_Canvas(&Frame1);
         }else{
             DOT_Draw_Canvas(&Frame2);
         }
         AnimationFrame++;
     }
     ```

     > 메인 로직에서 각각의 LED가 어떻게 켜지는지 몰라도 되도록 추상화했습니다.

     ```c
     //Dot_graphic_library.c
     void DOT_Draw_Canvas(RenderQueue *renderQueue){
         char MappedPoints[DOT_SIZE][DOT_SIZE] = INIT_POINTS;
         RowBits Frames[DOT_SIZE] = {0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00};
     
         while (renderQueue->cur != NULL){
             Drawable D = renderQueue->cur->value;
     
             switch (D.type){
             case TYPE_Points:
                 MappingPointsToDotMatrix(MappedPoints, D.Points);
                 break;
     
             case TYPE_Line:
                 MappingLineToDotMatrix(MappedPoints, D.line);
                 break;
     
             case TYPE_Circle:
                 MappingCircleToDotMatrix(MappedPoints, D.circle);    
                 break;
     
             default:
                 printf("Drawble Type invalid! : %d\n", D.type);
                 break;
             }
             
             MoveNext(renderQueue);
         }
         //그리기
         Generate_Hex_Code(Frames, MappedPoints);
         RenderingFrame(Frames);
         //커서 맨앞자리로 다시 옮겨놓기
         renderQueue->cur = renderQueue->head;
     }
     ```

     > 그려질 대상이 담겨있는 원형큐를 순회하며 LED에 쓰일 바이너리 값을 계산할 수 있도록 했습니다.

   - 입력과 출력 동시에 받기

     입출력 라인에 제한이 있었기 때문에 스위치와 도트 매트릭스, 7-segment를 동시에 읽거나 쓸 수 없었습니다. 따라서 스위치를 누를 때 즉각적으로 반응하면서 화면은 계속해서 나타나도록 하기 위해서 메인 프로세스는 스위치 입력 감지와 7-segment, 도트 매트릭스 쓰기로 이루어진 한 사이클을 100ms마다 반복하도록 구현했습니다.

[Repository](https://github.com/WooSeob/IoT_Lecture)



