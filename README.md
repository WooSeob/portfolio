# 변우섭: BackendDeveloper

안녕하세요.

개발을 좋아하며 소프트웨어 아키텍트의 꿈이 있는 주니어 개발자 변우섭입니다.

자발적인 필요성에 의해 즐겁게 공부하며

배운것을 적용시켜 기존의것을 개선하는것을 좋아합니다.

부족한점이 많지만 코드 한줄한줄에 깊은 고민을 담아내는 개발자가 되고 싶습니다.



## :computer:프로젝트 이력

### 1. 같이하실(팀) - Backend, Android

같이하실은 배달앱 사용시 높은 최소주문금액과 배달팁에 부담을 느끼는 1인가구를 위해

주문하고자 하는 가게를 중심으로 사용자들이 모이고, 함께 주문할 수 있도록 돕는 서비스 입니다.

#### 기술스택

**백엔드**

`NestJS` `TypeORM` `MySQL` `Socket.io` `AWS S3` `Firebase Cloud Messaging` `Jest` `winston` `Swagger`

**안드로이드**

`Java` `AAC` `Room` `DataBinding` `ViewBinding` `Retrofit` `Socket.io`

#### 특징

- 실제 서비스를 목표로 개발중이며 막바지 단계에 와 있습니다.
- NestJS를 도입해 Controller, Service, Domain의 레이어드 구조로 개발 했습니다.
- 주요 유스케이스들에 대해(서비스) 테스트 코드를 작성해 개발했습니다.

[Repository(server)](https://github.com/WooSeob/baemin-mate)



### 2. [Web Catchmind](http://catchm1nd.herokuapp.com)(개인) - Fullstack 

#### 개요

'[캐치마인드](https://cmind.netmarble.net/main.asp)'라는 게임을 node.js 백엔드와 Angular프론트엔드, socket.io를 통해서 웹 버전으로 구현했습니다.

#### 기술스택

`Express` `TypeScript` `mongoDB` `mongoose` `socket.io` `Angular`

웹서버 프레임워크는 Express를 사용했으며 데이터베이스는 mongoDB를, ODM은 mongoose를 사용했습니다. 객체지향적 특징을 더 잘 활용할 수 있도록 백엔드 또한 TypeScript로 구현했습니다. 

#### 기술적 특징

- MAP 자료구조를 통한 방 관리

  서버에서 방을 관리하기 위해서 방 id를 키로 하고 방 객체를 값으로 하는 Map을 사용하고 방 찾기 요청이 들어오면 존재하는 방 중 참여인원이 가장 작은방의 id를 반환하거나 새로 방을 생성하고 방의 id를 반환하도록 구현했습니다.

-  스테이트 패턴과 템플릿 메서드 패턴을 통한 게임 진행 로직 구현

   설정된 게임 시간과 라운드 수에 따라 게임은 자동적으로 진행되어야 하고 각 상황마다 유저들이 행할 수 있는 행동이 다르기 때문에 스테이트 패턴을 사용해 게임 진행 로직을 구성했습니다. 또한 스테이트가 바뀔 때마다 클라이언트 모두 스테이트를 동기화하고 필요한 정보를 송신해야 했기 때문에 템플릿 메서드 패턴을 사용했습니다.

-  스트래티지 패턴을 통한 그리기 모드 구현

   클라이언트에서 유저가 그림을 그릴 때 펜 모드 인지 지우개 모드인지에 따라 다르게 작동할 수 있도록, 더욱이 다른 그리기 도구가 추가될 가능성을 염두에 두어 스트래티지 패턴을 통해 그림 그리기를 구현했습니다. 

<img src="C:\Users\byunw\AppData\Roaming\Typora\typora-user-images\image-20211122164140597.png" alt="image-20211122164140597" style="zoom: 67%;" />

> 자기 차례에 해당하는 유저는 제시어에 대해 그림을 그리고 나머지 유저들은 그림을 통해 제시어를 추측하는 게임입니다.

#### 회고

- 서버측 게임 룰 코드에 서버 -> 클라이언트 송신 코드가 함께 있어 디버깅과 기능 추가가 어렵겠다는 판단을 했습니다.
  - 서버-클라이언트 간 주고받는 메시지를 따로 정의하고, 서버가 메시지를 보내는 기능을 담당하는 클래스를 새로 작성했습니다.
  - 게임 상태 클래스를 따로 만들고 게임 룰을 담당하는 코드에서는 게임 상태 클래스에 업데이트를 요청하고, 게임 상태 클래스에서 실제로 게임 상태를 변경함과 동시에 클라이언트로 변경된 상태를 전송하도록 작성하고 있습니다.
- 게임 서비스 객체가 싱글톤이 아님
  - 현재 코드는 소켓 연결마다 해당 소켓을 멤버로 가지는 서비스 객체를 생성해 내고 있습니다.
  - 하지만 "해당 서비스 객체는 소켓외엔 멤버가 없기에 여러개의 객체를 생성할 필요가 있는가?" 라는 의문이 생겼습니다.
  - 따라서 이러한 문제를 해결하는 구조에대해 고민중에 있습니다.
- 테스트 코드 작성
  - 지속적인 기능추가, 리팩토링을 시도하다 보니 기존의 여러개의 브라우저를 띄워놓고 직접 테스트 해보는 방식은 다음과 같은 문제가 있었습니다.
    1. 정해진 테스트 셋, 절차가 없음
    2. 직업 하다보면 특정 절차를 빼먹는 등 실수할 위험이 있음
    3. 테스트 비용(시간)이 점점 크게 증가함

[Repository(server)](https://github.com/WooSeob/web-catchmind-server)

[Repository(client)](https://github.com/WooSeob/web-catchmind-client)



### 3. Tutor2Tutee(팀) - Backend

#### 개요

한경대학교에서 주관하는 튜터링 프로그램에서 튜터와 튜티의 매칭을 통해 참여를 더욱 증진시킬 수 있도록 하는 웹 서비스를 개발했습니다.

#### 기술 스택

`Express` `TypeScript` `mongoDB` `mongoose` `socket.io` `React.js`

#### 기여내용

- mongoose 스키마 설계

- HTTP API (회원 가입, 인증, 튜터링 개설, 참가, 출석, 강의 검색) 를 제공하는 백엔드 개발

- socket.io를 통한 채팅기능 엔드포인트 구현

- 데모 시연을 위한 더미 데이터 생성툴 개발

#### 협업 방법

![google docs를 통한 협업](https://user-images.githubusercontent.com/23726218/118573518-ae8b5180-b7bd-11eb-9c27-ee547f1f72a2.png)

[google docs](https://docs.google.com/spreadsheets/d/1Pe2ZcPZiRUYBfrYW3ZOcvmtuUUuG0Yn3Lkc-9folDto/edit#gid=0) 와 [github](https://github.com/WooSeob/pbl3-server-side)을 통해 다른 팀원들과 작업을 분담해서 진행했습니다.



#### 회고

1. 카테고리 기반 검색기능 

   - 겪었던 문제 

     관심도가 급상승하는 과목을 알아내기 위해 사이트의 상단에 배치한 검색창을 통해 검색이 많이 되는 과목을 통해 유추할 수 있으리라 판단했습니다. 하지만 문제는 문자열 그 자체로 검색량을 집계해선 안 된다는 것이었습니다. 예를 들어 "컴퓨터 구조"에 대한 검색과 "컴구"에 대한 검색은 동일하게 "컴퓨터 구조" 라는 과목에 대해 검색했다고 여기고 해당 과목에 검색량을 집계해야 지능적인 추천 기능을 구현할 수 있으리라 생각했습니다.

   - 접근 / 해결 방법

     먼저 "동일한 개념을 지칭하는 문자열들은 서로 비슷할 것이다"라는 가정을 하고, 동일한 개념을 칭하는 문자열을 정점으로 하고 문자열 간 편집 거리(Levenshtein Distance)를 가중치를 간선으로 하는 그래프 자체가 문자열에 대한 추상적인 지칭일 것이라고 생각했습니다.

     따라서 기존 DB에 일치하는 문자열이 입력되면 해당 지칭에 대한 검색 결과를 반환하고, DB에 없는 문자열이 입력되면 기존 그래프 중 가장 적합한 그래프에 편입시키거나, 해당 문자열로 새로운 그래프를 만들고 검색 결과를 반환하도록 했습니다.

     하지만 위 방법이 처음에 기술한 문제를 잘 해결해 주지는 못했습니다.

       첫 번째로 데이터가 입력되는 순서에 영향을 받는다는 것이었습니다. 각 그래프의 가중치 평균과 상수로 지정해둔 역치를 비교해서  검색어를 분류하도록 구현했기 때문에 ['컴퓨터 구조', '생활 원예', '컴구', '컴구조'] 순으로 입력되면 4개 문자열 전부 같은 그래프로 분류되는 문제가 발생하는 것이었습니다. 따라서 "유사한 검색어끼리, 앞뒤 그래프끼리는 되도록 편집 거리가 길게"라는 조건에 맞춰 데이터를 미리 준비해서 서비스 전 동작 시켜 DB에 구성되도록 했습니다. 

       두 번째로 검색에 중복되는 단어와 줄임말이 자주 사용될 수 있다는 것이었습니다. 서비스 특성상 전공/수업 명이 주로 검색된다고 가정했을 때 00공학, 00학 등이 검색이 많이 되는 것이었습니다. 또한 '컴퓨터공학' 을 '컴공'으로 줄여서 사용하는 경우 맨 처음 한 가정을 벗어나는 경우가 발생할 수 있었습니다. 따라서 이러한 경우를 예외로 두어 00공학 등의 단어가 들어오면 '공학' 등의 단어를 떼어내고, 두 단어가 줄임말 관계에 있다는 것이 확인되면 계산된 편집거리에 1보다 작은 상수를 곱해서 의도적으로 편집거리를 작게 만들어 해결했습니다.

       세 번째로 검색이 이뤄지는 동안에도 계속 DB의 그래프가 변화한다는 것이었습니다. 검색 순서에 영향을 받기 때문에 서비스 중에 입력되는 검색어는 그래프가 있는 DB를 수정하지 않고 버퍼로 사용하는 다른 DB(분류에는 사용되지 않는)에 기록하도록 했습니다. 그리고 검색 결과에 대한 만족/불만족을 유저에게서 피드백으로 받도록 하고, 응답한 유저가 일정 수 이상일 때 만족 비율이 높으면 그래프가 있는 DB로 해당 검색어를 편입하도록 구현했습니다. 

   - 결과

     미리 준비한 테스트 데이터에선 나름대로 잘 작동하는 것처럼 보였습니다. 하지만 대부분의 분류 기준(편집거리 역치, 전처리에 곱해질 가중치값 등)이 직접 실행해보고 조금씩 조정한 상수값들이었고, 평가 기준 또한 없었기 때문에 일반적으로 잘 동작한다고 말할 수 없었습니다. 후에 와서 이런 문제들을 해결하는데 머신러닝이 주로 사용된다는 것을 알게 되었고, 잘 알려진 방법을 통해서 기능을 구현했다면 하는 아쉬움이 남습니다.

[데모 동영상](https://www.youtube.com/watch?v=X0MH60IjdQc&t=493s)



### 4. 임베디드 시계, 날씨 프로그램(개인) - Embedded

#### 개요

ARM 프로세서 기반에 임베디드 리눅스에서 7-segment에 현재 시각 또는 타이머를 표시하고, 현재 날씨 정보를 받아와 8x8 도트 매트릭스 상에 이모티콘으로 재생하는 프로그램을 개발했습니다. 

![demo](https://user-images.githubusercontent.com/23726218/118643217-394c6a80-b817-11eb-9ae3-a52bfb01e81b.png)

#### 특징

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



