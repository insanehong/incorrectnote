{
    "title": "과연 반응형 웹 디자인만이 해답일까?",
    "author": "Insanehong",
    "date": "2012-08-30T15:18:32.786Z",
    "categories": [
        "a11y"
    ],
    "tags": [
        "responsive web design",
        "반응형",
        "웹",
        "디자인",
        "responsive",
        "web",
        "design"
    ],
    "acceptComment": true,
    "acceptTrackback": true,
    "published": "2012-08-30T15:18:32.786Z",
    "status": "publish",
    "important": false,
    "advanced": {}
}

# 소개
이 글은 `반응형 웹 디자인(Responsive Web Design)' 에 대해 굉장히 비판적인 내용들을 담고 있다. 특히 반응형 웹 디자인은 사용자 입장의 기술이 아닌 개발자 혹은 운영적 측면에서 나온 기술임을 말하고자 하는 것이 이 글의 목표이다.

# 반응형 웹 디자인 (Responsive Web Design)
>사용자가 접하는 웹 페이지 UI를 디자인하는 한 방법인 반응형 웹 디자인은 가능한 현재 환경에 스스로 적응하여 적절한 UX를 제공하는 구성으로 변화하는 특징을 가지고 있다.  이는 웹페이지가 실행되고 있는 디바이스와 여러 종류의 사이즈에 관계없이 레이아웃이 유동적으로 변화하기 때문이다.

정의에서 말했듯이 반응형 웹 디자인은 상황에 맞게 레이아웃이 변화한다. 즉 각기 다른 환경에 따라 다른 레이아웃을 제공하기 위해 새로운 페이지로 이동하는 것이 아니라 현재의 페이지 그대로 그 구성만 변화하는 것이다. 

이를 `One Source Multi Device(OSMD)` 혹은 `One Source Multi Use(OSMU)` 이라고도 하며 최근 각광 받고 있는 N Screen 대응책 중 하나이다. 

![반응형 웹 디자인](./@img/responsiveweb.jpeg)

# 반응형 웹 디자인이  사용자를 위한 기술일까? 정말?
반응형 웹 디자인은 `N Screen` 대응 측면에서는 현재 나와 있는 기술중에는 가장 고도화되고 최적화된 방법중 하나라고 믿어 의심치 않는다. 웹 애플리케이션을 개발하고 서비스하는 회사 입장에서는 이 방법론이 `최소의 비용`으로 유지보수가 가능한 효과를 기대할수 있는 방법일 수 도 있다. 하지만 이를 두고 절대 `사용자`를 논하는 오류를 범하지 않기를 바란다.

**반응형 웹 디자인은 애시당초 개발과 운영의 최소비용을 위해 탄생하였다.**

# 희생의 논리를 감춰주는 Mobile First
>가장 작은 화면의 디바이스인 모바일 환경에서 보여질 UI를 가장 먼저 디자인하는 방식인  `Mobile First`는 `모바일 디바이스` -> `테블릿PC` -> `데스크탑` 레이아웃 순으로 적용 되어진다.

반응형 웹 디자인을 적용할 때 가장 많은 화두가 되는 것은 `모바일 퍼스트` 이다. 가장 작은 화면을 가진 모바일에서 데스크탑과 같은 큰 화면에 보이는 모든 컨텐츠가 억지로 작은 화면안에 넣어지면서 생기는 UX 비효율성에 의해 생겨난 개념이기도 하다.

`미디어 쿼리(@media)`를 지원하지 않는 브라우저에서도 적응이 가능한 `OSMU` 레이아웃으로 유지시켜 줄수 있는 방법으로 사용되기도 한다. 

하지만 생각을 약간 비틀어보면 여기에는 재미있는 함정들이 숨어 있다. 

## 사용자를 위해서 모바일을 먼저 해야한다고?? 이게 사실이야?? 진짜야??
어떤 크기의 디바이스 환경에서 원하는 컨텐츠를 소비하는 사용자가 불편함이 없어야 하기 때문에 생겨났다는 `모바일 퍼스트` 전략은 사용자의 편의를 위한것 보다는 하나의 페이지로 모든 디바이스에 대응 해야하기 때문에 생겨난 운영의 편리를 위한 전략이다.

>단 여기서 말하는 모바일 퍼스트에 대한 이야기는 절대적으로 반응형 웹 디자인에 한정되어 있다.

가장 중요한 기능에 초점을 맞추어 `Kitchen Sink` 문제를 해결하고 사용자에게 핵심적인 기능을 깔끔하게 정리해서 보여줄수 있다는 모바일 퍼스트의 전략 역시 데스트탑의 20%정도 뿐 되지 않는 모바일의 컨텐츠 수용능력을 가진 커버하기 위한 전략이다. 

물론 데스크탑에서 광고와 같이 사용자가 불필요하게 노출되고 있는 정보들이 많은 것은 사실이다. 하지만 데스크탑에서 보여지는 여러가지 컨텐츠들이 꼭 불필요한 정보이고 이 들이 굳이 동일 화면에서 보여질 필요가 없다고 하는 것은 너무 모바일에 편향된 생각일 수밖에 없다. 

## 데스크탑은 항상 불필요한 정보만을 나열하고 있는 걸까?
모바일 퍼스트로 인해 정리되어 깔끔하고 간결한  UI를 제공하는 것이 나쁘다는 것은 아니다. 
하지만 한번에 제공하는 정보 양이 많다고 해서 사용자에게 꼭 나쁘다는 것은 잘못된 착각이다.

사용자가 데스크탑과 모바일에서 동일한 컨텐츠를 소비하기 위해 해야하는 수고비용 측면을 생각해보자. 

충분한 켄버스 요건을 갖춘 데스크탑에서는 특정 정보에 대해 사용자에게 좀더 상세하고 자세한 정보를 제공하며 한번에 클릭으로도 더 많은 컨텐츠를 이용하거나 더 많은 정보들을 습득 할수 있다. 

이는 매우 중요한 요소중 하나이다. 핵심기능을 뽑아내고 사용자에게 절제된 Flow 를 제공하는 것은 사용자의 컨텐츠 소비에 제약을 거는 것과 같다. 

즉 모바일 퍼스트로 인하여 2~3뎁스로 밀려난 컨텐츠들은 어떠한 경우에는 사용자에게 외면 당할수도 있는 것이다. 물론 핵심기능이나 주요 서비스는 2~3뎁스로 밀려나지 않을 수 있지만 이미 충분한 컨텐츠 수용성을 가진 켄버스를 가지고 있음에도 이를 잘 활용하지 못하는 것은 사용자뿐 아니라 서비스 제공 업체에게도 피해가 될수 있다. 

>광고가 필요 없는 정보라고? 정말?? 그럼 돈은 어떻게 벌지?

광고가 사용자에게는 불필요한 정보일 수도 있지만 기업입장에서는 정반대 입장이란 것은 절대 잊어서는 안된다. 

#  상호 피해가 될 수 밖에 없는 데스크탑, 모바일 UX
데스크탑과 테블릿을 포함한 모바일기기는 전혀 다른 UX를 가진다. 가장 특징적인 것은 역시 마우스, 키보드 조합과 터치,슬라이드 조합일 것이다. 

특히 반응형 웹 디자인으로 구성하게 되는 많은 경우에 상하 스크롤이 길어지는 문제에 대해서는 딱히 좋은 해결방법은 없다. 지금으로선 그저 최대한 숨길수 있는 녀석들을 찾아 `hide` 처리하는 경우가 많다. 

모바일의 작은 화면에서 가장 효과적이고 효율적인 방법은 가로 슬라이드 터치기법을 이용한 레이아웃 이동이다. 하지만 여기에는 한번에 많은 양의 컨텐츠를 불러오는 문제와 마크업 구조에 대한 문제를 해결해야 한다.

데스크탑과 모바일은 사용자에게 제공되는 컨텐츠 제공 기법에서도 큰차이를 보인다. 특히 overflow:scroll 에서는 엄청난 레이아웃 구조의 차이를 가져오게 된다. 
물론 iscroll등과 같은 도구를 이용하여 비슷한 환경을 제공 할수는 있어도 원천적으로 overflow에 대한 고려가 없는 모바일 환경과 데스크탑을 융합하기에는 많은 부족한 면이 따른다. 

# 컨텐츠 처리 비용은 모두 사용자가 지불한다.
반응형 웹 디자인을 적용하면서 `모바일 퍼스트`, `데스크탑 퍼스트` 등 어떤 방법을 사용하던지 문제되는 녀석이 바로 모바일 환경에서 의 `컨텐츠 비용`이다.

모바일 디바이스는 휴대가 편리한 장점에 비해 컨텐츠 소비량에 따른 베터리 소비 문제를 동반하고 `WIFI` 환경 혹은 `무제한 데이터` 방식을 사용하지 않는 사용자에게는 통신 비용에 대한 문제를 동반하게 된다. 

모바일 디바이스에서 `hidden` 처리 되어지는 불필요한 `img`, `js`, `tag` 정보를 불필요하게 다운로드 해야하는 문제가 발생하게 된다. 이는 곧 사용자의 통신 비용과 네트워크 상태에 따른 렌더링 속도에 직접 적인 영향을 미친다. 

즉 모바일에 특화 된 사이트보다 로딩속도,렌더링 비용, 통신비용 등에서 절대적으로 값비싼 웹 어플리케이션이 되어버리는 현상이 일어나는 것이다. 

특히 `img` 렌더링은 강제적은 크기 조정은 불필요한 CPU 연산을 강요한다. 즉 동일한 컨텐츠라 할지라도 크기조정에 따른 연산 과정이 더 필요하다면 이는 곧 베터리소모에 직접적인 영향을 주게 되는 것이다. 휴대용 기기에 전원케이블을 연결하고 다니지 않는다면 이는 사용자에게 좋은 일은 절대 아닐 것이다. 

이에 따른 수많은 방법론들이 제공 되고 있지만 이들 역시 디바이스에 따른 추가 렌더링 혹은 JS 연산을 동반해야 함은 바뀌지 않는다.
 

# 그럼 어쩌란 말인데? 반응형 웹 디자인 하지 말라고?
>절대로 반응형 웹 디자인을 하면 안된다는 말이 아니다. 반응형 웹 디자인이 만능이 아니고 이것만이 절대적인 지표로 받아들이면 안된다는 것이다.

본인 역시 반응형 웹 디자인을 매우 좋아한다. 그리고 이를 주위에 알리기 위해 많은 노력을 해온 사람중 한명이다. 

하지만 반응형 웹 디자인을 접한 이들은 이것이 절대적인 기술인 것처럼 받아들이는 모습을 종종 보인다. 

페이스북은 웹 애플리케이션을 시작해서 모바일에서 `하이브리드 웹앱`을 적용하여 서비스하다가 최근 모바일 서비스를 `네이티브 앱`으로 변경하였다.


반응형 웹이 절대적이고 무조건적인 선택의 기술이였다면 절대 그런일은 일어날 수 없었다. 당연한거 아닌가? 페이스북도 반응형 웹으로 변경했어야 될테니까.

하지만 현실은 그렇지 않다. 반응형 웹 디자인은 적절한 곳에 사용될때 그 빛을 발한다.
특정 한 서비스를 지향하는 웹 애플리케이션의 경우 반응형 웹 디자인을 적용하면 괜찮을 수 있다. 특히 이런 서비스는 모바일 퍼스트에도 적합한 서비스 형태를 띠고 있다. 

하지만 무분별하게 반응형 웹 디자인을 적용하는 것은 바람직하지 않다. 오히려 `데스크탑 전용 웹` + `모바일,테블릿용 반응형 웹 디자인`을 갖춘 서비스가 훨씬 더 좋은 방향을 보이는 경우도 많기 때문이다. 

마지막으로 이 글은 `OSMU` 만 바라보고 반응형 웹 디자인에 무분별한 신뢰를 바치는 사람들을 위해 작성 했음을 밝히다. 

반전이 하나 있다면 이렇게 막 떠들었지만 정작 본인은 반응형 웹 디자인을 스스로 적용하고 이 방법론을 널리 알리는데 앞장서는 한사람이란 것 정도? ^^ 

**By Insanehong**
