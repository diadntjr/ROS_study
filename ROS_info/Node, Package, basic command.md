# ROS 2 Node, Package, Basic Command

## Node란?
<p></p>
로봇 개발을 하기 위해서는 로봇을 구성하는 여러 <b>센서</b>들, 그리고 이들 센서 데이터를 통해 지속적으로 <b>판단</b>하고 <b>동작</b>해야 하는 시스템이 필요하다.(물론 이 외에 다른 부분들 또한 필요하다)<br>
<img src="https://www.researchgate.net/publication/324568048/figure/fig1/AS:616399525384196@1523972507555/NAO-A-typically-complex-humanoid-robot-system-There-are-as-much-as-versatile-sensor-and_Q320.jpg"><br>

### 예시
<p></p>
자동 혼합곡 생성기라는 로봇을 들고 왔을때, 다음과 같은 과정을 거치게 된다.

1. Button을 통해 작동 모드 설정
2. 각 위치에 배치되어 있는 포토 인터럽트 센서를 통해 쌀을 받을 수 있는 칸이 해당 위치에 도착되어 있는지 판단
    1. 도착하지 않았다면 모터를 구동 판단
    2. 도착하였다면 해당 위치의 곡물 조절기 작동 판단
3. 해당 판단을 통하여 SPI 통신을 이용해 실제 모터 신호 제어 구동
4. 종료 지점까지 도달시, 출발 지점으로 복귀

<a href="https://github.com/diadntjr/Dia_ArduinoAutoMultigrainRiceGenerator">해당 프로젝트 소스파일</a><br>

위의 내용들에서 1,2,3,4 기능을 각각 따로 수행하는 <b>Node</b>들이 존재하며, 이들 사이에 서로 데이터를 주고 받는 구조가 갖추어 진다.

<img src="https://docs.ros.org/en/foxy/_images/Nodes-TopicandService.gif">

## Topic, Service, Action
<p></p>
각 Node들끼리 통신을 하는 방법들인데, 저마다 특징이 존재한다.
