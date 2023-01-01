---
title: Javascript 로그인 성공?
date: "2022-12-10T22:12:03.284Z"
description: "프로그래머스 문제풀이"
---

#### 문제
> 
머쓱이는 프로그래머스에 로그인하려고 합니다. 머쓱이가 입력한 아이디와 패스워드가 담긴 배열 id_pw와 회원들의 정보가 담긴 2차원 배열 db가 주어질 때, 다음과 같이 로그인 성공, 실패에 따른 메시지를 return하도록 solution 함수를 완성해주세요.
<br>아이디와 비밀번호가 모두 일치하는 회원정보가 있으면 "login"을 return합니다.
로그인이 실패했을 때 아이디가 일치하는 회원이 없다면 “fail”를, 아이디는 일치하지만 비밀번호가 일치하는 회원이 없다면 “wrong pw”를 return 합니다.

https://school.programmers.co.kr/learn/courses/30/lessons/120883
#### 처음 생각했던 방식
 1.userId = id_pw[0] userPw = id_pw[1]로 저장해 for문을 이용하여 비교
```js
let arr = [];

const userId = id_pw[0]
const userPw = id_pw[1]

  for (let i = 0; i < db.length; i++) {
    if (db[i][0] == userId && db[i][1] !== userPw) {
      arr.push("wrong pw");
    } else if (db[i][0] == userId && db[i][1] == userPw) {
      arr.push("login");
    }
  }

````


  2.db.flat()을 써서 db안 배열을 벗겨낸 다음에 userId와 userPw로 저장해 id_pw의 값들과 비교하였는데 db안에 id_pw의 요소가 있기만 해도 "login"이 되는 현상
 ```js
id_pw =["meosseugi","1234"]

db = [["rardss", "123"], ["yyoom", "1234"], ["meosseugi", "1234"]]

db.flat() = ["rardss", "123", "yyoom", "1234", "meosseugi", "1234"]
````
  


 #### 풀이 순서
>
1.db에 회원들의 아이디인 id_pw[0]가 포함된 배열을 추출해서 userData에 저장
->array.find를 이용
```js
const userData = db.find(([el])=> el == id_pw[0])
````
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/find <br>
2.userData의 비밀번호 userData[1]가 회원들의 비밀번호 id_pw[1]랑 같으면 "login" 그렇지 않으면 "wrong pw"를 리턴
```js
if(userData){
   return userData[1] == id_pw[1] ? "login" : "wrong pw"
}
````
3.아이디가 일치하는 회원이 없다면 "fail" 리턴




#### 나의 풀이 코드
> 
```js
function solution(id_pw, db) {
const userData = db.find(([el])=> el == id_pw[0])
if(userData){
   return userData[1] == id_pw[1] ? "login" : "wrong pw"
}
else return "fail"
}
```