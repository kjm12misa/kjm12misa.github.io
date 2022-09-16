## 객체(Object)
~~~javascript
//Superman/name:clark/age:33

const superman = {
    name : 'clark',//키(key) : 값(value),
    age : 33,
}
~~~
1. 객체 - 접근, 추가, 삭제
~~~javascript
//접근
superman.name 
superman['age'] 

console.log(superman.name) //'clark'
console.log(superman['age']) //33

//추가
superman.gender = 'male';
superman['hairColor'] = 'black';

// 삭제
delete superman.hairColor;
~~~
2. 단축 프로퍼티
~~~javascript
const name = 'clark';
const age = 33;

const superman = {
    name : name,
    age : age,
    gender : 'male',
}

//단축 프로퍼티 
const superman ={
    name,
    age,
    gender : 'male',
}
~~~
3. 프로퍼티 존재 여부 확인
- 어떤 값이 넘어오는지 확신 할 수 없을 때 사용하면 된다? 함수의 인자나 API 데이터 통신으로 받아올 때.
- '키(key)' **in** 객체명 : true or false
~~~javascript
const superman = {
    name : 'clark',
    age : 33,
}

console.log(superman.birthDay) //undefined
console.log('birthDay' in superman) //false
console.log('age' in superman) //true
~~~
- 예시
~~~javascript
//예시 1)
function makeObject(name, age){
	return{// 값 반환
	name,
	age,
	hobby: "sleep",
	};
}

const Mike = makeObject("Mike", 30);
console.log(Mike);

console.log('age' in Mike) //true
console.log('birthday' in Mike) //false

//예시 2)
function isAdult(user){
	if(!('age' in user) || // user에 age가 없거나 'or'
		 user.age < 20){ // 20살 미만이거나
		return false;
	} 
	return true;
}

const Mike = {
	name : 'Mike',
	age : 30,
};

const Json = {
	name : 'Json',
};

console.log(isAdult(Mike)) //true
console.log(isAdult(Json)) //false
~~~
4. 객체 for ... in 반복문
~~~javascript
const Mike = {
	name: "Mike",
	age: 30,
};

for(x in Mike){
	console.log(x) // "name", "age"
	console.log(Mike[x]) //"age", 30 -> Mike['age']
}
~~~
5. method
- 객체 프로퍼티로 할당 된 함수
- 화살표 함수는 일반 함수와는 달리 자신만의 this를 가지지 않으므로 내부에서 this를 사용하면, **그 this는 외부에서 값을 가져옴.**
~~~javascript
//예시 1)
const superman ={
    name: 'clark',
    age: 30,
//    fly: function(){
// 아래와 같이 단축할 수 있음. function을 지울 수 있음.
    fly(){
        console.log('날아갑니다~')
    }
}

//예시 2)
let boy ={
    name: 'cale',
    showName(){
        console.log(`${this.name}`);
    }
};

let girl ={
    name: 'skalet',
    sayHello(){
        console.log(`${this.name}`);
    }
};

//화살표 함수 사용 예시
let boy ={
    name: "Mike",
    sayHello()=>{
        console.log(this); //전역 객체 *브라우저환경: window, Node js: global
    }
};

boy.sayHello();
this != boy
~~~
6. 배열(Array)
- **순서**가 있는 **리스트**
- 대괄호[]로 묶고 쉼표,로 구분
- 문자, 숫자, 객체, 함수 등도 포함할 수 있음
~~~javascript
//1번 유빈, 2번 인균, ... 30번 선우

let students = ['유빈', '인균', ... '선우'];

//인덱스
console.log(students[0]); //유빈
console.log(students[1]); //인균
console.log(students[29]); //선우

//인덱스를 이용해 변경 가능
students[0] = '지미';
console.log(students); // ['지미', '인균' ... '선우']

//여러 종류를 포함 할 수 있음
let arr = [
    '세정', //문자
    33, //숫자
    false, //불린
    {
        //객체
        name: 'Mike',
        age: 30, //
    },
    //함수
    function(){
        console.log('TEST');
    }
];
~~~
- length : 배열의 길이
~~~javascript
//1번 유빈, 2번 인균, ... 30번 선우
let students = ['유빈', '인균', ... '선우'];

students.length // 30
~~~
- push() : 배열 끝에 추가
~~~javascript
let days = ['월', '화', '수'];
days.push('목')
console.log(days)//['월', '화', '수', '목']
~~~
- pop() : 배열 끝 요소 제거
~~~javascript
let days = ['월', '화', '수'];
days.pop()
console.log(days)//['월', '화']
~~~
- 추가(unshift)/제거(shift)
~~~javascript
//추가
let days = ['월', '화', '수'];
days.unshift('금', '토', '일');
console.log(days)//['금', '토', '일', '월', '화', '수']

//제거
let days = ['월', '화', '수'];
days.shift();
console.log(days)//['월', '화', '수']
~~~
- for 반복문
~~~javascript
let days = ['월', '화', '수'];

for(let index = 0; index < days.length; index++){
    console.log(days[index]) // 0~2까지 반복
}
~~~
- for ... of 반복문
~~~javascript
let days = ['월', '화', '수'];

for(let day of days){
    console.log(day) //
}
~~~