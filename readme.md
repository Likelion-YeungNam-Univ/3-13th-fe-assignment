## 3회차 과제
-  정리 주제:  :file_folder: [배열](#배열) |  :busts_in_silhouette: [객체](#객체) |   :hammer_and_wrench:  [함수](#함수)
---
:file_folder:
### 배열

<details>
<summary>배열 생성</summary>

```js
const animal = [];
animal[0] = "개";
animal[1] = "고양이";
animal[2] = "토끼";
```

```js
const animal = new Array("개", "고양이", "토끼"); // 위 코드와 같은 배열
```

```js
const animal = ["개", "고양이", "토끼"]; // 위 코드와 같은 배열

console.log(animal[0]); // 개
console.log(animal[1]); // 고양이
```

</details>

<details>
<summary>배열 관련 함수</summary>

<details>
<summary>map()</summary>

- 배열의 모든 요소에 대해 주어진 함수를 호출하고, 결과를 새 배열로 반환

```js
const nums = [1, 2, 3];
const doubled = nums.map(x => x * 2);
console.log(doubled); // [2, 4, 6]
```

</details>

<details>
<summary>push()</summary>

- 배열 끝에 요소를 추가

```js
animal.push("사자");
console.log(animal); // ["개", "고양이", "토끼", "사자"]
```

</details>

<details>
<summary>length</summary>

- 배열의 길이 반환

```js
console.log(animal.length); // 4
```

</details>

<details>
<summary>at()</summary>

- 지정한 인덱스의 요소를 반환

```js
console.log(animal.at(1));   // "고양이"
console.log(animal.at(-1));  // "사자"
```

</details>

<details>
<summary>pop()</summary>

- 마지막 요소를 제거하고 반환

```js
animal.pop(); // "사자"
console.log(animal); // ["개", "고양이", "토끼"]
```

</details>

<details>
<summary>shift()</summary>

- 첫 번째 요소를 제거하고 반환

```js
animal.shift(); // "개"
console.log(animal); // ["고양이", "토끼"]
```

</details>

<details>
<summary>기타 함수들</summary>

- `unshift()` : 배열의 시작 부분에 요소 추가  
- `delete` : 특정 인덱스 요소 삭제 (배열 길이 유지)  
- `concat()` : 두 개 이상의 배열 합치기  
- `copyWithin()` : 배열 내부 요소 복사하여 덮어쓰기  
- `flat()` : 중첩 배열 평탄화  
- `splice()` : 요소를 추가하거나 제거하거나 교체  
- `toSpliced()` : 원본 유지, 일부 수정한 새로운 배열 반환  
- `slice()` : 배열의 일부를 추출 (원본 유지)

</details>

</details>


<br>

> 참고 : https://www.w3schools.com/js/js_array_search.asp

---
 :busts_in_silhouette:
### 객체

<details> 
<summary>객체 생성</summary>

```js
const cat = {
name: "나비",
age: 3,
breed: "코리안숏헤어",
color: "회색",
isIndoor: true,
sound: "야옹"
};

const cat = new Object(); // 위와 같은 객체 생성 방식
cat.name = "나비";
cat.age = 3;
cat.breed = "코리안숏헤어";
cat.color = "회색";
cat.isIndoor = true;
cat.sound = "야옹";
```

</details>

<details> 
<summary>속성 접근</summary>

```js
console.log(cat.name);     // "나비"
console.log(cat["sound"]); // "야옹"
```

</details>

<details> 
<summary>속성 추가 / 수정</summary>

```js
cat.favoriteFood = "참치"; // 속성 추가
cat.age = 4;               // 속성 수정
```

</details>

<details> 
<summary>속성 삭제</summary>

```js
delete cat.sound; // sound 속성 제거
```

</details>

<details> 
<summary>Object.keys()</summary>

- 객체의 키 목록을 배열로 반환

    ```js
    console.log(Object.keys(cat));
    // ["name", "age", "breed", "color", "isIndoor", "favoriteFood"]
    ```

</details>

<details> 
<summary>Object.values()</summary>

- 객체의 값 목록을 배열로 반환

    ```js
    console.log(Object.values(cat));
    // ["나비", 4, "코리안숏헤어", "회색", true, "참치"]
    ```

</details>

<details> 
<summary>Object.entries()</summary>

- 객체를 [키, 값] 쌍의 배열로 반환

    ```js
    console.log(Object.entries(cat));
    /*
    [
    ["name", "나비"],
    ["age", 4],
    ["breed", "코리안숏헤어"],
    ["color", "회색"],
    ["isIndoor", true],
    ["favoriteFood", "참치"]
    ]
    */
    ```

</details>

<details> 
<summary>Object.assign()</summary>

- 다른 객체의 속성을 병합

    ```js
    const extra = { vaccinated: true };
    Object.assign(cat, extra);
    console.log(cat.vaccinated); // true
    ```

</details>

<details> 
<summary>in 연산자</summary>

- 해당 속성이 객체에 있는지 확인

    ```js
    console.log("breed" in cat);  // true
    console.log("weight" in cat); // false
    ```
</details>

---
:hammer_and_wrench:
### 함수
<details> <summary> 함수 선언 </summary>

```js
function Hello(name) {
  alert("안녕하세요. " + name + "님!");
}

Hello("홍길동");  // 함수 호출
```
</details>

<details> <summary> 화살표 함수 </summary>

```js
const Hello = (name) => {
  alert("안녕하세요." + name + "님!");
};

Hello("홍길동"); // 함수 호출
```

</details> <details> <summary>콜백 함수</summary>
함수의 인자로 전달되는 함수

어떤 작업이 끝난 다음에 실행될 함수를 정의

```js
function greet(name, callback) {
  console.log("안녕하세요. " + name + "님!");
  callback();
}

greet("홍길동", () => {
  console.log("오늘도 좋은 하루 되세요!!");
});
```

</details>

<details> <summary> Async 함수 </summary> 
 - 콜백함수와 마찬가지로 많은 작업이 일어 났을 때 유용하다.

 > 참고 : https://www.w3schools.com/js/js_async.asp

</details>
