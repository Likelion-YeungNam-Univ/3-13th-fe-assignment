# 3회차 과제

- 정리 주제: 함수, 배열, 객체

## 함수

같은 내용을 연속적으로 반복한다면 반복문이 적절하겠지만,
불연속적으로 반복된다면 반복문 사용이 어렵다.

이럴 때 사용하는 게 "함수"

강의 자료에서

"자주 쓰는 동작에 이름을 붙여서 저장해두는 것"

"스마트폰 단축 번호 기능처럼, 한 번 저장해 두면 언제든 불러 쓸 수 있는 기능"

이라는 문장이 함수를 이해하기에 매우 좋았다.

함수는

1. 이름
2. 함수의 매개변수
3. 실행될 코드

의 키워드로 구성되어 있다.

예시로 덧셈 기능을 하는 함수를 만들어보자

function sum(left, right) {
document.write(left + right);
}

함수 이름은 sum
이름 옆에 소괄호 안에 left와 right는 매개변수(parameter)
중괄호 안에 document.write(left + right);가 실행될 코드인 것.

함수를 호출할 때는 함수 이름과 사용될 인자(argument)를 넣어 호출하면 된다.

sum(2,3);

함수의 장점으로는

1. 유지보수가 좋아짐
2. 웹페이지의 크기가 줄어듬
3. 여러 곳에서 같은 로직을 사용하고 있다고 확신할 수 있음
4. 이름이 붙어있기 때문에 코드의 정체를 분명하게 이해할 수 있음
   등이 있다.

그럼 화살표 함수로 예시를 바꿔보자
sum = (left, right) => document.write(left + right);
가 된다.
기존 함수 구성에서 function을 떼어내고 함수 이름 = (매개변수) => 실행될 코드로 만들 수 있다.
매개변수가 하나라면 소괄호 조차도 생략할 수 있다고 한다.
하지만 하나도 없을 경우엔 소괄호를 비워놓고 이때는 생략할 수 없다고 한다.
지금은 실행되는 코드가 한 줄이라 중괄호도 생략했지만, 여러 줄일 경우엔 표시하도록 하자.

이제 가장 헷갈렸던 콜백 함수를 살펴보자
콜백 함수는 매개변수로 함수 객체를 전달해서 호출 함수 내에서 매개변수 함수를 실행하는 것.. 이라는데...
간단하게 매개변수로 함수 자체가 전달되는 것이라고 생각하자

위의 예시를 콜백 함수를 사용해서 바꿔보자

function sum(left, right) {
document.write(left + right);
}
이었던 함수의 구조를

function sum(left, right, callback) {
var num = left + right;

    callback(num);

}

function result(res) {
console.log("결과는" + res + "입니다.");
}

sum(2, 3, result);

이렇게 만들수 있겠다.
sum을 호출하면 2와 3을 더한 값이 num에 들어가고 이 num의 값을 콜백함수인 result의 인자로 사용하게 되는 것이다.

화살표 함수를 적용해서 더 간단하게 만들어보면

function sum(left, right, callback) {
var num = left + right;

    callback(num);

}

sum(2, 3, (num) => {
console.log("결과는" + num + "입니다.");
});

중간에 function result로 함수를 정의하지 않고 sum 함수의 인자로 함수 자체를 화살표 함수 형태로 넣어 축약할 수 있다.

## 배열

배열은 여러 개의 값을 저장하고 관리하는 데에 사용되는 자료구조로 간단히 수납상자 정도로 생각하면 되겠다
영어로는 array

배열은 대괄호로 시작해서 대괄호로 끝난다. []
주로 대괄호 안에 값을 넣어 선언하는 방법을 사용한다.
이 값들은 쉼표로 구분할 수 있다.
const fruits = ["apple", "banana", "coconut"];
배열의 각 항목들은 요소라고 한다. element

배열의 각 요소를 꺼내오려면 인덱스(index)를 사용해야 하는데, 인덱스는 0부터 시작하며 대괄호 안에 인덱스 값을 넣어서 접근할 수 있다.

fruits[0]; -> "apple"
fruits[1]; -> "banana"

배열의 length 속성이란 게 있는데,
말 그대로 배열의 길이 즉, 요소의 갯수를 알 수 있다.
fruits.length; -> 3
length 속성은 쓰기가 가능하다!
예시로
fruits.length = 2;
fruits; -> ["apple", "banana"]
길이를 2로 지정하면 그만큼만 남기고 잘리는 것을 볼 수 있다.
이때 길이를 다시 3으로 지정해도 삭제된 값이 복구되지 않는다.
fruits.length = 3;
fruits; -> ["apple", "banana", empty]
이런 특징을 이용해서 배열을 초기화할 때
fruits.length = 0;을 사용해서 배열을 비울 수 있다.
물론, fruits = [];으로 빈 배열을 할당하는 방법도 있다.

요소를 추가하는 방법을 알아보자

1. 특정 인덱스를 지정하여 추가
   fruits[3] = "pineapple";
   3번 인덱스에 pineapple이 추가된다.
2. push() 메소드
   fruits.push("melon");
   fruits 배열 가장 끝에 "melon"이 추가된다.
3. length 속성
   fruits[fruits.length] = "grape";
   fruits 배열의 길이 값을 인덱스로 사용해서 "grape"이 추가된다.
   맨 뒤에 추가하는 push()와 같은 기능

그럼 반대로 요소를 삭제하는 방법도 알아보자
간단하게 delete 연산자를 사용할 수 있는데
delete fruits[3];
fruits; -> ['apple', 'banana', 'coconut', empty, 'melon', 'grape']
그 요소의 값만 지워지고 빈 자리로 남는 걸 볼 수 있다.

자리까지 지우고 싶다면 splice() 메소드를 사용하면 된다.
splice(시작 인덱스, 삭제할 요소 갯수)
fruits.splice(2, 1);
fruits 배열의 2번 인덱스인 "coconut"부터 1개를 삭제해라는 뜻이 된다.
fruits; -> ['apple', 'banana', 'pineapple', 'melon', 'grape']
'coconut'이 삭제되고 요소 갯수도 5개로 줄어든 것을 볼 수 있다.
사실 splice()는 요소를 삭제하는 기능 뿐만 아니라 다른 기능들도 있지만 다음에 알아보는 걸로..

## 객체

데이터를 구조화하고 저장하는 데 사용하는 기본 단위.
객체는 속성(property)과 메소드(Method)로 구성되며, 속성은 key와 value의 쌍으로 이뤄져있다.

객체의 특징을 알아보자

1. 중괄호 내부에 Key : Value의 형태로 속성을 정의
2. 각 속성은 쉼표로 구분
3. 함수를 포함할 수 있으며, 함수는 일반 함수 선언과 화살표 함수로 정의할 수 있음

const user = {
name: "철수",
age: "18",
isAdult: 'ture'
};

속성에 접근하는 방법을 알아보자

1.  점 표기법
    객체 이름 뒤에 점을 붙이고 접근하려는 속성 이름을 붙이면 된다.
    user.name -> '철수'
2.  대괄호 표기법
    속성 이름을 문자열 형태로 대괄호 안에 넣어 접근하는 방식
    뭔가 배열의 인덱스와 유사한 형태 같다.
    user["name"] -> '철수'

속성을 수정, 추가, 삭제하는 방법도 알아보자

1. 수정
   점 표기법, 대괄호 표기법 둘 다 가능하다.
   user.name = "맹구";
   user['age'] = '21';

2. 추가
   새로운 속성을 추가하는 것도 가능하다.
   추가도 점 표기법, 대괄호 표기법 모두 사용 가능.
   user.email = 'mangoo12@example.com';
   user["address"] = 'Seoul 123'

3. 삭제
   삭제는 delete를 사용하면 된다.
   이 방식 또한 점 표기법, 대괄호 표기법 모두 사용 가능하다.
   delete user.age;
   delete user["address"];

JavaScript에서 const 키워드를 사용하여 변수를 선언하면 재할당이 불가능하다.
하지만, 객체의 경우엔 const로 선언한 후에도 객체 내부의 속성은 변경할 수 있다는 특징이 있다!! (위의 예시도 그렇다.)

document.querySelector();
사실 여태 쓰던 document. << 얘도 객체였다고..
querySelector() << 얘는 객체에 속해있는 함수인 Method인 것
