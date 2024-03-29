---
layout: post
title:  "Optimization Problems"
subtitle:   "Repository에 올리기"
categories: Data_Science
tags: Optimization
comments: true
---
---

![image](https://user-images.githubusercontent.com/70193130/189824450-38c155c8-3a83-4426-b902-05fb1c5c073f.png)
+ 목적함수를 설정하고 함수에 max값 또는 min값을 찾아가는 과정 
+ 최적화 모델의경우 목적함수를 최대화 또는 최소화하는 동시에 조건을 만족시켜야함
![image](https://user-images.githubusercontent.com/70193130/189824469-8d3f437d-b7ad-4fba-9ea9-01a0665dbf0f.png)
+  담을 수 있는 최대 무게가 정해진 배낭과 함께 각각의 무게와 가치가 주어진 아이템의 집합이 주어짐
+ 배낭에 담은 아이템들의 가치의 합이 최대가 되도록 하는 아이템들의 부분집합을 찾는 문제
![image](https://user-images.githubusercontent.com/70193130/189824480-a5623f65-3ee0-45e5-b4cc-2a56aa003220.png)
+ 벡터 V는 아이템의 사용유무를 알려주는 벡터 (만약 아이템i를 사용했다면 V[i]=1)
+ 벡터 I는 아이템의 value와 weight정보가 들어있는 벡터
![image](https://user-images.githubusercontent.com/70193130/189824489-3b68d2cd-eda7-42f2-83b2-fe1101db8486.png)
+ 배낭문제의 예시를 들어보자
+ 음식의 따른 선호도가 존재한다.
+ 음식에는 칼로리가 있으며 최적화 조건을 칼로리로 설정한다.
+ 조건을 만족하면서 선호도가 가장 높게 합이 설정된 set을 구한다.
![image](https://user-images.githubusercontent.com/70193130/189824496-8ae600c0-4346-4c94-8fd1-bca35f2ba42e.png)
+ value는 선호도를 의미 
+ 각 음식에는 해당하는 칼로리가 표시
![image](https://user-images.githubusercontent.com/70193130/189824503-50cdf433-8c16-4ffd-b8f0-0ad80a85c2b4.png)
+ 배낭문제를 Brute Force 알고리즘으로 조합이 가능한 모든 아이템 set을 구한 후 가장 최적의 결과를 구하는것이 정확하겠지만 계산량의 문제로 좋은 방법은 아니다.
+ Greedy알고리즘으로 구하는것은 최적의 결과를 항상 보장해주는것은 아니지만 근사값을 구할 수 있다.

![image](https://user-images.githubusercontent.com/70193130/190043476-72299ad3-ebb1-4d1f-b377-a648d3f4b8f9.png)

+ Greedy알고리즘이 복잡도의 효율성은 NlogN이다
+ 정렬을 퀵 정렬을 사용(NlogN)+for문(N)