# AI_Robot
컴퓨터공학과 인공지능 및 로봇실습 정리입니다.
## 모의담금질 알고리즘
![image](https://github.com/wonchihyeon/AI_Robot/assets/58906858/4c7da6a3-e75a-419c-8607-ac841562c75c)
```
높이가 최대인 구간을 구하는 것이 목표
욕심쟁이 알고리즘 - hill climbing 알고리즘 - Greedy 문제점을 해결한 알고리즘 - 높은 곳으로 가기 위해서는 낮은 곳을 거쳐야 한다.
```
![image](https://github.com/wonchihyeon/AI_Robot/assets/58906858/4bc07e46-f758-4917-9cc9-994c9e852a61)
```
Temperature가 높을수록 확률이 낮아짐
```
![image](https://github.com/wonchihyeon/AI_Robot/assets/58906858/4a418a0c-844a-4a8b-9f6f-f38ce32be34f)
```
current solution energy 10개
working solution energy 변형을 가했더니 20개로 나빠졌다. grid algorithm이였다면 버려야 하는데 담금질 알고리즘에서는 한번의 기회를 더 준다.
확률을 계산. 온도가 50도인 상황에서의 확률을 계산한다.
10-20 = -10 (working-current) 지수함수(-를 붙여서 아래로 내려오는 그림) -> 0.818731의 확률 (0에서 1중에 0.8은 높다) 80%

current solution energy 3 working solution enery 7
3-7=-4 온도를 2도로 낮췃더니 확률이 0.1로 낮아졌다.(energy conflict 충돌이 줄어듬) 확률이 낮아졌다.

current solution - working solution energy 개수가 많아져서 상황이 나쁘지만 온도를 낮췄더니 확률이 더 낮아졌다. 10%

current 3 working 7 3-7 = -4
온도가 50
```
![image](https://github.com/wonchihyeon/AI_Robot/assets/58906858/1e938373-f377-49ab-bb51-597a80f1cb14)
```
max_length // 여왕의 수 30
energy 0 -> 0.5
initial temperature 30.0
final temperature 0.5
alpha 0.99 온도를 한번 낮출 때 0.99씩 낮춘다
sters per change 30도부터 100번 낮춘다.

tool dev c++
```
## 23.09.19 ART(적응적 공명 이론)
![image](https://github.com/wonchihyeon/AI_Robot/assets/58906858/034e1224-ea5c-4fcb-909e-a9f004c7526d)
```
ART1이 처음에 나오고 많은 변형된 알고리즘이 나왔다.
학습알고리즘 (지도(supervise)학습, 비지도(unsupervise)학습, 강화학습())
생물에서 동기를 얻었다.

ART1은 비지도(unsupervise)학습이다.
추천 시스템에 적응적 공명 이론을 적용한다.

클러스터링 알고리즘
유사한 것들을 모아서 비슷한 것들을 모아서 나눈다.
나눈 것들에 이름을 붙인다.
분류하는데 사용한다.(지도학습-> 답이 정해져있다)
몇덩어리로 묶느냐는 문제에 따라 달라지는거(답이 X 비지도학습)

이미 알고있는 거랑 다른 것이 나타나면 새로운 것인 것으로 안다.

1이면 구매한거고 0이면 구매안한거다

고객이 구매한 물품을 분류해서 구매 패턴이 들어가있다.
비슷한 물건을 구매한 사람들을 묶어낸다. <- 추천 시스템에 사용될 수 있다.
키-몸무게 데이터를 쉽게 얻을 수 있다. 클러스터링을 적용
small medium large로 이름을 붙여서 구매전략을 짤 수 있다.

prototype vector 초기 값을 임의로 생성
다른 각각의 예가 초기 벡터랑 비슷한지 비교

vigilance test 각성 테스트

클러스터의 개수는 적어지고 덩어리는 커진다.
클러스터의 개수는 많아지고 덩어리는 작아진다.

덩어리로 묶는 일을 계속할 것인가? more prototype 덩어리의 크기를 결정
NO -> 클러스터의 개수를 생성(다른 덩어리를 생성)

첫 번째 프로토타입 벡터는 첫 번째 고객을 쓰거나 랜덤하게 선정한다.
P prototype E example d 전체 품목의 개수

Prototype 10개가 있는데 example이 얼마나 비슷(Similar = proximty)한지 비교
(3.3)덩어리의 크기를 결정하고 (3,2), (3,3) 두 개의 테스트를 만족하면
프로로타입의 모형을 변경(다른 덩어리를 생성)

(3,4) 다른 덩어리를 생성한다. (새로운 멤버가 들어올 때마다 프로토타입을 갱신)
갱신하게 되면 문제가 발생한다. 이전에는 멤버에 속하지 않았던 것이 멤버에 속해지는 것이
가능해진다.

클러스터의 특징을 강화한다. 멤버를 왠만하면 비슷한 것으로 할지 아니면
특징을 크게 구분할 것인지 결정

p1이랑 e는 비슷하다 베타는 1.0으로 신경x 로우값이(클러스터의 크기를 결정 0.9)

proximity test 같은 데 1로 같은 거의 개수를 센다 (P0 n E)
vigilance test 로우값이랑 비교

p1 and ex 원래프로토타입과 새로고른 것을 and 연산


```
