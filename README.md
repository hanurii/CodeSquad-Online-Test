# 2단계: 팀데이터 입력 및 시합 기능 구현

## 2단계 클린 코딩
* 전역변수 사용을 최소화한다.
* 함수(또는 메소드)의 크기는 15줄 이하를 권장한다.
* 함수(또는 메소드)의 들여쓰기는 최대 3단계로 구현한다.

## 2단계 요구사항 1: 팀데이터 입력 및 저장
* 두 야구팀의 팀이름과 선수 데이터를 입력한다.
* 각 팀은 9명의 타자와 한명의 투수로 이루어진다.
* 타자 정보: 순번, 이름, 타율을 저장한다. 타율이란 각 타자가 안타를 칠 수 있는 확률로 타율 h는 0.1 < h < 0.5이고 소수 세째 자리까지 입력한다. (ex: 0.347, 0.120)
* 입력한 팀 데이터에 대한 저장하기 및 출력하기 기능을 구현한다.
* 편의를 위해 에러 처리 등의 기능을 구현한다.

## 2단계 요구사항 2: 시합하기 기능 구현
저장된 데이터를 기반으로 두 팀이 시합하는 기능을 구현한다.

* 1단계에서 입력한 두 팀이 가상으로 시합을 실시한다.
* 시합은 6회까지 진행되며 6회에도 승패를 알 수 없을 경우 무승부로 기록된다.
* 각 회는 회초 / 회말로 나뉘며 회초에는 팀1, 회말에는 팀2의 타자가 경기를 진행하게 된다. 타자가 경기를 진행하는 팀을 이하 공격팀이라고 한다.
* 3아웃이 될 경우 공격팀의 공격이 끝나게 된다. 회초 공격, 회말 공격이 끝나면 다음 회로 넘어간다 (1회초 -> 1회말 -> 2회초 -> ... )
* 타자는 1번 타자부터 차례로 타석에서 타격을 수행하고, 안타 / 아웃시 다음 선수가 타격을 수행한다. 9번 타자 이후에는 1번으로 돌아간다.
* 타자의 타격은 안타 / 스트라이크 / 볼 / 아웃 중 하나의 결과를 갖는다. 타자의 타율을 h라고 할 때 각각의 확률은 아래와 같다.

```

-안타: h, 0.1 < h < 0.5
-스트라이크: (1 - h) / 2 - 0.05
-볼: (1 - h) / 2 - 0.05
-아웃: 0.1

```

* 1단계처럼 세 번의 스트라이크는 아웃, 네 번의 볼은 안타이다.
* 매 회에서 네 번의 누적된 안타는 1 득점으로 이어지며, 이후부터는 1안타당 추가로 1득점이 발생한다.
* 경기 진행상황과 경기의 최종 결과를 화면에 표시한다.
* [11/29 업데이트] 기존 스트라이크와 볼의 확률 계산식에 오류가 있어 / 3 에서 / 2 로 수정하였습니다.