# Docker

내가 느낀 전체적인 도커의 메커니즘 : 어떠어떠한 것을 빌드해서 이미지를 만들고 
-> 이미지를 도커로 띄운 뒤 -> 이미지를 받아서 로컬에서 개발작업을 진행   

!!많은 시행착오를 거쳐 도커의 메커니즘에 대해 이해가 조금 되었다.
1. Dockerfile을 만든다.
2. 해당 디렉토리 위치에서 docker build를 한다.
3. docker build을 하면 이미지가 생성된다.
4. 이미지가 생성됐으면, 해당 이미지로 docker run을 한다.
5. docker run을 하면 컨테이너가 만들어지고 해당 이미지를 컨테이너 안으로 넣는다?띄운다?
6. 그럼 환경셋팅이 된다...?   

틀린 부분도 있겠지만 아주 조오금 조오오오오금 메커니즘이 이해가 됐다.   
앗 참고로 음... 저런 run이니 이미지 파일들이니 어떤 컨테이너가 실행중인지를 GUI로 확인할 수 있는 프로그램이 Docker Desktop 같다 ㅎㅎ..
***

1. 도커엔진 - 도커를 실행하면 Dockered라는 데몬 프로그램이 서버로 실행.   
**여기서 잠깐! 데몬 프로그램이 뭘까?   
   https://blogger.pe.kr/770  (포그라운드, 백그라운드, 데몬 프로세스)    
   https://haruhiism.tistory.com/9   
   

2. 도커실행 : 도커 이미지를 받아서 컨테이너로 실행   
   ** -it 라는 명령어는 -i와 -t 옵션이 합쳐진 옵션, -i는 호스트와 컨테이너 상호 입출력을 맞추고,
   -t는 TTY를 활성화해서 컨테이너에 터미널로 입력이 가능하게 한다.   
   ** TTY가 뭐지?!   
https://cosmosproject2015.tistory.com/143 (TTY, PTS, PTY)   
   

3. 도커 volume : 데이터를 컨테이너에 저장하지 않고 호스트에 저장하는 방식   
https://www.daleseo.com/docker-volumes-bind-mounts/
   
   
4. 도커빌드 : Dockerfile로 사용자 정의 이미지를 만듬   

**공부하기 : 도커 아키텍쳐, 컨테이너-OS 간의 통신 구조   
***
Docker의 개념 및 핵심 설명 : 
https://khj93.tistory.com/entry/Docker-Docker-%EA%B0%9C%EB%85%90
   
***
Docker 예제 실습중 갱장히 이상한 오류가 발생했다.  

failed to solve with frontend dockerfile.v0: failed to read dockerfile: open /var/lib/docker/tmp/buildkit-mount174403522/Dockerfile: no such file or directory
   
구글링을 계속 해봤지만 dockerfile -> Dockerfile 로 이름을 바꾸라는 답변밖에 없었다.   
하지만, 오류가 고쳐지지 않았고 터미널을 Open한 디렉토리 경로를 상위 폴더 위치로 open을 해서 났던 오류였다 ㅎㅎ