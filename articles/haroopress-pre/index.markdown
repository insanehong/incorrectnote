{
    "title": "하루프레스설치 전 살펴볼것들",
    "author": "Insanehong",
    "date": "2012-08-11T10:34:51.178Z",
    "categories": [
        "haroopress"
    ],
    "tags": [
        "haroopress",
        "git",
        "node.js",
        "npm",
        "nvm",
        "os x",
        "mac",
        "ssh"
    ],
    "acceptComment": true,
    "acceptTrackback": true,
    "published": "2012-08-11T10:34:51.178Z",
    "status": "publish",
    "important": false,
    "advanced": {}
}

# 하루프레스를 설치하기 위한 준비
하루프레스는 `node.js` 와 `git`을 필수로 필요로 한다. 로컬에서만 작업을 한다면 더이상의 설치에 필요한 요소들은 없지만 실제 블로그로서 서비스를 하기 위해서는 [http://github.com](http://github.com)에 repository 를 만들어야 한다. 

[하루프레스 공식 사이트](http://haroopress.github.com)에 잘 나와있지만 본인이 하루프레스를 설치파고 포스팅 하기 위해 했던 뻘짓들을 조금이나마 공유하기 위해 지금부터 하루프레스를 사용하기 위한 기본적인 설치가이드를 소개하려고 한다. 

**앞으로 나올 내용들은 철저하게 본인의 Macbook pro(산사자)에서 작업되었던 내용으로서 Os X 기준으로 작성되었다**
 
# 로컬에 Git 설치하기 
사실 Os X에는 Git이 기본 탑제 되어 있는 것으로 알고 있었다. 하지만 산사자 업데이트 후 Git 명령어가 말썽을 부린다는 분들이 많이 발생 하였다. 그래서 이번 단계는 Terminal에서 갑자기 git 명령어가 듣지 않는 다거나 본인과 같이 Mac을 처음 접하는 사람들만 참고하면 될 것이다. 

```
$ git
- bash: git : command not found
```
위와 같은 상황에 봉착했다면 [http://www.hongkiat.com/blog/mountain-lion-git-fix/](http://www.hongkiat.com/blog/mountain-lion-git-fix/) 를 참고하면 쉽게 해결 가능 할 것이다. 

#  node.js 설치하기
로컬에 node.js를 설치할때에는 package 나 소스코드로 직접 설치하는 것보다 `NVM(Node Version Manager)`를 통하여 사용하는 것이 좋다. 

## nvm을 이용하여 node.js 설치하기

```
$ git clone git://github.com/creationix/nvm.git ~/.nvm
```
nvm 역시 바로 사용할 수 없고 `.profile`에 등록을 해주어야 한다. 

```
$ echo 'source ~/.nvm/nvm.sh' >> ~/.profile; source ~/.profile
```
이제 nvm을 사용하여 node.js 설치하기 위한 준비가 끝났으니 설치를 해보도록 하자.
이글을 적는 시점에서 node.js의 최신버전은 v0.8.7 이였기에 v0.8.7 버전을 설치 해보도록 하자

```
$ nvm install v0.8.7
$ nvm use v0.8.7
$ nvm alias default v0.8.7
```
설치가 끝났으면 설치가 잘되었는지와 사용하고자 하는 버전이 잘 설정 되었는지 확인해 보면 된다. 

```
$ node -v
v0.8.7
```
버전 정보가 설정한대로 잘 나온다면 설치가 완료 된 것이다. 

## npm 설치 하기
`npm(Node Package manager)` 는 node.js 의 모듈들을 쉽게 설치 할 수 있게 도와주는 녀석이다. 하루프레스에서도 엔진에 종속된 모듈들을 initalize 과정에서 자동으로 받아 주기 때문에 그전에 npm을 설치 해 주어야 한다.

```
$ curl http://npmjs.org/install.sh | sh
```
설치가 끝났으면 제대로 설치 되었는지 확인을 해보자.

```
$ npm -v
1.1.48
```

# 로컬 SSH Key 발급하기
로컬에서 github.com 에 일련의 작업을 수행하기 위해서는 ssh key를 등록 하여야 한다.

```
$ ssh-keygen -t rsa -C "input your email address"
``` 

위와 같이 `input your email address` 부분에 사용할 이메일 주소를 입력하면 다음과 같은 결과가 나온다

```
Generating public/private rsa key pair.
Enter file in which to save the key (/Users/#yourusername#/.ssh/id_rsa):
```
위와 같은 화면이 나오면 엔터를 눌러준다. 그럼 비밀번호를 입력하라는 메세지가 나오고 비밀번호를 입력하면 비밀번호를 확인차 다시 입력해 달라는 메세지가 나온다. 

```
Enter passphrase (empty for no passphrase): (비밀번호 입력+엔터)
Enter same passphrase again: (동일한 비밀번호 입력+엔터)
```
ssh key가 제대로 발급 되었는지 확인을 해보려면

```
$ cd .ssh/
$ ls -al
```
`id_rsa`, `id_rsa.pub` 파일이 존재하면 제대로 발급 된것이다. 

# 마무리
이제 하루프레스를 설치할 준비는 다 되었다. 이후의 작업은 [하루프레스 공식 사이트](http://haroopress.github.com)에 잘 나와있다. 
위에서 발급 받은 ssh key를 github.com 에서 등록해주기만 한다면 그외 모든 작업은 
하루프레스 메뉴얼을 따라서 진행 하면 된다. 

**By Insanehong**
