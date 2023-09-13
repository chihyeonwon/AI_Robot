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
