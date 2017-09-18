---
layout: post
title: 공짜로 챗봇 개발하기 2 - (번외)C9으로 앵무새 봇 만들기!(with KakaoTalk)
---
##### * 이 글은 챗봇 개발을 위한 기본적인 환경구성 방법을 소개합니다.
##### * 이 글은 개인적인 챗봇 개발경험을 바탕으로 작성되었습니다.

### 1. [C9 (https://c9.io)](https://c9.io)을 이용하는 이유?
---
 C9은 챗봇을 개발하기에 필요한 환경요소(Https Node.js 서버환경)를 갖추고 있다. 때문에 이를 이용하면 챗봇을 간단히 만들고 테스트하기에 용이한 임시 테스트 서버를 갖출 수 있다.  
* C9같은 경우 아마존에게 인수된 이후 가입절차(VISA카드 인증)가 까다로워졌으니, [Heroku](https://www.heroku.com)와 같은 다른 IDE를 써도 무방하다.
* [IDE비교 참고링크](http://blog.nnoco.com/258)를 통해 IDE를 비교해보고 자신에게 맞는 서비스를 선택하자.  

### 2. 앵무새 봇?
---
 말 그대로 사용자가 메세지를 보냈을 때 보낸메세지 그대로 응답해주는 봇을 말한다. 이 봇을 통해 메신저서버와 나의 봇서버의 연결이 제대로 되어 있는지 확인할 수 있다. 이제 카카오톡을 기반으로한 간단한 앵무새봇을 만들어 보자!!  

### 3. Node.js서버 생성
---
1. C9가입을 완료하고 로그인을 하였다면, DASHBOARD를 선택!  
![1](https://github.com/Tadoya/tadoya.github.io/blob/master/images/c9/1.png?raw=true)  
2. Create a new workspace를 선택!  
![2](https://github.com/Tadoya/tadoya.github.io/blob/master/images/c9/2.png?raw=true)  
3. Workspace name을 정하고, 아래 Choose a template에서 Node.js를 선택 후 Create workspace 선택!  
![3](https://github.com/Tadoya/tadoya.github.io/blob/master/images/c9/3.png?raw=true)  
4. workspace 생성 중..  
![4](https://github.com/Tadoya/tadoya.github.io/blob/master/images/c9/4.png?raw=true)  
5. workspace 생성완료!  
![5](https://github.com/Tadoya/tadoya.github.io/blob/master/images/c9/5.png?raw=true)  
6. app.js 파일을 생성한 후 다음코드를 입력하고 상단의 run버튼을 누르면 Node.js 서버가 동작되고, 로그의 URL을 누르면 "Hello world"를 확인할 수 있다.  
![6](https://github.com/Tadoya/tadoya.github.io/blob/master/images/c9/6.png?raw=true)  
```javascript
    const express = require("express");
    const app = express();

    app.get('/', function(req, res){
        res.send('Hello world!');
    });

    app.listen(process.env.PORT, function () {
    console.log('Example app listening on port!'+process.env.PORT);
    });
```  

### 4. [KakaoTalk 플러스친구 (https://center-pf.kakao.com/login)](https://center-pf.kakao.com/login) 만들기
---
1. 카카오톡 플러스친구에 로그인한 후, 새 플러스 친구를 선택!  
![1](https://github.com/Tadoya/tadoya.github.io/blob/master/images/plusfriend/1.png?raw=true)  
2. 필수사항을 모두입력 후 플러스친구 개설!  
![2](https://github.com/Tadoya/tadoya.github.io/blob/master/images/plusfriend/2.png?raw=true)  
3. 아직은 테스트용이니 그냥 확인 선택!  
![3](https://github.com/Tadoya/tadoya.github.io/blob/master/images/plusfriend/3.png?raw=true)  
4. 왼쪽 메뉴에서 스마트채팅 선택!  
![4](https://github.com/Tadoya/tadoya.github.io/blob/master/images/plusfriend/4.png?raw=true)  
5. API형을 선택!
![5](https://github.com/Tadoya/tadoya.github.io/blob/master/images/plusfriend/5.png?raw=true)  
6. 여기까지 왔으면, 이제 봇서버와 플러스친구를 연결준비!
![6](https://github.com/Tadoya/tadoya.github.io/blob/master/images/plusfriend/6.png?raw=true)  

### 5. 연동하기!  
---
1. 앱 이름을 정하고, 앱 URL에는 C9서버 실행 시 부여받은 url을 입력!  
(아직 서버 설정을 하지 않았기 때문에 Fail!)  
![1](https://github.com/Tadoya/tadoya.github.io/blob/master/images/c9andkakao/1.png?raw=true) 
2. 봇서버를 등록하기 위해선 [몇 가지 요건](https://github.com/plusfriend/auto_reply)을 만족 시켜야 하므로 해당 [소스코드](https://github.com/Tadoya/parrot_kakako)를 참고하여 C9에 기본적인 코드를 작성!  
![2](https://github.com/Tadoya/tadoya.github.io/blob/master/images/c9andkakao/2.png?raw=true) 
3. 서버를 실행시키고, **API 테스트**를 실행!  
(만약, 서버 실행 시 router.get관련 오류가 난다면, express버전 문제일 가능성이 크므로, express를 삭제 후 express4 이상으로 설치한다.)  
![3](https://github.com/Tadoya/tadoya.github.io/blob/master/images/c9andkakao/3.png?raw=true)  
4. API 테스트를 통과했다면, 앵무새 봇이 완성 되었다. 카카오 친구에서 내 봇을 찾아 테스트해보자!  
![4](https://github.com/Tadoya/tadoya.github.io/blob/master/images/c9andkakao/4.png?raw=true)  
![5](https://github.com/Tadoya/tadoya.github.io/blob/master/images/c9andkakao/5.png?raw=true) 


### + 참고사항 : 개인적으로 정리해 놓은 [KakaoTalk Bot API](https://www.slideshare.net/SeongSikChoi/kakao-botplus-friend)와 [LINE Bot API](https://www.slideshare.net/SeongSikChoi/linebot) SlideShare Link

### + C9은 실행 후 일정 시간이 지나면 자동으로 종료된다. 때문에 임시서버로는 이용할 수 있지만, 실제로 챗봇을 서비스하려면 개인서버를 가져야 한다. 그리고 이는 AWS를 이용해 해결 할 수 있다.

---
공짜로 챗봇 만들기 시리즈  
1. [개발환경 살펴보기](https://tadoya.github.io/How-to-make-Chatbot_1/)
2. ***(번외)C9으로 앵무새 봇 만들기***
3. [AWS로 내 서버 만들기](https://tadoya.github.io/How-to-make-Chatbot_3/)
4. 내 서버에 C9 개발환경 구성하기
5. 무료도메인 만들기(내도메인.한국)
6. SSL 적용하기(HTTPS)
7. C9에서 작성한 소스를 내 서버로 이전하기  

---
 [<<<< 이전 게시물](https://tadoya.github.io/How-to-make-Chatbot_1/) ------ [다음 게시물 >>>>](https://tadoya.github.io/How-to-make-Chatbot_3/)