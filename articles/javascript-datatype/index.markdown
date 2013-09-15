{
    "title": "Javascript기초 - 데이터타입",
    "author": "Insanehong",
    "date": "2012-08-12T04:20:19.346Z",
    "categories" : [
	 "javascript"
    ]	,
    "tags": [
        "javascript",
        "datatype",
        "자바스크립트",
        "데이터ㅏ입"
    ],
    "acceptComment": true,
    "acceptTrackback": true,
    "published": "2012-08-12T04:20:19.346Z",
    "status": "publish",
    "important": false,
    "advanced": {}
}

# 소개
프로그래밍 언어를 처음 배울때 가장 먼저 다루는 부분이 바로 그 언어의 데이터타입 이다. 대부분의 기초 프로그래밍 서적들도 첫장에서 데이터 타입에 대해 설명을 하고 있으며 데이터 타입을 숙지 하지 않고서 해당 언어를 다룬다는 것은 **"스펠링을 모르면서 작문을 하겠다는 것과 같다"** 라고 생각한다.
그런 이유로 자바스크립트 기초의 가장 첫번째 포스틩이 될 이 글에서는 자바스크립트에서 사용되는 데이터 타입에는 어떤 것들이 있으며 그 특징은 무엇인지 다루어 보고자 한다.

# 자바스크립트에서 사용되는 데이터 타입
자바스크립트에는 `Number`, `String`, `Boolean`, `Function`, `Object`, `Null`, `undefined`,`Array` 등의 데이터 타입이 존재한다.
하지만 `Array`,`Function`,`Date`,`RegExp` 와 같은 데이터는 엄밀히 따지면 `Object`이다. 자바스크립트를 객제기반 언어라고 하는 이유이기도 하다. 실직적으로 자바스크립트에서 사용되는 대부분의 데이터 타입은 객체로 존재하며 그에 따른 사용또한 객체기반이 될수 밖에 없다.
그래서 자바스크립트 기술 문서들은 다음과 같이 데이터 타입을 분류 한다.

* 수 (Number)
* 문자열 (String)
* 부울,불린 (Boolean)
* 객체 (Object)
 * 함수 (Function)
 * 배열 (Array)
 * 날짜 (Date)
 * 정규식 (RegExp)
* 널 (Null)
* 정의되지않음 (Undefined)

# Number
숫자를 표현하거나 산술 연산을 하는데 사용되는 데이터 타입이다. 기본적으로 `+, -, *, /` 등의 산술연산이 가능하며 Math 라는 내장객체를 이용하여 수학함수를 이용한 결과를 얻을 수도 있다.
명세에 따르면 자바스크립트의 Number는 *"64비트 형식 IEEE 754 값"* 으로 정의 된다. 이 때문에 자바스크립트에서 간혹 의도하지 않은 어이없는 결과로 인하여 개발자를 열받게 하기도 한다

```javascript
console.log(0.1+0.2);
> 0.30000000000000004 // ????????? 이런 미친 결과가 나오니 주의해야 한다.
```
## Number Casting :: parseInt(), parseFloat()
자바스크립트는 변수선언시 데이터 타입을 명시하지 않는다. 그래서 숫자형 데이터가 아닌 문자열 데이터로 숫자를 표현하는 일도 많다. 그런 이유로 자바스크립트 코딩을 하다보면 **데이터형 변환(casting)**을 해야하는 경우가 종종 발생한다. 자바스크립트의 캐스팅을 이용한 데이터형 변환에 자주 사용되는 내장객체 중 `parseInt()`를 이용하면 문자열을 **정수**로, `parseFloat()`를 사용하면 **실수**로 치환 할수 있다.

```javascript
console.log(parseInt("010", 10));
> 10
```
`parseInt()` 의 두번째 인자는 치환하고자하는 문자열이 몇진수의 숫자를 표현한 문자열인가를 나타낸다 . 위 예제는 "010" 을 10진수 표현의 문자열이라는 의미다. 이와 같은 원리로 두번째 인자를 2로 변경 하여 2진수를 나타낸 문자열이라고 한다면 그 결과는 위 예제와 다른 값이 출력된다.

```javascript
console.log(parseInt("010", 2));
> 3 // 010 을 2진수로 판단하여 10진수 정수로 변환한 값을 출력해준다.
```

재미있는 사실 하나는 위 예제들에서 **두번째 인자를 전달하지 않으면 원하는 결과와 전혀 다른 값이 출력**된다.

```javascript
console.log(parseInt("010"));
> 8 // ??? 뜬금없이 8 이 출력된다.

```
이런 어이없는 결과가 나오는 이유는 간단하다.  `parseInt()` 는 두번째 인자인 진법을 지정하지 않으면 **0x로 시작하면 16진수**, **0으로 시작하면 8진수**로 인식하여 그 결과를 출력하기 때문에 "010"을 8진수로 인식하여 8이라는 결과를 출력한 것이다. 그러니 정확한 결과값을 원한다면 두번째 인자를 반드시 전달해주는 것이 좋다.
또한가지 주의 해야 할 것은 `parseInt()`는 소수점을 과감하게 버림한다. 그러니 **소수점을 표현하고자 한다면 `parseFloat()`를 사용**하여야 한다.

`parseFloat()`를 사용하면 `parseInt()`에서 나왔던 두번째 인자 미전달로 인한 황당한 결과의 초래도 막을 수 있다.

```javascript
console.log(parseFloat("010"));
> 10 //정확히 10진수를 반환한다. 

console.log(parseFloat("010.333"));
> 10.333
```

## Not a Number :: NaN 과 isNan()
위에서 설명한 문자열에서 숫자형으로 데이터형변환시 대상이 되는 문자열이 숫자를 표현한 문자열표현이 아닌경우 자바스크립트는 `Not a Number`의 약자인 `NaN` 을 리턴 하며 말그대로 **해당 하는 값이 숫자가 아니란 뜻**이다. 이 `NaN`은 자바스크립트를 다루면서 반드시 인지하고 있어야 하는 결과 중 하나 이기도 하다.

```javascript
console.log(parseInt("hello world", 10));
> NaN
```

자바스크립트에서 **해당 데이터가 NaN 인지  검사해주는 `isNaN()` 이라는 내장 객체**가 존재하는데 이 `isNaN()` 객체는 상당히 많은 활용도를 가지는 내장객체이다. isNan() 은 NaN 인지 여부를 검사하는 함수임으로 **NaN 일때  true** 를 반환한다.

```javascript
console.log(isNaN(NaN));
> true

console.log(isNaN("hello"));
> true
```

## Number의 무한대의 표현식 :: Infinity , -Infinity 과 isFinite()
자바스크립트의 특별한 표현식중 하나가 바로 이 **무한대를 나타내는 Infinity** 이다. 0보다 큰 양의 무한대는 Infinity, 0보다 적은 음의 무한대는 -Infinity로 표현 되는데 이는 산술연산의 결과 혹은 데이터 값이 무한대값을 가지는 경우 자바스크립트가 출력하는 결과값이다.

```javascript
console.log(1 / 0);
> Infinity

console.log(-1 / 0);
> -Infinity
```

`isFinite()는` 산술결과 혹은 전달된 인자값이 **유한의 형태를 가지는 것인지를 검증**하는 내장 객체이다. 즉 **인자값이 숫자이면서 무한대가 아니면 true, NaN 혹은 무한대의 Infinity , -Infinity 이면 false를 리턴** 한다.

```javascript
console.log(isFinite(1 / 0));
> false

console.log(isFinite(NaN));
> fasle

console.log(isFinite(1));
> true
````

# String (문자열)
**String은 문자열을 표현하는데 사용되는 데이터 타입**이다. 자바스크립트의 문자열은 **16비트 유니코드 문자들의 연결구조** 이기도 하다. 즉 문자열이라 함은 문자 하나하나가 연결되어 하나의 표현을 이루는 데이터를 말하는 것이다.
## String property :: length
이글 초반에 언급했듯이 자바스크립트의 **대부분의 데이터타입은 객체로 존재**하고 있다. **문자열의 typeof는 당연히 String** 이다. 하지만 문자열또한 객체로서 활용가능한 **property와 method를 가지고 있는 특이한 형태의 데이터 타입**이다. 그러한 이유로 php 에서 문자열의 길이를 구하기위한  strlen() 함수와 같이 별도의 내장함수를 사용하지 않고도 문자열이 가지고 있는 property인 length 만으로도 그 길이를 알수 있다.

```javascrip
console.log("hello".length);
> 5
```

## String method : replace(),charAt(),toUpperCase(),split()
**문자열은 객체에 의존적으로서 객체의 수행을 담당한다는 메소드(함수와 메소드의 차이는 객체를 다룰때 자세히 정의 하겠다.) 를 가지고 있다.** 이들 메소드들은 문자열을 여러가지 형태로 변환하거나 문자열 정의에서 밝힌 문자 하나하나의 연결중 특정 위치의 값을 가져오는데 활용할 수 있다.

```javascript
console.log("hello world".charAt(0));
> h // charAt() 를 활용하여 문자열의 특정 자리에 위치한 문자를 반환.````

console.log("hello world".replace("hello","goodbye"));
> goodbye world // replace() 를 활용하여 문자열 치환을 수행.

console.log("hello world".toUpperCase());
> HELLO WORLD //toUpperCase()를 이용하여 문자열을 대문자로 치환.

console.log("1+2+3+4+5".split("+"));
> ["1","2","3","4","5"] // split() 를 활용하여 "+" 를 기준으로 문자열을 나누어 배열로 반환한다.
```

# Null (값 없음) 과 undefined
자바스크립트는 **값이 없음을 나타내는 `null`** 과 **초기화(선언) 되지 않았거나 값이 할당되지 않았음을 나타내는 `undefined`**라는 특별한 데이터 타입이 존재한다. 자바스크립트를 활용함에 있어서 `null` 과 `undefined`의 차이를 정확히 이해하지 않는다면 훗날 큰 곤욕을 치를 지도 모른다.
**`null` 은 자바스크립트 개발자가 의도적으로 비어있는 값을 부여**한 것이고 `undefined` 는 **애당초 어떤한 값도 할당되지 않은 것**이다. 자바스크립트는 변수의 선언과 초기화를 동시에 하지 않아도 된다. 이는 다른 언어에서도 마찬가지로 활용되지만 자바스크립트에서는 특이하게 선언만 하고 초기화 되지 않은 변수는 초기화되지 않았거나 값이 할당되지 않았음을 표현하는 `undefined` 라는 값을 할당받는다.

```javascript
var a; // 선언만 되고 초기화 되지 않은 변수;
console.log(a);
> undefined // 초기화가 이루어지지 않았음으로 java-script 엔진이 undefined를 강제적로 할당한다.
```

하지만 유념해야하는 것이 있다. 위 예제의 결과는 undefined 지만 아래의 예제를 보면 null과 undefined가 굉장히 햇갈리게 된다.

```javascript
var a;
console.log(typeof a);
> undefined // 초기화가 이루어지지 않았음으로 당연히 undefined

console.log(a==undefined);
> true // 당연히 a==undefined 는 true를 반환 한다.

console.log(a==null);
> true // typeof 는 undefined 이지만 null 인지 검증하면 true를 반환 한다.

console.log(null==undefined);
> true // null==undefined 검증은 true를 반환한다.
```

위 예제를 보면 `null`과 `undefined`는 그닥 별반 차이가 없어 보인다. 검증에 따른 결과가 둘다 `true` 이기 때문이다. 하지만 **선언조차 하지 않은 변수를 활용한다면 이야기가 틀려진다.**

```javascript
console.log(typeof a);
> undefined // 선언되지 않은 변수를 사용함에 따라 자바스크립트 엔진이 강제적으로 undefined를 할당한다. 

console.log(a==undefined);
>  // error. 선언되지 않은 변수이기에 undefined의 데이터타입이지만 사용할 수는 없는 문법 오류이다.
```

그럼 정확하게 `null`과 `undefined`를 구별하기 위해서는 어떻게 해야하느냐? 간단하다 **`null`은 변수가 참조하는 객체가 없음(null)**을 나타내고, **`undefined`는 그 변수가 참조하는 객체를 아직 지정하지 않았음(not initialized)**을 뜻한다. 따라서 `undefined` 값을 가지는 변수는 할당을 통해 값을 가지며 이 값(객체)을 해제할때 `null` 이 되는 것이다.

```javascript
var a;
console.log(a);
> undefined // 아직 값이 할당되지 않은 undefined

a = "hello world";
console.log(a);
>  hello world // a는 "hello world"의 문자열 객체를 할당 받았음으로 null,undefined가 아닌 hello world 이다.

a=null;
console.log(a);
> null // a가 참조하는 hello world 라는 문자열 객체를 해제하였기에 undefined가 아닌 null 이다.
```

# Boolean (부울,불린)
자바스크립트도 부울 혹은 불린으로 불리우는 이 데이터 타입은 **true,false값을 가지는 논리 데이터 타입**이다 . 자바스크립트뿐만 아니라 대다수의 프로그래밍 언어에서 가장 많이 사용되는 이 Boolean 데이터 타입은 `Boolean()` 함수를 이용하여 검증을 수행할수 있다.

```javascript
console.log(Boolean("hello"));
> true;

console.log(Boolean(""));
> false;
```

흔히 가장 많이 활용되는 if(a) 라는 형태의 제어문은 if(Boolean(a)) 의 약식 표현인 것이다.

# 갈무리
이번 포스팅에서는 자바스크립트에서 사용되는 데이터 타입에 대해 다루었다. 하지만 글을 차분히 잘 읽은 사람이라면 이미 깨닿고 있을 Object에 대해서는  이번장에서 다루지 않았다. 그 이유는 Object에 대해 논하려면 이글의 스크롤바는 밑도 끝도 없는 해저 깊숙히 박혀 있어야 할듯 하기에 데이터 타입에 대한 글에서 독립시켜 별도로 다룰 예정이기 때문이다.

어쨋든간에 이번장에서는 자바스크립트를 다루면서 반듯이 이해하고 있어야할 기본중에 기본인 데이터 타입에 대해 다루었으며 이런 기초들 하나하나가 곧 front-end 개발자로서 성장해 나가는 밑거름이며 앞으로 자바스크립트를 다루면서 애매한 상황에서 햇갈리지 않고 자신이 원하는 프로그램코드를 작성하는데 큰 도움이 될것이다.
그럼 이번장은 여기서 마무리하고 다음 포스팅이 될 Object에 대해 정리는 훼이크고 사실 지금 사무실에서 혼자 뻘짓중이기때문에 밤이 늦은 관계로 이젠 슬슬 집에 들어가야겠다.

**by @insanehong**

참고 문서

**[https://developer.mozilla.org/en/A_re-introduction_to_Java-Script](https://developer.mozilla.org/en/A_re-introduction_to_Java-Script)**


