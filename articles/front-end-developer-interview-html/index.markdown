{
    "title": "front-end 개발자 인터뷰 문제 - HTML 영역",
    "author": "Insanehong",
    "date": "2013-05-09T12:29:39.682Z",
    "categories": [
        "reference"
    ],
    "tags": [
        "front-end",
        "developer",
        "interview"
    ],
    "acceptComment": true,
    "acceptTrackback": true,
    "published": "2013-05-09T12:29:39.682Z",
    "status": "publish",
    "important": false,
    "advanced": {}
}

몇일전  [front-end 개발자 인터뷰 질문](https://github.com/Songhun/Front-end-Developer-Interview-Questions/blob/master/Korean/README_KR.md) 이라는 내용의 글이 Github 에 공개되어 많은 사람들에게 거론되길래 보게 되었다. 

나름 괜찮은 질문 내용이며 각 영역별로 얼마나 많은 관심을 가지고 있나를 잘 알수 있는 내용들의 질문들이라 생각 되었다. 

이에 나름 오지랍을 펼쳐 각각의 영역별 답을 작성해 볼가? 라는 생각으로 한 섹션씩 작성보기로 했다. 

물론 개인의 지식한계선에서 작성된 답안들이니 이것들이 정답이라고 맹신하는 일은 없기 바란다. 틀린부분이나 다른 의견이 있으면 언제든 피드백을 통해 수정하여 반영할 예정이다. 

어째거 첫 섹션으로 html 관련 문제에 답을 달아본다.

# HTML 관련 질문

## 1. doctype 이 하는 일은 뭔가요? doctype을 몇개나 댈수 있나요?
 > doctype  이란 DTD(Document Type Definition)를 선어하기 위한 태그로서 문서의 렌더링 모드를 설정하거나 유효성 검사에 사용될 기준을 정의 하는 것을 말한다. 
 
### html 4.0.1 doctype

1. <!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Strict//EN" "http://www.w3.org/TR/html4/strict.dtd">
2. <!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
3. <!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Frameset//EN" "http://www.w3.org/TR/html4/frameset.dtd">
 
### xhtml 1.0 doctype

1. <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 4.01 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd"> 
2. <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 4.01 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
3. <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 4.01 Frameset//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-frameset.dtd">

### xhtml 1.1 doctype
1. <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN" "http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd"> 

### html5 doctype
1. <!DOCTYPE html>

## 2. 스탠더드 모드와 관용(쿼크) 모드간의 차이를 말해보세요.
스탠더드 모드와 관용모드의 차이는 하위호환성을 유지하기 위해 현재 표준에 어긋나는 형식을 지원할 것인가 ? 혹은 하위 호환성을 배재하고 현재 표준 형식만을 인정하는가의 차이를 보인다.

사용할 랜더링 모드는 doctype 선언시 결정되는데 FPI(formal public identifier), FSI(formal system identifier) 이 모두 선언되어야 스텐더드 모드로 랜더링 하게 된다. 

### 스탠더드 모드
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">

### 쿼크 모드
1. <!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" >
2. doctype  을 선언하지 않는 경우.

## 3. XHTML 페이지를 운용할 때 발생하는 제약으로는 뭐가 있나요?
XHTML 는 사실 문서 렌더링 면에서는 html 4.0.1 과 크게 다르지 않다. html 을 기반으로  xhtml 이 구성되어졌기 때문이다. 
하지만 이들 사이에는 몇가지 차이점이 생긴다. 서로 각가의 모드에서만 지원하는 몇가지 제약들이 존재한다. 

xhtml 에서의 마크업 문서 작성시 다음의 제약을 지켜야 한다. 

1. 닫힘 태그가 없는 단독 선언 태그일 경우 끝에 공백과 함께 "/" 를 사용해야한다. 예) <br />
2. body 안에서 태그로 감싸지지 않은 단독 텍스트를 사용해서는 안된다. 
3. 인라인 요소가 블록 요소를 감싸면 안된다. 
4. `&` 는 반드시 `&amp;` 로 대체하여야 한다. 
5. 태그 이름이나 속성에 대문자를 사용해서는 안된다. 
6. `attribute` 선언시 `shortcut` 을 사용해서는 안된다. 

물론 위에 나온 제약사양 보다 더 많은 제약이 존재한다. 

## 4. 다국어가 포함된 페이지는 어떤 방식으로 제공하나요?

다국어 지원의 방법은 front-end 보다 back-end 에서 지원하는 경우가 많다. 하지만 front-end 에서도 해야할 일은 있다. 
바로 encoding 방식과 문서에서 주로 사용하는 언어 설정을 해주는 것은 필수다. 

그리고 다국어 지원을 위한 css(언어특성상 box 모델링에 영향을 주는 경우도 있다)와 javascript message set 을 언어형식에 맞게 분리 하는 것도 필요하다. 

html 선언시 웹접근성,웹표준에 맞추게 된다면 주요 사용언어를 기입해주어야 한다. 

```html
<!doctype html>
<html lang="ko>
.
.
.
</html>
```

javascript 의 경우 cookie 등을 이용하여 설정된 언어설정을 global variable 로 저장해 놓는다면 message set 을 선택하는데 편하다. 

## 4. HTML5에서 XHTML문법을 사용할 수 있나요? HTML5에서 XML을 어떻게 사용하나요?

html5 표준은 기본적으로 하위호환성을 지키는 것으로 시작되었다. 즉 html5 에서 xthml 을 사용하던, html 4.0.1 의 표준을 사용하던 문제 될것이 없다. 

* xhtml 문법 작성시에는 `MIME` 타입을 `application/xhtml-html` 로 지정해 준다.
* 파일 최상단에 인코딩을 지정해 준다. `<?xml version="1.0" encoding="UTF-8"?>`
* 네임스페이스를 명시해준다. `<html xmlns="http://www.w3c.org/1999/xhtml">`

위와 같이 해당 문서에서 xhtml 문법을 사용할 것을 명시해준다면 큰 문제가 되는 일은 없을 것이다. 

## 5. data-* 속성은 무엇을 하는 것인가요?

custom data attribute 는 굉장히 많은 역활을 담당한다. 웹표준 마크업 제약사항에는 표준에 정의되 attribute 외의 사용은 문법에 어긋난 것으로 간주하여 validator 에서 이를 오류로 분류한다. 

하지만 이는 많은 제약사항을 가지게 되면 특히 예전부터  validation 등에 사용하기 위하여 표준에 정의 되지 않은 `attribute` 사용하거나 `class` 명에 명시하며 많이 사용해 왔다.

이를 한번에 해결해준 녀석이 `data-*` 이다. 말그대로 사용자가 임의 설정하여 선언하고 사용할 수 있다. 정확히는 문서를 다루는 html 마크업 에서 data 에 대한 정의를 선언할수 있게 도와주는 역활을 담당한다. 

본인이 자주 사용하는 방법을 예로 들어 보겠다. 

```html 
// validation 을 위한 데이터셋 저장
<form name="actionForm">
<input type="text" name="account" data-valide="notnull alphanum" value=""/>
<input type="email" name="email" data-valide="email" value=""/>
<input type="password" name="passwd" data-valide ="notnull alphanum  min:6" />
</form>

// button action  을 위한 설정값 저장
<button type="button" data-button-type="modal" data-action-target="layer"> modal layer open</button>

// input 데이터의 수정내역을 원본으로 복귀 하기 위한 origin data 저장
<input type="text" name="username" value="insanehong" data-origin-data="insanehong" />
```
위와 같은 사용을 하게 된다면 javascript 단에서 action 에 대한 설정을 fixed 시키지 않고 유연하게 적용할 수 있다. 

## 6. HTML4에서 콘텐츠 모델(content models)은 무엇이며, HTML5의 그것과 다른 점은 무엇인가요?

html4  의 경우 단순한 콘텐츠 모델을 따른다. `블락(block)`, '인라인(inline)` 요소로 구분하여 `인라인 안에 블락요소의 선언을 하면 안된다` 라는 단순한 문법을 지시한다. 

하지만 html5 에서는 이부분이 더욱 엄격하게 적용된다. html5 에서는 각 그룹요소들을 카테고리별로 나누어 제약을 걸어두고 있으며 자식요소에 대한 엄격한 제한 규칙을 가지고 있다. 

## HTML5를 오픈웹플랫폼(open web platform)으로 생각해본다면, 어떤 것들로 구성돼 있을까요?

> 사실 개인적으로 html4,html5 등의 버전을 붙히는 것을 좋아 하진 않는다. 언어를 다룰때 특정 버전을 붙혀가면서 하는 경우는 그리 많지 않다. 그래서 html5 라고 강조하는 것을 약간 약팔이라고 생각하고 있다. 

html5 의 구성은 크게 4가지로 구분된다고 생각한다. 

1. 시멘틱 마크업
2. 미디어 핸들링을 위한 내장 플렛폼 
3. application API
4. 오프라인 핸들러

개인적으로 css3 를 html5 에 포함시켜 소개하는 것도 잘못되었다고 생각한다. 

## 7. 쿠키(Cookies)와 세션저장소(sessionStorage)와 로컬저장소(localStorage)의 차이점을 설명해주세요.

### Cookies
쿠키는 서버가 클라이언트에 남기고 싶은 정보를 저장하는 텍스트기반 파일 이다. 이는 response header 에 포함된  `Set-Cookie` 필드를 참조하여 클라이어트에 작성되어 지며 유효범위를 url, 혹은 도메인 기반으로 정의 할수 있다. 
파일 사이즈의 제한이 있으며 텍스트 파일 기반으로 동작하기때문에 사용자가 언제든 쿠키 정보를 열람 할수도 있고 클라이언트에 저장된 쿠키정보를 request header 에 항상 포함하여 서버로 알려주기 때문에 패킷사이즈를 늘리는 1등공신을 한다.

그런 이유로 공통된 혹은 의미없는  cookie(서버가 알필요가 없는)정보를 response-header 에서 제외하는 것도 front-end 최적화 작업에 포함되어 진다. 

### sessionStorage
세션 스토리지는 쿠키와 같이 파일형태로 저장되지 않고 window  객체에 저장된다. 즉 윈도우에 dependency 가 걸려있기 때문에 해당 윈도우가 열려있는 동안만 데이터를 유지하면 윈도우가 닫히게 되면 저장되 데이터도 사라져 버리게 된다. 

active action 을 수행하는 동안만 유지되어야 하는 정보등을 저장해 둘때 유용하게 사용된다. 

### localStorage
로컬 스토리지는 세션스토리지와 마찬가지로 파일형태가 아닌 브라우저에 자체에 저장되는 저장소로 세션스토리지와 다르게 윈도우가 닫혀도 그 내용을 유지 시킬수 있다. 특히 용량제한 및 보존기간에 대한 제약이 없어 web application 에서 영구적으로 보존 관리 되어야하는 경우 사용하게 된다. 

트위터의 경우 새 트윗 입력창에 입력되는 내용이 로컬스토리지에 등록되어 윈도우를 닫았다가 다시 열어도 그 내용을 복원해 준다. 
























