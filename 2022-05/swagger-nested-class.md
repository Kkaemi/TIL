# Swagger 내부 중첩 클래스 이름이 같을 경우 하나만 인식되는 버그 해결
현재 회사에서는 스프링 부트 2.6.x 버전을 사용중  
2.6.x 부터 springfox 적용이 안되는 버그 발생  
강제로 적용할 수는 있으나 자연스럽다는 생각이 안듬
<br>

springdoc 사용하기로 함
<br>

근데 내부 클래스 이름이 같으면 하나만 적용되는 버그가 있었음  
ex) `PlaylistDetailResDto.SongDto` && `DuplicateCheckListResDto.SongDto`
<br>
<br>

## 해결 방법
`properties` 혹은 `yml` 파일에 다음 한줄만 추가해주면 된다.  
`springdoc.use-fqn=true`
