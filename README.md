## :pushpin: 프로필

- 이름: 김혁진
- 1999.11.11 출생
- phone: 010-9406-3580
- Email: r3rumasi2@gmail.com
- GitHub: [github.com/kimhyeokjin1111](https://github.com/kimhyeokjin1111)
</br>

> 한경대학교 졸업(2018.03-2024.02)  
> 경동고등학교 졸업(2015.03-2018.02)
> 

</br>

## :pushpin: attitude
```
여러 방법을 적용할 수 있는 유연한 사고를 가진 개발자를 목표로 하고 있습니다.
```

</br>

## :pushpin: 스택

![Java](https://img.shields.io/badge/java-%23ED8B00.svg?style=for-the-badge&logo=openjdk&logoColor=white)
![Spring](https://img.shields.io/badge/spring-%236DB33F.svg?style=for-the-badge&logo=spring&logoColor=white)
<img src="https://img.shields.io/badge/html5-E34F26?style=for-the-badge&logo=html5&logoColor=white">
<img src="https://img.shields.io/badge/javascript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=white">
<img src="https://img.shields.io/badge/CSS-1572B6?style=for-the-badge&logo=CSS3&logoColor=white">

</br>

## :pushpin: 툴

<img src="https://img.shields.io/badge/eclipseide-2C2255?style=for-the-badge&logo=eclipseide&logoColor=white">
<img src="https://img.shields.io/badge/intellijidea-000000?style=for-the-badge&logo=intellijidea&logoColor=white">
<img src="https://img.shields.io/badge/github-181717?style=for-the-badge&logo=github&logoColor=white">
<img src="https://img.shields.io/badge/git-F05032?style=for-the-badge&logo=git&logoColor=white">
<img src="https://img.shields.io/badge/visual studio code-007ACC?style=for-the-badge&logo=visualstudiocode&logoColor=white">

</br>

## :pushpin: 프로젝트
### 1. [hippoBook](https://github.com/Integerous/goQuality)
>개인 책장 서비스 및 커뮤니티 사이트 (팀 프로젝트)  
>개발 기간: 2024.4.21 ~ 2024.5.30 
>  
>기술 스택:  
>Java 17 / Spring Boot / JSP / html / Javascript
>Oracle / MyBatis

</br>

## 1. 제작 기간 & 참여 인원
- 2024년 4월 27일 ~ 5월 30일
- 팀 프로젝트

</br>

## 2. 사용 기술
#### `Back-end`
  - Java 17
  - Spring Boot 3.0
  - Gradle
  - Oracle 11.2.0

</br>

## 3. ERD 설계
<p align="center">  
  
  ![ddl](https://github.com/kimhyeokjin1111/myGitHub/assets/159498606/2aadb451-ce7d-41f3-9d20-cfaa95442b8e)
  
</p>

## 4. 핵심 기능

### 4.1. (OpenAi API)
해당 사이트에 대해 답변해줄 수 있는 챗봇입니다. 
OpenAi API를 활용하여 Client의 요청(질문)에 대해 응답해줍니다.

### 4.1.1. 전체 흐름
<p align="center">
  <img src="https://github.com/kimhyeokjin1111/myGitHub/assets/159498606/78f131bf-120d-4d00-aa66-f7e50a39f6b0">
</p>
<p align="center">
  <img src="https://github.com/kimhyeokjin1111/myGitHub/assets/159498606/d00a303b-f3d8-4cf9-be7a-c74474197e2d" width=300 margin-right=10>
  <img src="https://github.com/kimhyeokjin1111/myGitHub/assets/159498606/6f2142c8-9ef8-4878-9e2c-f50a77a1bf7b" width=300 margin-right=10>
  <img src="https://github.com/kimhyeokjin1111/myGitHub/assets/159498606/7efccc75-3aea-499b-82a9-9c3c6dd9f881" width=300>
</p>

### 4.1.2. 사용자 요청

- **Session userId 체크** 
  - 화면단에서 th:if를 이용해 session.userId이 null인지 확인합니다.
  - null이라면 모달버튼을 생성하지 않습니다.
    
[chatbot.html 코드 확인](src/main/resources/templates/chatbot/chatbot.html)

- **Fetch 비동기 요청** 
  - 사용자의 채팅를 POST방식으로 비동기 요청을 날립니다.
  - (요청 보냈을 때 채팅이 url상에 노출되는 점과 채팅에 특수문자가 있는 경우 데이터가 손상되는 점  
    REST단에서 채팅에 대한 OpenAi의 답변을 받고 이를 데이터베이스에 INSERT처리를 하는 점을 고려해 POST방식으로 명시해주었습니다.)
    
[chatbot.js 코드 확인](src/main/resources/static/js/chatbot/chatbot.js)
 
### 4.1.3. RestController

- **요청 처리** 
  - RestController에서는 화면단에서 넘어온 요청(채팅)을 받고, Service 계층에서 로직 처리를 넘깁니다.

- **결과 응답** 
  - Service 계층에서 넘어온 로직 처리 결과(OpenAi의 답변)를 화면단에 응답해줍니다.
 
[ChatbotApi.java 코드 확인](src/main/java/com/example/hippobookproject/api/chatbot/ChatbotApi.java)

### 4.1.4. Service

- **과거 채팅 내역 불러오기** 
  - 데이터베이스단에서 채팅 내역을 받아옵니다.
  - OpenApi API 요청body의 message에 과거 채팅 내역을 추가해줍니다.

- **OpenAi API endpoint로 웹 통신** 
  - WebClient 만들어진 body를 endpoint에 요청해줍니다.
  - 공식사이트에 명시된대로 POST방식을 사용해주고 response 1개의 값을 리턴받기 위해 bodyToMono로 사용하였습니다.

- **채팅 내역 저장하기** 
  - 사용자 채팅과 api통신의 response의 컨텐츠에 접근하여 답변을 데이터베이스단에 전달합니다.  

[ChatbotService.java 코드 확인](src/main/java/com/example/hippobookproject/service/chatbot/ChatbotService.java)

### 4.1.5. Database

- **채팅 내역 검색 및 저장**
  - session.userId와 일치하는 사용자 채팅 내역을 읽어 service단으로 넘깁니다.
  - service단에서 넘어온 채팅 내역을 데이터베이스에 저장합니다.

</div>

</br>

## 4. 담당 파트 

- **관리자 페이지**
  - 사용자 검색 페이지
  ![Honeycam 2024-06-05 12-00-54](https://github.com/kimhyeokjin1111/myGitHub/assets/159498606/c3528db8-5362-481c-a04b-0791cd5dde28)
  - 사이트 방문수 차트 페이지
  ![Honeycam 2024-06-05 12-10-05](https://github.com/kimhyeokjin1111/myGitHub/assets/159498606/1d11899c-38ec-4010-b640-373a32759504)
  - 신고 컨텐츠 처리 페이지
  ![GIF 2024-06-07 오후 12-28-22](https://github.com/kimhyeokjin1111/myGitHub/assets/159498606/36d0c89d-f1d2-4543-92c5-8bdd44a4e33a)
  - 팔로우 수 달성 스티커 승인 페이지
  ![GIF 2024-06-11 오전 2-24-27](https://github.com/kimhyeokjin1111/myGitHub/assets/159498606/65e2b991-9cbe-4c4a-82b3-322c5368cffe)
 
- **도서 페이지**
  - 도서 검색 페이지
  ![GIF 2024-06-10 오전 8-51-17](https://github.com/kimhyeokjin1111/myGitHub/assets/159498606/a42c8ef9-cadc-4129-8a92-60f9f20eee19)
  - 도서 정보 페이지
  ![GIF 2024-06-10 오전 8-56-55](https://github.com/kimhyeokjin1111/myGitHub/assets/159498606/619c538c-ab4f-4c1a-828c-ae3e64b450e6)
  

- **게시판 페이지**
  - 게시글 메인 페이지
![GIF 2024-06-10 오전 9-01-17](https://github.com/kimhyeokjin1111/myGitHub/assets/159498606/1b51b26d-e476-4608-a7ce-8933c243c687)
  - 게시글 뷰 페이지
![GIF 2024-06-10 오전 9-05-30](https://github.com/kimhyeokjin1111/myGitHub/assets/159498606/6f59afff-5bc2-4987-83e3-b458559216f2)
