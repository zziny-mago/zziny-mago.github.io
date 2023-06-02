---
layout: post
title:  "Constant and Variable Tensors"
subtitle: "python,데이터 사이언티스트, 인공지능 개발자를 위함"
categories: Tensorflow
tags: Tensorflow
comments: true
---
    






    
---
~~~
    t1=tf.Variable([1,2,3])
    t2=tf.constant([1,2,3])

    print(type(t1))
    print(type(t2))
~~~

+ 텐서플로우에서 사용되는 2가지 텐서타입
+ constant -> EagerTensor
+ Variable -> ResourceVariable

~~~
    t1=tf.constant([1,2,3])
    t2=tf.Variable([1,2,3])
    #t3=tf.constant(t2)
    t4=tf.Variable(t1)

    print(type(t4))
~~~

+ 텐서타입은 constant->Variable만 가능
+ GradientTape을 없애버리는 이유떄문에 


~~~
    t1=tf.convert_to_tensor([1,2,3])
    t2=tf.Variable([1,2,3])
    t3=tf.convert_to_tensor(t2)

    print(type(t1))
    print(type(t3))
~~~

+ convert_to_tensor로 Variable->constant 변환가능
+ 기본값으로 constant 적용

~~~
    t1=tf.Variable([1,2,3])
    t2=tf.constant([4,5,6])
    t3=tf.Variable([1,2,3])
    t4=tf.constant([4,5,6])

    print(type(t2+t4))
    print(type(t1+t2))
    print(type(t1+t3))
~~~

+ 연산 수행시 EagerTensor로 연산 그래프가 형성 됨