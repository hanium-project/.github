
## :police_car: 실시간 위치 기반 셀프 경호 어플리케이션 [Police-in-my-pocket]<br/>
- 저희 Police in my pocket은 긴급 상황 인식 및 자동 알림 신고 기능이 있는 스마트 경호 어플리케이션입니다.
- 사용자가 출발지와 목적지를 입력하고 확인 버튼을 클릭하면, 경로 및 사용자의 실시간 위치를 추적합니다.
- 긴급 상황이 발생하여 사용자가 직접 신고하거나 AI 모델이 사용자의 비명 소리를 인식하면 자동으로 신고가 발동합니다.
- 신고가 발생하면 신고가 발생한 위치를 데이터베이스에 저장합니다.
- 저장된 데이터를 통해 내 주변 위치 정보를 지도에 표시하여 위험 상황이 발생한 정보, 치안 시설 정보를 볼 수 있습니다.

## Contents
- [Tech Stack](#Tech-Stack)       
- [Demo](#Demo)       
- [Project Structure](#Project-Structure)       
- [How to Install and run this project](#How-to-Install-and-run-this-project)      
- [Contributor](#Contributor)

## Tech Stack
<img width="852" alt="스크린샷 2022-11-13 오전 12 08 30" src="https://user-images.githubusercontent.com/96467030/201482634-43b6ec56-6745-494f-9f17-149fcae222b8.png">
 
## Demo
- 로그인
<p align="center"><img src="https://user-images.githubusercontent.com/104436038/204987042-e3a25c5b-69df-48dc-b610-6968cf2ce7eb.png" width="200" height="350"/><p>

- 회원가입
<p align="center"><img src="https://user-images.githubusercontent.com/104436038/204987054-3e26bb6d-8f89-4f7e-9979-e5c66c5ba66b.png" width="200" height="350"/><p>

- 메뉴 화면
<p align="center"><img src="https://user-images.githubusercontent.com/104436038/204987059-4ec9a454-c428-4b94-b46c-0ea09ccd6abe.png" width="200" height="350"/><p>

- 위치 기반 서비스(LBS)
<p align="center"><img src="https://user-images.githubusercontent.com/104436038/204986656-80096c49-6a76-46bd-a9cb-4afd1cb825df.png" width="200" height="350"/><p>
  GPS 신호와 구글 지도 API를 사용하여 사용자의 실시간 위치를 추적한다. 위급 상황 발생 시 사용자의 위치를 등록된 지인에게 메시지를 보내는 위치 기반 서비스(LBS) 기능을 제공한다.

- 주요 연락처 등록
<p align="center"><img src="https://user-images.githubusercontent.com/104436038/204987090-f2cb42f5-be05-470a-b190-545b59597244.png" width="200" height="350"/><p>
  사용자가 귀갓길에 앱을 실행하여 위급 상황이 발생했을 때, 메시지를 전송할 가족 또는 지인의 이름과 문자를 주요 연락처로 설정할 수 있도록 한다. 

- 검색 및 등록 서비스
<p align="center"><img src="https://user-images.githubusercontent.com/104436038/204987076-7434b80a-f697-4d2e-a0da-e4281fc2ce6f.png" width="200" height="350"/><p>
  사용자가 앱을 이용하기 위해서 내리는 마지막 정거장과 사용자의 목적지까지의 정보가 필요하므로 사전에 등록할 수 있도록 한다.

- 검색 서비스
<p align="center"><img src="https://user-images.githubusercontent.com/104436038/204981750-254b9710-e2a1-4c47-ab4b-97f64dd30123.png" width="200" height="350"/><p>
  구글에서 제공하는 place API를 사용하여 버스 정류장과 지하철역 등 주소 정보를 쉽게 검색할 수 있도록 한다.

- 안심 귀가 서비스
<p align="center"><img src="https://user-images.githubusercontent.com/104436038/204987102-92142f9b-c7cb-48b9-b82a-e3f8939a2eaa.png" width="200" height="350"/><p>
  이용자의 현재 위치는 빨산색, 출발지 위치는 노란색, 도착지는 파란색 마커를 사용하여 가독성을 높일 수 있도록 한다. 
 
## Project Structure
### Frontend

```
.
├── App.js
├── android/
├── app.json
├── index.js
├── ios/
├── node_modules/
├── package.json
├── assets/          // 각종 자원을 모아놓은 폴더
│   ├── images/
│   ├── sounds/
│   └── fonts/
├── src/        // 소스 코드를 모아놓은 폴더
│   ├── screens/       // 화면 단위의 코드
│   ├── api/           // 기능 구현을 위한 코드
│   ├── component/     // 재사용 가능한 컴포넌트 코드
│   ├── tempdata/      // api 테스트를 위한 mock data
│   └── styles/        // 스타일 코드
├── configs/        // 각종 설정을 위한 폴더
├── react-native.config.js       
└── yarn.lock
```

### Backend

- 도메인형 구조로 설계했습니다.

```
└── src
    └── main
       ├── java
       │   └── com
       │       └── pocket
       │           └── police
       │               ├── PoliceInMyPocketBackendApplication.java
       │               ├── domain
       │               │   ├── dangerlocation
       │               │   │    ├── controller
       │               │   │    ├── dto
       │               │   │    ├── entity
       │               │   │    ├── repository
       │               │   │    └── service
       │               │   ├── safelocation
       │               │   │    ├── controller
       │               │   │    ├── dto
       │               │   │    ├── entity
       │               │   │    ├── repository
       │               │   │    └── service
       │               │   ├── user
       │               │   │    ├── controller
       │               │   │    ├── dto
       │               │   │    ├── entity
       │               │   │    ├── repository
       │               │   │    └── service
       │               │   ├── usercontact
       │               │   │    ├── controller
       │               │   │    ├── dto
       │               │   │    ├── entity
       │               │   │    ├── repository
       │               │   │    └── service
       │               │   └── userlocation
       │               │        ├── controller
       │               │        ├── dto
       │               │        ├── entity
       │               │        ├── repository
       │               │        └── service
       │               │
       │               └── global
       │                   ├── common
       │                   ├── config
       │                   ├── security
       │                   ├── service
       │                   └── statusresponse
       │               
       └── resources
            ├── application-email.yml
            ├── application-message.yml
            ├── application-mysql.yml
            ├── prometheus.yml
            └── application.yml
``` 

## How to Install and run this project
### 1) run on Local environment

1. Clone this project
    
    ```
    git clone https://github.com/hanium-project/Police-in-my-pocket.git
    ```
    
2. Frontend
    1. node module install
        
        ```
        npm install (--legacy-peer-deps)
        ```
        
    2. custom font link
        
        ```
        npx react-native link
        
        ```
        
    3. Android run
        
        ```
        npm run android
        
        ```
        
    4. iOS run
        
        ```
        cd ios
        pod install
        cd ..
        npm run ios
        
        ```
        
3. Backend
    - change datasource url in application.yml
        
        ```
        datasource:
            driver-class-name: com.mysql.cj.jdbc.Driver
            url: jdbc:mysql://localhost:3307/polin   # 3307 -> 3306
            username: {USER_NAME}
            password: {USER_PASSWORD}
        ```
        
    - Install redis
    - run `SpringBootApplication.java` in IntelliJ IDEA

### 2) run on Docker container
1. Clone this project
    
    ```
    git clone https://github.com/hanium-project/Police-in-my-pocket.git
    ```
    
2. Frontend
    - Same as above.
        
3. Backend
    - ./gradlew clean build
    - docker-compose build
        ```
        docker-compose up -d --build
        ```

## Contributor

| Name    | 유희진   |  문지영   | 장세은 |  손효정    |
| ------- | -------| ---------| ----- | -------- |
| Profile | <img width="200px" src="https://avatars.githubusercontent.com/u/96467030?v=4" />   | <img width="200px" src="https://avatars.githubusercontent.com/u/104436038?v=4" />  | <img width="200px" src="https://avatars.githubusercontent.com/u/78543382?v=4"/>    | <img width="200px" src="https://avatars.githubusercontent.com/u/81282601?v=4">  |
| Role    | Team Leader, Frontend, Backend, DevOps  | Frontend, DevOps | Frontend, Backend   | Frontend |
| gitHub  | [yu-heejin](https://github.com/yu-heejin) | [ziyoungmoon](https://github.com/ziyoungmoon)   | [isprogrammingfun](https://github.com/isprogrammingfun)                        | [hyooojing](https://github.com/hyooojing)   |
