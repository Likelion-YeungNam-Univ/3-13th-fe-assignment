3회차 과제
==========
- 정리 주제 : 콜백 함수, 배열, 객체

## 1. 콜백 함수
__*콜백 함수란?*__  
*-> 다른 함수의 인자로 전달되는 함수*
- 자바스크립트에서 함수는 다른 함수를 파라미터로 받아서 내부에서 그 함수를 호출 할 수 있는데 이걸 **"콜백"** 이라고 함
- 파라미터로 콜백 함수를 전달받고 함수 내부에서 필요할 때 콜백 함수를 호출할 수 있음

   
<일반 코드>
```javaScript
// 두 수의 합을 리턴하는 함수
function add(x, y) {
    return x + y;
}

// 결과 출력 함수
function printResult(result) {  
    console.log(result);
}

printResult(add(10,20));
```
<콜백 함수로 구현한 코드>
```javaScript
function add(x, y, print) {
    print(x + y)  // x + y 결과를 print 함수에 넘겨서 호출 -> 여기서 print가 콜백 함수!
}

function printResult(result) {
    console.log(result);
}

add(10, 20, printResult) // add 함수 호출 -> printResult 함수를 콜백 함수로 전달
```
- add 함수에 콜백 함수를 받을 print라는 파라미터를 추가하고 내부에서 x와 y의 합을 인자로 전달
- print의 파라미터의 인자로 printResult 함수 전달 -> printResult 함수가 콜백 함수
- 먼저 add 함수가 호출된 후 printResult 함수가 add 함수 내부에서 나중에 호출됨
  
```javaScript
function add(x, y, print) {
    print(x + y);
}

add(10, 20, (result) => {
    console.log(result);
});
```
- 콜백 함수는 정의된 함수 뿐만 아니라 익명 함수도 전달 가능함
   - 익명 함수? - 이름이 없는 함수

#### # 콜백 함수가 필요한 이유
- 자바스크립트는 코드를 위에서 아래로 순차적으로 실행함
- 그러나 코드가 다른 행위가 일어난 뒤에 실행되는 경우도 있고 순차적으로 실행되지 않을 때도 있음 -> **비동기 프로그래밍**
- 콜백은 태스크가 끝나기 전에 함수가 실행되지 않는 것을 보장 -> 비동기 자바스크립트 코드를 작성할 수 있게 해줌
  
- 콜백 함수를 이벤트 선언을 위해 사용하기도 함
- JS 심화 수업 시간에 배운 이벤트 처리에서도 콜백 함수가 쓰였음!!
```html
<!--html-->
<button id="btn">Click me</button>

```
```javaScript
const btn = document.quertSelector("#btn");
// 클릭 이벤트가 발생하면 이 화살표 함수를 콜백으로 실행
btn.addEventListener("click", () => {  
    alert("클릭!");
});
```
- 사용자가 버튼을 클릭했을 때 "클릭!" 메시지를 출력하는 팝업창을 띄움
- 첫 번째로 버튼의 id 값을 사용하여 버튼을 선택하고 addEventListener 메소드를 사용하여 이벤트 리스너 추가
- 첫 번째 파라미터 : 이벤트의 타입인 "클릭"
- 두 번쩨 파라미터 : 버튼이 클릭되었을 때 팝업창을 띄우는 콜백 함수

## 2. 배열
__*배열이란?*__  
*-> 순서가 있는 컬렉션을 저장할 때 쓰이는 자료구조*  
- 자바스크립트 배열은 타입이 고정되어있지 않아서 서로 다른 타입의 원소들을 적재할 수 있음
- 동적으로 크기가 변할 수 있어서 크기를 지정할 필요가 X

#### # 배열의 생성
```javaScript
var arr1 = [1, true, "JavaScript"]; // 배열 리터럴을 이용하는 방법 -> 주로 쓰는 방법
var arr2 = Array(1, true, "JavaScript"); // Array 객체의 생성자를 이용하는 방법
var arr3 = new Arrray(1, true, "JavaScript"); // new 연산자를 이용한 Array 객체 생성 방법
```

#### # 배열의 접근
- 배열의 각 요소를 가져오기 위해 **인덱스**를 사용
- 인덱스는 0부터 시작, 대괄호 [] 안에 인덱스 값을 넣어 요소에 접근
```javaScript
var arr = ["JavaScript"];  // 요소가 하나인 배열 생성
var element = arr[0]; // 배열의 첫 번째 요소를 읽어서 대입
arr[1] = 10; // 배열의 두 번째 요소에 10 추가 -> 배열의 length가 1에서 2로 늘어남
arr[2] = element; // 배열의 세 번째 요소에 element의 값(JavaScript) 대입 -> length: 3

console.log(arr); // 배열의 요소 모두 출력 : JavaScript, 10, JavaScript
console.log(arr, length) // 배열의 길이 출력 : 3 
```

#### # 배열 요소 추가
(1) 방법 1 : 특정 인덱스를 지정하여 추가
```javaScript
var arr = [1, true, "Java"];
arr[4] = "Script";
```
(2) 방법 2 : push() 메소드 이용
```javaScript
arr.push("자바스크립트");
```
(3) 방법 3 : length 프로퍼티를 이용 -> 가장 빠름
```javaScript
arr[arr.length] = 100;  // 배열 맨 마지막에 100을 추가
```
- 출력 결과 : 1, true, Java, , Script, 자바스크립트, 100
- 인덱스 3 에는 배열 요소가 존재하지 x -> 배열 요소가 없는 부분을 **배열의 홀(hole)** 이라함
- 자바스크립트에서는 배열의 홀을 undefined 값을 가지는 요소처럼 취급함

#### # 배열 요소 삭제
- 배열은 객체이므로 배열 요소를 삭제할 때 delete 연산자 사용 가능
- **But, 이때 length에는 변함이 X**
-> 해당 요소를 완전히 삭제하려 length 프로퍼티에도 반영되게 하려면 **Array.prototype.splice** 메소드를 사용해야함
```javaScript
const numArr = ['zero', 'one', 'two', 'three'];
delete numArr[2]; // 요소의 값만 삭제됨 -> ["zero", "one", empty, "three"]
numArr.splice(2,1); // 요소 자체를 완전히 삭제하여 배열 크기가 줄어듦 -> ["zero", "one", "three"]
```

#### # 배열 요소 정렬
```javaScript
let arr1 = [2, 1, 5, 3, 4];
arr.sort();  // 오름차순 정렬
console.log(arr1);  // [1, 2, 3, 4, 5]

let arr2 = [1, 2, 3, 4, 5];
arr2.reverse();  // 내림차순 정렬
console.log(arr2); // [5, 4, 3, 2, 1]
```

## 3. 객체(Object)
__*객체란?*__  
*-> 여러 속성을 하나의 변수에 저장할 수 있도록 해주는 데이터 타입*
- 자바스크립트는 객체 기반의 스크립트 언어이며, 자바스크립트를 이루고 있는 거의 모든 것이 객체
- Key - Value 쌍을 저장할 수 있는 구조
```javaScript
var user = {
   name: "Hyejin",  // Key : name, Value : "Hyejin"
   age: 22    // Key : age, Value : 22
};

console.log(user.name); // Hyejin
console.log(user['age]); // 22
```
#### # 객체의 특징
- 객체는 변수임
- 객체에는 많은 값이 포함될 수 있음
- 객체는 중괄호 표기로 생성
- Key : 문자열 or 기호 여야함
- Value : 모든 유형
- 객체에서 명명된 값을 Properties 라 함
- 객체 변수를 복사하면 참조가 복사되고 객체가 복제되지 않음
```javaScript
let user = { name : "Hyejin" };
let admin = user;
```
<img src="https://github.com/user-attachments/assets/37b3ce6c-2368-46cc-bf7d-9962b165c905" width="400">


#### # Property(프토퍼티)
__*프로퍼티란?*__  
*-> 객체 내부의 속성*
- 객체는 프로퍼티로 구성됨
- " key : value "의 형식
```javaScript
var user = {
   name: "Hyejin", 
   age: 22 
};
```
- 위 코드의 user 객체의 프로퍼티 수는 2개 !
#### # 객체에 Key-Value 추가
```javaScript
var person = {
    name: "Hyejin"
};

console.log(person.name);  // 결과 : Hyejin
console.log(person.age);  // 결과 : undefined (존재하지x)

person.age = 22; // 추가하는 방법 (person["age"] = 22; 도 가능)
console.log(person.age);  // 결과 : 22
```

#### # 객체 Key-Value 수정
```javaScript
var person = {
    name : "Hyejin",
    age : 22
};

console.log(person.name);  // 결과 : Hyejin
console.log(person.age);  // 결과 : 22

person.age = 20; // 수정하는 방법 (person["age"] = 20; 도 가능)
console.log(person.age);  // 결과 : 20
```

#### # 객체 Key-Value 삭제
```javaScript
var person = {
    name : "Hyejin",
    age : 22
};

console.log(person.name);  // 결과 : Hyejin
console.log(person.age);  // 결과 : 22

delete person.age;  // 삭제하는 방법
console.log(person.age); // undefined (더 이상 존재하지 x)
```

```
