# 목차
1. 배열
2. 객체
3. 비동기 처리

<br>

### 1. 배열

여러 개의 데이터를 순서대로 저장하는 자료구조. 각 데이터는 인덱스틀 통해 접근할 수 있으며, [ ]로 정의함.
<br>

- **배열의 특징**
  - 순서 있음
  - 동적 크기
  - 다양한 데이터 타입
- 배열 예시

  ```js
  const fruits = ["apple", "banana", "cherry"];  // 배열 선언
  console.log(fruits[0]);  // "apple" (첫 번째 요소)
  
  fruits.push("orange");  // 배열 끝에 "orange" 추가
  console.log(fruits);  // ["apple", "banana", "cherry", "orange"]
  
  fruits[1] = "blueberry";  // 두 번째 요소 수정
  console.log(fruits);  // ["apple", "blueberry", "cherry", "orange"]

  ```

- 배열 주요 메서드
  - `push()` : 배열의 끝에 요소를 추가
  - `pop()` : 배열의 마지막 요소를 제거
  - `shift()` : 배열의 첫 번째 요소를 제거
  - `map()`: 배열의 각 요소를 변환해서 새로운 배열을 반환
  - `filter()`: 조건에 맞는 요소들만 새로운 배열로 반환
  - `forEach()`: 배열을 순회하며 각 요소에 대해 작업
<br>

### 2. 객체

키와 값의 쌍으로 데이터를 저장하는 자료구조, 키를 통해 값에 접근할 수 있으며, { }로 정의함.
<br>

- **배열의 특징**
  - 순서 없음
  - 키는 고유해야 
  - 다양한 데이터 타입
- 배열 예시

  ```js
   const person = {
    name: "John",
    age: 30,
    isMarried: false
  };
  
  console.log(person.name);  // "John" (객체의 속성에 접근)
  
  person.age = 31;  // 객체 속성 수정
  console.log(person.age);  // 31
  
  person.city = "New York";  // 객체에 새로운 속성 추가
  console.log(person.city);  // "New York"


  ```

- 객 주요 메서드
  - `Object.keys()` : 객체의 키를 배열로 반환
  - `Object.values()` : 객체의 값을 배열로 반환
  - `Object.entries()` : 객체의 키와 값을 [키, 값] 형태로 배열로 반환
<br>

### 3. 비동기 처리

시간이 오래 걸리는 작업을 동기적으로 처리하지 않고, 작업이 끝날 때까지 기다리지 않고 다른 작업을 진행하는 방식.
<br>

- **1. 콜백 함수** : 비동기 함수가 끝난 후 실행될 다른 함수를 인자로 넘겨주는 방식
    
  ```js
  function fetchData(callback) {
    setTimeout(() => {
      console.log("데이터 가져옴!");
      callback();  // 작업 끝난 후 콜백 호출
    }, 1000);
  }
  
  fetchData(() => {
    console.log("데이터 처리 완료!");
  });
  ````
<br>

- **2. 프로미스** : 작업이 완료되면 `resolve`나 `reject`를 통해 결과를 전달하고, 이 결과는 `.then()`이나 `.catch()`로 처리할 수 있음.
  ```js
  function fetchData() {
    return new Promise((resolve, reject) => {
      setTimeout(() => {
        const success = true;
        if (success) {
          resolve("데이터 가져옴!");  // 성공하면 resolve
        } else {
          reject("데이터 오류!");  // 실패하면 reject
        }
      }, 1000);
    });
  }
  
  fetchData()
    .then(result => {
      console.log(result);  // 데이터 가져옴!
    })
    .catch(error => {
      console.log(error);  // 데이터 오류!
    });
  ```
<br>

- **3. `async` / `await`** : `await`는 프로미스가 해결될 때까지 기다린 후 결과를 반환하고, `async`는 함수가 프로미스를 반환한다고 선언.

  ```js
  async function fetchData() {
  const result = await new Promise((resolve) => {
    setTimeout(() => resolve("데이터 가져옴!"), 1000);
  });
  console.log(result);
  }
  
  fetchData();  // 1초 후에 '데이터 가져옴!' 출력
  ```












 
