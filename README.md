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
-> 빠르고 간단하게 한 두개의 객체를 만들 때 객체 초기자를 사용한다다
