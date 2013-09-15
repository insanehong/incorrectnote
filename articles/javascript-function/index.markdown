{
    "title": "Function Declarations(함수선언) vs Function Expressions(함수표현)",
    "author": "Insanehong",
    "date": "2012-08-15T00:55:35.753Z",
    "categories": [
        "javascript"
    ],
    "tags": [
        "javascript",
	"function declarations",
	"function expression",
	"함수선언",
	"함수표현",
	"자바스크립트"
    ],
    "acceptComment": true,
    "acceptTrackback": true,
    "published": "2012-08-15T00:55:35.753Z",
    "status": "publish",
    "important": false,
    "advanced": {}
}

# 소개
이번 글은 `function`이란 주제를 다뤄볼가 한다.  javascript에서 function 은 매우 중요한 녀석이다. 특히 객체를 다루면서 이 function은 절대 빠질수도 빠져서도 안되며 이에 대한 이해가 없다면 javascript 객체에 대한 이해를 제대로 하지 못할 것이다. 그런 이유로 이 글은  Object에 대해 다루기전에 다뤘다면 더 좋았을 거라 생각하지만 사실 자바스크립트에는 연관된 내용이 너무 많은 탓이라며 스스로를 위로하고 있다. 하지만 너무 늦기전에 function에 대한 썰을 풀어놔야 앞으로 연재될 `Execution Context`와 `this`,`closure` 를 이해 할 수 있기에 이번 글을 통해 자바스크립트에서의 function에 사용에 대해 알아보도록 하겠다. 

# Function at javascript

## 자바스크립트에서의 function 이란?
>독립적으로 분리된 로직으로서 프로그램 수준에서 미리 정의되어 있거나 사용자정의에 의해 만들어진 실행단위를 일컫는 말이다. 자바스크립트의 function은 `Fisrt-Class-Object` 로서 **변수나 데이터 구조 안에 담을 수 있으며 인자로 전달할 수 있고 반환 값으로도 사용할 수 있으며 , 런타임에 생성할 수 도 있다.** 

이처럼 자바스크립트에서 function은 `Fisrt-Class-Object` 이면서  모든 함수객체의 프로토타입인 Function Prototype Object의 생성자 함수가 가리키는 class 개념이기도 하다. **function 또한 일반 객체처럼 취급**될 수 있다. 그래서 **익명함수를 비동기 함수의 `callback` 과 같은 형식으로 넘길 수 있는 것**이다. 

이런 함수에 대해 알아보기 전에 반드시 집고 넘어가야하는 것이 있다. 바로 `함수선언(Function Declarations)` 과 `함수표현(Function Expressions)`에 대한 구분이다.

## 함수선언(Function Declarations) 이란?
>함수선언은 `Function Statement` 라고도 하며 말그대로 함수 문장이란 뜻이다. 이는 곧  실행가능한 코드블럭이 아니며 함수의 정의를 나타내는 문장으로 해석되며 따라서 코드해석에 따른 수행결과가 존재하지 않는다는 것을 의미한다.

`Statement` 라는 개념을 잘 집고 넘어가야 한다. 함수 선언문이 `Statement` 라고 하는 말은 정의에서 밝힌것 처럼 코드블럭 자체는 **실행가능 코드가 아니라는 것**이다. 즉 해당 코드블럭을 **콘솔에서 실행하여도 어떠한 결과도 return 되지 않는다**. 그러한 이유로 함수선언문을 Class와 동일한 개념으로 이해해도 무방하다. 

```javascript
//Function Declarations
function foo() {
    console.log('hello');
}
```

이러한 statement 는 console 에서 실행을 시켜도 아무런 결과를 반환하지 않는다.
 
![return](./@img/state.jpeg)

## 함수표현(Function Expressions) 이란?
>함수표현은 `Function Literal` 이다 이는 실행 가능한 코드로 해석 되어지거나 변수나 데이터구조에 할당되어지고 있음을 의미한다. 즉 해당 코드블럭이 실행코드로서 해석되어지며 동시에 코드실행에 따른 결과값을 가지거나 특정 변수에 할당된 값으로 존재한다. 

이처럼 함수표현은 함수리터럴로  특정변수에 할당되거나 즉시 실행가능한 코드 블럭으로서 존재하는 함수를 의미하는 것이다. 함수표현이 실행코드로서 해석되기 위해서는 ()를 이용하여 함수를 감싸 주어야 한다. 이를 `자기호출함수(self invoking function)` 라고도 한다. 자기호출함수는 **재귀함수와는 다른 개념**이다. 재귀함수는 함수 안에서 자신을 호출하는 형식이지만 자기호출함수는 **해석과 동시에 실행되는 코드블럭**을 말한다. 

```javascript
//anonymous function expression
var foo = function() {
    console.log('hello');
};

//named function expression
var foo = function foo() {
    console.log('hello');
};

// self invoking function expression
(function foo() {
    console.log('hello');
})();
```
위 코드에서` named function expression`는 매우 특이하다. foo 라는 변수에 이름있는 함수를 할당하고 있다. 흔히 알고 있는 함수리터럴과는 좀 거리가 있다. 하지만 이 `named function expression`에는 한가지 특징이 있다. 바로 해당 함수의 이름은 함수밖에서는 사용할수 없다는 것이다. 

```javascript
var foo = function A() {
    A(); // 실행가능 
}

A(); //  Syntax Error
```
**즉 재귀호출외에는 그다지 쓸대가 없다.** 하지만 이런 표현식이 가능하다는 것은 알고 있다고 나쁠것은 없지 않은가? 함수표현은 자기호출함수을 이용하여 콘솔에서 실행결과를 받을 수 있다. 

![return](./@img/func.jpeg)

이들 함수선언과 함수표현은 함수호출 방법에서는 큰 차이가 없다. 하지만 **호이스팅(hoisting) 관점에서는 큰 차이 **를 보이게 된다.

# 호이스팅(hoisting) 이란
>인터프린터가 자바스크립트 코드를 해석함에 있어서 **Global 영역의 선언된 코드블럭을 최상의 Scope로 끌어올리는 것**을 호이스팅이라 한다. 

즉 Global 영역에 선언된 변수 또는 함수는 자바사크립트 엔진이 가장 먼저 해석하게 된다. 단 할당구문은 런타임과정 이루어지기 때문에 hosting 되지 않는다. 

이 정의가 다소 어려울수도 있다. 하지만 단순하게 **선언문은 항시 자바스크립트 엔진 구동시 가장 최우선으로 해석**한다고 이해하면 쉬울 것이다. 즉 인터프린터가 자바스크립트의 코드를 해석하면서 코드작성 순서에 상관없이 global 영역에 선언되어 있는 변수나 함수의 선언문들을 먼저 수집하여 전역객체의 속성으로 등록시켜 둔다는 것이다. 그렇기 때문에 전역변수와 전역함수는 자바스크립트 코드의 어떠한 위치에서도 실행이 가능한 것이다. 

하지만 같은 이유로 너무 많은 선언문이 남발되어 있는 자바스크립트 코드는 실행코드의 해석시점이 뒤로 밀리게 됨으로서 자바스크립트 실행코드의 구동시점이 길어지는 좋지않는 결과를 가져오기도 한다.

이 hoisting에서 중요한 부분은 **statement 는 hoisting 되지만 할당은 hoisting 되지 않는 다는 것**이다. 즉 {} 안의 내용은 포함하지만 = 연사자를 사용한 값은 hoisting 되지 않는다. 

```javascript
//#예제 1 : 함수선언에서의  호이스팅
foo();
function foo() {
    console.log('hello');
};
> hello

//#예제 2 : 함수표현에서의  호이스팅
foo();
var foo = function() {
    console.log('hello');
};
> Syntax Error 
```

위 코드에서 알수 있듯이 함수선언은 foo(); 라는 실행코드를 해석하기 이전에 foo 함수에 대한 선언을 호이스팅하여 global 객체에 등록시키기 때문에 오류 없이 수행된다. 하지만 함수표현은 변수에 `함수리터럴을 할당`하는 구조이기 때문에 Hoisting  되지 않으며 `Syntax Error` 를 발생시킨다. 

이러한 Hoisting은 자바스크립트 코드를 사람이 해석하는데 많은 혼란을 주게 된다. 그런 이유로 자바스크립트 코드를 작성할대 **선언문은 항상 최상위에서 작성하는 것을 권고**하고 있다. 

그럼 지금까지 이해한 내용을 가지고 아래의 퀴즈들을 풀어보도록 하자. 아래의 퀴즈들을 보고 바로 답이 나온다면 더이상 이글을 읽을 필요는 없을 것이다. 

## Hoisting Question
```javascript
//Question 1:
function foo(){
    function bar() {
        console.log('hello');
    }

    return bar();

    function bar() {
        console.log('world');
    }
}
foo();

//Question 2:
function foo(){
    var bar= function() {
        console.log('hello');
    };
    return bar();
    var bar = function() {
         console.log('world');
    };
}
foo();
```

## Hoisting Question 폴이
### Question 1. 풀이
```javascript
function foo(){
    function bar() {
        console.log('hello');
    }

    return bar();

    function bar() {
        console.log('world');
    }
}
foo();
```
자바스크립트 엔진이 구동되는 시점에 global 영역에 선언된 foo 함수를  hoisting 한다. 이때 foo의 statement 인 {} 블럭안의 내용 또한 같이 따라 올라간다. 런타임에서 해석되는 실행코드보다 선언문이 먼저 해석되기 때문에 return bar(); 라는 실행문이 해석되기 전에 function bar()로 선언된 함수선언문이 먼저 해석 되어 지고 두번째로 선언된 bar 함수 역시 return 구문보다 먼저 해석되어 진다. 그렇기 때문에 퀴즈 1번에서 실행코드를 만나기 전까지 자바스크립트가 해석한 foo함수는 아래와 같다. 

```javascript
function foo(){
    function bar() {
        console.log('hello');
    }
    
   function bar() {
        console.log('world');
    }
    return bar();
}
```

foo() 호출되고 런타임 과정에서 return bar() 라는 실행문은 가장 나중에 선언된 함수를 실행하게 되고 **'world'**를 출력한다. 여기까지 이해가 완벽하게 되었다면 너무 당연하겠지만 같은 이유로 아래의 코드 역시 정상적으로 실행되며 **'world'**를 출력한다. 

```javascript
foo();
function foo(){
    function bar() {
        console.log('hello');
    }
    return bar();    
   function bar() {
        console.log('world');
    }

}
```

### Question 2. 풀이
```javascript
function foo(){
    var bar= function() {
        console.log('hello');
    };
    return bar();
    var bar = function() {
         console.log('world');
    };
}
foo();
```

2번 퀴즈에서 역시 foo 함수는 hoisting 되어 런타임이전에 미리 해석되어 진다. 하지만 {}안에 작성된 var bar 라는 변수는 함수리터럴을 할당받고 있다. 할당은 런타임 시점에서 이루어지고 자바스크립트 엔진은 런타임 이전까지는 강제적으로 undefinde 를 할당하게 된다. 즉 hoisting 되어진 foo 함수안에 구조는 실행코드를 만나기 전까지는 아래와 같이 해석되어 진다. 

```javascript
function foo(){
    var bar= undefined;
    var bar= undefined;
    bar= function() {
        console.log('hello');
    };
   return bar();
}
```

2번째로 작성된 함수표현식은 실행조차 되지 않는다. 런타임에서는 자바스크립트 엔진이 해석한 순서로 실행되기 때문에 할당구문보다 먼저 return 이 실행되어 버린다. 그렇기 때문에 2번 퀴즈는 **'hello'** 를 출력한다. 같은 이유로 아래의 코드는 Syntax Error 를 뱉어내게 된다. 

```javascript
function foo(){
   return bar(); 
   var bar= function() {
        console.log('hello');
    };
    var bar = function() {
         console.log('world');
    };
}
foo();
```

# 갈무리
이번 글에서는 함수선언과 함수표현의 차이와 호이스팅에 대해 알아보았다. 사실 호이스팅을 사용한 코드작성은 절대 추천하고 싶지 않다. 코드 가독성이 너무나도 떨어지게 되어 코드를 해석하는데 있어 혼란을 격게 될수도 있기 때문이다. 하지만 이번 글에서 이해한 함수선언과 함수표현은 후에 연재될 Excution Context 를 이해하는데 있어 필수적인 요소중 하나다. 그러니 이번글을 읽고 이해가 잘안된다면 차분한 마음으로 다시 읽어보거나 더 싶게 풀이된 다른 레퍼런스를 찾아보길 바란다. 다음 연재인 function #2는 `arguments` 객체와 `Constructor` 가 될것이다. 

**by Insanehong**
