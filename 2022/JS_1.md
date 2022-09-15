# while문, do while문, break, continue, switch문

### while 반복문

~~~javascript
let i = 0;

while(i<10){
    console.log(i);
    i++;
}
~~~
### do.. while
- 반복문을 한번 실행하고 조건문 확인. 콘솔 위치에 따라서 9까지 출력(i++ 위에 위치) 되거나 10까지 출력(i++ 아래 위치)이 됨.
~~~javascript
let i = 0;

do {
  console.log(i)
  i++;  
} while(i<10)
~~~
### break, continue

- break
~~~javascript
while(true){
 let answer = confirm('go?');
 if(!answer){//취소 버튼 이면 멈추는 코드
   break;
    }
}
~~~
- continue
~~~javascript
// 짝수 값 출력.
for(let i = 0; i < 10; i++){
  if(i%2){
    continue;
  }
  console.log(i)
}
~~~
- switch
  - 케이스가 다양할 경우 더 간결하게 쓸 수 있음. 
~~~javascript
// switch문

switch(평가){
  case A:
    //A일 때 코드
  case B:
    //B일 때 코드
}

//if문 

if(평가 == A){
  //A일 때 코드
}else if(평가 == B){
  //B일 때 코드
}

// 두 코드는 동일한 값을 출력.
~~~
예시)
~~~javascript
let fruit = prompt('무슨 과일?');

switch(fruit){
  case 'apple':
    console.log('100 won');
    break;
  case 'watermelon':
    console.log('200 won');
    break;
  case 'banana':
    console.log('300 won');
    break;
  case 'melon':
  case 'pear':
    console.log('500 won');
    break;
}
//위와 같이 종류는 다르지만 함수값이 같다면 같이 묶어도 된다.
~~~
---
## 함수(function)
![alt text](/img/function_1.png)
- 함수 작성
~~~javascript
function showError(){
    alert('에러가 발생했습니다. 다시 시도해주세요.');
}

showError();
~~~
- 매개변수가 있는 함수
~~~javascript
//예시 2)
function sayHello(name){
    const msg = `Hello, ${name}`;
    console.log(msg);
}
sayHello('Mike');

//예시 2)
let msg1 = 'Hello!!'

console.log('함수 호출 전')
console.log(msg1)
function sayHello(name){
    let msg = 'Hello';
  console.log(msg)
    if(name){
      msg += `, ${name}`;
    }
  console.log('함수 내부')
    console.log(msg);
}

sayHello();
sayHello('Mike');
console.log(msg)
~~~
- OR 매개 변수
~~~javascript
function sayHello(name = 'friend'){
  let msg = `Hello, ${name}`
  console.log(msg)
}

sayHello();
sayHello('Jane');

//"Hello, friend"
//"Hello, Jane"
~~~
- return 으로 값 반환
~~~javascript
function add(num1, num2){
  return num1 + num2;
}
const result = add(2,3);
console.log(result)

//5
~~~
- 에러 확인
~~~javascript
function showError(){
  alert('에러발생');
  return;
  alert('이 코드는 실행되지 않습니다.')
}
const result = showError();
console.log(result);
~~~
![함수 정리](/img/function_2.png) 

---

### 함수 표현식
- 코드에 도달하면 생성
~~~javascript
let sayHello = function(){
    console.log('Hello');
}

sayHello();
~~~
![함수 표현식](/img/function_3.png)
- 예시
1. 함수 표현식
~~~javascript
showError();

let showError = function(){
console.log('error');
}
~~~

### 함수 선언문
- 어디서든 호출 가능
~~~javascript
// 예시1)
funcion sayHello(){
    console.log('Hello');
}

sayHello();

// 예시2)
sayHello();

funcion sayHello(){
    console.log('Hello');
}
// 사용 가능 범위가 코드 보다 위임(호이스팅)
~~~
### 화살표 함수(arrow function)
~~~javascript
// 기존 함수
let add = function(num1, num2){
    return num1 + num2;
}
// 화살표 함수 : function 빠지고 => 로 바꿔 쓸 수 있다.
let add = (num1, num2)=>{
    return num1 + num2;
}

// 리턴문 단축 : 중괄호, return 대체로 괄호() 사용.
let add = (num1, num2)=>(
        num1 + num2;
)

// 리턴문이 한개일 때 : 괄호 생략 가능
let add = name => `Hello, ${name}`;
)

// 인수가 없는 함수 : 괄호 생략 불가능
let showError = () =>{
    alert('error');
}

// 리턴 코드 전 여러줄의 코드가 있을 경우 일반 괄호 사용 불가능

// 틀린 예시
let add = function(num1, num2){
    const result = num1 + num2;
    return result;
}

// 맞는 예시
let add = (num1, num2)=>{
    const result = num1 + num2;
    return result;
}
~~~

[코딩악마_자바스크립트 기초](#https://www.youtube.com/watch?v=KF6t61yuPCY&t=2833s)