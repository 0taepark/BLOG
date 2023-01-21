---
title: Synchronous-Asynchronus
date: "2023-1-23T22:40:32.169Z"
description: cs지식 동기 비동기
---

### 자바스크립트는 동기? 비동기?

> 자바스크립트는 **싱글 스레드 기반**으로 프로세스를 처리한다.
> 단일 호출 스택 기능으로 한번에 하나의 일을 처리 한다. 그러므로 자바스크립트에서는 동기 방식이 Default이다. 때문에 하나의 함수를 처리하는데 시간이 오래 걸리면 다음 실행해야할 함수에 지장을 줄 수있다.

### 1. 동기(Synchronous: 동시에 일어나는)![](https://velog.velcdn.com/images/pyt1665/post/83bb9f15-b84c-4923-8957-39f8b4371f12/image.png)

> 동기식 처리 모델(Synchronous processing model)은 직렬적으로 태스크(task)를 수행한다. 즉, 태스크는 순차적으로 실행되며 어떤 작업이 수행 중이면 다음 작업은 대기하게 된다. 다음 함수의 실행이 중단되는 것을 Blocking이라고 한다.

> 동기 방식은 설계가 간단하고 직관적이지만 결과가 주어질 때까지 대기해야 하는 단점이 있다.

```js
function taskA() {
  console.log("A TASK END")
}

taskA()

console.log("코드 끝")
```

![](https://velog.velcdn.com/images/pyt1665/post/1c49d595-cbf6-4d7d-97a5-55a5841a3355/image.png)

### 2. 비동기(Asynchronous: 동시에 일어나지 않는)![](https://velog.velcdn.com/images/pyt1665/post/dadddbec-3091-4c6b-bd55-9e57a6237b3c/image.png)

> 비동기식 처리 모델(Asynchronous processing model)은 병렬적으로 태스크를 수행한다.
> 즉, 태스크가 종료되지 않은 상태라 하더라도 대기하지 않고 다음 태스크를 실행한다. 예를 들어 서버에서 데이터를 가져와서 화면에 표시하는 태스크를 수행할 때, 서버에 데이터를 요청한 이후 서버로부터 데이터가 응답될 때까지 대기하지 않고(Non-Blocking) 즉시 다음 태스크를 수행한다.

> 비동기방식은 동기보다 복잡한 설계이지만 요청에 따른 결과가 반환되기까지 시간이 걸리더라도 그 시간 동안 다른 작업을 할 수 있으므로 효율적이다.

```js
function taskA() {
  console.log("A TASK END")
}
taskA()

function taskB() {
  setTimeout(() => {
    console.log("B TASK END")
  }, 2000)
}

taskB()

console.log("코드 끝")
```

> 만약 이 코드가 동기적으로 동작해야 한다면
> "A TASK END" 출력 -> 2초를 기다린 후 "B TASK END" 출력 -> "코드 끝" 출력이 되어야 한다

![](https://velog.velcdn.com/images/pyt1665/post/1ea0bc05-e224-468d-96bb-7689cd6cd4ca/image.png)

#### "B TASK END"가 마지막에 출력되는 이유

> 1. taskA가 실행되어 console.log("A TASK END")가 출력된다.
> 2. taskB가 실행되는데 setTimeout은 비동기 작업이므로 즉시 실행되고 종료되며 실행 내용이 이벤트루프로 던져진다.
> 3. 바로 다음 코드 console.log("코드 끝") 을 출력한다.
> 4. 이벤트로프에서 2초 뒤에 콜백함수 (() => {console.log("B TASK END")}) 를 실행한다
