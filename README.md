# AI_Robot
컴퓨터공학과 인공지능 및 로봇실습 정리입니다.
[컴파일러사이트](https://www.onlinegdb.com/)
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
## 23.09.27
![image](https://github.com/wonchihyeon/AI_Robot/assets/58906858/1f409057-8a59-4af5-a8ce-73fbf4cb4b29)        
![image](https://github.com/wonchihyeon/AI_Robot/assets/58906858/c8d3e415-ad13-4651-ad00-b45ac7e2afa3)     
```
TSP (Traveling Salesman Problem) <- 최단 거리를 찾는 데 조건 모든 노드를 한 번씩만, 중복 x
거리의역수 거리가 짧아지면 좋아짐짐

max CITIES <- 노드의 수
max distance <- 거리

노드의 수 만큼 랜덤하게 생성 -> 어떤 직선 경로로 이동했을 때 거리가 작을 것인가.

만든 순서대로 가봐라 cities(생성순서) -> 최적화 -> soluction best, 최적화 경로
```
##23.10.11
#### 다층 신경망 학습(1. 출력 계산, 2. 역전파(학습)
![image](https://github.com/chihyunwon/AI_Robot/assets/58906858/166c5cc4-98fb-4210-84dd-12e00f936533)
#### 역전파(학습) 알고리즘 
![image](https://github.com/chihyunwon/AI_Robot/assets/58906858/a2781b29-cbfb-48fd-a53b-10c1ae8ff0f9)

```
신경망학습은 1. 출력계산(feed forward), 2. 그 결과를 가지고 학습하는 두 단계로 나뉜다.
출력계산, 학습

전진전파의 결과로 가중치를 수정하는 역전파 단계

0.0이나와야하는데 0.5097이라는 결과가 나왔다. 오차를 계산하고
가중치를 수정하는 단계를 거친다.

역전파도 두 단계로 나뉜다.
계산할 때 화살표가 들어오는 것

입력층 -> 중간층 -> 출력층 (다층 신경망 학습)
출력층 -> 중간층 -> 입력층 (역전파 학습) 

1. 출력층 중간층 사이의 가중치 수정

2. 중간층에서 입력층 가중치 수정
```
[Playground.tensorflow](https://playground.tensorflow.org/#activation=tanh&batchSize=10&dataset=circle&regDataset=reg-plane&learningRate=0.03&regularizationRate=0&noise=0&networkShape=4,2&seed=0.17816&showTestData=false&discretize=false&percTrainData=50&x=true&y=true&xTimesY=false&xSquared=false&ySquared=false&cosX=false&sinX=false&cosY=false&sinY=false&collectStats=false&problem=classification&initZero=false&hideText=false)    
![image](https://github.com/chihyunwon/AI_Robot/assets/58906858/a795c442-1d1e-4c49-8a35-43597cca62eb)     
![image](https://github.com/chihyunwon/AI_Robot/assets/58906858/50a6c9c9-4367-4d48-900b-38962b8d9bc9)    
``` 
x1 -1.5
x2 0.01

신경망의 구조 (입력층, 중간층, 출력층) 모델 설계
layer의 개수, 뉴런 개수를 정해서 코딩

학습을 하려면 중간층이 있어야 가중치값과 계산

층에 뉴런을 추가하면 더 오차가 낮아진다.

0에 가까울수록 영향이 없어짐

정보전달양이 학습으로 드러난다
```
## Evolving GAME AI Behaviors
![image](https://github.com/chihyunwon/AI_Robot/assets/58906858/9f2856f3-936f-4c11-8f53-c3564cd72889)
```
게임 AI가 동작을 정해야 해야 할 때 신경망 알고리즘 응용하여 적용한다.

입력에 따라 동작을 결정할 수 있다..

Input Neurons (네모)
hidden neuron 중간 뉴런(동그라미)
output Neurons 출력 뉴런(동그라미)

선을 긋는 데 핵심 : 하나의 뉴런은 다음 층의 모든 뉴런에 연결이 된다.

feedforward, backprop(역전파)
```
![image](https://github.com/chihyunwon/AI_Robot/assets/58906858/6c09a55b-68f2-4bb0-b415-8ed88bc4c466)
```
sigmoid
val <- 입력*가중치의 sum 합

mse error
입력값에 따른 결과값은 sample data와는 다르다.

```
![image](https://github.com/chihyunwon/AI_Robot/assets/58906858/b5d80d7f-8420-4617-82c9-60583256bb32)

```
강화 학습 유전알고리즘

1. 모집단(답을 모아놓음) 문제를 인코딩
2. 프로그램(명령어 instruction)을 만든다 단순한 알고리즘을 나타내는
3. 탐색알고리즘이면서 최적화알고리즘이다. 자연의 진화 현상을 흉내낸

진화론은 발전이 아니라 환경에 대한 변화다.

적합도 평가하고 natural selection 선택

맛의 점수를 다 더하고 그 중 점수로 나눠서 7/31 = 0.23

유전연산 : 교차 crossover, 돌연변이 mutation

돌연변이 <- 낮은 비율로 부정적인 결과를 얻는 경우가 많다.

라면번호=재료를 이진법
```
## 23.10.18

```
스택머신 <- 주소가 없이 데이터를 넣고 뺄 수 있는 스택이 있다.
가상 컴퓨터(소프트웨어)는 레지스터가 없고 스택이라는 메모리만 있다. 스택에 있는 데이터만 처리(계산)한다.
이 컴퓨터가 실행할 수 있는 프로그램은 많이 없지만 성능은 비슷하다.

유전 알고리즘을 프로그램을 만드는 데 응용하겠다
이 프로그램은 우리가 사용하는 일반적인 컴퓨터에서 돌아가는 것이 아니라 스택머신(가상 컴퓨터)에서 사용할 수 있는
프로그램을 만들어보겠다.

DUP 복사, SWAP 교환, ADD 합, MUL 곱, OVER 밑 복사 아래에 있는 것을 올려둔다. , NOP 더 이상 실행할 명령어가 없다.

DUP 스택 맨 위의 값을 하나 빼서 복사한다음 다시 넣는다.
CPU가 명령어를 보고 스택의 값을 바꾼다.

OVER A B <- B A B 탑이 A였는데 A밑의 B를 복사해서 A위에 올린다.

명령어 배열에 숫자로 매칭한 명령어들을 넣는다. 0->DUP, 1->SWAP ~
명령어에 숫자를 붙인다.

배열이라 길이가 가변적이다.

명령어의 배열을 교차, 돌연변이한다.
교차, 돌연변이의 부분을 무조건 랜덤

프로그램: 명령어의 집합(배열)이 있으면

x의 8승을 계산하는 프로그램을 만들어봐라. 만든 프로그램이 실제로 x의 8승을 계산하는 지 적합도를 판단한다.

스택 맨위의 값 3 -> DUP MUL DUP MUL -> 3 * 3 * 3 * 3 8번

DUP MUL DUP MUL DUP MUL -> DUP3 MUL3
3의2승 * 3의 2승 -> 3의 4승 3의 4승 -> 3의 8승
```
![image](https://github.com/chihyunwon/AI_Robot/assets/58906858/d25377fa-8c2f-4e81-9a1a-9e7f7882b987)
```
문제가 달라지면 문제에 대응되는 값을 다르게 해야한다.

result의 argument의 개수를 꼭 넣어줘야 한다.
x, y, z 입력이라면 3개를 넣어줘야한다.
```

23.11.07
## Artificial Life 인공생명
[the nature of code](https://natureofcode.com/book/)
[processing 언어](https://www.processing.org)
![image](https://github.com/mr-won/AI_Robot/assets/58906858/5d3f4b9b-1831-4680-92d5-42cfa546c909)   
```
보이드(boids) 알고리즘

the nature of code : 코드의 본질

Flocking
도넛 토러스

무리를 왜 지어서 이동하는가?
적당하게 따라가면서 피해야함

alignment 진행 방향을 설정

separation alignment cohesion 세 벡터의 합

sep.mult(1.5); < 숫자는 비
ali.mult(1.0);
coh.mult(1.0);

size 화면크기
i<200 <- 200마리

1. 규칙은간단하다.2. 지역룰local rule

gamee of life 규칙
각 세포는 ‘죽어’ 있거나 ‘살아’ 있는 두가지 상태 중 한가지 상태를 갖는다
죽은 세포의 이웃 중 정확히 세 개가 살아 있으면 그 세포는 살아난다(‘태어난다’).
살아 있는 세포의 이웃 중에 두 개나 세 개가 살아 있으면, 그 세포는 계속 살아 있는 상태를 유지하고,
이외에는 ‘외로워서’, 또는 ‘숨이 막혀서’ 죽어버린다.

살아있는세포 이웃에 4개 -> 인구밀집 죽어버림

이웃-> 내 주위에 8공간
```
## 23.11.08
```
인공 생명은 행동 합성에 중점을 두겠다. 컴퓨터 내에 합성해서 만들어 냈다.

행동 합성은 동물이 어떤 식으로 간단하면서 인공적으로 만들어진 상황에 따라서 행동하느냐에 대한 연구이다.
합성된 인공생명체들이 나름대로 의사결정을 내리고 의사결정하는 방법을 스스로 배워서 진화해 나가는 형태이다.(유전알고리즘을 포함)
```
## 23.11.14
![image](https://github.com/mr-won/AI_Robot/assets/58906858/d0fb067d-33a1-4209-b831-107e5398073b)    
![image](https://github.com/mr-won/AI_Robot/assets/58906858/a16c964a-56f2-4497-92aa-88acd1fad0b1)    
```
먹이사슬

식물은 움직이지 않는 것이라면 초식동물(herbivores)은 자기가 살아가는 환경을 감지하면서 살아간다.
육식동물도 마찬가지인데 육식동물(Carnivores)은 초식동물을 먹는 것으로 가정한다.
육식동물은 한동안 먹지않고도 살아갈 수 있지만 기아현상으로 굶어죽을 수 있다.
음식을 많이 섭취하면 새로운 새끼를 낳는다.(재생산)

재생산과정에서 사용되는 유전연산은 돌연변이이다.(교차는 사용하지 않는다.)
풀은 생명으로서의 대접은 못받고 초식동물은 먹이도먹으면서 도망쳐야한다.

이 세계에서 어떻게 살아남아야하는 지에 대한 전략이 없다. 
어떻게 predator에게 피해야하는 지 모른다. 이 모든 세부사항은 경험에서 배운다. 간단한 환경에서

물체들이 살아가는 공간은 toroid 도너스 그리드형태의 공간이다.
토너스 세계는 원환체 환경이다.

Agent는 하나의 간단한 시스템이다. 외부에 들어온 입력에 대한 판단을 한 후에 행동을 취한다.

Agent는 세 개로 구성되어있따. 뇌, 인지, 행동, 반응하지 않으면 의미없다.
재생산을 통해서 부모가 가지고 있는 것을 물려준다.

Sensor
Agent에서 풀은 빠진다.(food 취급)
감지(Sensor)하고 행동하는(Actual)

Agent가 바라보는 영역은 front, left, right하고 4칸 Proimity 인접영역으로 받아들인다.
보는 방향에 따라서 달라진다. agent가 left를 보고 있으면 left가 front가 된다.
인접영역에 있을 때 먹을 수 있다.

1. proximity 2. front 3. left 4. right

실제세계에서 가장 중요한 개념이 locality다. 

감지할 수 있는 것이 12개이다. front, left, right에 초식동물,육식동물,식물이 있나 없나를 세보니
12개의 상태를 체크한다. 개수는 상관없음

Actuators 모터나 펌프같은 것

환경에 대해서 자기가 보고 있는 방향으로 한 발 앞으로 가는 것
왼쪽이나 오른쪽으로 방향을 바꾸는 것

proxmity 인접 영역에 식물이나 초식동물이 있으면 육식동물이 뇌에서 판단하고 먹을 수 있다..

Brain Agent 뇌 영역

게임환경에서 사용하는 유닛은 finite automata 유한 상태 기계를 사용한다.
하지만 신경망에서는 사용하지 않는다.

게임환경과는 다르다.

눈은 딴건 안보고 영역 중에 초식동물이 front 영역에 있나 없나 본다. 있으면 1을 보내고 없으면 0을 보낸다.
영역 중에 육식동물이 front영역에 있나 없나 본다. 있으면 1 없으면 0
영역 중에 풀이 front영역에 있나 없나 본다. 있으면 1, 없으면 0

다음 세 개 왼쪽, 다음 세 개 오른쪽, 다음 세 개 인접영역

front에 육식동물이 있고 right에 초식돔울이 있다면 그 결과는 010 000 100 000
front, left, right, proximity

뇌가 100억개 12 * 4 = 48 출력은 4개를 정한다.
turn left, turn right, move, eat 12곳에서 영역을 받아들여서 숫자들이 써져있다. 가중치기 때문에
첫번째 들어오는것 0 x 1, 다음 꺼 1 x 1 = 1 가중치와 곱한다. 양수면 행동을 해라 음수면 행동 하지마라

유전알고리즘을 이용한다.

bj + < bj 는 바이오스 인풋
ui 12곳의 입력값(0과 1),  sum the product 곱한 다음(ui*wi) 더한다.(j+wiui)

ui는 외부의 입력 wi는 사람마다 가지고 있는 환경이 가지고 있는 외부 입력의 정도는 사람마다 제각각이다.(가중치)
bj <- (바이오스 인풋) 마음의 소리에 대한 가중치 입력은 아님

책에서 마음의 소리는 bj

가중치에 따라서 똑같은 입력을 받더라도 결과가 다를 것이다. 이 가중치는 랜덤하게 결정된다.

agent action selection
winner-takes-all 승자독식 제일 높은 결과치를 취하여 행동을 취한다.
문제는 동점이 발생할 수 있다.

energy and metabolism 에너지와 신진대사
agent들은 환경에서 적절한 에너지를 섭취하면서 살아가는데 에너지가 바닥이 나면 agent는 없어진다.
매 시간 마다 각 agent의 에너지를 체크하여 0이된 agent는 제거한다.

에너지를 발생하는 것 : eating other object 다른 물건을 먹어서
먹이 활동은 일정한 규칙을 가진다. 먹이사슬의 정해진 규칙에 따라서 육식->초식->풀

중요한 점은 먹기만하면 에너지가 계속 쌓이기만 하는 것은 아니다.
살아가는 동안 일정한 비율의 에너지를 소비하면서 살아간다.

육식동물은 세월이 지날 때마다 1단위로 에너지가 줄어든다.
초식동물은 세월이 지날 때마다 2단위로 에너지가 줄어든다.

이것은 초식동물이 육식동물에 비해 살아남기 위해서 2배의 food 영양소를 섭취해야 한다.

반면에 육식동물의 먹이인 초식동물은 도망갈 수 있다는 점에서 불리하다.
초식동물은 가만히 있는 풀을 먹기만 하면 되니까 먹이를 얻기 쉽다. 풀이 도망가지는 않지만 다가오지도 않는다.
육식동물의 입장에서 초식동물은 다가올 수도 있고 도망갈 수도 있다.

재생산

agent가 충분한 에너지를 섭취해서 Agent가 에너지를 얻을 수 있는 최대양의 90%가 되면 새끼를 나을 수 있다.
충분을 가진 두 agent가 무성생식을 하도록 한다.

새끼를 나았을 때 가중치를 수정한다. 무작위로 바꾼다. agent가 살아남을 수 있는 능력을 그대로는 아니지만 물려준다.

재생산에서 대가는 없을 수가 없다. it is not without consequences.
새끼에게 에너지를 공유해야 한다.
진화의 속도조절용 시계역할을 한다.<-에너지를 보충하고 공유하여 에너지를 감소시키는 행위는

Death

먹히면 죽는다. 육식동물은 굶어죽는 일이 발생한다.
굶어죽거나 먹혀서 죽거나

Competition

시뮬레이션 동안에 강력한 생존경쟁이 일어난다.
육식동물은 초식동물 쪽으로 다가가서 사냥하는 행위에 대한 요령이 생긴다
동시에 초식동물 또한 먹이를 잘 찾으면서 동시에 육식동물을 피하는 행위에 대한 요령이 생긴다.
이런 경쟁관계가 컴퓨터 프로그램 시뮬레이션을 만들어서 전략들을 통찰해볼 수 있다.
```
## 추가교재안(2)

![image](https://github.com/mr-won/AI_Robot/assets/58906858/12c65fe1-6ba8-445f-af8d-2719e720cea2)    
![image](https://github.com/mr-won/AI_Robot/assets/58906858/e53e2736-9d6f-418f-87dc-392feb12e576)   
``` 
Sample Iteration

꽤 학습이 되어서 잘 살아남은 Agent는 어떻게 액션을 선택하는 지를 반복해서 들여다 보겠다.
설명하고자 하는 예로는 300살 동안 살아남은 초식동물의 생존에 대한 선택방식을 분석하겠다.
생존에 대한 선택방식: 풀을 잘 먹으면서 육식동물 포식자를 피하는 지에 대해
default값은 100살 

뇌를 열어봤더니 뇌가 오른쪽거

input 값과 행동에 대한 가중치 값을 곱해서 구한다.

바이오스 1 0 1 0

7.7에서 풀을 뜯어먹음 eat 1
7.8 풀을 뜯어 먹어서 풀이없음, 바이오스, 뇌하고 입력만 달라짐 입력의 마지막 풀이 있는 상황이 아님

결과적으로 먹이를 찾기 위해 왼쪽으로 행동하는 행동을 하게된다.

```
## 23.11.21
#### 인공생명 코드 설명
```
세상의 크기 30 MAX GRID 30X30 900 칸 중에
MAX_PLANY 35 35군데에 풀
MAX_AGENTS를 36

만년 돌아가는동안 최고령자를 max age 초식: 89 육식 : 173
마리수 9 9, repro 53, 137, gen 새끼를 낳은 수

두 종족의 최고령자들의 뇌를 파일에 저장
위에꺼 89살 먹은 초식동물 뇌의 가중치 눈 12개 각각에 관해서
Left 12
Right 12
Move 12
Eat 12
```
#### 규칙 기반 전문가 시스템
```
뇌의 두정엽이 활성화됨

사례에 대한 설명

기호주의(논리), 연결주의(계산)
기호만 가지고는 안되서 knowledge 지식을 붙였다.
지식을 컴ㅍ터 안에 넣는다. 데이터를 저장하는 방법은 정해져있다.(변수)
지식이라는 것은 어떻게 컴퓨터 안에 넣을까에 대한 연구

if-then 지식을 묶어서 표현해야 한다-> 객체지향 방법론 대두
지식이 너무 많아서 만들 수가 없다.

돌파구 -> 특정한 일을 잘하는 전문가 시스템을 만들자

인공지능 역사 중 최초의 상업적인 인공시스템이 된다. ai의 붐
알파고 -> 바둑만 잘두는 전문가 시스템

지금의 ai 회사가 갖춰야 할 것 -> 분야의 전문 ai 시스템
chatgpt -> 전문가 시스템을 극복, 능가하는 시스템

규칙에 기반한 전문가 시스템

기호주의 ai 시스템에서 지식 기반 시스템이 탄생했다.

지식을 가중치로 저장

지식(규칙)

전문가 시스템은 3가지로 구성되어 있다.
working memory 정해진 사실을 저장함 -> 디스크 
rule memroy 규칙을 저장함(knowledge base) -> 보조메모리 같은 느낌
inference engine 추론 엔진(Logic)

정해진 사실을 보고 추론엔진이 규칙을 찾는다. 이 행위를 match resolve fire라고 한다.
사실과 규칙의 matching
if(사실) then 규칙

사실 -> 규칙 적용 -> 사실이 변화 -> 변화된 사실에 맞는 규칙 적용
매 순간마다 사실과 규칙을 찾는 매칭작업(추론 inference)을 한다.

추론 방향에 따른 분류

forward chain(연쇄) 전방향 추론
새로운 사실 생성

역방향 추론-> 규칙을 보고 사실을 추론 -> 거꾸로 실제 사실을 추론해서 추론의 결과가 나오는 지 본다.

추론 전략에는 두 가지가 잇다. 역방향 추론은 가설(목적)으로부터 실행된다. 

지금의 병원시스템은 역방향추론 환자가 암인 것을 증명해야 한다.

전방향과 역방향 추론과의 관계

전방향 추론 : 몇개의 지식을 넣으면 여러 개의 사실이 발생한다.
역방향 추론 :사실을 알기위해서 여러개의 규칙을 알아야한다.

현실세계에서는 양방향 추론을 해야한다.(by directional chaning)

추론엔진에서 하는 일들으 세부적으로 설명 다음시간
```

## 23.11.22

```
규칙을 실행한다. 피철철 사실에 대해서 규칙을 실행(fire)적용한다. -> 피철철이라는 사실이 없어지고 새로운 사실이 발생한다.
이전에 사실은 없어진다.

그림으로 나타내지만 컴퓨터에 데이터는 연결리스트로 표현한다.

사실에 기반한 적용을 규칙하려고 새로운 사실들을 추가한다.

if 사실 and 사실 and 사실 then 규칙

working memory에 추가

프로그램 소스
c언어
(defrule bird-test
 (has-feathers ?) <- 깃털이 있으면
=>
 (Bird ?) <- 새다.
)
if (has-feathers ?) => then (bird ?) 깃털이 있으면 새다.


젖먹이를 하면 포유류다.

ungulate-test1 말굽동물이냐
사실이 두 개 mammal, chews-cud 포유류면서 되새김질을 한다면 말굽동물이다.

포유류면서 hoofs(말굽이 있으면) 말굽동물이다.

Fault Tolerance 장애 허용(결함 포용) <- 시스템
 
오류가 발생했을 때 시스템이 다운되지 않고 견뎌내는 것

지식을 규칙의 형태로 나타내는 단순한 시스템

블랙보드 시스템 아키텍처 agent들이 돌아다니다가 다른 agent들과 통신하기 위해서
blackboard에 데이터를 던짐 전체적으로 볼 수 있음

입력을 받아서 출력을 내는 시스템이 있다 하자. 센서가 두 개라면 한 센서가 망가져도 다른 센서로
작동하게 하여 시스템의 다운을 막는다.(교체)

망가진 센서가 정상적인 센서로 바뀌면 다시 그 센서로 작동하도록 한다.

규칙을 적용해서 새로운 지식이 적용되도록 한다. 사실을 바꾼다.

규칙을 바꾸면서 새로운 전문가 시스템을 만든다.

working sensor1, working sensor2 정상적인 센서가 2개 작동하고 있다.
스위치를 넣기 전이기 때문에 mode는 failure 상태이다.
timer 인덱스 10초동안 시간을 걸어놓는다. 10초가 지나면 이벤트가 발생한다.

규칙을 한 번만 적용되게 한다.
규칙을 읽는 방법
(sensor-failed) 센서1 또는 센서 2가 망가진다.
-> 작동중이던게 망가진다라는 뜻이기 때문에 working, failed 라고 표현한다.

working 메모리에서 날려버려야 한다. 작동하고 있던 센서를 메모리에서 날려버려야 한다.
->delete (sensor-working) 지식에서 없애버려라.

check-active : 활성화된 시스템
-> 망가졌다와 비활성화는 다른 개념이다.

sensor-active 활성화 중인 센서가  망가졌다.
-> 정상적으로 돌아가고 있는가? No -> 센서를 교체한다.
delete sensor-active 활성화 중인 센서를 없앤다. 메모리에서 없앤다. active인 상태가 없으니까
워킹메모리를 non-active상태로 만든다. add(sensor-active none)

make-working(active) : 센서를 active로 만든다. 
액티브된 센서가 없으면서 working 센서가 있으면. sensor-active none, sensor-working
활성화된 상태인걸 넣고 (add sensor-active)
시스템상태를 실패에서 정상으로 고친다.(delete failure, add normal)
비활성화된 센서를 없앤다. (Delete sensore-active none)


센서가 두 개 다 고장나면
failure 정상적이면서 액티브된게 없다(둘다 고장) -> 방법이없다면
mode를 실패로한다. 안전이니 정상인 상태를 없애고 기다린다.

주기적으로 문제를 일으킴 순환적

timer-triggered 1 <- 시계 인덱스 1 1-10 첫번째 시계가 트리거된 경우
첫번째 시계가 하는 일 -> 1번 센서를 고장냄
add sensor failed sensor1 1번센서가 고장났다라는 사실을 추가한다.
두번째 시계를 시작한다. enable timer 2 10 -> 10초후에 시간이 다되면 trigger2가된다.

첫번째 트리거에서 1번센서를 망가트림
두번째 트리거에서 1번센서를 수리한다.
세번째 트리거에서 망가졌던 1번센서가 고쳐져서 working상태가 되었다.
망가진 센서1의 상태를 지우고 센서1을 할당한다. 4번째 시계를 작동시킨다.

4번째 시계는 2번센서를 수리해서 2번센서가 사용가능한 working상태가 되었고
센서2를 할당한다.

트리거 4에서 1번 타이머를 실행시킨다. 결과 -> 1->2->3->4->1->2->3->4->1->2->3->4

이 프로그램을 수정하고 싶으면 시계를 랜덤하게 하거나 변경한다.

































```




