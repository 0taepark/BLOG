---
title: Javascript JadenCase문자열만들기
date: "2023-01-07T23:46:37.121Z"
description: "프로그래머스 문제풀이"
---

#### 문제

> JadenCase란 모든 단어의 첫 문자가 대문자이고, 그 외의 알파벳은 소문자인 문자열입니다. 단, 첫 문자가 알파벳이 아닐 때에는 이어지는 알파벳은 소문자로 쓰면 됩니다. (첫 번째 입출력 예 참고)
> 문자열 s가 주어졌을 때, s를 JadenCase로 바꾼 문자열을 리턴하는 함수, solution을 완성해주세요.

https://school.programmers.co.kr/learn/courses/30/lessons/12951

#### 풀이 순서

> 1.for문을 이용하여 배열의 0번째 요소이거나 요소 앞에 공백인 조건 생성 2.조건을 충족하였다면 대문자로 변환, 조건을 충족하지 못했자면 소문자로 변환

```js
if (i == 0 || s[i - 1] == " ") {
  answer += s[i].toUpperCase()
} else {
  answer += s[i].toLowerCase()
}
```

3.결과를 출력

>

#### 나의 풀이 코드

>

```js
function solution(s) {
  let answer = ""
  for (let i = 0; i < s.length; i++) {
    if (i == 0 || s[i - 1] == " ") {
      answer += s[i].toUpperCase()
    } else {
      answer += s[i].toLowerCase()
    }
  }
  return answer
}
console.log(solution("3people unFollowed me"))
console.log(solution("for the last week"))
```

#### 결과

![](https://velog.velcdn.com/images/pyt1665/post/155d9e01-5810-4f5b-921c-0206b7d33ef7/image.png)
