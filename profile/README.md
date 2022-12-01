# Police-in-my-pocket
### :police_car: 실시간 위치 기반 셀프 경호 어플리케이션 [Police-in-my-pocket] <br/>
저희 Police-in-my-pocket은 긴급 상황 인식 및 자동 알림 신고 기능이 있는 스마트 경호 어플리케이션입니다. 사용자가 출발지와 목적지를 입력하고 확인 버튼을 클릭하면, 경로 및 실시간 위치를 추적합니다. 이때, 긴급 상황이 발생하여 사용자가 직접 신고하거나 AI 모델이 사용자의 비명 소리를 인식하면 자동으로 신고가 발동합니다.
### README.md 파일 작성중입니다.

### Tech Stack
<img width="852" alt="스크린샷 2022-11-13 오전 12 08 30" src="https://user-images.githubusercontent.com/96467030/201482634-43b6ec56-6745-494f-9f17-149fcae222b8.png">


### Members
|NAME|유희진          |문지영    |손효정           |장세은            |
|---|---|---|---|---|
|Role|Frontend, Backend, DevOps, Team Leader          |Frontend    |Frontend           |Frontend, Backend            |
|Github|[yu-heejin](https://github.com/yu-heejin)|[ziyoungmoon](https://github.com/ziyoungmoon)|[hyooojing](https://github.com/hyooojing)   |[isprogrammingfun](https://github.com/isprogrammingfun)  |
 
 
 
### 앱 개발 및 실행 화면

- 위치 기반 서비스(LBS)

  ![image01](https://user-images.githubusercontent.com/104436038/204981509-aa688713-49c6-4365-ab9d-ed1cc8d8dffc.png)

  GPS 신호와 구글 지도 API를 사용하여 사용자의 실시간 위치를 추적한다. 위급 상황 발생 시 사용자의 위치를 등록된 지인에게 메시지를 보내는 위치 기반 서비스(LBS) 기능을 제공한다.

- 주요 연락처 등록

  ![image02](https://user-images.githubusercontent.com/104436038/204981644-77595564-21a3-447f-9671-abca096f3b5a.png)

  사용자가 귀갓길에 앱을 실행하여 위급 상황이 발생했을 때, 메시지를 전송할 가족 또는 지인의 이름과 문자를 주요 연락처로 설정할 수 있도록 한다. 

- 검색 및 등록 서비스

  ![image03](https://user-images.githubusercontent.com/104436038/204981657-2bfab596-2ddf-4c9b-b047-2f1003ad0a47.png)

  사용자가 앱을 이용하기 위해서 내리는 마지막 정거장과 사용자의 목적지까지의 정보가 필요하므로 사전에 등록할 수 있도록 한다.

- 검색 서비스

  ![image08](https://user-images.githubusercontent.com/104436038/204981750-254b9710-e2a1-4c47-ab4b-97f64dd30123.png)

  구글에서 제공하는 place API를 사용하여 버스 정류장과 지하철역 등 주소 정보를 쉽게 검색할 수 있도록 한다.

- 안심 귀가 서비스

  ![image07](https://user-images.githubusercontent.com/104436038/204981713-62b7ff9a-42f9-411a-a304-2cb2bb1e567e.png)

  이용자의 현재 위치는 빨산색, 출발지 위치는 노란색, 도착지는 파란색 마커를 사용하여 가독성을 높일 수 있도록 한다. 

- 문자 서비스

  ![image09](https://user-images.githubusercontent.com/104436038/204981772-9982111e-a182-46bf-9d88-3fe1a1bef13f.png)

  긴급 상황이 발생하여 신고가 되면 등록된 지인에게 신고 문자가 발송된다.
  
  
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

### 2) run on Docker environment

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
    - ./gradlew clean build
    - docker-compose build
        
        ```
        docker-compose up -d --build
        ```

