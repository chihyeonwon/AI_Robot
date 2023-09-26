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
[K-means 알고리즘 K-평균 알고리즘](https://ko.wikipedia.org/wiki/K-%ED%8F%89%EA%B7%A0_%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98)   
![image](https://github.com/wonchihyeon/AI_Robot/assets/58906858/6659a26e-9eef-470c-8ba2-a42fbae08cc0)    
```
k-평균 클러스터링 알고리즘은 클러스터링 방법 중 분할법에 속한다.
 분할법은 주어진 데이터를 여러 파티션 (그룹)으로 나누는 방법이다. 예를 들어 n개의 데이터 오브젝트를 입력받았다고 가정하자.
이 때 분할법은 입력 데이터를 n보다 작거나 같은 k개의 그룹으로 나누는데, 이 때 각 그룹은 클러스터를 형성하게 된다.
다시 말해, 데이터를 한 개 이상의 데이터 오브젝트로 구성된 k개의 그룹으로 나누는 것이다.
이 때 그룹을 나누는 과정은 거리 기반의 그룹간 비유사도 (dissimilarity) 와 같은 비용 함수 (cost function) 을 최소화하는 방식으로 이루어지며
이 과정에서 같은 그룹 내 데이터 오브젝트 끼리의 유사도는 증가하고, 다른 그룹에 있는 데이터 오브젝트와의 유사도는 감소하게 된다.[7]
 k-평균 알고리즘은 각 그룹의 중심 (centroid)과 그룹 내의 데이터 오브젝트와의 거리의 제곱합을 비용 함수로 정하고,
이 함수값을 최소화하는 방향으로 각 데이터 오브젝트의 소속 그룹을 업데이트 해 줌으로써 클러스터링을 수행하게 된다.

개인 맞춤형 추천 시스템Personalization

시간이 구매자들에게 중요하다. 소비자의 행동을 결정짓는 요소이기 때문이다.
```
## Sum Vector
![image](https://github.com/wonchihyeon/AI_Robot/assets/58906858/2b03837d-07e4-4c0f-9703-54b9d34a9c9f)      
![image](https://github.com/wonchihyeon/AI_Robot/assets/58906858/d340a645-ee23-40f0-8d07-32a2d9c98723)    
```
sum vector
u, v, w 소비자들이 100% 같을 순 없다. 각 품목에 있는 1의 개수를 더한다.

직관적으로 가지고 있는 소비자에게는 추천해주지 않는다(3). <- 후속 모델이 나오면 보내준다.
숫자가 적은 소비자에게는 바로 추천해준다(0)

sum vector를 흝어가면서 
```
## 23.09.26 개발일지
#### Ant Algorithms
![image](https://github.com/wonchihyeon/AI_Robot/assets/58906858/ac34c7ee-fdc3-4f58-aa84-dce520ce944d)     
![image](https://github.com/wonchihyeon/AI_Robot/assets/58906858/cf4faa7b-f2e4-4726-af74-8022aa8b5f79)    
## 길이
![image](https://github.com/wonchihyeon/AI_Robot/assets/58906858/987f3284-805f-4e57-bf9d-addb66f02de2)   
![image](https://github.com/wonchihyeon/AI_Robot/assets/58906858/ea7d600e-5617-4d2f-8768-ee3e5b5f2ab9)

```
stigmergy 낙인찍다

Pru (r에서 u로 가는 데 확률) : 경로의 길이를 알 수 있다. 페로몬의 양이 같을 때 짧은 길로 가겠다.
(r,u)<- 인덱스는 없어도 된다. 거리가 낮을 수록 좋다. 거리의 역수 L분의 1
알파, 베타는 튜닝을 위한 계수다. 계수로 어디에 중요성을 둘지를 결정한다. 초매개변수

앞에꺼가 페로몬양 뒤에꺼가 거리

로우 = 0.6 페로몬의 양이 60%씩 줄어든다.

u1 = 10, u2 = 20 10분걸리고 20분걸린다.

Q/L Q= 상수 10
```
