# Closure

### * 사전지식
    일급객체란?
        다른 객체들에 일반적으로 적용 가능한 연산을 모두 지원하는 객체.

    일급객체의 조건
        - 모든 요소는 함수의 실제 매개변수가 될 수 있다.
        - 모든 요소는 함수의 반환 값이 될 수 있다.
        - 모든 요소는 할당 명령문의 대상이 될 수 있다.   
>출처 : 위키백과 https://ko.wikipedia.org/wiki/%EC%9D%BC%EA%B8%89_%EA%B0%9D%EC%B2%B4


### 클로저 예시

```go
package main

import "fmt"

func adder() func(int) int {
	sum := 0
	return func(x int) int {
		sum += x
		return sum
	}
}

func main() {
	pos, neg := adder(), adder()
	for i := 0; i < 10; i++ {
		fmt.Println(
			pos(i),
			neg(-2*i),
		)
	}
}
```   

클로저는 함수가 종료되어도 변수가 사라지지 않고, 계속 존재하며 사용할 수 있게 해줌   
일반적인 함수의 지역변수들은 Stack 영역에 할당 됨   
그러나 클로저를 이용하면 함수가 컴파일러에 의해 ***in-line*** 화 되고 사용하는 변수가 클로저화 되어 stack에서 heap으로 넘어감

    In-line:본문에서 함수를 호출 시 호출이 아닌 대치를 통해 overhead를 줄일 수 있게 함.   

    단점 : 코드의 길이가 길어지면 실행코드가 커질 수 있고 일반함수 취급을 받을 수 있다.
    

### 사용목적
* 함수가 종료된 후에도 데이터에 엑세스할 수 있음   
    - 예시) 함수 호출 횟수 카운팅, 
    - ( 추가 여지 있음 )


