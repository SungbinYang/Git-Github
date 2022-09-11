> 인프런의 강민철님의 [모두의 깃 깃허브](https://www.inflearn.com/course/%EB%AA%A8%EB%91%90%EC%9D%98-%EA%B9%83-%EA%B9%83%ED%97%88%EB%B8%8C/dashboard) 강의를 참조하였습니다.

# 준비하기

## 깃이 없는 세상: 버전과 버전관리

먼저 깃이란 무엇일까? 사전적 정의는 '버전을 관리해주는 도구'이다. 요즘 실무 개발자들은 깃을 통해 프로젝트 소스를 올리고 변경하고 삭제하고 한다. 그럼 왜 깃을 쓰는지 깃이 없었을 시절을 생각해보자.

### 깃이 없는 세상

깃이 없으면 아마 여러 문제점들이 나오겠지만 가장 큰 이슈는 이 3가지이다.

- 변경내역 확인이 어렵다.
- 작업을 되돌리기 어렵다.
- 협력하기 어렵다.

그럼 왜 이 3가지 이슈가 큰 문제인지 살펴보자.

#### 변경내역을 확인하기 어렵다.

대개 파일을 단순히 저장하면 이전에 어떤 내용에서 변경이 되었는지 추적하기가 어려워진다. 그래서 변경내역이 발생할 시, 파일을 계속 생성하는 것은 메모리 낭비가 심할 것이다. 또한 최종본이 될 때까지 어떠한 변경사항으로 만들어졌는지 확인할 길이 없다.

#### 버전을 되돌리기 어렵다.

위의 네이버 사이트가 있는데 일부 부분을 변경하고자 한다. 그래서 예를 들어 로고 모양을 변경하였다. 디자인을 변경하는 과정에서 소스 코드 파일 곳곳을 수정하거나 삭제했을 것이다. 하지만 로고 모양을 다시 원상태로 복구를 하고 싶을 때, 다시 말해, 이전으로 돌리고 싶을 때, 깃을 사용하지 않으면 어려워진다.

#### 협력하기 어렵다.

우리는 실무에서 대개 프로젝트에 대해 특정 모듈을 분리하여 개발을 진행한다. 그리고 추후에 각 개발한 모듈들을 합치는 작업을 진행한다. 하지만 깃이 존재하지 않으면 이 모듈에서는 어떤 파일을 생성했고, 삭제했으며 수정을 하였는지 즉, 수 많은 코드의 변경사항을 확인하고 작업을 되돌리고 협업하기 어렵다. 하지만, 변경사항(=버전)을 조금 더 일목요연하기 관리하자는 생각으로 깃이 필요하기 된 것이다.

### 버전과 버전관리 이해하기

- 버전이란 유의미한 변화가 결과물로 나오는 것을 말한다.
- 버전관리란, 변경내역들을 기억하며, 필요하다면 작업을 되돌리며 여러명의 코드를 쉽게 나누고 합치고 개발하는 것을 말한다.

## 깃/깃허브/소스트리란?

- 깃: 버전 관리 해주는 도구 = 버전관리시스템
- 소스트리: 깃을 편하기 쓸수 있는 프로그램
- 깃허브: 원격 저장소 호스팅 서비스 = 인터넷으로 깃을 관리하는 프로젝트를 관리해주는 서비스 (+ 개발자들 SNS)

## 깃 설치하고 설정하기

본 필자는 환경이 mac os이므로 mac 기준으로 작성하겠다.

먼저 횐경은 [homebrew](https://brew.sh/index_ko)가 설치되었다는 가정하에 진행한다.

```shell
$ brew install git
```

위의 명령어 한 줄이면 바로 설치가 된다. 이후에 설정이 필요한데 설정하는 명령어는 다음과 같다.

### 개행문자 설정

```shell
 $ git config --global core.autocrlf input ( 개행 문자 설정 :: MAC 기준 )
 $ git config --global core.autocrlf true ( 개행 문자 설정 :: Windows 기준 )
```

### 사용자 정보, 커밋(버전 생성)을 위한 정보 등록

```shell
$ git config --global user.name 'YOUR_NAME'
$ git config --global user.email 'YOUR_EMAIL'
여기서 사용자 이름은 아무거나 지정해도 되지만 되도록 깃에 등록한 이름으로 하는것이 좋다.
```

### 구성확인

```shell
$ git config --global --list
```

## 소스트리 설치하기

[소스트리](https://www.sourcetreeapp.com/)를 방문하여 다운을 받는다.

다운받은 파일을 실행 후, 깃의 사용자이름과 사용자 이메일을 작성한다.

그러면 설치완료가 된다.

## 깃허브 가입

[깃허브](https://github.com/)로 들어가서 일반 웹사이트 가입하는 것처럼 가입하면 된다.

## 로컬 저장소 만들기

먼저 이론적인 학습하기 전에 이전에 설치한 소스트리로 로컬저장소를 세팅해준 후 이론 학습을 하기로 한다. 여기서 로컬 저장소란 깃으로 관리되는 버전들이 모여있는 저장소를 의미하며 목적지 경로란 해당경로를 깃으로 관리한다고 정의한 것이다.

### 소스트리 로컬 저장소 생성

먼저 소스트리를 켜고 새로만들기라는 탭에 로컬저장소 생성이라는 버튼을 클릭한다.

여기서 임의로 만든 폴더를 목적지 경로로 설정 후 생성하기 버튼을 클릭하면 아래와 같이 생성된다.

그리고 해당 디렉터리를 보면 .git이라는 파일이 생긴것을 볼 수 있다.

그리고 소스트리의 생성된 로컬저장소를 클릭하면 다음과 같은 화면이 열린다.

이 화면에서 해당 목적지 경로의 버전 히스트로가 저장되고 관리된다.

## 버전관리의 큰 그림

깃이 관리하는 공간은 총 3개의 공간이 존재한다.

- 작업 디렉터리(working tree) : 버전 관리의 대상이 위치하는 공간 (.git이 있는 디렉터리)
- 스테이지: 다음 버전이 될 후보가 올라가는 공간 (스테이지를 인덱스라고도 불린다.)
- 저장소: 버전이 만들어지고 관리되는 공간

여기서 작업 디렉터리는 사용자 눈에 보이는 공간이지만 스테이지와 저장소는 깃이 관리하는 가상의 공간 즉, 눈에 보이지 않는 디렉터리이다.

### 하나의 버전이 만들어지는 과정

우리는 하나의 버전을 만드는 과정을 알아 볼 것이다. 먼저 작업 디렉터리에 여러 파일들이 존재하고, 엄청난 소스코드가 수정되었다고 가정하다. 이런 수많은 변경사항 중에 버전으로 만들고 싶은 변경사항을 스테이지에 올리는 작업이 필요하다. 이것을 스테이지에 add 한다라고 부른다. 버전관리를 하고 싶은 변경사항을 스테이지에 올렸으면 이 파일들을 저장소에 올리는 과정이 필요한데 이것을 저장소로 커밋한다고 한다.

내용을 요약하면 아래와 같다.

- 작업 디렉터리 내에서 변경사항 생성
- 스테이지로 add
- 저장소로 commit
