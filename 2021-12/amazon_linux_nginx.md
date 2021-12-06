# EC2 Amazon linux OS Nginx 설치

1. 설치  

`sudo yum install nginx`명령어 입력 시 `sudo amazon-linux-extras install nginx1` 명령어를 입력하라고 메세지가 나온다.  
중간에 y를 눌러줘서 설치를 완료하면 끝.

<br>

2. 시작  

- `sudo service nginx start` Nginx 시작  
- `sudo service nginx restart` Nginx 재시작
- `sudo service nginx status` Nginx 상태 체크

<br>

3. 설정

Nginx 설정 파일 경로  
> /etc/nginx/nginx.conf

해당 경로 이동 후 `sudo vim nginx.conf` 명령어로 수정해서 Nginx 설정
