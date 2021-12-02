# vue .env 설정

>***‼️ vue-cli 버전 3 이상***

<br>

- package.json
<img width="483" alt="스크린샷 2021-12-02 오전 10 22 27" src="https://user-images.githubusercontent.com/64781807/144340364-085ff3d6-7945-4031-9c0c-88ace21d2ec0.png">

`--mode <커스텀 모드>` 이 부분에서 설정해준 모드에 따라서 루트 디렉토리에 존재하는 `.env.<커스텀 모드>` 파일과 매칭된다.

<br>

- .env
<img width="282" alt="스크린샷 2021-12-02 오전 10 29 06" src="https://user-images.githubusercontent.com/64781807/144340997-ce0cc324-23e6-4744-a42c-1c867c0ac3c0.png">

변수 등록은 사진과 같이 `VUE_APP_`으로 시작하는 변수만 인식된다.
