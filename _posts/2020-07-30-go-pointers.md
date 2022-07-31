---
layout: post
title: Go에서 Pointer 사용하기
date: 2020-07-30 09:00:00 +0300
category : Go
use_math : true
---   

GO는 설치되어 있지 않지만 실행을 해보고 싶다면, [여기](https://tour.golang.org/methods/20)에서 간단하게 돌려 볼 수 있다.

## Go Pointers

Go에는 포인터가 있지만 포인터 연산은 불가능하다. 구조체 변수는 구조체 포인터를 이용해 접근 할 수 있다. 포인터를 이용하는 간접적인 접근은 실제 구조체에도 영향을 미친다. 


```go
package main

import (
	"fmt"
)

type Vertex struct {
	x int
	y int
}

func main() {
	p := Vertex{1, 2}
	q := &p
	q.x = 1e9
	fmt.Println(p)
}

```

결과 : 

![go6](/public/img/go6.png){: width="20%" height="20%" }{: .center}