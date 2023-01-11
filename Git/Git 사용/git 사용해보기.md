# Git 사용

## git 사용시 알아야할 개념

### 1. repository (저장소)

프로젝트 진행시 필요한 파일을 담은 프로젝트 디렉토리가 있다 가정하자. git으로 프로젝트 디렉토리의 버전을 관리하면 원하는 시점마다 디렉토리의 안에 어떤 것들이 있는지 어떻게 변하는지 기록할 수 있다. git이 이러한 정보들을 기록하는 곳을 레포지토리라고 한다.

즉, 레포지토리 안에는 프로젝트의 초기 모습부터 최근 모습까지 버전별로 담기게 된다. git 사용시 프로젝트안에 .git이라는 디렉토리가 만들어지는데 이 디렉토리를 레포지토리라고 한다. (버전별 프로젝트 모습, 버전별 변경 사항에 대한 설명등과 같은 사항들이 저장되어 있다. -> 프로젝트 디렉토리와 레포지토리는 다른 개념)

### 2. commit (커밋)

프로젝트 디렉토리 안에서 작업을 진행하다보면 현재의 모습을 하나의 버전으로 남기고 싶을때가 있다. 이때 프로젝트 디렉토리의 모습을 하나의 버전으로 남기는 작업을 '커밋한다'라고 표현한다. 커밋을 하게될 경우 프로젝트 당시의 모습이 사진처럼 레포지토리에 저장되며 이때 고정된 결과물 자체도 커밋이라 한다. (레포지토리에 저장된 커밋을 참조하면 과거의 프로젝트 디렉토리의 모습을 볼 수 있음)

### 정리

**커밋**: 프로젝트 디렉토리의 특정 모습을 하나의 버전으로 남기는 행위 & 그 결과물

**레포지토리**: 커밋이 저장되는 곳 (.git 디렉토리, 프로젝트 디렉토리와 별개)

## git 사용

터미널에서 'MathTool'이라는 프로젝트 생성

```
mkdir MathTool
```

git으로 버전관리를 하기 위해 다음 명령어 실행

```
git init
```

현재 폴더에 비어있는 레포지토리를 생성 (.git)

만든 MathTool 디렉토리에서 파일을 하나 생성 후 저장 (예시로 calculator.js을 만듬)

커밋을 하기 전에 반드시 `config` 명령어를 통해 깃에게 커밋한 사람을 알려줘야 한다.

```
git config user.name "codeit"
git config user.email "cloud@codeit.kr"
```

이후 커밋 (현재 디렉토리의 모습을 레포지토리에 하나의 버전으로 저장)
커밋에는 이름, 이메일 뿐만 아니라 커밋에 대한 정보(어떤 내용을 커밋했는지: 커밋 메시지)도 포함되어야함.

```
git commit -m "Create calculator.js"
```

다음과 같은 에러가 발생할 수 있는데 아직 깃으로 작업을 하지 않았기 때문에 버전 관리의 대상이 아니라는 에러 문구이다. (untracked -> git에 의해 추적되지 않고 있다.)

```
nothing added to commit but untracked files present (use "git add" to track)
```

위의 에러가 발생한 이유는 커밋을 할 때 커밋할 파일을 미리 지정해줘야 하기 때문이다. 즉, 파일을 생성하거나 수정하면 해당 파일의 새로운 모습이 커밋에 포함될 것이라 지정해줘야 커밋이 가능하며 이러한 사전 작업을 'add'라고 한다.

add 명령어 (커밋에 반영하고 싶은 파일을 지정)

```
git add calculator.js
```

이후 다시 커밋을 하면 정상적으로 커밋이 되는 걸 확인할 수 있다.
(아래 메시지의 root-commit은 프로젝트의 첫 번째 커밋이라는 의미이다.)

```
[master (root-commit) 29d433f] Create calculator.js
 1 file changed, 7 insertions(+)
 create mode 100644 calculator.js
```

### 정리 (커밋에 관한 주의사항)

1. 처음으로 커밋을 하기 전 `config` 명령어로 사용자의 이름과 이메일 주소를 설정
2. 커밋할 파일을 `git add`로 지정
3. 커밋 메시지 남기기 (`git commit -m`)

## git의 3가지 작업 영역

git은 내부적으로 크게 다음과 같은 3가지 종류의 작업 영역을 두고 동작함.

**1. working directory**

**2. staging area**

**3. repository**

첫 번째 영역인 **working directory**란 작업을 하는 프로젝트 디렉토리를 말한다. (위의 작업을 예시로 들면 MathTool이 이에 해당)

두 번째 영역인 **staging area**는 git add한 파일들이 존재하는 영역. 커밋을 하게되면 staging area에 있는 파일들만 커밋에 반영된다.

세 번째 영역인 **repository**는 working directory의 변경 이력들이 저장되어 있는 영역. 즉, 커밋들이 저장되는 영역을 말한다.

- working directory에서 작업 후,
- 작업한 파일들을 git add,
- 커밋을 하면 staging area에 있던 파일들의 모습이 스냅샷처럼 레포지토리(.git 디렉토리)에 저장됨

<img src = "./image.png">

<img src = "./image2.png">

**만약 working directory에서 여러 파일을 수정하는 작업을 하고 일부만 커밋에 반영하고 싶을때, 반영하고 싶은 파일들만 git add를 통해 staging area에 올리고 커밋에 반영할 수 있기 때문에 staging area가 필요하다.**

working directory는 working tree, staging area는 index라고도 한다.

### git add 더 알아보기

1. 'git status'를 통해 현재 상태를 확인 가능 (깃이 인식하고 있는 프로젝트 디렉토리의 현재 상태를 보여줌 -> 커밋하기전 git status로 staging area에 수정한 파일이 전부 있는지 확인할때 사용)

2. 'git add 디렉토리명/' 을 해주면 디렉토리내의 모든 파일이 staging area에 추가됨.

3. 'git add .'을 해주면 현재 프로젝트 디렉토리내에서 변경사항이 생긴 모든 파일을 staging area에 추가함. (이렇게 자주 쓰임)

## git이 보는 파일의 4가지 상태

Git으로 관리되는 파일은 일종의 '상태(status)'라는 걸 가지고 있다.

일단 Git에서 파일들은 크게 다음 2가지 상태를 가진다.

1. Untracked 상태
2. Tracked 상태

그리고 Tracked 상태는 다시 아래와 같은 3가지 상태로 나눌 수 있다.

1. Staged 상태
2. Unmodified 상태
3. Modified 상태

1) Untracked 상태

Untracked는 '추적되지 않고 있는'이라는 뜻. 이 상태는 파일이 Git에 의해서 그 변동사항이 전혀 추적되고 있지 않는 상태를 뜻함. 예를 들어, 파일을 새로 생성하고 그 파일을 한 번도 git add 해주지 않았다면 이 상태이다.

2. Tracked 상태

파일이 Git에 의해 그 변동사항이 추적되고 있는 상태입니다. 이 상태는 다시 그 특성에 따라 3가지 상태로 나뉘게 된다.

(1) Staged 상태

파일의 내용이 수정되고나서, staging area에 올라와있는 상태를 Staged(스테이징된, stage area에 올려진) 상태.

새로 생성한 파일에 내용을 쓰고 git add를 해주거나
한 번이라도 커밋에 포함됐었던 파일이라도 내용을 수정하고 git add를 해주면 이 상태.

(2) Unmodified 상태

현재 파일의 내용이 최신 커밋의 모습과 비교했을 때 전혀 바뀐 게 없는 상태면 그 파일은 Unmodified(수정되지 않은, 변한 게 없는) 상태. 커밋을 하고 난 직후에는 working directory 안의 모든 파일들이 이 상태가 된다.

(3) Modified 상태

최신 커밋의 모습과 비교했을 때 조금이라도 바뀐 내용이 있는 상태면 그 파일은 Modified(수정된) 상태.

이렇게 Git에서 파일은 매 순간 4가지 상태 중 하나의 상태에 있게 된다. 이 내용을 그림으로 정리하면 아래와 같다.

<img src = "./image3.jpeg">

- Add the file : Untracked 상태의 파일을 처음으로 git add 해주면 Staged 상태가 된다.
- Edit the file : 최신 커밋과 비교했을 때 차이가 없는 Unmodified 상태의 파일의 내용을 수정하면 Modified 상태가 된다.
- Stage the file : Modified 상태의 파일을 git add 해주면 Staged 상태가 된다.
- Remove the file : 파일을 삭제하면 당연히 Git에서 더이상 인식하지 않는다.
- Commit : 커밋을 하면 staging area에 있던 파일들이 커밋에 반영되고, 이제 모든 파일들은 최신 커밋과 차이가 없게 되니까 Unmodified 상태가 된다.

### git reset

git add로 staing area에 올린 파일을 git reset을 사용하여 staging area에서 제거할 수 있다.

```
git reset '파일명'
```

staging area에서만 제거할 뿐, 변경된 모습은 working 디렉토리에 그대로 남아 있음(즉 변경된 작업상태는 그대로 유지)

### git 커맨드의 사용법 알기

```
git help '알고 싶은 커맨드의 이름'
man git-'알고 싶은 커맨드'
```

을 통해 커맨드의 의미 혹은 사용법을 좀 더 자세히 알 수 있다.

ex)

```
git help add
man git-add
```

사용하면 해당 커맨드에 대한 설명이 자세히 나오는데 해당 설명 화면에서 나가고 싶다면 'q' (quit)을 입력하면 된다.

## git 커맨드 정리

- git init : 현재 디렉토리를 Git이 관리하는 프로젝트 디렉토리(=working directory)로 설정하고 그 안에 레포지토리(.git 디렉토리) 생성
- git config user.name 'codeit' : 현재 사용자의 아이디를 'codeit'으로 설정(커밋할 때 필요한 정보)
- git config user.email 'teacher@codeit.kr' : 현재 사용자의 이메일 주소를 'teacher@codeit.kr'로 설정(커밋할 때 필요한 정보)
- git add [파일 이름] : 수정사항이 있는 특정 파일을 staging area에 올리기
  git add [디렉토리명] : 해당 디렉토리 내에서 수정사항이 있는 모든 파일들을 staging area에 올리기
- git add . : working directory 내의 수정사항이 있는 모든 파일들을 staging area에 올리기
- git reset [파일 이름] : staging area에 올렸던 파일 다시 내리기
- git status : Git이 현재 인식하고 있는 프로젝트 관련 내용들 출력(문제 상황이 발생했을 때 현재 상태를 파악하기 위해 활용하면 좋음)
- git commit -m "커밋 메시지" : 현재 staging area에 있는 것들 커밋으로 남기기
- git help [커맨드 이름] : 사용법이 궁금한 Git 커맨드의 공식 메뉴얼 내용 출력
