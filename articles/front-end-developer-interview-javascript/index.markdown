{
    "title": "front-end 개발자 인터뷰 문제 - javascript 영역",
    "author": "Insanehong",
    "date": "2013-05-12T02:57:41.466Z",
    "categories": [
        "reference"
    ],
    "tags": [
        "font-end",
        "interview",
        "javascript"
    ],
    "acceptComment": true,
    "acceptTrackback": true,
    "published": "2013-05-12T02:57:41.466Z",
    "status": "publish",
    "important": false,
    "advanced": {}
}

이글은 이전 [front-end 개발자 인터뷰 문제 - html 영역](http://insanehong.kr/post/front-end-developer-interview-html) 에 이은 `javascript  문제`에 대한 글이다. 

이글을 처음 보게 된다면 이전글을 먼저 읽어보길 바란다. 

# Javascript에 관련된 질문들

## 1. Java와 Javascript의 다른 점은 무엇인가요?
Javascript 는 애당초 Java 애플릿의 대체자로 만들어지게 된 배경으로 javascript 라는 이름이 사용될뿐 전혀 연관성이 없는 언어이다. 

* java 는 `typed static` 언어인 반면 javascript는   `none typed` 언어로서 동적으로 자료형을 검사하게 된다. 
* java는 class 기반 컴파일+인터프린트 oop 언어이지만 javascript 는 prototype 기반의 인터프린트 언어이다. 
* javascript 는 스크립트 언어의 특성상 컴파일 없이 동작하게 됨으로 언어를 번역할수 있는 엔진이 동적으로 모든 사항을 처리하기 때문에 컴파일 언어에 비해 실행이 늦거나 실행이전에 오류 검출이 용이하지 않다. 
 
## 2. undefined와 undeclared 변수는 무엇인가요?
Javascript는 `undefined` 라는 특별한 형태가 존재한다. javascript를 대충 공부하게 되면 `undefined` 와 `null` 의 차이를 잘 이해하지 못하는 경우도 많다. 

모든것이 object 로 통하는 javascript 에서의 `null`  은 값이 아닌 객체 참조의 연결을 해지하는 것을 말한다. 즉 어떤 참조값이 존재 하지 않음으로 비어있는 값을 가진 변수가 되는 것이다. 

undefined 는  선언만 되어지고 특정 값이 할당되지 않는 경우 javascript 엔진에 의해 자동으로 할당되는 값이다. 즉 특별히 할당된 값이 없는경우 일반적인 언어처럼 null 이 아니고 undefiend  가 할당 되는 것이다. 

또한  객체가 소유하지 않은  프로퍼티에 접근하게 될 경우에도  undefined 가 반환된다. 

`undeclared` 변수란 선언하지 않고도 사용가능한 변수라고 한다. 하지만 정확히는 이는 javascript 의  scope 개념에서 따져보면 유효범위를 지정하지 않은 변수다. 

javascript는 `none typed` 언어로서  `var` 라는 키워드를 사용하여 변수를 사용하는게 보편적으로 알려져 있는 사실이다. 

하지만 이 `var`  키워드는 선언을 위한 키워드가 아니고 해당 변수의 유효범위를 지정하는 역활을 한다. 해당 키워드를 지정하지 않은 변수는 global scope  에 저장 된다. 하지만 여기에는 한가지 제약사항이 따른다. 

var  키워드 없이 사용된 변수는 할당문을 만나기전에 해당 변수에 참조를 만나면 오류를 내뱉게 된다. 

```
foo = 1;
console.log(foo+2);
>3

console.log(foo+2);
foo=1;
> Uncaught ReferenceError: foo is not defined

```

javascript 자료형에 대한 정리는 [Javascript기초 - 데이터타입](http://insanehong.kr/post/javascript-datatype/) 에 정리해 놓았으니 참고 하길 바란다. 

## 3. 클로져(Closure)는 무엇이며, 어떻게/왜 사용하는지 설명해주세요
클로져를 제대로 이해하기 위해서는 javascript 의 `scope`,  `scope chain`,  `context` 에 대한 이해가 선행 되어야 한다.

간단히 설명하자면 클로저는 현재의 유효범위를 넘어 scope chain으로 연결되어 있는 객체,변수등의 참조를 발생시키는 것을 말한다. 

javascript는 실행코드 블럭 단위로 context 를 스텍에 쌓게 되고 push, pop 을 통해 코드블럭이 실행 된다. 이때 각각의 실행 코드블럭이 수행되는 시점에서 실행 환경을 저장하게 되는데 이는 실행 유효범위인 scope 에 의해 결정된다. 

이 scope 는 chain구조로 연결되어 있어 현재 실행 시점 이전의 scope 를 타고 올라가는 형태로 참조 되기 때문에 현재 scope 에 선언되지 않는 객체참조가 가능하다. 

이는 java 등의 언어만 다루던 사람들에겐 좀 의아한 모습으로 동작한다. local 변수와 global 변수의 경계와 유요범위 설정에 대한 이해를 한번에 무너트려버리기 때문이다. 

## 4. 익명함수\(anonymous function\)는 주로 어떤 상황에서 사용하나요?
익명함수의 사용은 함수 선언이 아닌 함수표현식을 이용하는 방법이다. 이는 곧 람다함수(함수 리터럴을 변수에 할당하는 방식)와  즉시실행구문을 만들어 낼수 있다는 말이다. 

이처럼 즉시실행 구문을 사용하면 javascript 가  유효범위를 선언 할 수 없다고 해도 강제적으로 private 변수를 만들어 내는 것이 가능 하다. 

```javascript
// i 라는 변수는 실행 시점에서만 사용되면 외부에서 접근 할수 없다. 
(function() {
   var i  = 'hello world' ;
    
{)();

console.log(i)
> error
```

즉 익명함수는 동적으로 할당되는 유효범위를 가지기 때문에 javascript 내에서 강제적인  유효범위 설정을 하는 경우 사용되게 됩니다. 

## 5. "Javascript 모듈 패턴(Javascript module pattern)"이 무엇인지 설명을 해주시고, 언제 사용하는지도 말씀해주시기 바랍니다.

javascript 의 모듈 패턴은 javascript 의 코드 관리 기법 중하나로서 javascript의 특성상 객체 핸들링을 위한 방법론중 하나이다. 

javascript 의 모듈 패턴은 일반적인 유효범위를 설정하는 언어에서와 같이 private 와 public 등의 캡슐화를 사용하는 방법이다. 

javascript 에서 함수 혹은 변수객체를 다룰때 중복된 name 사용으로 인한 문제를 방지하기 위해 주로  namespace 방법이 사용된다. 이는 global 영역에 객체 고유의 영역을 지정하고 변수와 함수 할당을 해당 namespace  하위로 두게 하여 중복된 name  으로 인한 오류를 피하는 방법이다. 

모듈 페턴은 이 네임스페이스 페턴에 언어적 유효범위를 추가 해논 것이라 이해하면 슆다. 

모듈을 작성함에 있어서 return  구문을 이용하여 공개될 영역과 내부적으로 처리할 영역을 구분하여 공개여부를 선택하게 하는 것이다. 

``` javascript
// namespace 패턴
var myApp = myApp || {}; // 네임 스페이스 선언

myApp.insanehong = function() {
	return 'insanehong';
};

myApp.helloworld = function() {
	return 'hello world';
}

// 모듈 페턴


var Messages = {h : 'hello', w : 'world', insane:'insanehong'};

var myApp = (function(msg) {
  var helloworld = msg.h+'  '+msg.w;
  var helloinsanehong = msg.h+' '+msg.insane;
  
  var printInsane = function () {
     return helloinsanehong;
  };
  
  var printhello = function() {
    return helloworld;
  };  
  
  return {
    foo1 : printInsane,
    foo2 : printhello
  };

})(Messages);


console.log(myApp.foo1());
> hello insanehong
console.log(myApp.helloworld);
> undefined
```

##  6. 호스트 객체\(Host Objects\)와 네이티브 객체\(Native Objects\)의 차이점은 무엇인가요?
네이티브 객체는 브라우저 혹은 구동 엔진에 내장되어 있는 객체를 말한다. 네이티브 객체는  built-in  객체와 달리 자바스크립트 엔진이 구성하고 있는 기본객체라고 하기보단 브라우저 혹은 사용되는 자바스크립트 엔진에 영향을 많이 받게 된다. B.O.M  이라는 브라우저객체 모델과 D.O.M  이라는 문서 객체 모델이 네이티브 객체에 포함되는데 이 객체의 사용성이 이를 구현한 구동엔진에 따라 각기 다르게 존재하는 경우가 있기 때문에 크로스 브라우징에 문제를 발생시키기도 한다. 

호스트 객체는 빌트인 객체와 네이티브객체에 포함되지 않은 사용자에 의해 생성된 객체를 의미한다. 자바스크립트 엔진은 빌트인 객체와 네이티브 객체를 구성한 이후 호스트객체를 해석하게 된다. 

## 7. 다음 코드의 차이점은 무엇인가요? javascript function Person\(\){}, var person = Person\(\), var person = new Person()

```javascript
function Person() {
  return 'hello world'; 
}
```
위 코드는 함수 선언이다. 이는 함수 객체 생성을 위한 기본 그릇이 되면 prototype 이 참조할 함수객체의 환경을 담고 있다. 
global scope 에서는 Person 이라는 함수가 선언되었다는 것만을 저장하면 내부구현 로직은 알지 못한다. 

`var person = Parson();` 은 함수 수행에 따른 return 을 변수에 저장한다는 의미이다. 즉 person 에는 'hello world' 가 할당된다. 

`var person = new Person()` 은 person  변수에  Person 함수 객체를 생성하여 할당한다는 의미가 된다. 이때 할달되는 객체는 Person 함수의 프로토타입을 기반으로 생성된다. 

## 8. .call과 .apply의 차이점은 무엇인가요?

Function.prototype 이 소유한 method 들이다. 이들은 함수와 메서드가 실행될 때 바인딩할 객체를 지정하여 함수가 실행될때의 context 의 유요범위를 직접 지정하며 this 를 할당 할수 있다. 

이들은 호출의 동적인 변화에 따라 각각 다르게 되는데 정적인 호출인 경우 call 을 동적인  호출에서는 apply를 사용하게 된다. 
즉 호출시 동적인 인자전달등이 필요할 경우 apply 를 정적으로 고정된 함수를 호출할 경우 call 사용하면 된다. 

bind() 메소드나 동적 callback 을 구현할때 apply가 사용되는 이유이기도 한다.  

## 9. Function.prototype.bind을 설명 하시오
8번 문제에서 잠깐 다루었던 내용과 비슷하다. 함수객체는 실행 시점에서 execution context 를 생성하며 현재의 실행 코드 범위를 뜻하는 this 를 할당하게 된다. 하지만 this 를 동적으로 할당해야 하는 경우가 있다. 특히 다양한 객체에서 동적으로 특정 액션을 할당하여 사용되는 함수의 경우 this 에 할당되는 객체를 예측하기가 힘들다. 

이럴때 bind 를 이용하여 실행 시점에서  context의  this 를 임의로  할당 해 주어 동적인 호출시에도 오류 없이 코드가 동작하게 할수 있다.  

ECMA-262, 5th edition 에 의하면 Function.prototype.bind()는 아래 코드와 같이 구현되어 있다. 

```javascript
if (!Function.prototype.bind) {
    Function.prototype.bind = function() {
        var funcObj = this;
        var original = funcObj;
        var extraArgs = Array.prototype.slice.call(arguments);
        var thisObj = extraArgs.shift();
        var func = function() {
            var thatObj = thisObj;
            return original.apply(thatObj, extraArgs.concat(
                Array.prototype.slice.call(
                    arguments, extraArgs.length
                )
            ));
        };
        func.bind = function() {
            var args = Array.prototype.slice.call(arguments);
            return Function.prototype.bind.apply(funcObj, args);
        }
        return func;
    };
}
```

## 10. Javascript에서 어떻게 상속을 하는지 설명할 수 있나요?
Javascript 는 공식적으로 상속을 지원하지 않는 프로토타입 기반 객체 확장을 지원하는 언어이다. 
이런 이유로 직접적인 상속을 구현 할수는 없지만 프로토타입 확장을 이용한 상속과 같은 의미를 구현해 낼수는 있다. 

간단한 prototype 을 이용한 상속 개념은 아래와 같이 구현 낼수 있다. 

```javascript

function Parent() {
  this.hello ='hello';
}

function Child() {
  this.world = 'world'; 
  this.helloworld = this.hello+' '+this.world;
}

Child.prototype = new Parent();
Child.prototype.constructor = Child;

var Obj = new Child();

console.log(Obj.helloworld);

```


prototype 관련 내용은 [Javascript 기초 - Object prototype 이해하기](http://insanehong.kr/post/javascript-prototype/) 을 참조하기 바란다. 

## 11. UA문자열을 이용하여 기능 검출(feature detection)과 기능 추론(feature inference)의 차이점을 설명 하시오.

사실 이문제는 제대로 의도를 파악하지 못했다. 다만 User-Agent 를 이용하여 네이티브 객체를 선택하는 것과 네이티브객체의 유무를 검사하여 분기처리하는 것으로 생각하였다. 

User-Agent는 브라우저 별로 공통적인 부분과 독립적인 요소로 나누어지게 되어 구동 엔진을 무엇을 선택하였는가를 알아낼수 있다. 이를 이용하여 이벤트 리스너 등과 같은 브라우저마다 각기 다른 방식으로 구현된 네이티브 객체(함수등)을 분기하여 처리 할수도 있으며 네이티브객체의 존재유무를 검사하여 해당 엔진이 해석가능한 객체 호출을 하는 방법등으로 크로스 브라우징문제를 해결하게 된다. 

## AJAX에 관해 가능한 자세히 설명하세요.
Asynchronous JavaScript and XML 의 약자로서 XMLHttpRequest 객체를 이용하여 비동기 방식으로 서버와 통신을 하는 것을 말한다. 

웹 브라우저의 클라이언트와  서버간 통신은 url를 이용한 http 통신으로 이루어진다. 즉 브라우저가 서버로 request를 날리기 위해서는 해당 브라우저의 url 주소를 변경하여야 하는데 이때는 페이지 이동이 일어나게 된다. 

하지만  ajax 의 경우  브라우저의 url 주소의 변경을 이용하지 않고 내부적으로 통신하여 response  를 받아오기 때문에 특정 데이터만 불러오거나 비동기로 데이터를 불러와야하는 경우 사용된다. 

이때  `Same Origin Policy` 정책으로 인해 cross domain 을 허용하지 않기 때문에 외부 도메인을 사용하여야 하는경우 JSONP, XML 등을 이용하여야 한다. 

## 12 . JSONP가 어떻게 동작 되는지 설명하세요.\(그리고,실제 AJAX와 어떻게 다른지 설명하세요.\)
 
앞서서 말했듯이  Ajax 는 크로스 도메인을 허용하지 않기 때문에 이를 해결하기 위하여  JSONP 를 이용한다. 
JSONP 는 GET 요청만이 가능하다. 

JSONP 는 script 코드가 D.O.M  트리에 추가되면 실행 되어 지면 외부 스크립트를 로드 할수 있다는 것에서 착안된 것으로 동적으로 외부 스크립트를 호출하면서 callback 함수를 명시해 주면 스크립트가 실행된후 callback 함수를 실행한다는 로직으로 구성된어 있다. 

## 13. "호이스팅(Hoisting)"에 대해서 설명 하시오.
호이스팅은 자바스크립트 엔진이 실행 컨텍스트를 생성하면서 scope 를 정의 할때 기술된 순서에 상관없이 선언부에 대한 처리를 해석 우선순위 최우선으로 끌어올려 먼저 해석하는 것을 의미한다. 

싶게 말해서 코드 작성 순서에 상관없이 선언구문을 최우선으로 해석한다는 것이다. 

```
foo='hello'
console.log(foo);
var foo;
> hello

```

이때 유념해야할 것이 하나 있는데 호이스팅은 선언에만 적용되고 할당구문에는 적용되지 않는다. 

```
console.log(foo);
var foo='hello world';
>undefined
```

이처럼 선언과 동시에 값을 할당하는 경우 호이스팅 되지 않으며 해당구문을 만나야만 해석하게 된다. 

## 14. FOUC가 무엇이며 FOUC를 어떻게 방지하나요?
FOUC(Flash Of Unstyled Content)는 외부의 CSS가 불러오기 전에 잠시 스타일이 적용되지 않은 웹 페이지가 나타나는 현상이다. 이를 해결하기 위해서 CSS 관련 로딩 구문은 반드시  head  안에 포함시켜  css  로드 전에 D.O.M  트리를 구성하는 것을 방지 주는 것이 좋다. 

> 이게 왜 Javascript 영역에 있는지 잘모르겠다. 혹은 내가 잘 모르는 뭔가가 있는 듯하다. 

## 15. 이벤트 버블링(Event Bubbling)에 대해서 설명하세요.
자바스크립트의 이벤트 전파는 다음과 같은 방식을 따른다. 

1. 이벤트 발생(사용자 이벤트 혹은 강제 이벤트 할당:trigger)
2. 이벤트 발생 객체를 찾기 위하여 하위 탐색(캡쳐)
3. 이벤트 발생 객체 도달 
4. 하위 탐색의 역순으로 복귀(버블링)

 IE의 경우 위와 같은 탐색에서 캡션단계를 지원하지 않음으로 이벤트 핸들링은 버블링을 기준으로 작성되어야 한다. 
 
어찌 되었건 이벤트가 발생한 타겟에서 시작하여 상위로 해당 이벤트가 계속 해서 전파되어 버린다. 이를 버블링이라하며 이와 같은 버블링으로 인한 오작동을 방지 하기 위해서는 `stopPropagation()` 을 이용하여 이벤트 전파를 차단해 주어야 한다. 

## 16. Javascript 객체를 확장하는 것이 좋지 않은 이유.
사실 이 문제도 제대로 이해하지 못했다. 그래서 이미 정이된 객체의 prototype을 특정영역에서 변경해 버리는 것에 대한 내용을 적는다.

Javascript의  객체를 Object.prototype 을 이용해서 확장하는 것은 좋은 방법이 아니다. 이는 기본적으로 참조 무결성을 깨틀여 버리게 된다  Object.prototype 을 확장하거나 변경하는 행위는 해당  prototype을 참조로 하는 모든 객체에 영향을 미치게 된다. 즉 특정 영역에서 변경을 위해 수행된 코드로 인해 애플리케이션 전체에 영향을 주게 된다는 것이다. 

이는 극히 위험한 일이다. 상황에 따라 변형되어버리는 이런 구조로는 프로그램을 예측할수도 없을 뿐아니라 추후 코드 실행의 무결성을 보장하지 않는다. 

## 17. Document Load 이벤트와 Ready 이벤트의 차이가 무엇인가요?

두 Event 모두 D.O.M 을 다루기 위한 이벤트 이다. 하지만 두 이벤트에는 큰차이가 있다. 

Ready 이벤트의 경우 D.O.M 트리가 만들어지면 발생한다. 즉 리소스 다운로드 상태와는 상관없이 Element  구조를 형성하게 되면 발생하게 된다. 하지만 이때 사용자가 리소스 핸들링을 위한 이벤트를 발생하게 된다면 오류를 내뱉게 된다. 

하지만  load 이벤트는 페이지에 정의된 모든 리소스의 다운로드가 완료될경우 발생하게 된다. load 이벤트 이후에는 어떤 리소스로의 접근도 가능하다.

## 18. ==와 ===의 차이점은 무엇인가요?

`===`는 typeof 를 포함 한다. 즉 단순히 값이 같다는 것외에도 데이터타입도 같이 검사하게 된다. 
javascript 에서는 아래와 같은 동작을 하게 됨으로 비교연산시 주의를 요한다. 

```javascript

if('3'==3) console.log('equal');
else console.log('not equal');
>equal;

if('3'===3) console.log('equal');
else console.log('not equal');
>not equal;

```

## 19. 브라우저의 URL에서 파라메터를 얻을 수 있는 방법에 대해서 설명하세요.
var params = document.location.split('?')를 이용하면 된다. 

## 20. Javascript의 "동일출처정책(the same-origin policy)"에 대해서 설명하세
Javascript 는  스크립트가 사용자의 입력을 캐내어 다른 페이지로 흘려보내는 것을 막기 위한 보안정책으로 동일 출처 정책을 가지고 있다.

> 스크립트는 자신을 포함한 문서와 다른 서버에서 불러온 문서의 내용은 읽을 수 없다. 이와 유사하게 스크립트는 다른 서버에서 불러온 문서에는 이벤트 리스너를 등록할 수 없다. 

## 21. 이벤트 딜리게이션\(Event Delegation\)에 대해서 설명하세요.
이벤트 딜리게이션은 이벤트가 발생되어야 하는 객체에 직접적으로 이벤트를 바인딩 시키는 것이 아닌 객체 상위 요소에 이벤트를 할당하고 인자로  evne 객체를 넘겨줌으로서 실제 이벤트 타겟에 간접적으로 이벤트 바인드 효과를 주는 것을 말한다. 

이는 javascript의 이벤트 할당이 메모리에 직접적으로 올라가게 됨으로 반복적이고 과다한 이벤트 할당은 프로그램 성능적으로나 반복적인 코딩등에 문제로 많이 사용되는 이벤트 바인딩 패턴이다. 

## 22. 다음 코드를 동작하게 만드세요. javascript [1,2,3,4,5].duplicator(); // [1,2,3,4,5,1,2,3,4,5]

```javascript

Array.prototype.duplicator = function() {
   var $this = this;
   return $this.concat($this);  
};

console.log([1,2,3,4,5].duplicator() );
>[1, 2, 3, 4, 5, 1, 2, 3, 4, 5]
```

사실 문제가 너무 많아 대충 대충 적었다. 이문제들에 대한 각가의 내용을 블로그에 한섹션으로 다뤄도 될정도의 분량을 뽑아 낼수 있기에 대충 대충 적어놓았다고 변명 해 본다. 





