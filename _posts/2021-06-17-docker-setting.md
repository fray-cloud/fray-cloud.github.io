---
layout: post
title: "[Docker] 도커 기존 이미지(컨테이너) 설정 변경 및 자동화"
subtitle: "config.v2.json 변경"
categories: markdown
tags: docker window setting

---
### 배경
필자는 OpenCV를 이용하여 Django 웹 프레임워크를 접목시켜 웹서비스 프로젝트를 진행했다.
진행 막바지에 실 사용자에게 배포를 해줘야 하는 상황이 왔고, 도커를 이용하여 이미지 배포를 하기로 했다.

#### 배포 진행과정
1. [OpenCV 환경이 이루어진 우분투](https://hub.docker.com/r/opencvcourses/opencv-docker) 이미지를 이용하여 진행
2. 컨테이너 실행 후 프로젝트 `git pull` 진행

#### 배포 진행 후 문제점
1. 컴퓨터 재부팅 시 도커 자동화 설정을 하지 않아 서버가 켜지지 않는 현상 발생
2. 컨테이너 실행 시 Django 가 자동으로 실행되지 않는 문제 

>Django 서버를 동작 시키려면 명령어로 `python manage.py reunserver ip:port` 를 입력해야 하는데 필자는 초반에 컨테이너 생성시 
명령어를 입력하기 위해 `docker run -it `로 컨테이너 start 후 attach 로 명령어를 입력했다.<br>
이렇게 되면 도커 프로그램 실행 후 컨테이너가 실행될 때 직접 `attach` 하여 수동으로 명령어를 입력해야하는 상황이기에 사실상 자동화를 하려면
컨테이너가 실행 될 때 명령어도 자동으로 입력이 되어 Django가 실행이 되도록 설정해야 했다.
 
### 도커 자동화
#### 자동화 과정
도커 Dasktop 실행 → 도커 컨테이너 실행

#### 도커 자동화 설정

1. 도커 Dasktop 설정
    - 도커 Dasktop 상단 설정 버튼 클릭 > General 탭 설정 활성화
        + Start Docker Desktop when you log in
        + Open Docker Desktop dashboard at startup
        <img data-action="zoom" src='{{ "/assets/images/post/docker-setting-general.jpg" | relative_url }}' alt='docker General'>
    - 재부팅 후 윈도우 설정 > 앱 > 시작프로그램 확인
        <img data-action="zoom" src='{{ "/assets/images/post/docker-setting-startapp.jpg" | relative_url }}' alt='docker startapp'>
        
2. 도커 컨테이너 설정
    - 처음 컨테이너 실행하는 경우
        + `docker run <options> <image> --restart=always`
    - 이미 컨테이너가 생성 되었을 경우
        + `docker update --restart=always <container>`
    >도커 컨테이너 생성 시 `--restart` 의 경우 default 값이 `no` (재시작하지 않음) 이기 때문에 재시작을 하려면 `always` 옵션을 넣어야 한다.

#### 도커 이미지 설정

> 필자는 이미 만들어진 이미지로 작업 했기 때문에 처음 이미지를 만들어서 설정 하는경우 [도커 빌드](https://www.44bits.io/ko/post/building-docker-image-basic-commit-diff-and-dockerfile) 를 참고하자.

1. 도커 정보 확인 하기
    - 명령어 `docker info` 를 사용하면 Docker Root Dir를 확인할 수 있는데 , 여기서 /var/lib/docker 로 나온다.
    <img data-action="zoom" src='{{ "/assets/images/post/docker-info.jpg" | relative_url }}' alt='docker info'>

    > 도커가 wsl 위에서 동작해서 win 10 이후에는 vhdx 형식으로 도커 데이터가 저장된다.
      따라서 도커 데이터에 접근하려면 도커로 마운트한 컨테이너를 생성해야 한다.

2. ext4.vhdx 파일 확인
    - `C:\Users\<username>\AppData\Local\Docker\wsl\data` 에 ext4.vhdx 파일을 확인한다.

3. 마운팅 컨테이너 생성
    - vhdx 내부에 접근하기 위해 다음과 같은 명령어를 실행한다.
    
   ~~~
   docker run -v/:/data -it ubuntu /bin/bash
   cd /data/var/lib/docker/containers/<container:id>
   ~~~

    <img data-action="zoom" src='{{ "/assets/images/post/docker-mount-container.jpg" | relative_url }}' alt='docker mount container'>
    
4. config.v2.json 수정
    - 파일 편집기를 이용하여 config.v2.json 파일을 수정한다.
    > docker container config 를 확인 하기 위해서 주로 `docker inspect <container>` 로 확인한다. 
      필자의 경우 config 내 CMD 와 ENTRYPOINT 를 수정하여 컨테이너 실행 시 Django runserver 명령어가 수행되도록 하기 위해 변경했다.


5. 도커 컨테이너 커밋
    - `docker commit <container> <image_name>` 명령어를 사용하여 이미지를 커밋한다.
    
#### 도커 이미지 실행
1. 도커 이미지 실행
    - `docker run -d --name <container_name> <image>` 명령어를 사용하여 이미지를 실행한다.


### 마침
도커를 이미지 빌드부터 시작하여 컨테이너까지 만들어 배포하는 과정은 구글만 쳐도 많이 나오지만, 정작 이미지를 pull 하여 받아올때
내부에 dockerfile 을 수정하는 방법은 찾기 어려웠다.<br>
또한 맥 기반이나 리눅스 기반이였으면 터미널로 슝슝 들어가면 그만이지만 .. 윈도우는 wsl 기반으로 되어있어서 자료를 찾는데 많은 어려움이 있었다.<br>
다음에 OpenCV 기반 이미지를 사용 하거나, Django 기반 이미지 사용할때 참고하면 도움 될 것 같다.
