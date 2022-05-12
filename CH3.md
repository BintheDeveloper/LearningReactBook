### 자바스크립트를 활용한 함수형 프로그래밍
---
- 함수가 1급 시민이 되려면 변수에 함수를 대입할 수 있고, 함수를 다른 함수에 인자로 넘길 수 있으며, 함수에서 함수를 만들어서 반환할 수 있어야 한다. 일급 시민이라는 말은 정수나 문자열 같은 다른 일반적인 값과 마찬가지로 함수를 취급할 수 있다는 뜻이다. 

```
const obj = {
  message: "함수를 다른 값과 마찬가지로 객체에 추가할 수도 있습니다.",
  log(message) {
    console.log(message);
  }
}
obj.log(obj.message);
//함수를 다른 값과 마찬가지로 객체에 추가할 수도 있습니다.

const messages = [
  "함수를 배열에 넣을 수도 있습니다.",
  message => console.log(message)
]

message[1](message[0]) // 함수를 배열에 넣을 수도 있습니다.
```

```
const insideFn = logger => {
  logger("함수를 다른 함수에 인자로 넘길수도 있습니다.");
};

insideFn(message => console.log(message));

//함수를 다른 함수에 인자로 넘길수도 있습니다.
```

- 함수가 함수를 반환할 수도 있다. <span style="color:red;">이 예제의 위 아래는 어렵다.</span>
```
const createScream = function(logger) {
  return function(message){
    logger(message.toUpperCase()+"!!!")
  };
};

const scream = createScream(message => console.log(message));

scream('createScream은 함수를 반환합니다.');
// CREATESCREAM은 함수를 반환합니다.
```
- 자바스크립트에서는 함수가 일급 시민이기 때문에, 자바스크립트를 함수형 언어라고 말할 수 있다.

- 함수형 프로그래밍은 <strong>선언적 프로그래밍</strong>이라는 더 넓은 프로그래밍 패러다임의 한 가지이다. 
- 선언적 프로그래밍은 필요한 것이 어떤 것인지를 기술하는 과정에 더 방점을 두고 애플리케이션 구조를 세워나가나는 프로그래밍 스타일이다.
- 이에 반해 명령형 프로그래밍은 코드로 원하는 결과를 달성해 나가는 과정에만 관심을 두는 프로그래밍 스타일이다.

 - 선언적 방식이 더 읽기 쉽고, 더 추론하기 쉽다. 각 함수의 구현 방식은 함수라는 추상화 아래에 감춰진다. 더 자세한 정보는 <a href="https://oreil.ly/7MbkB">위키</a>에서 찾아볼 수 있다.

  <br/>

- 함수형 프로그래밍의 개념

|이름|내용|
|------|---|
|불변성|함수형 프로그래밍에서는 데이터가 변할 수 없다.|
|순수 함수| 파라미터에 의해서만 반환값이 결정되는 함수를 뜻한다. 순수 함수는 최소한 하나 이상의 인수를 받고, 인자가 같으면 항상 같은 값이나 함수를 반환한다. <span style="background-color:#fff5b1; color:black">순수 함수에는 부수효과(side effect)가 없다</span>. 리액트에서는 UI를 순수 함수로 표현한다|
|안녕| 안녕|

```
const frederick = {
  name:"Frederick",
  canRead: false,
  canWrite: false
};

function selfEducate() {
  frederick.canRead = true;
  frederick.canWrite = true;
  return frederick;
}

selfEducate();

//순수하지 않은 함수의 예시
```
- 데이터가 변경 불가능하다면 애플리케이션에서 어떻게 무언가를 바꿀 수 있을까? map, reduce 두 함수를 이용한다.

|함수|기능|
|---|---|
|join| 배열의 모든 원소를 인자로 받은 구분자로 연결한 문자열을 반환한다. 원래의 배열은 그대로 남는다. (배열에 대한 다른 해석을 제공할 뿐이다. 실제로 어떻게 만드는지는 신경쓰지 않는다. - <span style="color:yellow">선언적</span>)|
|filter| <strong>술어</strong>를 유일한 인자로 받는다. 술어는 boolean 값, 즉 true나 false를 반환하는 함수를 뜻한다.|
|map|술어가 아니라 <strong>변환 함수</strong>를 인자로 받는다. 그 함수를 배열의 모든 원소에 적용해서 반환받은 값으로 이뤄진 새 배열을 반환한다. map 함수는 객체, 값, 배열, 다른 함수 등 모든 자바스크립트 타입의 값으로 이뤄진 배열을 만들 수 있다.

```
const highSchools = schools.map(school => ({name:school}));

console.log(highSchools);

//[
//{name: "Yorktown"},
//{name: "Washington  & Lee"},
//{name: "Wakefield"},
//]

// 객체로 이루어진 배열을 반환하는 map 함수
```

```
const editName = (oldName, name, arr) => 
  arr.map(item => {
    if (item.name === oldName) {
      return {
        ...item,
        name
      };
    } else {
      return item;
    }
  });

  //위의 함수는 다음과 동일하다.

  const editName = (oldName, name, arr) =>
    arr.map(item => (item.name === oldName ? {...item, name} : item))
```

<strong>74쪽에서 계속</strong>