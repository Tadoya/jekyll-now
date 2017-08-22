---
layout: post
title: 공짜로 나만의 챗봇을 개발해보자! 1. 개발환경 살펴보기
---
##### * 이 글은 챗봇 개발을 위한 기본적인 환경구성 방법을 소개합니다.
##### * 이 글은 개인적인 챗봇 개발경험을 바탕으로 작성되었습니다.


### 1. 챗봇을 개발하려면 무엇이 필요할까??
---
챗봇은 보통 (SSL환경이 적용된 도메인을 갖춘) HTTPS 서버에 서버사이드 스크립트 언어를 이용하여 개발한다.

  - 서버(server)  
    챗봇 개발에는 기본적으로 *Webhook을 위한 **봇 서버**가 필요하다.  
    [*Webhook : 메신저 서버로부터 사용자의 이벤트를 수신하기 위한 방법(API개념)]

  - 도메인(domain)  
    챗봇 메신저 대부분이 Webhook을 사용하려면 **HTTPS 환경의 URL**를 통해 Webhook을 하도록 권장(or 요구)한다.

  - 서버사이드 스크립트(server-side scripting)) 
    JavaScript를 사용할 줄 안다면 **Node.js**를 기반으로 개발하는게 편리하다.  


### 2. 공짜로 개발환경을 구성하려면??
---
HTTPS 서버를 구성하기 위해선 금전적 비용이 필요하다.
하지만! 이 금전적 요소들을 무료로 해결할 수 있는 방법이 있다.
지금부터, 그 방법들을 간단히 소개하고자 한다.

  - 서버? [AWS(Amazon Web Services)](https://aws.amazon.com/ko/) 로 나만의 서버를..   
  서버는 [AWS 프리티어](https://https://aws.amazon.com/ko/free/?sc_channel=PS&sc_campaign=acquisition_KR&Country=KR&sc_publisher=Naver&sc_medium=brandsearch_PC&sc_content=brandsearch&sc_detail=main_title&sc_category=Beginner&sc_segment=Beginner)를 이용하여 해결할 수 있다. AWS는 신규 가입자에게 1년 간 아마존서비스를 무료로 이용할 수 있는 프리티어 서비스를 제공한다. [자세히 보기](https://tadoya.github.io/How-to-make-Chatbot_3/)

  - [http://내도메인.한국?](http://내도메인.한국) 이게 도메인 주소였어?  
    먼저 도메인 주소가 필요한 이유는 뭘까? Webhook은 SSL(Secure Sockets Layer)이 적용된 URL을 요구한다. 따라서, SSL을 적용하려면 도메인 주소가 필요하다. (특별한 경우가 아니라면 IP주소만으로 SSL을 적용할 수 없다.)  
    결론적으로 "[내도메인.한국](http://내도메인.한국)"을 이용하여 무료로 도메인 주소를 얻을 수 있다. [자세히 보기](https://tadoya.github.io/How-to-make-Chatbot_5/)
  
  - SSL? [Lets' Encrypt](https://letsencrypt.org)로 해결!  
    도메인주소를 만들었다면, 이제 SSL을 적용한 HTTPS 통신환경을 통해 챗봇을 개발하기 위한 서버 환경 구성을 끝낸다.  
    [Lets' Encrypt](https://letsencrypt.org)나, [GOGETSSL(예전 ComodoSSL)](https://www.gogetssl.com)을 이용하면 무료로 SSL를 적용할 수 있다.

  - (번외) 위 세 가지 조건을 모두 갖춘 [C9](https://c9.io)!  
     [C9](https://c9.io)은 IDE서비스 중 하나이다. 그리고 이를 이용하면 위와 같은 환경구성 과정없이 챗봇을 개발할 수 있다. 물론, 이는 임시적인 개발환경을 제공할 뿐, 실제 챗봇 서비스를 운영하려면 나만의 서버를 갖고 있어야한다.  

---
공짜로 챗봇 만들기 시리즈
1. ***개발환경 살펴보기***
2. [C9으로 앵무새 봇 만들기](https://tadoya.github.io/How-to-make-Chatbot_2/)
3. [AWS로 내 서버 만들기](https://tadoya.github.io/How-to-make-Chatbot_3/)
4. 내 서버에 C9 개발환경 구성하기
5. 무료도메인 만들기(내도메인.한국)
6. SSL 적용하기(HTTPS)
7. C9에서 작성한 소스를 내 서버로 이전하기  

---  
[<<<< 이전 게시물](https://tadoya.github.io/Hello-World/) ------ [다음 게시물 >>>>](https://tadoya.github.io/How-to-make-Chatbot_2/)