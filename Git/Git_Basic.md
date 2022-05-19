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
> Markdown의 본질은 글에게 역할을 부여하는 것이다.
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

## 03. Github

---

### 01) 정의

- Git을 사용하는 프로젝트를 지원하는 **Web 호스팅 서비스**

> ⭐ **Github를 많이 사용하는 이유**
>
> 프로젝트의 모든 구성원들이 온라인을 통해 소스코드를 효율적으로 관리 할 수 있다.

### 02) 초기설정

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

### 03) 업로드

```bash
$ git add .
$ git commit -m "간단한 이유"

# add + commit
$ git commit -a

$ git push origin master

# -u 옵션을 사용하면, 두 번째 커밋부터는 저장소 이름, 브랜치 이름을 생략 가능
$ git push -u origin master
$ git push
```

### 04) 구조

![](https://hphk.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F357df618-2ddf-4f18-b96c-c1b0787a1a45%2FUntitled.png?table=block&id=56fbaebf-cfba-4dbf-b129-711c2a89dae0&spaceId=daa2d103-3ecd-4519-8c30-4f55e74c7ef4&width=2000&userId=&cache=v2)

![이미지 출처: https://sjh836.tistory.com/](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=http%3A%2F%2Fcfile6.uf.tistory.com%2Fimage%2F237B984B58CE95E90BD98B)

## 04. 

---

