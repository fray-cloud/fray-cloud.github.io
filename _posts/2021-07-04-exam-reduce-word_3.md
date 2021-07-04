---
layout: post
title: "[정보처리기사] 정처기 단답형 + 약술"
subtitle: "내가 틀린 문제들 정리"
catalog: true
tags:
    - 정보처리기사
    - 이론
---

#### 별다줄 시리즈는 아래 링크로!
- [별다줄 part 1](https://fray-cloud.github.io/2021/06/19/exam-reduce-word/)
- [별다줄 part 2](https://fray-cloud.github.io/2021/06/19/exam-reduce-word_2/)

정처기의 문제 유형 중 단답형 문제와 약술형 문제가 출제된다.
- **단답형** : 단어의 정의를 기반으로 출제하여 단어를 답을 쓰도록 하는 유형
- **약술형** : 단어를 제시하여 약술하도록 출제하여 단어의 정의에 맞게 답을 쓰도록 하는 유형

따라서 내가 틀린 생소한 단어를 기반으로 단어 + 단어 정의 를 정리해보려 한다.

`SOA`(서비스 지향 아키텍처)

1. 정보 시스템 구현을 위해 가장 선진화된 아키텍처
2. 분할 APP 조각들을 Loosely-coupled 하게 연결
3. 하나의 완성된 어플리케이션 구현

`PICONET`

1. 여러개 독립된 통신 장치가 블루투스, UWB, 통신기술 사용하여 통신망 형성
2. 사전 네트워크 정의 및 계획 없이 상황에 따라 조정 프로토콜에 의해 마스터-슬레이브 역할
3. 수십미터 이내 좁은 공간 네트워크 형성
4. 정지 또는 이동하는 장치 모두 포함

`Zigbee`

1. 저속 전송속도 갖는 홈 오토메이션 및 데이터 네트워크 위한 표준기술
2. 버튼 하나로 하나의 동작 잡아 집안 제어
3. IEEE 802.15 표준, 메시 네트워크

`와일드카드`

1. 컴퓨터에서 특정 명령어로 명령을 내릴 때, 여러 파일을 한꺼번에 지정할 목적으로 사용하는 기호
2. 주로 특정한 패턴이 있는 문자열 혹은 파일을 찾거나, 긴 이름을 생략할 때 쓰임
3. 쿼리 와일드카드
    - `%` : 0개 이상 문자열 일치
    - `[]` : 1개 이상 문자 일치
    - `[*]` : 1개 이상 불일치
    - `_` : 특정 위치 1개 문자 일치
    
`DoS`

1. 특정 서버에게 수많은 접속 시도 만듦
2. 다른 이용자가 정상 서비스 불가
3. 서버 자원 소진시켜 본래 의도대로 사용하지 못하게 함

`JSON`

1. 속성-값 쌍, 키-값 쌍 데이터 오브젝트
2. 인간이 읽을 수 있도록 텍스트 사용하는 개방형 표준 포멧

`Deque`

1. 양쪽 끝 삽입 및 삭제 가능 자료구조
2. 두개 포인터, 양쪽 삭제 삽입 가능

`UWB`

1. 중심 주파수 20% 점유 대역폭
2. 500MHz 이상 대역폭
3. GHz 대 초 광대역

`킬 스위치`

1. 도난 시 스마트폰 작동을 웹에서 정지
2. 일종의 자폭

`자료사전`

1. 자료요소, 자료요소 집합, 자료 저장소의 의미 및 그들간 관계 등을 구체적 명시하는 사전
2. 조직에 속해있는 다른 사람들에게 특정 자료 용어가 무엇을 의미하는지 알려주기 위함

`방화벽`

1. 미리 정의된 규칙, 불법침입 방지
2. 상호간 영향 차단

`IDS`(침입 탐지 시스템)

1. 이벤트 모니터링
2. 실시간 탐지

`IPS`(침입 방지 시스템)

1. 실시간 차단
2. 유해 트래픽 능동 처리

`데이터 마트`

1. 데이터를 한 부분으로 특정 사용자가 관심 갖는 데이터를 담은 비교적 작은 규모 데이터

`데이터 웨어하우스`

1. 급증하는 다량의 데이터를 효과적 분석 및 정보화
2. 여러 계층의 사용자들이 효율적으로 사용할 수 있는 데이터 베이스

`MQTT`(Message Queuing Telemetry Transport)

1. IoT 장치, 텔레메트리 장치 등 최적화되어 사용할 수 있도록 개발된 프로토콜
2. 브로커를 사용한 Publish/Subscribe 방식
3. 라이트 메세징 전송하는 프로토콜
4. 저전력 센서, 스위치, 밸브 등 기기에 대한 표준적 인터넷 환경 자원
5. 프로토콜 리소스 점유 최소화 및 한정된 자원 시스템 지원

`CSMA`(반송파 감지 다중 접속)

1. 각 노드들이 프레임을 전송하려고 공유 매체(반송파)에 접근하기 전에,
2. 먼저 매체가 사용중인지 확인(Carrier Sensing)하며 다중접속(Multiple Access)하는 방식
3. `CSMA/CD`(반송파 감지 다중접속/충돌 탐지)
    - 유선 LAN
4. `CSMA/CA`(반송파 감지 다중접속/충돌 회피)
    - 무선 LAN
    
`스팸 차단 솔루션`

1. 메일 서버 앞단 위치하여 프록시 메일서버 동작
2. 메일 바이러스 검사, 내부에서 외부 본문 검색 가능 통한 정보 유출 방지

`거리벡터 알고리즘`

1. 거리와 방향위주로 만들어진 라우팅 알고리즘
2. 벨만 포드 알고리즘 이용

`링크상태 알고리즘`

1. 최단 경로로 만들어진 라우팅 알고리즘
2. 다익스트라 알고리즘 이용

`OLAP`(온라인 분석 처리)

1. 데이터 웨어하우스의 데이터를 전략적인 정보로 변환
2. 의사결정 지원 역할

`MLFQ`(다단계 피드백 큐)

1. FCFS + RR(라운드 로빈) 스케쥴링
2. 새로운 프로세스는 높은 우선순위
3. 실행시간이 길어질 수록 점점 낮은 큐
4. 마지막은 RR 방식

`대칭키 암호화 알고리즘`

1. 암호화와 복호화에 같은 암호 키를 쓰는 알고리즘
2. 단위에 따라 스트림 암호와 블록 암호로 나눔
<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  overflow:hidden;padding:10px 5px;word-break:normal;}
.tg th{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  font-weight:normal;overflow:hidden;padding:10px 5px;word-break:normal;}
.tg .tg-9wq8{border-color:inherit;text-align:center;vertical-align:middle}
.tg .tg-c3ow{border-color:inherit;text-align:center;vertical-align:top}
.tg .tg-0pky{border-color:inherit;text-align:left;vertical-align:top}
</style>
<table class="tg">
<thead>
  <tr>
    <th class="tg-0pky">대분류</th>
    <th class="tg-0pky">중분류</th>
    <th class="tg-0pky">알고리즘</th>
    <th class="tg-0pky">설명</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-9wq8" rowspan="6">대칭키 방식</td>
    <td class="tg-9wq8" rowspan="5">블록 암호 알고리즘</td>
    <td class="tg-0pky">DES</td>
    <td class="tg-0pky">1. 64bit 블록, 128bit 암호화 키<br>2. 16 round</td>
  </tr>
  <tr>
    <td class="tg-0pky">3-DES</td>
    <td class="tg-0pky">1. 암호화 키 2개 사용</td>
  </tr>
  <tr>
    <td class="tg-0pky">AES</td>
    <td class="tg-0pky">1. 128 평문 128 암호화<br>2. 키 크기에 따라 10/12/14 round 수행<br>3. 라운드 키 수 = N + 1</td>
  </tr>
  <tr>
    <td class="tg-0pky">SEED</td>
    <td class="tg-0pky">1. KISA 주관, ETRI 개발<br>2. 국제표준 부합, 민간 사용 목적</td>
  </tr>
  <tr>
    <td class="tg-0pky">ARIA</td>
    <td class="tg-0pky">1. NSRI 개발<br>2. 공공 사용목적, 비밀키 규격 AES 동일</td>
  </tr>
  <tr>
    <td class="tg-c3ow">스트림 암호</td>
    <td class="tg-0pky">RC-4</td>
    <td class="tg-0pky">1. TLS, WEP 사용<br>2. Octec 단위 기반 암호화</td>
  </tr>
  <tr>
    <td class="tg-9wq8" rowspan="2">비대칭키 방식</td>
    <td class="tg-c3ow">인수분해</td>
    <td class="tg-0pky">RSA</td>
    <td class="tg-0pky">1. 큰 숫자를 소인수 분해 하는것 어려움 기반 개발<br>2. 공개키만 가지고 개인키 추측 불가</td>
  </tr>
  <tr>
    <td class="tg-c3ow">이산대수</td>
    <td class="tg-0pky">DSA</td>
    <td class="tg-0pky">1. 이산대수 어려움을 안정성 바탕 개발</td>
  </tr>
</tbody>
</table>