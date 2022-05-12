### 리액트를 위한 자바스크립트
---
- if/else 블록 안에서 변수를 새로 만들면, 그 변수의 영역이 그 블록 안으로만 한정되지 않는다.

- let 키워드를 사용하면, 변수의 영역을 코드 블록 안으로 한정시킬 수 있다. let을 사용하면 블록 안에서 글로벌 변수를 보호할 수 있다.

- 중괄호가 새로운 영역을 만들어내지 못하는 다른 부분으로는 for 루프가 있다. for 루프 안에서 i를 선언해도 글로벌 영역에 i가 생긴다. <br>
=> let을 사용하면 영역이 블록으로 제한된다.

- 템플릿 문자열은 공백을 유지해줌.

- 함수 선언 또는 함수 정의는 
```
function logCompliment() {
  console.log("잘했어요!");
}
logCompliment()
```

- 함수 표현식은
```
const logCompliment = function() {
  console.log("잘했어요!");
};
logCompliment();
```

- 함수 선언은 호이스팅되지만 함수 표현식은 호이스팅되지 않는다. 즉, 함수 선언을 작성하기 전에 함수를 호출해도 된다. 

- 값을 돌려받기 위해 함수를 호출한다. 함수에 return문을 추가하면 된다. 

- ES6 명세에는 디폴트 파라미터<sup>default parameter</sup>가 추가됐다. 함수를 호출하면서 인자값을 지정하지 않으면 디폴트 값이 쓰인다. 

- 화살표 함수를 사용하면 function 키워드 없이도 함수를 만들 수 있다. 또한 return을 사용하지 않아도 식을 계산한 값이 자동으로 반환된다. 

```
const lordify = function(firstname) {
  return `켄터베리의 ${firstname}`;
}

const lordify = firstname => `켄터베리의 ${firstname}`;
```

- 하지만 결과를 계산하기 위해 여러 줄을 사용해야 한다면 중괄호로 함수 본문 전체를 둘러싸야 한다. 
```
const lordify = (firstname, land) => {
  //함수 식
}
```

- 객체를 반환하고 싶으면 어떻게 해야 할까? 반환하려는 객체를 괄호로 둘러싸면 된다. (<span style="background-color:#fff5b1; color:black">자주 하는 실수이므로 꼭 기억해야 한다!</span>)
```
const person = (firstName, lastName) => ({
  first: firstName,
  last: lastName
});
```

<strong>화살표 함수와 영역에서 계속</strong>

