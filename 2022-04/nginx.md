## Nginx config 설명

Amazon Linux에서 설치하는 방법이 조금 다름 `sudo yum install nginx` 치면 콘솔에 대체 명령어 나옴  
<br/>
Amazon Linux는 `/etc/nginx` 경로에 있는 `nginx.conf` 파일 참조하고 있음  
우분투는 `/etc/nginx/sites-available` 경로에 있는 `default` 파일 참조하고 있음  

<br/>
기본 엑세스 로그 경로 `/var/log/nginx/access.log`
<br/>
기본 에러 로그 경로 `/var/log/nginx/error.log`

---
* 프론트 빌드파일 정적 호스팅  
ex) vue, react
```shell
location / {
        # IP allow, deny
        allow 123.123.123.123;
        allow 456.456.456.456;
        deny all;

        # 프론트 빌드 파일 경로 (해당 스코프 안에서 오버라이딩 가능)
        root /opt/front-end/dist/;
        index index.html index.htm;
        try_files $uri /index.html;
}
```
<br/>

---
* 리버스 프록시
```shell
location /api/ {
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
        proxy_set_header Host $http_host;
        proxy_set_header X-Nginx-Proxy true;

        proxy_redirect off;

        proxy_pass http://127.0.0.1:8080/api/;
}
```
<br/>

---
* 그냥 추가 설명 ㅎㅎ
```shell
location /some/path/ {
        # 헤더 추가
        add_header 'Access-Control-Allow-Origin' 'http://localhost:3000';
        
        # 경로 축약
        alias /var/lib/jenkins/workspace/inst/;
}
```
