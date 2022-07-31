---
layout: post
title: 파이썬과 텐서플로우의 차이
date: 2020-02-07 09:00:00 +0300
category : MachineLearning
use_math : true
---

간단하게 텐서플로우와 파이썬 문법 비교 해보겠습니다.

## Python ? Tensorflow

우선 간단하게 1에서 5까지의 숫자를 출력해보도록 하겠습니다. 

```python
x = 0
for i in range(5):
    x = x+1
    print(x)
```

파이썬으로 하면 위와 같으며, Tensorflow로 하면 아래와 같습니다. 

```python
x = tf.Variable(0, name='x')
model = tf.global_variables_initializer()
	
with tf.Session() as sess:
    for i in range(5):
        sess.run(model)
        x = x + 1 
        print(sess.run(x))
```

아무래도 간단하게 출력하고 확인할 수 있는건 Python만한게 없네요.
이번에는 Numpy을 Tensor로 구현해보도록 하겠습니다.

```python
import numpy asnp
a=np.zeros((2,2))
b=np.ones((2,2))

print(a)
print(b)
```

아래와 같이 바꿀 수 있습니다.

```python
import tensorflow as tf
a=tf.zeros((2,2))
b=tf.ones((2,2))

with tf.Session() as sess:
    print('=========tensorflow========')
    print(sess.run(a))
    print(sess.run(b))
```
