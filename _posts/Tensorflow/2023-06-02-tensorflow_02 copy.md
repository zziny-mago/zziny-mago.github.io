---
layout: post
title:  "Gradient Tape in Tensorflow"
subtitle: "python,데이터 사이언티스트, 인공지능 개발자를 위함"
categories: Tensorflow
tags: Tensorflow
comments: true
---


### Gradient Tape in Tensorflow

~~~
    t1=tf.Variable([1,2,3], dtype=tf.float32)
    t2=tf.Variable([10,20,30],dtype=tf.float32)

    with tf.GradientTape() as tape:
        t3=t1*t2
    
    gradients=tape.gradient(t3,[t1,t2])
    print(type(gradients))

    print('dt1',gradients[0])
    print('dt2',gradients[1])

    <class 'list'>
    dt1 tf.Tensor([10. 20. 30.], shape=(3,), dtype=float32)
    dt2 tf.Tensor([1. 2. 3.], shape=(3,), dtype=float32)
~~~

+ t3에 대한 t1,t2 편미분 값
+ tape의 경우 dtype=tf.float32 설정 해야함

~~~
    t1=tf.Variable([1,2,3], dtype=tf.float32)
    t2=tf.Variable([10,20,30],dtype=tf.float32)


    with tf.GradientTape() as tape:
        t3=t1*t2
        t4=t2+t3
        
    gradients=tape.gradient(t4,[t1,t2,t3])
    print(type(gradients))

    print('dt1',gradients[0])
    print('dt2',gradients[1])
    print('dt3',gradients[2])

    <class 'list'>
    dt1 tf.Tensor([10. 20. 30.], shape=(3,), dtype=float32)
    dt2 tf.Tensor([2. 3. 4.], shape=(3,), dtype=float32)
    dt3 tf.Tensor([1. 1. 1.], shape=(3,), dtype=float32)
~~~

+ t2의 경우 chain rule에 의해 나온 값


~~~
    t1=tf.constant([1,2,3], dtype=tf.float32)
    t2=tf.Variable([10,20,30],dtype=tf.float32)

    with tf.GradientTape() as tape:
        t3=t1*t2
        
    gradients=tape.gradient(t3,[t1,t2])
    print(type(gradients))

    print('dt1',gradients[0])
    print('dt2',gradients[1])

    <class 'list'>
    dt1 None
    dt2 tf.Tensor([1. 2. 3.], shape=(3,), dtype=float32)
~~~

+ constant 텐서는 기록되지 않음


~~~
    x_data=tf.random.normal(shape=(1000,) ,dtype=tf.float32)
    y_data=3*x_data+1

    w = tf.Variable(-1.)
    b = tf.Variable(-1.)

    LR = 0.01
    w_trace, b_trace = [], []

    for epoch in range(10):
        for x, y in zip(x_data, y_data):
            with tf.GradientTape() as tape:
                predictions = w*x + b
                loss = (predictions - y)**2
            gradients = tape.gradient(loss, [w, b])

            w = tf.Variable(w - LR*gradients[0])
            b = tf.Variable(b - LR*gradients[1])
            w_trace.append(w.numpy())
            b_trace.append(b.numpy())
            
    fig,ax=plt.subplots(figsize=(20,10))

    ax.plot(w_trace,label='weight')
    ax.plot(b_trace,label='bias')

    ax.tick_params(lablesize=20)
    ax.legend(fontsize=30)
    ax.grid

~~~

![image](https://github.com/ndb796/python-for-coding-test/assets/70193130/cc4e5114-ccef-4bbc-bc7b-c81aea78c8f4)


+ tf.Variable 함수를 사용해 변수텐서 유지


