# 터미널 OpenSSL을 사용해서 랜덤 문자열 만들기

- base64
```bash
openssl rand -base64 <숫자>
```

- hex
```bash
openssl rand -hex <숫자>
```

<br>

> 명령어 마지막의 숫자는 base64 or 16진수로 인코딩 되기 전 문자열의 바이트 수
