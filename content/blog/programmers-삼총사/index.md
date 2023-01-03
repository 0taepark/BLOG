---
title: Javascript 삼총사 
date: "2022-12-24T23:46:37.121Z"
description: "프로그래머스 문제풀이"
---

#### 문제
> 
한국중학교에 다니는 학생들은 각자 정수 번호를 갖고 있습니다. 이 학교 학생 3명의 정수 번호를 더했을 때 0이 되면 3명의 학생은 삼총사라고 합니다. 예를 들어, 5명의 학생이 있고, 각각의 정수 번호가 순서대로 -2, 3, 0, 2, -5일 때, 첫 번째, 세 번째, 네 번째 학생의 정수 번호를 더하면 0이므로 세 학생은 삼총사입니다. 또한, 두 번째, 네 번째, 다섯 번째 학생의 정수 번호를 더해도 0이므로 세 학생도 삼총사입니다. 따라서 이 경우 한국중학교에서는 두 가지 방법으로 삼총사를 만들 수 있습니다.<br>
한국중학교 학생들의 번호를 나타내는 정수 배열 number가 매개변수로 주어질 때, 학생들 중 삼총사를 만들 수 있는 방법의 수를 return 하도록 solution 함수를 완성하세요.

https://school.programmers.co.kr/learn/courses/30/lessons/131705
#### 처음 생각했던 방식
> 
 1.입력된 변수 중에 총 3개의 수를 더한 값이 0이 되어야하므로 삼중 for문을 활용<br>
 2.삼중 for문을 활용하여 i, j, k 의 값을 더했을때 0이면 answer값 증가<br>
 3.number[i] + number[j] + number[k]의 값이 0과 같다면, answer 값이 증가하도록 작성
```js
function solution(number) {
    var answer = 0;
    for (let i = 0; i < number.length; i++) {
        for (let j = i + 1; j < number.length; j++) {
            for (let k = j + 1; k < number.length; k++) {
                if (number[i] + number[j] + number[k] === 0) {
                    answer++;
                }
            }
        }
    }
    return answer;
}
````
>   


 #### 풀이 순서
> 
1.삼중 for문이 아닌 이중 for문을 활용하여 문제 풀기 <br>
2.두개의 요소를 더한 값과 더한 값의 -1을 곱한 값을 더하면 0<br>
3.두개의 요소를 뽑아 그 수에 -1을 곱하고 그 외 요소들 중 -1을 곱한 값과 일치하는 것을 추출하여 배열에 저장 
```js
for (let i = 0; i < number.length; i++) {
    for (let j = i + 1; j < number.length; j++) {
      let num = (number[i] + number[j]) * -1;
      let count = number.slice(j + 1).filter((el) => el === num).length;
````
3. 배열의 길이를 count += answer
> 


#### 나의 풀이 코드
> 
```js
function solution(number) {
  let answer = 0;
  for (let i = 0; i < number.length; i++) {
    for (let j = i + 1; j < number.length; j++) {
      let num = (number[i] + number[j]) * -1;
      let count = number.slice(j + 1).filter((el) => el === num).length;
      answer += count;
    }
  }
  return answer;
}
console.log(solution([-2, 3, 0, 2, -5]))
console.log(solution([-3, -2, -1, 0, 1, 2, 3]))
console.log(solution([-1, 1, -1, 1]))
```

#### 결과
> 
1.나의 풀이 방식
![](https://velog.velcdn.com/images/pyt1665/post/25bb966c-656a-48bc-942d-3b158daeedc6/image.png)
> 

> 
2.처음 생각했던 방식
![](https://velog.velcdn.com/images/pyt1665/post/e392eb66-1e42-459c-a972-1e0fdca41e7f/image.png)

> 