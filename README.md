## 3회차 과제

- 정리 주제: 함수, 배열, 객체체

### 함수

- 함수란 자주 쓰는 동작에 이름을 붙여서 저장해두는 것을 의미한다.
- 함수를 사용하는 이유는?
  - 함수가 없으면 같은 코드를 계속해서 복사, 붙여넣어야 하기 때문에 사용한다.
  - 이렇게 코드를 구현하면 나중에 수정할 때 해당 동작을 실행하는 모든 부분을 일일이 찾아서 바꾸는 일을 줄일 수 있다.

#### 함수 표현법

- JS에서 함수 표현법은 크게 두 가지로 나뉜다.

  ##### 정규 표현

  ```
  function Hello(name) {
  alert("안녕하세요. " + name + "님!");
  }
  Hello("홍길동");
  ```

  - function은 함수 생성을 알리는 말
  - 함수의 이름 뒤에 괄호가 꼭 붙어야 하고, 괄호 안에는 함수에 전달할 정보인 매개변수가 들어간다.
  - 중괄호 내에는 함수 호출 시 실행할 명령어가 들어간다.
  - 따라서 함수를 호출하면 "안녕하세요. 홍길동님!"이 출력된다.
    <br>

  ##### 화살표 표현 함수

  ```
  const Hello = (name) => {
      alert("안녕하세요. " + name + "님!");
  }
  Hello("홍길동");
  ```

  - 화살표 함수를 쓰면 function 키워드를 사용해서 함수를 만드는 것보다 더 간단하게 표현할 수 있다.
  - 말 그대로 화살표(=>) 표시를 써서 함수를 선언한다.
  - 화살표 함수에는 제약 조건이 존재한다.
    - 무조건 익명함수로만 사용할 수 있다.
    - 메소드나 생성자 함수로 사용할 수 없다.
  - 이런 제약이 있어도 화살표 함수를 사용하는 이유는 this 바인딩에 차이가 있기 때문이다!
    <br>

  ##### 화살표 함수 this

  - JS의 this는 상황에 따라 다르게 바인딩된다.
    - 전역 공간의 this = 전역 객체
    - 메소드 호출 시 메소드 내부의 this = 해당 메소드를 호출한 객체
    - 함수 호출 시 함수 내부의 this = 지정되지 않음
  - 세 번째 this와 같이 함수를 호출했을 때 그 함수 내부의 this는 지정되지 않는다.
  - 그리고 this가 지정되지 않은 경우, this는 자동으로 전역 객체를 바라보기 때문에 함수 호출 시 함수 내부에서의 this는 전역 객체가 된다고 정리할 수 있다.
    <br>

    ```
    const cat = {
        name: "meow",
        foo1: function() {
            const foo2 = function() {
                console.log(this.name);
            }
            foo2();
        }
    };

    cat.foo1();
    ```

    - cat.foo1() 메소드 호출 시 내부 함수 foo2가 실행된다.
    - 함수가 호출됐으므로 foo2 내부의 this는 지정되지 않아서 곧 전역 객체를 가리킨다.
    - 전역 객체에 name이란 속성은 존재하지 않으므로 undefined가 뜨게 된다!

    ```
    const cat = {
        name: "meow",
        fool: function() {
            const foo2 = () => {
                console.log(this.name);
            }
            foo2();
        }
    };
    ```

    - 위 코드와 달라진 점은 cat 객체의 내부함수 foo2가 화살표 함수로 선언됐다는 점이다.
    - 이렇게 우리가 의도한대로 meow가 잘 찍힌 이유는 무엇일까? = 바로 화살표 함수의 this 바인딩 때문이다!

##### 화살표 함수의 this 바인딩

- 이게 가능한 이유는 화살표 함수에는 this가 아예 없기 때문이다!
- 즉, function을 선언한 함수를 실행할 때 this가 존재하긴 하지만 값을 지정하지 않는다. 따라서 화살표 함수로 선언한 함수에는 this가 아예 없다.

    <br>
    ##### 콜백함수란?
      - 함수의 인자로 전달되는 함수. 일이 끝난 다음에 실행할 함수를 의미한다.
      ```
      function greet(name, callback) {
          console.log("안녕하세요. " + name + "님!");
          callback();
      }

      greet("홍길동", () => {
      console.log("오늘도 좋은 하루 되세요!");
      });
      ```

      - 콜백 함수는 왜 필요한가?
          - 실제 웹페이지에서는 서버에서 데이터를 받아오는 동안 다른 작업을 하고, 데이터를 다 받아오면 그 다음 작업을 하는 것처럼 동시에 많은 일이 일어난다.
          - 이럴 때 콜백함수를 쓰면 이 행동이 끝나면, 다음 행동으로 특정 작업을 실행하도록 설정할 수 있다!

- 이처럼 this.name은 cat 객체의 내부에 지정된 "meow"일 줄 알았는데, undefined가 나왔다.
- 함수를 호출할 때 그 함수를 호출한 배경의 상황이 this에 담기는 건 화살표 함수에서 구현 되어있다.

### 배열

#### 배열이란?

- 여러 개의 데이터를 하나의 그룹처럼 묶어서 저장하고, 각 데이터를 순서대로 담은 인덱스로 접근할 수 있는 자료구조
- 여러 개의 데이터를 쉽게 관리하기 위해서 배열을 사용한다.

```
const snack = ["바나나킥", "새우깡", "포카칩"];

console.log(snack[0]);
console.log(snack[1]);
console.log(snack.length);
```

- 위와 같이 0이나 1과 같은 값을 주면 인덱스 순서대로 데이터에 접근할 수 있다.
- 인덱스는 숫자로 나타내고, 0부터 시작한다.
- 배열 snack에 .length를 붙이면 해당 배열의 전체 길이를 반환한다.

#### 배열 관련 함수

- map() : 배열의 모든 요소에 어떤 작업을 하고 싶을 때 사용한다.
  ```
  const nums = [2, 4, 6, 8, 10];
  const divNum = nums.map(num => num / 2);
  console.log(divNum);
  ```
  <br>
- filter() : 조건에 맞는 요소만 추출하고 싶을 때 사용한다.

  ```
  const users = [
  { name: "마이클", ring: 6 },
  { name: "르브론", ring: 4 },
  { name: "코비", ring: 5 }
  ];
  const players = users.filter(player => player.ring >= 5);

  console.log(players);
  ```

  <br>

- some() : 배열에 하나라도 조건을 만족하는 게 있으면 true, 아니면 false 반환
  ```
  const goat = users.some(user => user.ring > 3);
  ```

### 객체

#### 객체란?

- 속성과 값을 한 쌍으로 묶어서 저장하는 자료구조
- 사람, 동물, 물건과 같이 무언가를 구체적으로 표현하고 싶을 때 사용하는 것이 객체이다.
  예시로, 고라파덕이라는 캐릭터 카드가 있을 때
- 이름: 고라파덕
- 속성: 물
- 체중: 20

이런 데이터를 객체로 표현하면 아래와 같다.

```
const character = {
  name: "고라파덕",
  type: "물",
  weight: 50
  // 총 3개의 프로퍼티로 구성
  // name, type, hp는 key
  // 고라파덕, 물, 20은 value
};
```

##### 프로퍼티란?

- 객체는 key-value 쌍으로 묶은 덩어리들로 이루어져 있다.
- 이 한 쌍을 프로퍼티(property)라고 한다.
- 따라서 위 예시의 프로퍼티는 총 3개이다!

#### 객체 기본 구조

const pokemon = {
name: "고라파덕",
type: "물",
weight: "20"
};

- 이 pokemon 객체는 포켓몬(고라파덕)의 정보를 담고 있는 객체이다.
  <br>
- 이제 해당 객체의 정보를 사용하기 위해서 점 표기법 또는 대괄호 표기법을 사용한다.

// 점(dot) 표기법

```
console.log(pokemon.name);
```

// 대괄호 표기법

```
console.log(pokemon['type']);
```

#### 객체 관련 함수

- 아래 함수들은 전부 배열 형식으로 반환해준다.

  - Object.keys(): 객체의 모든 속성(key)만 반환해준다.
    ```
    const foo = Object.keys();
    console.log(foo);
    ```
  - Object.values(): 객체의 모든 값(value)만 반환해준다.
    ```
    const foo = Object.values();
    console.log(foo);
    ```
  - Object.entries(): 객체의 속성(key)와 값(value)을 함께 반환해준다.
    ```
    const foo = Object.entires();
    console.log(foo);
    ```
    <br>

- 배열을 객체로 변환하는 방법

  - Objects.assign(): 원래 객체를 합칠 때 주로 사용하나, 이를 이용해 배열을 객체로 변환할 수 있다. 이때 인덱스 값을 key로, 사용자가 작성한 요소 값들을 value로 변환된다.

    ```
    const arr = ['사과', '수박', '귤'];
    const obj = Object.assign({}, arr);

    console.log(obj);
    ```

- 객체를 배열로 변환하는 방법

  - Object.keys()와 Array.prototype.map()을 이용한 방법으로, Object.keys()는 인수로 들어온 객체의 key값을 배열에 넣어 반환하고, 이 때 반환된 배열의 map 메소드를 이용하여 key에 대응하는 값들을 반환하도록 만든다.

  ```
  const obj = {'0': 1, '1': 2, '2': 3};
  const arr = Object.keys(obj).map(key => obj[key]);
  console.log(arr); // [1, 2, 3]
  ```

  - 해당 작업은 Object.values() 혹은 Object.entries()로 해결 가능하다.
