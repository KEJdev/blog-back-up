---
layout: post
title: Go언어 문자열 반환하는 함수 만들기
date: 2019-12-18 09:00:00 +0300
category : Go
---

오늘은 GO언어에서 Package, Exported names, 함수에 대해 알아보도록 하겠습니다. 함수는 Python과 비슷해서 어렵지는 않고, 하면서 같이 패키지나 임포트도 잠시 훝어보는 시간을 가져보겠습니다. GO언어가 깔려 있다면 .go 파일을 만들고, 만약에 블로그 예제와 함께 테스트로 돌려보고 싶다면 [여기](https://play.golang.org/)를 눌러 GO놀이터를 이용하여 따라하시면 됩니다.

## 패키지(Package)

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

## 임포트(Imports)

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

## 익스포트(Exported names)

패키지를 Import 하면 패키지가 외부로 export한 것들(메서드나 변수, 상수등)에 접근 할 수 있습니다. Go언어에서는 첫 문자가 대문자로 시작하면 그 패키지를 사용하는 곳에서 접근 할 수 있는 exported name이 됩니다. 예를 들어 Foo와 FOO는 외부에서 참조할 수 있지만 foo는 참조 할 수 없습니다. 

## 함수(function)

함수에 관해서는 사실 저번 포스팅에서도 잠깐 다룬적이 있습니다. 하지만 오늘은 조금 더 깊게 들어가보도록 하겠습니다. GO의 함수는 다음과 같은 규칙을 같습니다.  

- 함수는 매개변수(인자)를 가질 수 있습니다.
- 두 개 이상의 매개변수가 같은 타입일때, 같은 타입을 취하는 마지막 매개변수에만 타입을 명시하고 나머지는 생락할 수 있습니다.  
- 하나의 함수가 여러개의 결과를 반환할 수 있습니다. 


하나의 함수가 두개의 문자열을 반환하는 함수를 한번 만들어보겠습니다. GO에서는 함수를 만들때, func를 붙이면 함수를 만들 수 있습니다. 

```go
package main

import "fmt"

func swap(x, y string) (string, string) {
  return y, x
}

func main() {
  a, b := swap("hello", "world")
  fmt.Println(a, b)

}
```

코드를 보면 함수 swap 라는 함수를 만들었고 문자열 두개를 받아 문자열 두개를 반환하는 함수라는 것을 알 수 있습니다.  **swap(x,y string)**은 x와 y값을 입력 받는데, 문자열을 받겠다는 뜻이며, 뒤에 있는 **(string, strain)**은 return값을 문자열로 하겠다는 뜻입니다. 

## 변수 

func main()을 살펴보면 **:=**라는 문자를 볼 수 있는데 함수내에서 짧은 선언을 위해 사용합니다. 월래는 변수를 선언할때, **var**를 사용합니다. 그래서 a라는 변수에 10이라는 숫자를 넣고 싶다면 아래와 같이 써야하는 것이 맞습니다.  


```go
var a = 10 
```

그렇지만 편하게 **:=**을 사용하면 var과 명시적 타입을 생략 할 수 있습니다. 하지만! 함수 밖에서는 사용할 수 없으니 주의 해주세요. GO에선 변수 선언과 함께 변수 각각을 초기화 할 수있습니다. 초기화 하는 경우 타입을 생략 할 수 있습니다. 

