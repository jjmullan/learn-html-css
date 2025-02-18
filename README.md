###### Likelion Front-end School

# HTML/CSS

[실습 예제 보기](https://jjmullan.github.io/learn-html-css/)

## 목차

###### 2025-02-12

0. [Github](#0-github)

   협업 환경 세팅하기 <br />
   git clone, git pull, npm i

1. [HTML 개요](#1-html-개요)

   Hyper Text Markup Language 란 <br />
   &lt;tag&gt; 구성요소 <br />
   HTML 문서 구조

###### 2025-02-13

2. [HTML 제목과 단락](#02-html-제목과-단락)

   &lt;h1&gt; ~ &lt;h6&gt; <br />
   &lt;p&gt;

3. [HTML 이미지와 피규어]()

   &lt;image&gt; <br />
   &lt;figure&gt;

4. [HTML 하이퍼링크]()

   &lt;a&gt; <br />

###### 2025-02-17

5. [HTML 순서형, 비순서형 목록]()

6. [HTML 정의형 목록]()

7. [HTML 프레이징 요소]()

8. [HTML 인용문과 줄바꿈]()

9. [HTML 테이블]()

10. [HTML 컨테이너 요소]()

###### 2025-02-18

11. [HTML section, main 요소]()

12. [HTML 텍스트 레벨 요소]()

13. [HTML address 요소]()

14. [HTML picture, source 요소]()

15. [HTML video, track 요소]()

16. [HTML iframe, object 요소]()

17. [HTML map, area 요소]()

18. [HTML form (input) 요소]()

###### 2025-02-19

<br />
<br />
<br />
<br />

###### 2025-02-12

## 0. Github

### 0-1. 협업 환경 세팅하기

**스크럼 리더** _scrum leader_ 는 원활한 협업 환경 세팅을 위해 [필요한 package 를 devDefendency 로 설치](#devdefendency-로-package-설치하기)하고(e.g. live-server, prettier) [package.json](#packagejson-작성-예시), [.gitignore](#gitignore-작성-예시), .prettierrc.cjs 등 필요 환경 세팅을 완료한 뒤, github repository 를 생성, push 해두어야 한다.

#### devDefendency 로 package 설치하기

```bash
npm install {패키지명} --save-dev
npm i {패키지명} -D
```

#### .package.json 작성 예시 : live-server, prettier

```javascript
{
  "scripts": {
    "start": "live-server . --port=3000 --host=localhost --no-browser",
    "format": "prettier . --check"
  },
  "devDependencies": {
    "live-server": "^1.2.2",
    "prettier": "^3.5.0"
  }
}
```

#### .gitignore 작성 예시

```bash
# Node.js 관련
node_modules/   # npm 패키지 폴더 (용량 많음) -> npm i 로 패키지 관리로 재설치 가능
dist/           # 빌드 결과물
.env            # 환경 변수 파일 (API 키, DB 비밀번호 등 보안 중요)

# 운영체제 & 편집기 관련
.DS_Store       # macOS의 숨김 파일
Thumbs.db       # Windows의 썸네일 캐시 파일
*.swp           # Vim 편집기 임시 파일
.idea/          # JetBrains IDE 설정 폴더
.vscode/        # VS Code 설정 폴더

# 로그 & 임시 파일
*.log           # 로그 파일
npm-debug.log*  # npm 디버그 로그
yarn-debug.log* # Yarn 디버그 로그
yarn-error.log* # Yarn 에러 로그

# 임의 파일 또는 파일 형식을 지정할 수 있다
test.html
*.js
```

#### package.json 의 "scripts" 사용 예시

```bash
# scripts 에 사용한 package 수동 명령어 사용 예시
npm start
npm run format
```

#### git push 사용 예시

```bash
git push

# 저장소 별칭(origin), 브랜치명(main) 을 지정할 수 있다
git push origin main
```

<br />

### 0-2-1. git clone : Github repository 가져오기

팔로워는 git clone 명령어를 사용하여 스크럼 리더의 Github repository 를 local 에 복제하여, 협업 환경을 동기화한다.

#### git clone 예시

```bash
git clone https://github.com/seulbinim/ssam-html-css.git

# 레퍼지토리 별칭을 임의로 변경하여 가져오고 싶을 떄
git clone -o {브랜치명} https://github.com/seulbinim/ssam-html-css.git
```

#### repository 가 잘 연결되었는지 확인하기

```bash
# 현재 git repository 의 별칭과 github 링크를 확인할 수 있다
git remote -v
```

#### repository 연결 제거하기

협업 환경에서 프로젝트가 종료할 때까지 연결을 제거하지 않는다.

```bash
git remote rm origin
```

<br />

### 0-2-2. git pull : 최신 커밋 유지하기

최초로 github 의 repository 를 pull 할 때 별칭과 브랜치명을 입력한다. 이후 작업할 때는 별칭과 브랜치명을 생략해도 된다.

```bash
# 최초로 pull 할 때
git pull origin main

# 1회 이상 pull 할 때
git pull
```

<br />

### 0-2-3. npm i : 의존성 패키지 설치하기

용량과 버전 관리를 문제로 git 에서는 node_modules/ 폴더를 동기화하지 않는다. git clone 으로 repository 를 가져왔다고 하더라도, node_modules 폴더는 package 가 설치되는 저장소 역할을 하기 때문에 반드시 Local 환경에 설치되어 있어야 한다. 이때, `npm i` 코드로 빠르고 간단하게 설치할 수 있다.

**주의 : 패키지를 설치하기 전 반드시 git pull 명령을 사용하여 최신 내용으로 업데이트가 필요하다**

```bash
# 최신 commit 유지
git pull

# node_modules/ 폴더 설치
npm install
npm i
```

<br />

## 01. HTML 개요

### 01-1-1. Hyper Text 란 ?

정적인 형태의 텍스트에 문서를 연결될 수 있도록 하여, 텍스트 _Text_ 의 기능을 초월 _Hyper_ 하였다.

### 1-1-2. Markup Language 란 ?

태그 _&lt;Tag&gt;_ 를 사용하여 콘텐츠의 의미와 구조를 지정하고, 표시 _Markup_ 하여 컴퓨터가 이해할 수 있는 언어 _Language_ 로 치환한 것이다.

#### Text vs Hyper Text Markup Language

```html
<!-- Text -->
멋쟁이사자처럼

<!-- HTML -->
<회사명>멋쟁이 사자처럼</회사명>
```

<br />

### 01-2. &lt;tag&gt; 구성 요소

태그 _tag_ 는 여는 태그 &lt;&gt;, 닫히는 태그 &lt;/&gt;, 속성 _attribute_, 내용 _content_ 으로 구성된다.

![img](./src/assets/june/html_elements.png)

속성은 태그에 대한 부가적인 정보를 제공한다.

```html
<!-- 기존 -->
<과정>프론트엔드</과정>

<!-- 파트 속성을 추가하여, HTML/CSS 라는 부가적인 설명을 할 수 있다. -->
<과정 파트="HTML/CSS">프론트엔드</과정>
```

태그는 트리 형태의 부모-자식 구조를 가질 수 있다. 트리 형태 구조는 추후 DOM 파트에서 자세하게 학습할 수 있다.

```html
<!-- p > strong + em -->
<p>
  This paragraph has some
  <strong><em>strongly emphasized</em></strong>
  content
</p>
```

<br />

### 01-3. HTML 문서 구조

#### DTD : Doctype Declaration

HTML5 등장 이전에 DTD는 총 3가지 형태 _Strict, Transitional, Frameset_ 를 지녔다. 최신 웹 표준을 따르는 **Strict** 는 빈 요소에는 꼭 슬래시(/)를 붙여야 한다거나, 속성에는 반드시 값을 가져야 한다(속성="값") 등 매우 엄격한 규칙을 지닌 가장 엄격한 문서 유형이다. 호환형의 **Transitional** 유형은 inline style 을 추가한다거나, 속성에 반드시 값을 가지지 않아도 되는 등 Strict 유형보다 덜 엄격한 유형이다. **Frameset** 유형은 &lt;frameset&gt;을 사용하여 여러 HTML 문서를 나눠 표시하는 유형이다.

HTML5 에서 DTD는 위 3가지 종류를 구분해서 사용하지 않는다.

```html
<!DOCTYPE html>
```

<br />

### 01-4. HTML 발전의 역사

(중략)

즉, **HTML5 는 Markup 속성 + API 기능을 구현하는 언어**이다.

<br />

###### 2025-02-13

## 02. HTML 제목과 단락

### 02-1. 제목 `h1` ~ `h6`

### 02-2. 단락 `p`

<br />

## 03. HTML 이미지와 피규어

### 03-1. 이미지 `img`

### 03-2. 피규어 `figure`

<br />

## 04. HTML 하이퍼링크

### 04-1. 하이퍼링크 `a`

<br />

###### 2025-02-17

## 05. HTML 순서형, 비순서형 목록

<br />

## 06. HTML 정의형 목록

<br />

## 07. HTML 프레이징 요소

<br />

## 08. HTML 인용문과 줄바꿈

<br />

## 09. HTML 테이블

<br />

## 10. HTML 컨테이너 요소

<br />

###### 2025-02-18

## 11. HTML section, main 요소

<br />

## 12. HTML 텍스트 레벨 요소

<br />

## 13. HTML address 요소

<br />

## 14. HTML picture, source 요소

<br />

## 15. HTML video, track 요소

<br />

## 16. HTML iframe, object 요소

<br />

## 17. map, area 요소

<br />

## 18. form (input) 요소

<br />

###### 2025-02-19

## 19.

<br />

## 20.

<br />

## 21.
