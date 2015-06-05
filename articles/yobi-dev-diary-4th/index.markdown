{
    "title": "yobi-dev-diary-4th",
    "author": "Insanehong",
    "date": "2014-12-16T20:19:37.373Z",
    "categories": [
        "dev-diary"
    ],
    "tags": [
        "dev dirary",
        "yobi",
        "dirary"
    ],
    "acceptComment": true,
    "acceptTrackback": true,
    "published": "2014-12-16T20:19:37.373Z",
    "status": "publish",
    "important": false,
    "advanced": {}
}

# 14. 12.16(Tue)

spring boot 에서 template engine 으로 thymeleaf 사용하면서 문제가 생겼다. 

thymeleaf 를 html5 모드로 돌렸더니 self end tag 관련 error 로 html 파싱을 제대로 해주지 못했다. 

```
//문제가된 설정
spring.thymeleaf.mode=html5
```

self close tag 가 없어 문제가 된 태그는 `link` 와 `meta`! 

하지만 html5  스펙에서 해당 태그들은

```
Tag omission in text/html:
No end tag.
```

와 같이  정의되어 있어 self end tag 를 생략해도 무방한 상태.

뭔가 이상해서 구글신에게 물어본 결과 이미 known issue 였고 이미 solution 도 나와 closed 된 이슈였다. 

[https://github.com/spring-projects/spring-boot/issues/1270](https://github.com/spring-projects/spring-boot/issues/1270)

해결책은 

```
spring.thymeleaf.mode=LEGACYHTML5 
```

로 설정하는 것인데 추가적으로 pom.xml 에서 

```
<dependency>
   <groupId>net.sourceforge.nekohtml</groupId>
   <artifactId>nekohtml</artifactId>
   <version>1.9.21</version>
</dependency>
```

를 추가 해주는 것까지 해줘야 제대로 동작한다. 적용 결과 아무문제없이 html 을 잘 파싱해주었다. 

client source build 까지 만들었다가 routing 문제로 고민에 빠졌다. 

angularjs 의 routing 을 사용해서 SPA 로 만들기에는 application 의 복잡도가 너무 큰 탓에

결론적으로 spring 의 routing 을 사용해서 jsp 의 도움을 받기로 했고 그 결과 앞서 처리한 트러블슈팅은

쓸모없게 되어 버렸다. 하지만 이후에 저런 문제를 만나게 되면 원인과 해결책을 찾아보지 않아도 될테니 헛수고는 아닌듯.

어째듯 gulp build 가 jsp 파일을 문제없이 잘 처리해 줄수 있는지 찾아보고 테스트를 해봐야 할것 같다. 

