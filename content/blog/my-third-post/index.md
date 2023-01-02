---
title: Javascript 올바른 괄호 
date: "2022-12-17T23:46:37.121Z"
description: "프로그래머스 문제풀이"
---

#### 문제
> 
괄호가 바르게 짝지어졌다는 것은 '(' 문자로 열렸으면 반드시 짝지어서 ')' 문자로 닫혀야 한다는 뜻입니다. 예를 들어
"()()" 또는 "(())()" 는 올바른 괄호입니다.
")()(" 또는 "(()(" 는 올바르지 않은 괄호입니다.
'(' 또는 ')' 로만 이루어진 문자열 s가 주어졌을 때, 문자열 s가 올바른 괄호이면 true를 return 하고, 올바르지 않은 괄호이면 false를 return 하는 solution 함수를 완성해 주세요.

https://school.programmers.co.kr/learn/courses/30/lessons/12909



 #### 풀이 순서
>
1.tmp 빈 배열 
문자열 s를 반복문을 돌려 먄약 배열의 요소가 "(" 일때 빈 배열인 tmp에 넣어준다.
```js
tmp = [];
  for (let i = 0; i < s.length; i++) {
    if (s[i] == "(") {
      tmp.push(s[i]);
    }
````
 <br>
>  
2.for문을 돌린 s의 요소가 ")"이고 tmp의 tmt의 마지막 요소가 "(" 이면 tmp의 마지막을 제거해준다 (앞 뒤 개수가 맞아야 하기 떄문에)
> 
```js
else if((s[i] == ')' && tmp[tmp.length - 1] == '(')){
          tmp.pop();
      }
}
````
> 
3.그 외 false를 반환한다
> 
4.반복문이 끝나고 만약 tmp의 길이가 0이 아니면 짝이 맞지 않다는 것이기 때문에false를 반환하고 그 외 true를 반환한다.








#### 나의 풀이 코드
> 
```js
function solution(s) {
  tmp = [];
  for (let i = 0; i < s.length; i++) {
    if (s[i] == "(") {
      tmp.push(s[i]);
    } else if (s[i] == ")" && tmp[tmp.length - 1] == "(") {
      tmp.pop();
    } else return false;
  }
  if (tmp.length != 0) return false;
  else return true;
}
````

#### 다른 사람 풀이 코드
> 
```js
function solution(s){
    let stackCount = 0;
    for (let i = 0; i < s.length; i++) {
        stackCount += s[i] === '(' ? 1 : -1;
        if (stackCount < 0) return false;
    }
    return stackCount === 0 ? true : false;
}
````
1.스택 처럼 사용할 변수 setCount를 만들고 '('문자일때는 setCount에 1을 더해주고 ')'문자일때는 1을 빼주는 과정 거친다.
> 
2.그러던 와중 '(' 가 먼저 나온 것이 없는데 ')' 이 나왔다면 stackCount가 -1 이 될것이므로 올바른 괄호가 아니기 때문에 false를 반환한다
> 
3.반복문이 모두 끝나면 stackCount가 0보다 크다면 ')' 가 더 남아있다는 말과 같으므로 stackCount가 0일 때 true를 반환하고, 그렇지 않을때는 false를 반환하여 문제를 해결할 수 있다.
