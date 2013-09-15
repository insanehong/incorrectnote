{
    "title": "윈도우 사용자를 위한 git client 설치",
    "author": "Insanehong",
    "date": "2013-05-28T02:56:54.739Z",
    "categories": [
        "git"
    ],
    "tags": [
        "git",
        "windows",
        "tortoriseGit",
        "msysGit"
    ],
    "acceptComment": true,
    "acceptTrackback": true,
    "published": "2013-05-28T02:56:54.739Z",
    "status": "publish",
    "important": false,
    "advanced": {}
}

# Guide to Git for Windows 
 
이 글은 팀내 ***info Windows OS*** 사용자를 위하여 Git 설치 및 업무환경 세팅에 대하여 사내 위키 문서에 정리해 놓은 내용을 옮겨온 것입니다. 

***info Windows 7*** 을 기준으로 작성 되었으며 GUI 특히 ***info tortoiseSVN*** 에 익숙한 사용자 경험을 원하는 분들을 위하여  
***important TortoiseGit*** 의 설치와 ***important CLI***를 사용하기 원하는 분들을 위한 ***info mysysgit***의 설치 과정을 담고 있습니다.

## TortoiseGit 설치하기
* [다운로드](https://code.google.com/p/tortoisegit/wiki/Download?tm=2)

### 1. 다운로드 페이지 본인 컴퓨터에 맞는 설치 파일을 다운로드 받습니다.

![TortoiseGit 다운로드 페이지](./@img/tor1.jpg)

### 2. 다운로드된 파일을 실행 합니다. 

![TortoiseGit 다운로드 페이지](./@img/tor2.jpg)

### 3. 다음의 예시와 같이 설치를 진행 합니다. 

![TortoiseGit 설치1](./@img/tor3.jpg)

![TortoiseGit 설치2](./@img/tor4.jpg)

![TortoiseGit 설치3](./@img/tor5.jpg)

![TortoiseGit 설치4](./@img/tor6.jpg)

![TortoiseGit 설치5](./@img/tor7.jpg)

![TortoiseGit 설치6](./@img/tor8.jpg)

### 4. 설치가 완료되면 마우스 오른쪽 버튼을 눌러 TortoiseGit 이 제대로 설치 됬는지 확인 합니다. 

![TortoiseGit 설치 확인](./@img/tor9.jpg)

## ssh public key 만들기

***info github***, ***info gitlab***, ***info bitbucket*** 등을 이용하거나 별도로 구축한 원격의 저장소를 이용하기 위해서는 ***important ssh key*** 가 필요합니다. 

이후에 얘기할 ***info msysGit***을 이용하면 몇줄의 ***info commend***info 입력으로 간단하게 만들수 있지만 일단 windows 환경에서 ***important PuTTYgen*** 을 이용하여 만드는 법을 소개 합니다.

### 1. 윈도우 시작 > TortoiseGit 안에 있는 PuTTYgen 을 실행 합니다. 

![PuTTYgen 실행1](./@img/key1.jpg)

### 2. PuTTY Key Generator 실행 화면에서 Generate 버튼을 클릭 합니다.

![PuTTYgen 실행2](./@img/key2.jpg)

### 3. 표시된 영역에서 progress bar가 100%가 될때까지 마우스를 움직입니다.   

![PuTTYgen 실행3](./@img/key3.jpg)

### 4. 키 생성이 완료되면 Save Button 이 활성화 됩니다. password 를 사용하는 경우 비밀번호를 입력하고 Save Private Key Button 을 클릭합니다.

![PuTTYgen 실행4](./@img/key4.jpg)

### 5. 적당한 곳에 적당한 이름으로 저장합니다. ( 예제에서는 C:\Users\{username}\.ssh 디렉토리를 생성하고 key 라는 이름으로 저장 하였습니다.)

![PuTTYgen 실행5](./@img/key5.jpg)

6. public key 부분도 복사하여 별도의 파일로 저장해둔다. (추후 repository server에 public key를 등록해야한다.)

![PuTTYgen 실행6](./@img/key6.jpg)


## CLI 사용을 위한 msysGit 설치

Git은 여러모로 GUI보다는 CLI 에 최적화 있기 때문에 윈도우 사용자 중 CLI를 이용하고 싶은 분만 따라 하시면 됩니다. 
GUI 를 선호하시는분은 Skip 하셔도 됩니다. 

* [다운로드](https://code.google.com/p/msysgit/downloads/list)

### 1. msysGit Download 사이트로 접속후 최신버전의 설치 파일을 받습니다. \(git-버전.preview배포일자.exe\)

![msysGit 다운로드](./@img/msys1.jpg)

### 2. 다운로드 받은 파일을 실행 합니다. 

![msysGit 설치 실행](./@img/msys2.jpg)

### 3. 다음의 안내와 같이 설치를 진행 합니다. 

![msysGit 설치 실행](./@img/msys3.jpg)

![msysGit 설치 실행](./@img/msys4.jpg)

![msysGit 설치 실행](./@img/msys5.jpg)

![msysGit 설치 실행](./@img/msys6.jpg)

![msysGit 설치 실행](./@img/msys7.jpg)

![msysGit 설치 실행](./@img/msys8.jpg)

![msysGit 설치 실행](./@img/msys9.jpg)


## 참고 할만한 동영상
* [설치 가이드 영상](http://youtu.be/pp2S2lHjzZI)


