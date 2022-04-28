---
layout: post
title:  "Convolution"
subtitle:   "Repository에 올리기"
categories: GNN
tags: Spectral GCN
comments: true
---

## 컨볼루션의 개념
---
+ 누적된 반응을 계산하는것
+ 시간에 따라 신호간의 비슷한 정도를 나타내는것


![Alt Text](https://upload.wikimedia.org/wikipedia/commons/6/6a/Convolution_of_box_signal_with_itself2.gif)

![image](https://user-images.githubusercontent.com/70193130/165222729-4052da63-38bf-4b72-81ce-6dac14e4247c.png)
## 이산 컨볼루션
---
![image](https://user-images.githubusercontent.com/70193130/165223800-5a6a7d46-b279-4dd2-8dc8-b1dd0c226269.png)
+ 델타함수: 0에서는 1의 값을 출력하고 다른 모든곳에의 출력은 0이다.
![image](https://user-images.githubusercontent.com/70193130/165223822-449080c6-a6aa-4adb-9422-072fc0c22492.png)
<image src="https://user-images.githubusercontent.com/70193130/165223878-2b8ec4f1-ea60-4d32-8ee6-8f0bd2ed8436.png" height=120>

+ 임의의 시그널 x[n]을 단위 임펄스함수 델타[n]으로 분해하여 표현 할수 있다. 
+ x[k]는 함수가 아닌 x시그널의 함수값이니 상수값으로 생각하여 상수가 곱해진 신호의 합으로도 볼수 있다.


<p align="center">
  <image src=https://user-images.githubusercontent.com/70193130/165712944-fc8e5530-9319-482f-a702-dd607f9f2c2d.png>
</p>

+ (3)번의 식을 위와같이 쓸 수 있다. 
+ h[n]은 델타함수의 선형변환이다->LTI 시스템->임펄스 응답이라고도 하며 컨볼루션 시스템에 입출력에 관계를 표현
<p align="center">
  <image src=https://user-images.githubusercontent.com/70193130/165715571-949d3d36-b338-44ba-bbf6-dacd680554d0.png>
</p>

+ x[n]을 LTI시스템에 넣은 출력값 y[n] 
<p align="center">
  <image src=https://user-images.githubusercontent.com/70193130/165715605-c721383f-fd10-4570-b244-6160ebfac5c1.png>
</p>

<p align="center">
  <image src=https://user-images.githubusercontent.com/70193130/165716384-72af8e7c-3647-4518-8cbf-ed1b7b8b6dcf.png>
</p>

+ LTI시스템에 성질로인해 임펄수 함수들의 응답 h[n]의 컨볼루션으로 표현 
+ 델타함수가 이동할때마다 LTI시스템의 특성때문에 h[n]도 이동 LTI시스템의 <b>Time invariant</b>
+ x[k] 가 곱해지는것이 LTI시스템의 <b>scaling</b>
+ 시그마로 더해지는것 LTI시스템의 <b>additivity</b>



## 예제
---
![image](https://user-images.githubusercontent.com/70193130/165224059-aa6f3ef4-83e3-49fb-b643-4fdf8dc54603.png)


    def conv(v, w):
        c = np.zeros(v.shape)
        for n in range(len(v)):
            c[n] = 0
            for m in range(len(v)):
                c[n] += v[m] * w[n - m]  
        return c

        N = 20
    v = np.zeros(N)
    v[8:12] = 1
    w = np.zeros(N)
    w[1:5] = 1
    c = conv(v, w)

    fig = plt.figure()
    ax = fig.gca()
    ax.plot(v, '.-')
    ax.plot(w, '.-')
    ax.plot(c, '.-')
    ax.legend(['v', 'w', 'c'])
    ax.grid(True)