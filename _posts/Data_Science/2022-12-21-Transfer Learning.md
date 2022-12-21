---
layout: post
title:  "Transfer Learning"
subtitle:   "Repository에 올리기"
categories: Data_Science
tags: Data_Science
comments: true
---

# Transfer Learning 
+ ### 충분한 크기의 데이터 세트를 갖는 것이 힘듬
+ ### 네트워크를 처음 부터 학습하는 것이 아닌 사전학습 후 downstream task로 학습함


## Transfer Learning scenarios
### ConvNet기준으로 설명을 진행 

+ ### ConvNet as fixed feature extractor :사전 훈련된 네트워크를 가져오고 마지막 연결계층을 제거한 다음 나머지 ConvNet을 새 데이터 세트에 대한 fixed feature extractor로 사용

+ ### Fine-tuning the ConvNet : 새로운 데이터셋에서 ConvNet 을 재훈련하고 역전파를 사용하여 사전훈련된 네트워크의 가중치를 fine-tune하는 것 fine-tune하는 레이어의 부분을 정하여 초기단계의 레이어의 일반화 성능을 보존 할 수도 있다. 

## When and how to fine-tune?

### small or big, and its similarity to the original dataset
### ConvNet의 레이어 단계에 따른 특성을 상기하며 4가지 경우를 생각해보자

+ ### New dataset is small and similar to original dataset
        데이터셋의 크기가 작기때문에 오버피팅 문제가 발생 할 수 있어 fine-tune(x)

        데이터셋이 유사해서 ConvNet의 후반 레이어가 특징을 잘 잡을거라 생각 

        linear classifier만을 훈련하는것이 바람직하다.


+ ### New dataset is large and similar to the original dataset
        데이터셋의 크기가 커서 오버피팅 우려가 없음
        
        전체 네트워크를 fine-tune해도 괜찮음
+ ### New dataset is small but very different from the original dataset
        데이터셋의 크기가 작기때문에 classifier만을 훈련하는것이 바람직하다
        
        데이터셋 상이하기 때문에 feature들을 다루는 분류기 학습이 아니라 SVM같은 분류자를 
        훈련하는것이 더 좋을 수도 있음


+ ### New dataset is large and very different from the original dataset

        데이터셋의 크기가 크고 상이하니 사전훈련된 모델의 fine-tune을 하는것이 적합함

## Code
<https://tutorials.pytorch.kr/beginner/transfer_learning_tutorial.html>


## Reference
<https://cs231n.github.io/transfer-learning/>
