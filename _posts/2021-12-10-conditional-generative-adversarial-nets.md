---
layout: post
title: 논문 리뷰 - Conditional Generative Adversarial Nets
date: 2021-12-10 09:00:00 +0300
category : paper
---


Paper URL: [Conditional Generative Adversarial Nets](https://arxiv.org/abs/1411.1784) 

해당 논문은 Conditional GAN이라는 논문을 소개하고 있다.  간단하게 y라는 데이터를 추가하므로써 내가 원하는 데이터를 생성하는 것이 이 논문의 핵심이다.

기존의 GAN은 데이터가 생성되는데에 통제권이 없었다. 이뜻은 무엇일까? 
MNIST dataset을 기준으로 잡고 이야기 하자면, 내가 숫자 7 이미지를 원한다고 해서 모델이 7 이미지를 만들어주지 않는다는 이야기다. 

![cGAN](/public/img/cGAN.png){: width="90%" height="90%" }{: .center}

그렇다면 왜, GAN은 왜 우리가 원하는데로 이미지를 생성해주지 않는걸까?
그 이유는 GAN은 라벨의 정보를 가지고 학습하는 것이라, 데이터 분포를 학습하기 때문이다. 

![cGAN(1)](/public/img/cGAN(1).png){: width="70%" height="70%" }{: .center}

즉, 라벨에 대해 잘 모르지만서도 1을 1답게 하는 데이터 분포를 학습하기 때문이다. 

그렇다면, 우리가 원하는 데이터를 만들어주는 GAN을 만들려고 하면 어떻게 해야댈까?
라벨에 대해 잘 모르는 같으니, y라는 특정한 정보 y(라벨)을 넣어준다면, 분포와 함께 우리가 원하는데로 만들어 주지 않을까? 
이렇게 데이터를 우리가 원하는데로 제어하는 모델을 conditional GAN 이라고 한다.

![cGAN(2)](/public/img/cGAN(2).png){: width="70%" height="70%" }{: .center}

요점은 아래와 같다. 

1. Discriminator 조건을 토대로 생성된 이미지에 대해 진짜인가, 가짜인가를 판별하고 있다.
2. Generator는 y에 의해 조건을 토대로 이미지를 생성하고 있다.

수식은 GAN이랑 크게 다르지 않다.

![cGAN(4)](/public/img/cGAN(4).png){: width="70%" height="70%" }{: .center}

논문에서는 MNIST data에 대해 조건 y를 one-hot encoding 시킨 class label을 사용했으며 결과는 아래와 같다. 예쁘게 순서대로 나열된 결과를 볼 수 있다. 

![cGAN(3)](/public/img/cGAN(3).png){: width="70%" height="70%" }{: .center}

