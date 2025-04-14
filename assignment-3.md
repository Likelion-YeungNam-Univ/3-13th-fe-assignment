# 3회차 과제
- 정리 주제: 콜백함수, 배열, 객체
---
## 콜백함수

- **인자로 넘겨지는 함수**를 콜백 함수라고 한다. 단지 함수를 등록하기만 하고 어떤 이벤트가 발생했거나 특정 시점에 도달했을 때 시스템에서 호출하는 함수이다. **(함수 자체를 전달!)**
```js
functio func(callback) {
	callback();
}
function callback() {
	console.log("callback이다");
}

func(callback);
```
>위 예제는 콜백함수의 기본 형태이다.
#### 필요한 이유
- 가독성이나 코드 재사용 면에서도 사용 된다.
- 비동기 방식으로 작성된 함수를 동기 처리하기 위해 필요하다.
  - 동기 : 하나의 요청이 오면 완료가 된 후 다음 요청을 실행하는 방식
  - 비동기 : 어떤 요청이 오면 완료가 되기 전에 다음 요청을 실행하는 방식
>일상에서 자주 쓰는 절차나 순서를 이름 붙여 저장한다고 생각하기!
---
## 배열
- 특정한 요소들을 일정하게 모아 놓은 집합
#### 특징
- 배열에 들어 갈 수 있는 데이터에는 제한이 없다.
- 배열에는 순서가 있다.
#### 배열의 요소 추가, 삭제 메서드
  - **push 메서드**: 배열의 **마지막 위치**에 요소 추가
```js
let arr = [11,12,13];
let arr2 = [18, 19, 20];

arr.push(14); // arr에 단일 요소 추가
arr.push(15,16,17); // arr에 여러 요소 추가
arr.push(arr2); // 배열 arr에 배열 arr2가 추가, [11, 12, 13, 14, 15, 16, 17, [18, 19, 20]]
```
  - **spread 연산자**: spread(…) 연산자를 push메서드와 함께 사용해서 **요소를 추가**하고, **새로운 배열을 생성**할 수 있다.
```js
let arr = [11,12,13];
let arr2 = [18, 19, 20];

arr.push(...arr2); // Spread 연산자로 요소 추가, [11, 12, 13, 18, 19, 20]

let arr3 = [...arr, arr2] // 새로운 배열 생성, [11, 12, 13, 18, 19, 20]
```
  - **unshift 메서드**: 배열의 **첫 번째 위치**에 요소를 추가
```js
let arr = [11,12,13];
arr.unshift(10);
arr.unshift(7,8,9);
console.log(arr); // [7, 8, 9, 10, 11, 12, 13]

let arr1 = [1,2,3];
let arr2 = [4,5,6];

arr1.unshift(-1,0); 
console.log(arr1); //  [-1,0,1,2,3]

arr1.unshift(...arr2);
console.log(arr1); // [4, 5, 6, -1, 0, 1, 2, 3]
```
  - **splice 메서드**: 요소를 추가/제거하여 배열의 내용을 **수정**할 수 있다.
```js
let arr = ["a","b","c","d"]
arr.splice(1,0,'E','F'); // 첫번째 요소부터 0개의 배열 요소를 제거하고 'E','F'를 추가
```
 - **pop 메서드**: 배열의 마지막 위치의 요소 제거
```js
let arr = [11,12,13];
arr.pop()
arr.pop()
console.log(arr); // [11] 요소가 1개여도 여전히 배열
```
  - **shift 메서드**: 배열의 첫 번째 요소를 제거
```js
let arr = [11,12,13];
arr.shift();
console.log(arr); // [12, 13]
```
#### 필요한 이유
- 요소의 주소를 나타내는 ‘인덱스(index)’를 통해 원하는 요소에 빠르게 접근, 검색이 가능하다.
- 추가적으로 소모되는 메모리 양이 거의 없다.
---
## 객체
- **여러 속성을 하나의 변수에 저장할 수 있도록** 해주는 데이터 타입으로 `Key:Value` 형식으로 표현된다.
```js
const person = {
  name: 'John',
  age: 30,
  city: 'New York'
};
```
>위의 예제에서 person 객체는 name, age, city라는 세 가지 속성을 가지고 있다.
#### 객체의 정보 사용하기
- 점 표기법
```js
console.log(person.name);	   // John
```
- 대괄호 표기법
```js
console.log(person['age']);  // 30
```
#### 객체의 키와 값 추출
- **Object.keys()**
  - 객체의 모든 키를 배열로 반환
```js
let person = {
  name: "John",
  age: 30,
  city: "New York",
};

let keys = Object.keys(person);

console.log(keys); // ["name", "age", "city"]
```
- **Object.values()**
  - 객체의 모든 값들을 배열로 반환
```js
let person = {
  name: "John",
  age: 30,
  city: "New York",
};

let values = Object.values(person);

console.log(values); // ["John", 30, "New York"]
```
- **Object.entries()**
  - 객체의 각 키와 값의 쌍을 [key, value] 형태의 배열로 반환
```js
let person = {
  name: "John",
  age: 30,
  city: "New York",
};

let entries = Object.entries(person);

console.log(entries);
// [
//   ["name", "John"],
//   ["age", 30],
//   ["city", "New York"]
// ]
```
