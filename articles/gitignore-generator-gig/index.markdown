{
    "title": ".gitignore file generator gig 소개",
    "author": "Insanehong",
    "date": "2013-06-05T15:58:31.302Z",
    "categories": [
        "git"
    ],
    "tags": [
        "git",
        "gitignore",
        "generator"
    ],
    "acceptComment": true,
    "acceptTrackback": true,
    "published": "2013-06-05T15:58:31.302Z",
    "status": "publish",
    "important": false,
    "advanced": {}
}

# .gitignore file generator gig 

최근들어 잉여력이 폭팔하고 있는 관계로 무엇인가 생산적인 일을 해보려고 찾아해매던 중 항상 [gitignore.io](http://gitignore.io) 의 도움을 받아 생성해 오던 `.gitignore`  파일을 오프라인에서도 쉽게 사용할 수 있는 ***important CLI Command set***으로 만들어 보자 라는 참 잉여스런 생각을 하게 되었다. 

> [gitignore.io](http://gitignore.io) 에서도 CLI 로 사용가능한 방법을 지원하지만 이역시 RESTfull API 를 이용하는 방식이라 오프라인에서는 사용할 수 없다

## gig

***info gig***는  [gitignore template](http://github.com/github/gitignore) 를 사용한 node.js 기반의  `.gitignore` file generator 이다. 

***info gig*** 은 `.gitignore`  파일 자동 생성과 ***success Custom Template*** 생성을 지원하는 `CLI Command Set` 으로 구성되어 있다. 

```
$ gig --help
show   Display template condition.
gen    Create .gitignore files. If aleady .gitignore file   : append ignore conditions to .gitignore
pkg    Create custom template. If aleady same template file exists : append ignore conditions to templae file

Here are the options:
--help, -h       Display help text
--version, -v    Display currently version
--name, -n       create new package name
--override, -o   if aleady file exists, override content to file

Here are the template:
actionscript, android, appceleratortitanium, archives, autotools, bancha, c++, c, cfwheels, cmake,
cvs, cakephp, clojure, codeigniter, compass, concrete5, coq, dart, delphi, django,
drupal, eagle, eclipse, emacs, erlang, espresso, expressionengine, finale, flexbuilder, forcedotcom,
fuelphp, gwt, go, grails, haskell, intellij, java, jboss, jekyll, joomla,
jython, kohana, latex, leiningen, lemonstand, lilypond, linux, lithium, magento, matlab,
maven, mercurial, modelsim, monodevelop, netbeans, node, ocaml, osx, objective-c, opa,
oracleforms, perl, phpstorm, playframework, plone, pycharm, python, qooxdoo, qt, quartus2,
r, readme.md, rails, redcar, rhodesrhomobile, ruby, rubymine, sass, sbt, svn,
scala, sdcc, seamgen, sketchup, sublimetext, sugarcrm, symfony, symfony2, symphonycms, tags,
target3001, tasm, textmate, textpattern, turbogears2, typo3, unity, virtualenv, visualstudio, waf,
windows, wordpress, xilinxise, yii, zendframework, gcov, nanoc, opencart, test, vim
```
그럼 지금부터 각설하고 ***info gig***의 설치부터 사용법까지를 알아보도록 한다. 

## gig install

> ***info gig***  는 ***success node.js*** 로 만들어졌으며 ***important npm***을 통해서 배포 되었기 때문에 ***success node.js***와  ***important npm***이 설치 되어야 사용이 가능하다. 이들의 설치는 워낙 참고할만한 reference 가 널려있기에 생략한다. 

```
$ npm install -g gig
```


## tempate conditions 확인하기

***info gig*** 에서 지원하는 ***success show*** 명령어를 통해 `template` file 의 내용을 확인 할수 있다. 

```
$ gig show java osx intellij sublimetext
 java :
*.class

# Package Files #
*.jar
*.war
*.ear

osx :
.DS_Store
.AppleDouble
.LSOverride
Icon


# Thumbnails
._*

# Files that might appear on external disk
.Spotlight-V100
.Trashes

intellij :
*.iml
*.ipr
*.iws
.idea/

sublimetext :
# SublimeText project files
*.sublime-workspace
```

`.gitignore` 에 포함될 조건들을 확인 했으면 이제 `git repository` 에 `.gitignore` 파일을 생성해 보자.  

## generate .gitignore file for your git repository

위에서 확인한 조건들로 구성된 `.gitignore` 파일을 만들어 보도록 하자.

```
$ gig gen  java osx intellij sublimetext
Completed Generate!
/Users/insanehong/workspace/project/gigtest/.gitignore:

### java ###
*.class

# Package Files #
*.jar
*.war
*.ear

### osx ###
.DS_Store
.AppleDouble
.LSOverride
Icon


# Thumbnails
._*

# Files that might appear on external disk
.Spotlight-V100
.Trashes

### intellij ###
*.iml
*.ipr
*.iws
.idea/

### sublimetext ###
# SublimeText project files
*.sublime-workspace

```
간단한 명령어 한줄로 java, osx, intellij, sublime text 에서 생성하는 파일 혹은 디렉토리에 대한 조건을 가진 `.gitignore` 파일이 생성되었다. 

위의 경우 `.gitignore` 파일이 존재하지 않는 디렉토리에서 ***important gen*** 명령을 사용했기 때문에 파일을 새로 생성하여 만들었지만 이미 `.gitignore` 파일이 존재한다면 기존에 등록되어 있는 조건들에 추가 되어지게 된다. 

위에서 만든 조건에 window, vim 의 조건들을 추가 해자.

```
$ gig gen windows vim
Completed Generate!
/Users/insanehong/workspace/project/gigtest/.gitignore:

### java ###
*.class

# Package Files #
*.jar
*.war
*.ear

### osx ###
.DS_Store
.AppleDouble
.LSOverride
Icon


# Thumbnails
._*

# Files that might appear on external disk
.Spotlight-V100
.Trashes

### intellij ###
*.iml
*.ipr
*.iws
.idea/

### sublimetext ###
# SublimeText project files
*.sublime-workspace
### windows ###
# Windows image file caches
Thumbs.db
ehthumbs.db

# Folder config file
Desktop.ini

# Recycle Bin used on file shares
$RECYCLE.BIN/

### vim ###
.*.s[a-w][a-z]
*.un~
Session.vim
.netrwhist
*~
```
기존에 만들었던 java, osx, intellij, sublimetext 의 조건들에 새로 추가한 windows, vim 의 조건들이 추가된것을 확인 할수 있다. 

때로는 기존파일에 추가하는것이 아니라 기존파일을 무시하고 새로운 condition 으로 덮어쓰기를 해야하는 경우가 있다. 
이럴경우에는 ***info --override*** 혹은 단축옵션인 ***info -o*** 를 사용하면 된다. 

위에서 만들어진 `.gitignore` 파일을  osx, sublimetext 의 조건만 가진 새로운 녀석으로 교체 해보자.

```
$ gig gen -o osx sublimetext
Completed Generate!
/Users/insanehong/workspace/project/gigtest/.gitignore:
### osx ###
.DS_Store
.AppleDouble
.LSOverride
Icon


# Thumbnails
._*

# Files that might appear on external disk
.Spotlight-V100
.Trashes

### sublimetext ###
# SublimeText project files
*.sublime-workspace
``` 

기존의 파일을 osx, sublimetext 의 조건만을 가진 녀석으로 override 한것을 확인 할 수 있다. 

## 자주사용되는  template packaging 하기

지금까지 소개한 방법은 ignore 조건에 추가될 condition 을 하나하나 지정하여야 했다. 하지만 개발머신이 고정적이며 사용하는 환경이 자주 바뀌는 일이 없다면 좀더 쉬운 방법으로 생성하는 방법을 찾게 된다. 

이럴때는 자주쓰는 template 을 하나로 묶어 새로운 template package 로 만들어서 사용하면 좀더 간편하게 사용할 수 있다. 

본인은 imac, macbook pro 를 개발머신으로 사용하고 있고 sublime text2 와 intellij 를 사용하여 개발하고 있다. 
그래서 이 녀석들을 하나로 묶어 `mypkg` 라는 이름의 template 을 생성해 보겠다. 

```
$ gig pkg -name 'mypkg' osx sublimetext intellij
Completed packaging!
mypkg.gitignore :
### osx ###
.DS_Store
.AppleDouble
.LSOverride
Icon


# Thumbnails
._*

# Files that might appear on external disk
.Spotlight-V100
.Trashes

### sublimetext ###
# SublimeText project files
*.sublime-workspace

### intellij ###
*.iml
*.ipr
*.iws
.idea/
``` 
`mypkg` 란 이름으로 새로운 template 를 만들었다. 새로운  template 가 제대로 생성되었는지 확인 하는 방법은 
***info --help*** 를 통해 template list 를 확인하거나 ***info show*** 명령어를 통해 확인해보는 것이다. 

```
$ gig show mypkg
mypkg :
### osx ###
.DS_Store
.AppleDouble
.LSOverride
Icon


# Thumbnails
._*

# Files that might appear on external disk
.Spotlight-V100
.Trashes

### sublimetext ###
# SublimeText project files
*.sublime-workspace

### intellij ###
*.iml
*.ipr
*.iws
.idea/
``` 

***info pkg*** 또한 ***info gen*** 과 마찬가지로 기존의 동일한 template 파일이 존재하면 해당 파일에 조건을 추가하게 되며 새로운 조건으로 구성된 파일로 만들기 위해서 ***info --override*** 혹은 단축옵션인 ***info -o***  옵션을 사용하면 된다. 

방금 만든 `mypkg` 를 linux, vim 의 조건으로 변경해 보도록 하자

```
$ gig pkg -name 'mypkg' -o linux vim
Completed packaging!
mypkg.gitignore :
### linux ###
.*
!.gitignore
*~

### vim ###
.*.s[a-w][a-z]
*.un~
Session.vim
.netrwhist
*~
```

이로서 ***info gig***의 사용방법은 모두 익히게 되었다. 

이 녀석을 처음 생각하고 구현하기 까지는 총 3일 정도가 걸렸다. 첫째날은 아이디어를 구상해놓고도 회식으로 인하여 시간이 나지 않았고 다음날은 명령어셋을 어떻게 지원할것인가를 고민하였다. 

처음 구성한 명령어셋은 복잡하기도 하고 굉장히 세분화된 명령어들로 구성하였지만 오히려 많은 명령어를 지원하는 것이 되려 불편하다고 생각하여 과감히 3개의 명령어로 줄여버렸다. 

이 3개의 명령어로도 생각했던 모든 기능은 다 지원할 수 있다고 생각했기 때문에 더이상 명령어를 추가할 계획은 없다.(더 추가할 명령어가 있을지도 의문이다.)

어째든 이글을 적는동안에도 종종 버그 혹은 버그아닌 버그(??) 들이 발견되어 fetch를 거듭한 끝에 처음 공개할대 `v0.1.4` 였던 녀석이 지금은 `v0.1.7` 이 되어 버렸다. 

npm 특성상 동일 버전을 달고 업데이트를 할수 없기 때문에 어쩔수 없는 선택이였지만 제대로 테스트 하지 못한 본인의 잘못이 더 큰거 같다. 

어째든 여기까지 이글을 읽은 분이라면 꼭 `npm update -g gig` 명령을 수행해보기 바라며 이 글을 마친다.
 
