---
layout: post
current: post
cover:  ../assets/images/go_cover1.png
navigation: True
title: Go언어 덧셈 함수 만들기
date: 2019-12-11 09:00:00
tags: [GO]
sitemap :
  changefreq : daily
  priority : 1.0
class: post-template
subclass: 'post tag-go'
author: KEJdev
use_math: true
---  


오늘은 GO언어에서 Package, Exported names, 함수에 대해 알아보도록 하겠습니다. Python과 비슷하


--------------


> #### 패키지(Package)

GO언어의 모든 프로그램은 패키지로 구성되어 있습니다. 또한 main 패키지에서부터 실행을 시작하며, 패키지 이름은 디렉토리 경로의 마지막 이름을 사용하는 것이 규칙입니다. 예를 들어서 "path/filepath"를 사용한다면 패키지명은 filepath입니다. 

```go
packahe main

import "fmt"
import "math"

func main(){
  fmt.Println("Happy", math.pi, "Day")
}
// 출력 결과 : Happy 3.141592653589793 Day
```

--------------


> #### 임포트(Imports)

Go언어에서는 여러개의 "Package"를 소괄호로 감싸서 import를 표현합니다. 그래서 아래와 같이 import문장을 여러번 사용 할 수 있습니다. 


```go
package main

import ( 
  "fmt" 
  "math" 
)

func main() { 
  fmt.Printf("Now you have %g problems.",
  math.Nextafter(2, 3))
}
// 출력 결과 : Now you have 2.0000000000000004 problems.
```

--------------


> #### 익스포트(Exported names)


패키지를 Import 하면 패키지가 외부로 export한 것들(메서드나 변수, 상수등)에 접근 할 수 있습니다. Go언어에서는 첫 문자가 대문자로 시작하면 그 패키지를 사용하는 곳에서 접근 할 수 있는 exported name이 됩니다. 예를 들어 Foo와 FOO는 외부에서 참조할 수 있지만 foo는 참조 할 수 없습니다. 


--------------


