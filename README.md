## 3회차 과제
- 정리 주제 : 객체, 함수, 배열

> 참고 사이트 : https://inpa.tistory.com/entry/JS-%F0%9F%93%9A-%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EC%BD%9C%EB%B0%B1-%ED%95%A8%EC%88%98, https://ko.javascript.info/, https://developer.mozilla.org/ko/

### 객체
#### JS에서 객체란?
-> 자신과 관련된 속성들을 가진다. 객체의 속성은 객체에 붙은 변수라 할 수 있다
객체의 속성은 일반적 JS 변수와 똑같지만 객체에 붙어있다는 점에서만 차이점이 있다. 속성에 접근할 땐 마침표 표기법을 사용한다

```js
objectName.propertyName;
```

중괄호({})안에 쉼표로 구분한 속성 이름과 값의 목록으로 나타내는 객체 초기자로 나타낼 수도 있다

```js
const myCar = {
    make: "Ford",
    make: "Mustang",
    make: "1969",

};
```
만약 myCar.color 이라 접근했다면 이는 객체에 할당되지 않은 속성이므로 undefined 이다 (null X)

#### 속성 대괄호 표기법 접근
-> 속성 이름이 동적으로 정해지는 경우 유용하게 사용된다
```js
const myObj = new Object(),
  str = "myString",
  rand = Math.random(),
  obj = new Object();

myObj.type = "마침표 구문";
myObj["date created"] = "공백을 포함한 문자열";
myObj[str] = "문자열 값";
myObj[rand] = "무작위 수";
myObj[obj] = "객체";
myObj[""] = "빈 문자열까지";

console.log(myObj);
```
위 예제는는 네 개의 변수를 쉼표로 구분하여 한 번에 생성하고 할당하는 것이다. 모든 대괄호 표기법 안의 키는 심볼이 아닌 경우 문자열로 변환된다. 위 코드 myObj 에 obj 를 키로 추가하는 부분에서 JS 는 obj.toString() 메서드를 호출한 결과를 새로운 키로 사용한다다

#### 객체 속성 나열하기
: 객체 속성을 나열하거나 순회하는 방법에는 세 가지 내장된 방법이 있다
##### for..in (반복문)
-> 객체와 객체안에 존재하는 모든 열거 가능한 속성을 순회한다
##### Object.keys(o)
-> o 객체 자신만의 열거 가능한 속성 이름("키")을 배열로 반환한다
##### Object.getOwnPropertyName(o)
-> o객체 자신만의 모든(열거 불가능해도) 속성 이름("키")을 배열로 반환한다

#### 객체 초기자로 객체 생성
: 객체 초기자를 사용한 객체 생성 구문은 아래 코드와 같다
```js
const obj = {
  property_1: value_1, 
  2: value_2, 
  ...,
  "property n": value_n, 
}
```
위 코드에서 obj 는 새로운 객체 이름이다. 객체 초기자는 표현식이며 자신이 속한 선언문이 실행될 때 마다 새로운 객체를 생성한다. 
-> 빠르고 간단하게 한 두개의 객체를 만들 때 객체 초기자를 사용한다


### 함수
#### 함수란?
: 특정 작업을 수행하는 코드 블록으로 재사용 가능한 코드 블록이다.
```js
function add(x, y) {
  return x + y;
}
```
선언부에는 반드시 함수 이름이 필요하다
#### 화살표 함수?
: function 키워드 대신 => 사용하며 간결한 표현이 가능하다 
```js
let sum = function(a,b){
    return a+b
}
```
위의 함수를 화살표 함수로 바꾼다면? 
```js
let sum = (a,b) => a+b
```
위와 같이 (a,b) => a+b 는 인수 a와 b를 받는 함수이다. (a, b) => a + b는 실행되는 순간 표현식 a + b를 평가하고 그 결과를 반환한다
인수가 하나밖에 없는 경우 인수를 감싸는 괄호를 생략하는 것 또한 가능하다
#### 콜백 함수
: 콜백(Callback) 함수란 매개변수로 함수 객체를 전달하여 호출 함수 내 매개변수 함수를 실행하는 것이다.
```js
function sayHello(name, callback) {
    const words = '안녕하세요 내 이름은 ' + name + ' 입니다.';
    
    callback(words); // 콜백 함수 호출출
}

sayHello("홍길동", function printing(name) {
	console.log(name); 
});
```
위 코드에서 sayHello() 함수를 호출할 때 입력 매개변수로 문자열과 printing 함수 자체를 전달한다. 그 후 sayHello() 함수가 실행되면 실행문 안에서 함수가 들은 두 번째 매개변수인 callback을 괄호를 붙여 호출한다
**즉** 콜백함수란 일반적 변수나 값을 전달하는 것이 아닌 함수자체를 전달하는 것이다. 
또한 매개변수에 함수를 전달해 일회용으로 사용하기 때문에 굳이 함수 이름을 명시할 필요가 없어 보통 콜백 함수 형태로 함수를 넘겨줄 때에는 함수 이름이 없는 '익명 함수' 형태로 넣어주게 된다

#### 익명함수
: 함수의 이름이 없는 함수
```js
function sayHello(name, callback) {
    const words = '안녕하세요 내 이름은 ' + name + ' 입니다.';
    
    callback(words);
}

sayHello("홍길동", function (name) { // 함수이름 X
	console.log(name); 
});
```
익명함수는 한 번쓰고 말 로직을 인라인으로 정의할 때 혹은 외부에 노출되지 않은 스코프(변수나 함수가 유효한 범위)가 필요할 때 등 다양한 상황에서 사용됨

### 배열
: 순서가 있는 컬렉션을 다뤄야할 때 쓰는 자료구조
#### 배열선언
```js
let arr = new Array();
let arr = [];
```
#### 대괄호 안 초기 요소 넣어주기
```js
let fruits = ["사과", "오렌지", "자두"];
```
#### 배열내 특정 요소 얻기
```js
let fruits = ["사과", "오렌지", "자두"];

alert( fruits[0] ); // 사과
alert( fruits[1] ); // 오렌지
alert( fruits[2] ); // 자두
```
#### 배열 내 전체 요소 출력
```js
let fruits = ["사과", "오렌지", "자두"];

alert( fruits ); // 사과,오렌지,자두
```
#### 배열의 요소의 자료형엔 제약이 없다
#### pop & push
: 큐(queue) 는 배열을 사용해 만들 수 있는 대표적 자료구조인데 배열과 마찬가지로 순서가 있는 컬렉션을 사용하는데 사용한다
- push : 맨 끝에 요소 추가
- shift : 제일 앞 요소를 꺼내 제거한 후 남아있는 요소들을 앞으로 밀어줌 
> 배열엔 두 연산을 가능하게 해주는 내장 메서드 push, pop 이 있다.
: 큐 이외에도 스택이라 불리는 자료구조를 구현할 때도 쓰인다
- push : 요소를 스택 끝에 집어넣음
- pop : 스택 끝 요소를 추출

예시를 몇 개 들어보자면
```js
let fruits = ["사과", "오렌지", "배"];

alert( fruits.pop() ); // 배열에서 "배"를 제거

alert( fruits ); // 사과,오렌지
```
```js
let fruits = ["사과", "오렌지"];

fruits.push("배"); // 배 추가가

alert( fruits ); // 사과,오렌지,배
```
이러한 메서드는 배열 전용 메서드이고 문자열에선 정의 되지 않는다. 배열에서만 가능한 메서드들