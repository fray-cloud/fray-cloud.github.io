---
layout: post
title: "[Jetson] Jetson 업데이트(설치) 과정"
subtitle: Jetson AGX Xavier
catalog: true
tags: 
    - jetson
    - setting
    - VM

---
### [Jetson](https://www.nvidia.com/ko-kr/autonomous-machines/embedded-systems/product-development/) ??
간단히 설명하면 엔비디아사에서 영상분석 및 머신러닝을 위한 임베디드 컴퓨터를 뜻한다.
- ARM 아키텍처 CPU 장착
- 저전력 시스템
- 기계 학습 어플리캐이션 가속 설계
- CUDA 및 다양한 API 지원

### VM 환경 만들기
만약 Ubuntu 서버 환경이 구축 되어 있다면 VM 환경을 깔지 않아도 된다.
#### Virtual Box 설치
[VirtualBox](https://www.virtualbox.org/wiki/Downloads) 다운로드
1. Windows hosts 클릭
2. VirtualBox 설치
3. VirtualBox 6.1.22 Oracle VM VirtualBox Extension Pack →  All supported platforms 클릭
4. Extension Pack 설치
<img data-action="zoom" src='{{ "/img/post/jatson-virtual-box-install.jpg" | relative_url }}' alt='jatson virtual box install'>

#### Vitual Box 가상머신 만들기
1. [Ubuntu Desktop](http://old-releases.ubuntu.com/releases/18.04.2/) 설치

>필자가 아주 개고생 한 것이 Json Xavier 머신이 Ubuntu 18.04.2 버전이여서 VM Ubuntu 버전을
>20 버전대로 다운받았다가 SDK Manager 에 연결이 안되어서 오만 뻘짓을 했다 . 
>그러니 머신 내부에 우분투 버전을 확인 꼭 하길 바란다. 
> <img data-action="zoom" src='{{ "/img/post/jatson-setting-3.png" | relative_url }}' alt='jatson virtual box install'>

2. VM 실행 후 새로 만들기 클릭
3. 종류와 버전을 Linux / Ubuntu x64 선택
<img data-action="zoom" src='{{ "/img/post/jatson-virtual-box-setting-1.jpg" | relative_url }}' alt='jatson virtual box install'>
4. 메모리 4096MB 설정
5. 하드디스크 - 지금 새 가상 하드디스크 만들기 선택 후 만들기 클릭
6. VID 선택 후 다음 클릭
7. 동적 할당 선택 후 다음 클릭
8. 50GB 설정 후 만들기 클릭
9. 만들어진 VM 의 설정 클릭
10. USB 탭에 USB 3.0 컨트롤러 선택 후 확인 클릭
11. 저장소 탭에 비어 있음 저장장치 클릭 후 속성에 디스크 아이콘 클릭 → 디스크 파일 선택 클릭
<img data-action="zoom" src='{{ "/img/post/jatson-virtual-box-setting-2.jpg" | relative_url }}' alt='jatson virtual box install'>

#### 가상머신 실행

### JetPack 설치

1. 시작버튼 클릭
2. FireFox 에서 Nvidia SDK Manager 검색 후 .deb 파일 설치

> 2021.06.21 기준 1.5.1-7814 버전

3. ~~또는 터미널에서 다음과 같은 명령어 실행~~

```shell script
sudo dpkg -i sdkmanager_1.5.1-7814_amd.deb
```


만약 waiting for cache lock could not get lock /var/lib/dpkg/lock-frontend ... 이슈가 일어난다면! <br>
dpkg 및  apt lock 파일 삭제 & 업데이트 해주어야 한다.<br>
다음과 같은 명령어 실행


```shell script
sudo rm /var/lib/apt/lists/lock
sudo rm /var/cache/apt/archives/lock
sudo rm /var/lib/dpkg/lock*

# package update
sudo dpkg --configure -a
sudo apt update
``` 


> 우분투를 설치하고 패키저 업데이트를 습관화 해야할 것 같다 ..

4. Jatson 본체 앞부분의 C-port 와 호스트 컴퓨터 USB를 연결
5. VM 종료 및 USB 장치 연결 설정 후 시작
<img data-action="zoom" src='{{ "/img/post/jatson-setting-2.png" | relative_url }}' alt='jatson virtual box install'>
>  VM 이 실행중일 때 장치 → USB 로 연결할 수 있는데 ... 먹통이 되는 현상이 발생한다. <br>
   따라서 VM 을 종료 하고 시작 전에 연결 설정 후 시작하길 바란다.

6. SDK Manager 실행
    - nvidia 로그인
    - step1] continue
    <img data-action="zoom" src='{{ "/img/post/jatson-setting-4.png" | relative_url }}' alt='jatson virtual box install'>
    - step2] I accept the terms and conditions of the ... 체크 후 continue
    <img data-action="zoom" src='{{ "/img/post/jatson-setting-5.jpg" | relative_url }}' alt='jatson virtual box install'>
    - step3] 느긋하게 다운 받아지는 것을 기다리기
    


