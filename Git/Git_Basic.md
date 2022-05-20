# Git 기본

## 01. Markdown

---

### 01) 정의

- 일반 텍스트 기반의 경량 마크업(Markup) 언어

>⭐ **마크업(Markup)이란**
>
>마크업 언어는 글의 역할을 지정하는 일종의 표시로 둘러싸인 언어

### 02) 장단점

**장점**

1. 문법이 직관적이고 관리가 쉽다.
2. 지원 가능한 플랫폼과 프로그램이 다양하다.

**단점**

1. 표준이 없어 사용자마다 문법이 상이하다.
2. 모든 HTML 마크업 기능을 대신하지는 못한다.

> ⚠ **주의사항**
>
> Markdown의 본질은 글에게 **역할**을 부여하는 것이다.
>
> 글씨의 크기를 키우고 싶다는 이유로 내용에게 제목의 역할을 부여하면 안된다.

### 03) 문법
1. 제목

	```markdown
   # 제목1
   ## 제목2
   ### 제목3
   #### 제목4
   ##### 제목5
   ###### 제목6
	```

2. 목록

	- `tab 키`를 이용해서 들여쓰기
   
   ```markdown
   1. 혼합 해보기 1
   	- 순서 없음
   	+ 순서 없음
   	* 순서 없음
   2. 혼합 해보기 2
   	1. 순서 있음
   	- 순서 없음
   	2. 순서 있음
   ```
   
3. 강조

	```markdown
    *이탤릭체1* 
    _이탤릭체2_
	
    **볼드체1**
    __볼드체2__
	
    ~~취소선~~
	```

4. 코드

	````markdown
	`inline code`
	
	```python

	for i in range(10):
	print(i)
	```
	
	```bash
	$ touch test.txt
	```
	
	```
	Just plain text
	```
	````

5. 링크

	```markdown
   [GOOGLE](https://google.com)을 눌러서 구글로 이동하세요.
	```

7. 이미지

	```markdown
   ![Git로고](https://git-scm.com/images/logo@2x.png)
	```

9. 인용

	```markdown
    > 인용문을 작성합니다.
    >> 중첩된 인용문 1
    >>> 중첩된 인용문 2
    >>>> 중첩된 인용문 3
    >>>>> 중첩된 인용문 4
	```

11. 표

    - Typora에서는 ctrl + T 를 통해서 쉽게 표 생성이 가능하다.
    - 행을 늘릴 때는 ctrl + enter 를 누른다.

	```markdown
    | 동물   | 종류   | 다리 개수 |
    | ------ | ------ | --------- |
    | 사자   | 포유류 | 4개       |
    | 닭     | 조류   | 2개       |
    | 도마뱀 | 파충류 | 4개       |
	```

13. 수평선

	```markdown
    ---
    ***
    ___
	```
## 02. Git

---

### 01) 정의

- **Git**은 컴퓨터 파일의 변경사항을 추적하고 여러 명의 사용자들 간에 해당 파일들의 작업을 조율하기 위한 **분산 버전 관리 시스템**이다

> ⭐ **Git을 많이 사용하는 이유**
>
> 백업, 복구, 협업에 매우 효과적이다.

### 02) 구조

![Git구조](https://hphk.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fc86c667a-616f-45b6-892e-15da6a3c494e%2FUntitled.png?table=block&id=e49bee4e-6738-449a-b659-f466ae739007&spaceId=daa2d103-3ecd-4519-8c30-4f55e74c7ef4&width=2000&userId=&cache=v2)

### 03) 명령어

```bash
# Git 초기 설정 (최초 한 번만)
$ git config --global user.name "이름"
$ git config --global user.email "메일 주소"
$ git config --global -l

# 1. Git 관리폴더 설정
$ git init
Initialized empty Git repository in C:/Users/yeoub/GitStorage/TIL/.git/

# 2. WD -> SA
$ git add my_folder/
$ git add a.txt
$ git add .

# 3. SA -> Local
$ git commit -m "간단한 이유"

# 상태 확인
$ git status
$ git log --onelist
```

### 04) 특수 파일

1. README.md
   - 프로젝트 대문 설명
   - **버전관리 시작할 때 바로 만드는 것을 추천**
2. .gitignore
   - 추적하지 않을(버전을 만드지 않을) 파일/폴더 설정
   - 중요한 데이터 파일(개인정보, 유저데이터, Key 등)을 숨김
   - 이미 commit(추적)한 파일은 무시 ❌ -> **버전관리 시작할 때 바로 만드는 것을 추천**
   - [gitignore.io](https://www.toptal.com/developers/gitignore/)

## 03. Github

---

### 01) 정의

- Git을 사용하는 프로젝트를 지원하는 **Web 호스팅 서비스**

> ⭐ **Github를 많이 사용하는 이유**
>
> 프로젝트의 모든 구성원들이 온라인을 통해 소스코드를 효율적으로 관리 할 수 있다.

### 02) 초기 설정

> ⚠ **주의사항**
>
> Setting > Repositories > Repository default branch > `main -> master` 로 변경

1. Repositories > New > `Repository Name` 입력 > Create repository

2. `https://github.com/Username/Repository Name.git` 복사

```bash
# 추가
$ git remote add origin https://github.com/Username/RepositoryName.git
$ git remote -v
origin  https://github.com/Username/RepositoryName.git (fetch)
origin  https://github.com/Username/RepositoryName.git (push)

# 삭제
$ git remote rm origin
```

### 03) ⭐명령어

#### 01. 송신

```bash
##### 송신 (Local => Remote) #####
# WD -> SA
$ git add .

# SA -> Local Storge(Commit)
$ git commit -m "간단한 이유"

# WD -> Remote Storge(Commit)
$ git push origin master

# -u 옵션을 사용하면
# 두 번째 커밋부터는 저장소와 브랜치 생략 가능
$ git push -u origin master
$ git push
```

#### 02. 수신 (협업)

```bash
##### 수신 (Local <= Remote) #####
# Download(생성) Local X Remote O
$ git clone https://github.com/username/RepositoryName.git

# Update(수정)
$ git pull origin master

# 버전이 중복될 때 병합
# $ git merge
```

#### 03. 기타

```bash
#### 기타 ####

# 상태 확인
$ git status
$ git log --oneline
$ git log --oneline --graph --all

# 복구
$ git reset
```

### 04) 구조

![](https://hphk.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F357df618-2ddf-4f18-b96c-c1b0787a1a45%2FUntitled.png?table=block&id=56fbaebf-cfba-4dbf-b129-711c2a89dae0&spaceId=daa2d103-3ecd-4519-8c30-4f55e74c7ef4&width=2000&userId=&cache=v2)

![이미지 출처: https://sjh836.tistory.com/](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=http%3A%2F%2Fcfile6.uf.tistory.com%2Fimage%2F237B984B58CE95E90BD98B)

### 05) 권한 부여

- Settings > Collaborators > Manage access > Add people

### 06) Branch (가지)

- 독립적으로 어떤 작업을 진행하기 위한 개념이다.

![출처 : backlog.com/git-tutorial/kr](https://user-images.githubusercontent.com/105831105/169457261-8c61d302-9ccc-4a06-bdae-c5538e8be2c6.png)

![출처 : backlog.com/git-tutorial/kr](https://user-images.githubusercontent.com/105831105/169457314-7d831a92-1af2-4280-8397-d2f8d697a484.png)

![image](https://user-images.githubusercontent.com/105831105/169465384-412e8c76-28e1-4f1f-9ca1-8b86d6f86dce.png)

 #### 01. 명령어

```bash
# branch 목록
$ git branch

# branch 생성
$ git branch <branchname>

# branch 이동 master => <branchname>
$ git switch <branchname>

# merge (합병)
$ git switch master # master로 이동
$ git merge hotfix	# master ⊃ hotfix 

# branch 삭제
$ git branch -d hotfix
```

#### 02. Merge 3가지 상황

1. Fast-Forward (빨리감기)
   - master버전이 그대로이고, 추가된 branch의 버전이 최신버전일때
2. Auto-merging (자동합병)
   - 서로 수정 또는 추가된 파일이 겹치지 않을 때 (**단, 줄이 추가된 것은 겹친 것으로 판단**)
3. Comflict (충돌)
   - master와 branch 버전이 추가되고, 다른 작업자가 내가 같은 라인을 수정했을 때

> 🚫 **주의사항**
>
> **Git**은 **Commit**을 기준으로 움직이기 때문에 `Switch` 전에 반드시 `Commit`을 하고 이동해야한다.

#### 03. 유용한 기능

- Visual Studio Code -> Git Graph 플러그인

> 🚫 **주의 사항**
>
> 1. 왠만하면 Github에서 수정 ❌
>    - 기본은 Local에서 `push` 하고, Github에서 수정하지 않는다.
>    - 부득이한 경우 `pull`해서 받아와야 한다.
> 2. 프로젝트 폴더에 `git init` 설정해야 한다. 
>    1. 하위 폴더 `git init` ❌
>    2. 상위 폴더 `git init` ❌

## 04. Pull Request (업데이트 요청)

### 01) Feature Branch Workflow

- Shared repository model ( 저장소의 소유권이 ⭕ )

### 02) Forking Workflow

- Fork & Pull model ( 저장소의 소유권이 ❌ )

- ⁉**Forking Workflow를 사용하는 이유**

  1. 다른 사람이 동시에 작업할 수 있기 때문에

  2. 업로드 권한을 분리하기 위해서
  3. 내가 만든 새로운 기능 추가를 걔발자에게 제안하기 위해서

#### 01. 구조

![image](https://user-images.githubusercontent.com/105831105/169475375-22bf527f-3a6d-499b-b10e-063e62087f0d.png)

![image](https://user-images.githubusercontent.com/105831105/169480711-238bae46-e0fe-4209-93d8-9549b0176f04.png)

#### 02. 명령어

```bash
# Github에서 Fork로 Repositories 복제

# origine Remote Storge -> Local Storge
$ git clone https://github.com/edukyle/kakao_clone.git

# 원본 원격 저장소에 대한 이름은 upstream으로 붙이는 것이 일종의 관례
$ git remote add upstream https://github.com/AlexKwonPro/kakao_clone.git

# 기능 추가 branch 생성
$ git switch feature/login

# 기능 구현 후 Local Storge branch<feature/login> -> origine Remote Storge
# ! origine Local Storge branch<master>에 merge 하지않는다.
# $ git push origin master X
$ git push origin feature/login

# Github에서 Pull Request
```

```bash
#### 버전 업데이트 ####
# Pull Request 승인 후 다시 fork

# upstream => Local stroge
$ git switch master

# 새 버전 upstream -> Local Storge branch<master> pull (Fast-forward)
$ git pull upstream master

# 합병된 branch<feature/login> 삭제
$ git branch -d feature/login
```

---

## 04. 참고사이트

- [누구나 쉽게 이해할 수 있는 Git 입문](https://backlog.com/git-tutorial/kr/)
- [Git 특강](https://hphk.notion.site/hphk/Git-22-05-19-22-05-20-AI-18-10bbd9143cef46cf94cc4871b3039e98)
- [지옥에서 온 Git](https://www.youtube.com/playlist?list=PLuHgQVnccGMA8iwZwrGyNXCGy2LAAsTXk)
