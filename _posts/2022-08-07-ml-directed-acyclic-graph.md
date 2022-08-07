---
title: Deep Learning에서의 DAG구조
date:   2022-08-07 10:00:00 +0300
categories:  [Machine Learning,  ML]
sitemap :
math: true
mermaid: true
changefreq : always
priority : 1.0
use_math: true
---

DAG는 Directed Acyclic Graph의 약자이다.   
순환 그래프가 아닌 비순환 그래프를 말하며, 순환하는 싸이클은 존재하지 않고 일방향성만 가진다.  
그래프 종류와 딥러닝에서의 DAG구조에 대해 알아보자.  

## Graph 종류  

그래프에 대해 전부 다루게 되면 논점이 흐리게 될 것 같아, 무방향 그래프(Undirected Graph)와 방향 그래프(Directed Graph)만 간단하게 다룰 것이다. 

### 무방향 그래프 (Undirected Graph)

무방향 그래프는 말 그대로 방향이 없는 그래프를 말한다.  
간선을 통해 노드는 양방향으로 갈 수 있다. 

<center><img src = "../../assets/images/DAG1.png" ></center>  

### 방향 그래프 (Directed Graph)

방향 그래프는 간선에 방향이 있는 그래프를 말한다. 

<center><img src = "../../assets/images/DAG2.png" ></center>  

### 사이클(Cycle)과 비순환 그래프 (Acyclic Graph)

사이클은 단순 경로의 시작 노드와 종료 노드가 동일할 경우를 말하고 비순환 그래프는 사이클이 없는 그래프를 말한다.  

<center><img src = "../../assets/images/DAG3.png" ></center>  
<center>(좌)비순환 그래프 / (우)사이클 </center>  

## Directed Acyclic Graph  

DAG는 비순환 그래프를 말하며, 순환하는 사이클이 존재하지 않고 일방향성만 가진다.  

<center><img src = "../../assets/images/DAG4.png" width="650" ></center>  

순환한다는 것은 출발한 노드에서 시작하여 끝내 다시 시작노드로 돌아가는 것이 순환 반복될 수 있는 그래프인데, 
위 그래프처럼 다시 되돌아갈 간선이 없는 그래프라면 비순환 그래프라고 한다.  

## Deep Learning DAG 

일반적으로 DAG는 작업들의 우선순위를 표현할 때, DAG구조를 사용한다.  
예를 들어 공장에서 작업 스케줄링을 할 때, A라는 작업이 끝나고 B를 해야하고 B가 끝난 다음에는 C,D를 해야한다는 것을 DAG로 표현할 수 있다.  

딥러닝에서는 여러 개의 Task로 나뉘어서 순차적으로 실행할 필요가 있다. 만약 DAG가 아닌 사이클 구조를 가진다면 그 작업은 영원히 완수되기 어렵기 때문이다. 따라서 작업간의 순서를 그래프로 표현할때는 DAG로 표현하는 것이 일반적이다.

<center><img src = "../../assets/images/DAG5.png"  ></center>  

요즘은 이런 작업 흐름을 관리하기 위해 workflow 도구가 나와있으며 그 중 하나인 Airflow는 Graph View 기능을 제공한다.  