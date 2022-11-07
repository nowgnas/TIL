# ES6 정리

## Data type

```jsx
"hello"; // string
32; // integer
3.2; // float
```

숫자와 문자에 대한 `data type`은 기본적으로 `integer`, `string`이 있다. string은 문자열이며 `+`연산자로 문자들을 연결할 수 있다. 숫자 형태는 정수인 `integer`와 `float`이 있다. 숫자 형태는 사칙 연산 기호로 모두 연산이 가능하다.

## Variable

```jsx
const a = 3;
const name = "lee";

let letA = 5;
letA = 7; // 변수 업데이트
```

`javascript`는 `const`와 `let`으로 변수를 선언할 수 있다. `const`는 constant(불변) 변수이고, 변수를 업데이트 하고 싶은 경우에는 `let`을 사용하면 된다.
`let`은 최초 변수 선언 시에만 사용하며, 변수 값을 다시 업데이트 할 때는 `let`을 사용하지 않는다.

## Boolean

```jsx
// boolean
// user log in?? - true or false
const amIFat = true;

// nothing here
// null은 자연적으로 발생하지 않는다
const none = null;

// undefined
// 메모리에 존재하지만 값이 정의되지 않음
let something;
```

`boolean`타입은 `true`와 `false`가 있고, 값이 비어있는 경우인 `null`이 있다. `undefined`는 메모리에 존재하지만 값이 정의되지 않은 경우이다.

## Array

```jsx
const daysOfWeek = ["mon", "tue", "wed", "thu", "fri", "sat", "sun"];
// get value from array
console.log(daysOfWeek[5]);

// add element
daysOfWeek.push("push");
```

배열을 선언하는 방법은 다른 프로그래밍 언어와 비슷하다. `[]`안에 값들을 나열한다. 배열에서 값을 얻기 위해 `daysOfWeek[5]`와 같이 배열의 인덱스를 사용한다. `push()`를 사용해 배열의 마지막에 원하는 값을 추가할 수 있다.

## Object

```jsx
// object
const player = {
    // write property
    name: "nico",
    points: 10,
    fat: true,
};

console.log(player["name"]);
console.log(player.name);

// update property
// object가 constant인 것이며, property는 수정이 가능하다
player.fat = false;

// add property
player.lastname = "potato";
console.log(player);

// 간결한 메소드
const id = "id";
const userName = "user";

const user = {
    id,
    userName,
    info: function () {
        console.log("hello: " + this.id);
    },
};

user.info();
```

`object`는 파이썬에서 딕셔너리와 같은 역할을 한다. `{}`를 사용해 정의할 수 있다. 위 코드에서 `player`는 `object`, `player`를 구성하는 값들은 `property`라고 한다. `object`가 `const`로 선언이 되어 있어도 `property`는 수정이 가능하다. 원하는 `property`의 값을 호출하고 싶으면 `player[]`이나 `player.name`으로 호출할 수 있다. 같은 방법으로 `property`를 추가할 수 있다.

속성과 변수의 이름이 같은 경우 `id: id` 를 `id,` 로 사용할 수 있다.

## Function

```jsx
function hello(nameOfPerson, age) {
    console.log("hello my name is " + nameOfPerson);
    console.log("my age is " + age);
}

hello("lee", 20);

const player = {
    name: "nico",
    sayHello: function (otherPersonsName) {
        console.log("hello " + otherPersonsName);
    },
};

console.log(player.name);
player.sayHello("lynn");
```

함수는 `function name() {}`형태로 구성된다. `name(params)`처럼 괄호 안에 인자를 받아 함수 안에서 사용할 수 있다. 함수의 호출 방식은 `name()`이다.
한 가지 특이한 점이 있다면, `object`내에서도 함수 선언이 가능하다는 것이다. `property`로 함수를 사용할 수 있다.

# Destructuring Assignment(구조 분해 할당)

```jsx
const userObject = {
    id: "id",
    userName: "userName",
};

let { id, userName } = userObject;

console.log(id); // id

function testFunction({ id, userName }) {
    console.log(id + " " + userName);
}
testFunction({ id, userName });
// id userName
```

구조 분해 할당은 위 코드와 같이 객체의 속성 이름과 변수명이 같은 경우 사용할 수 있다.

함수의 파라미터로 넣는 경우에도 파라미터 이름과 변수명이 같고, `{}` 에 넣어주면 구조 분해 할당을 사용해 변수를 사용할 수 있다.

## Spread 연산자

```jsx
let arr = { val1: "val1", val2: "val2", val3: "val3" };
const { val1, ...remain } = arr;

console.log(val1);
console.log(remain);
// val1
// { val2: 'val2', val3: 'val3' }
```

spread 연산자 `…`으로 구조 분해 할당과 함께 사용할 수 있다. 속성 이름과 같이 사용하고 나머지 값들은 `…remain`으로 할당된다.

## Arrow function과 Default parameter

```jsx
const defaultFunction = (msg = "hello world") => {
    console.log("parameter: " + msg);
};

defaultFunction();
defaultFunction("안녕하세요");
// parameter: hello world
// parameter: 안녕하세요
```

Arrow function은 위 코드와 같이 사용할 수 있다.

default parameter 는 parameter 받는 부분에 값을 넣어주게되면 함수 호출 시 인자가 주어지면 해당 인자를 사용하고 인자가 없다면 default parameter를 사용한다.

## Backtick

```jsx
console.log(`backtick with variable ${userName} and ${id}`);
// backtick with variable userName and id
```

``백틱을 사용하면 문자열 내에`${}`를 사용해 변수를 넣을 수 있다.

## module

```jsx
exports.sign = user => {
    const payload = {
        id: user._id,
    };
    return jwt.sign(payload, secret, {
        algorithm: "HS256",
        expiresIn: "1h",
    });
};

exports.verify = token => {
    let decoded = null;
    try {
        decoded = jwt.verify(token, secret);
        return {
            ok: true,
            id: decoded.id,
        };
    } catch (error) {
        return {
            ok: false,
            message: error.message,
        };
    }
};
```

```jsx
import { sign, verify } from "../utils/jwt-utils";
...
```

module scope에 선언된 이름은 export 해서 사용해야 한다. 위 코드처럼 `export.functionName`으로 함수 하나를 export할 수 있다. 다른 파일에서 사용할 경우 `import { sign, verify } from “file 경로”;` 처럼 사용할 수 있다.

export default를 사용하는 경우 해당 모듈에서 `export default () {}` 내에 있는 변수나 함수만 export 된다.
