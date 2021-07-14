# Docker

내가 느낀 전체적인 도커의 메커니즘 : 어떠어떠한 것을 빌드해서 이미지를 만들고 
-> 이미지를 도커로 띄운 뒤 -> 이미지를 받아서 로컬에서 개발작업을 진행   
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
   