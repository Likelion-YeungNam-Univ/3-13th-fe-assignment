### 1. 콜백 함수
- 콜백 함수란? 매개변수로 함수 객체를 전달해서 호출 함수 내에서 매개변수 함수를 실행하는 것
- 비동기 프로그래밍을 할 때 많이 사용함

- 장점:
1. 시간이 오래 걸리는 작업을 처리할 때, 메인 흐름을 멈추지 않고 나중에 처리 가능
2. 함수의 정의를 다르게 해서 전달할 수 있음
3. 익명 함수로도 전달 가능
-  단점:
1. 콜백 지옥에 빠질 수 있다  
    ㄴ 콜백 지옥: 콜백 함수를 연속해서 쓸 때 코드의 들여쓰기 수준이 과도하게 깊어지는 것, 가독성 안 좋음
2. 에러 처리가 복잡해짐

- 콜백 함수 활용 예시
```js
function doSomethingLater(callback) { 
  console.log("2초 후 작업 시작..."); //먼저 즉시 실행되는 코드
  setTimeout(function() { //비동기 함수, 2초 뒤 콜백 실행
    console.log("작업 완료!"); //2초 뒤 실행될 코드
    callback(); //콜백 함수
  }, 2000); //2초
}
doSomethingLater(function() { 
  console.log("후처리 실행"); //콜백함수 내용, 작업 완료후 실행됨
});
```
예시 코드 출력 결과: 
2초 후 작업 시작...
(2초 후)
작업 완료!
후처리 실행  

---

### 2. 화살표 함수
- 화살표 함수란? function 키워드 대신 =>를 사용하는 함수 표현식

- 장점: 콜백 함수나 간단한 계산을 할 때 유용함
- 단점: this, arguments, super가 없고, 생성자 함수로 사용 불가

- 화살표 함수 활용 예시
```js
const add = (a, b) => a + b; //function 키워드 없이 함수 정의
console.log(add(2, 3)); //리턴값
```
예시 코드 출력 결과:
5   

---

### 3. Object.assign(target, sources) 함수
- Object.assign 함수란? 하나 이상의 source 객체를 target 객체에 복사해서 합치는 것
- target에는 복사한 내용을 담을 대상 객체
- sources에는 복사해올 원본 객체들 (여러 개)

- 장점: 
1. 여러 개의 객체를 한 번에 병합 가능
2. 기존 객체를 수정하거나 새로운 객체를 만들 수 있음
- 단점: 얕은 복사만 가능

- 활용 예시
```js
const user = { name: "은별", age: 20 }; //원본 객체
const copiedUser = Object.assign({}, user);  //user 객체 복사
console.log(copiedUser); //복사된 객체 출력
console.log(copiedUser === user); //원본과 복사본이 같은 객체인지 확인
```
예시 코드 출력 결과:
{ name: "은별", age: 20 }
false




