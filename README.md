<style>
   h5::before {
      content: '✍🏻 ';
   }

   h5 {
      color: blue;
      margin-left: 15px;
   }
</style>

###### Likelion Front-end School

# HTML/CSS

[실습 예제 보기](https://jjmullan.github.io/learn-html-css/)

## 목차

###### 2025-02-12

0. [Github](#0-github)

   협업 환경 세팅하기 <br />
   git clone <br />
   git pull <br />
   npm i

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

18. [HTML form (input) 요소 - 1]()

###### 2025-02-19

18. [HTML form (input) 요소 - 2]()

19. [HTML form (button) 요소]()

20. [HTML form (select, textarea) 요소]()

21. [HTML dialog 요소, popover 속성]()

<br />
<br />
<br />
<br />

###### 2025-02-12

## 0. Github

### 0-1. 협업 환경 세팅하기

**스크럼 리더** _scrum leader_ 는 원활한 협업 환경 세팅을 위해 [필요한 package 를 devDefendency 로 설치](#devdefendency-로-package-설치하기)하고(e.g. live-server, prettier) [package.json](#packagejson-작성-예시), [.gitignore](#gitignore-작성-예시), .prettierrc.cjs 등 필요 환경 세팅을 완료한 뒤, github repository 를 생성, push 해두어야 한다.

##### devDefendency 로 package 설치하기

```bash
npm install {패키지명} --save-dev
npm i {패키지명} -D
```

##### 예시 : .package.json 작성 - live-server, prettier

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

##### 예시 : .gitignore 작성

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

##### 예시 : package.json 의 "scripts" 사용

```bash
# scripts 에 사용한 package 수동 명령어 사용 예시
npm start
npm run format
```

##### git push

```bash
git push

# 저장소 별칭(origin), 브랜치명(main) 을 지정할 수 있다
git push origin main
```

<br />

### 0-2. git clone : Github repository 가져오기

팔로워는 git clone 명령어를 사용하여 스크럼 리더의 Github repository 를 local 에 복제하여, 협업 환경을 동기화한다.

```bash
git clone https://github.com/seulbinim/ssam-html-css.git

# 레퍼지토리 별칭을 임의로 변경하여 가져오고 싶을 떄
git clone -o {브랜치명} https://github.com/seulbinim/ssam-html-css.git
```

##### repository 가 잘 연결되었는지 확인하기

```bash
# 현재 git repository 의 별칭과 github 링크를 확인할 수 있다
git remote -v
```

##### repository 연결 제거하기

협업 환경에서 프로젝트가 종료할 때까지 연결을 제거하지 않는다.

```bash
git remote rm origin
```

<br />

### 0-3. git pull : 최신 커밋 유지하기

최초로 github 의 repository 를 pull 할 때 별칭과 브랜치명을 입력한다. 이후 작업할 때는 별칭과 브랜치명을 생략해도 된다.

```bash
# 최초로 pull 할 때
git pull origin main

# 1회 이상 pull 할 때
git pull
```

<br />

### 0-4. npm i : 의존성 패키지 설치하기

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

## 1. HTML 개요

### 1-1-1. Hyper Text 란 ?

정적인 형태의 텍스트에 문서를 연결될 수 있도록 하여, 텍스트 _Text_ 의 기능을 초월 _Hyper_ 하였다.

### 1-1-2. Markup Language 란 ?

태그 _&lt;Tag&gt;_ 를 사용하여 콘텐츠의 의미와 구조를 지정하고, 표시 _Markup_ 하여 컴퓨터가 이해할 수 있는 언어 _Language_ 로 치환한 것이다.

##### Text vs Hyper Text Markup Language

```html
<!-- Text -->
멋쟁이사자처럼

<!-- HTML -->
<회사명>멋쟁이 사자처럼</회사명>
```

<br />

### 1-2. &lt;tag&gt; 구성 요소

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

### 1-3. HTML 문서 구조

#### DTD : Doctype Declaration

HTML5 등장 이전에 DTD는 총 3가지 형태 _Strict, Transitional, Frameset_ 를 지녔다. 최신 웹 표준을 따르는 **Strict** 는 빈 요소에는 꼭 슬래시(/)를 붙여야 한다거나, 속성에는 반드시 값을 가져야 한다(속성="값") 등 매우 엄격한 규칙을 지닌 가장 엄격한 문서 유형이다. 호환형의 **Transitional** 유형은 inline style 을 추가한다거나, 속성에 반드시 값을 가지지 않아도 되는 등 Strict 유형보다 덜 엄격한 유형이다. **Frameset** 유형은 &lt;frameset&gt;을 사용하여 여러 HTML 문서를 나눠 표시하는 유형이다.

HTML5 에서 DTD는 위 3가지 종류를 구분해서 사용하지 않는다.

```html
<!DOCTYPE html>
```

<br />

### 1-4. HTML 발전의 역사

(중략)

즉, **HTML5 는 Markup 속성 + API 기능을 구현하는 언어**이다.

<br />

###### 2025-02-13

## 2. HTML 제목과 단락

### 2-1. h1 ~ h6

### 2-2. p

<br />

## 3. HTML 이미지와 피규어

### 3-1. img

### 3-2. figure

<br />

## 4. HTML 하이퍼링크

### 4-1. a

<br />

###### 2025-02-17

## 5. HTML 순서형, 비순서형 목록

### 5-1. ol

### 5-2. ul

### 5-3. li

<br />

## 6. HTML 정의형 목록

<br />

## 7. HTML 프레이징 요소

<br />

## 8. HTML 인용문과 줄바꿈

<br />

## 9. HTML 테이블

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

### 18-1. form

입력 폼 _form_ 은 서식을 담는 그릇 역할로, 모든 폼 요소의 부모 요소로 기능한다. form 태그의 속성으로 action, method, enctype, target 을 가질 수 있다.

- `action` 속성은 폼 데이터를 전송할 서버 측 스크립트의 URL 을 지정한다.
- `method` 속성은 데이터를 전송할 때 사용할 HTTP method 를 지정한다. 값으로는 get 과 post 를 갖는다.
  - get 은 폼 데이터를 URL의 쿼리 문자열로 전송한다.
  - post 는 HTTP 요청의 본문에 포함하여 전송하며, 데이터가 URL 에 노출되지 않아 보안상 더 안전하다.
- `enctype` 속성은 폼 데이터를 서버로 전송할 때 사용할 인코딩 방식을 지정한다.
- `target` 속성은 폼 데이터를 전송한 뒤 서버의 응답을 표시할 창 또는 프레임의 형태를 지정한다.

##### 예시 : 데이터를 post 방식으로 formspree 서버로 전송

```html
<form action="https://formspree.io/" method="post"></form>
```

<br />

### 18-2. fieldset 요소

<br />

### 18-3. legend 요소

<br />

### 18-4. label 요소

웹 접근성 면에서 폼 항목과 label 을 1대1로 대응해줘야 한다. 만약, label 을 대응하지 않기를 원한다면, 폼 항목에 `aria-label=""`로 웹 접근성을 향상할 수 있다.

<br />

### 18-5. input 요소

<br />

#### type="text" 속성

<br />

#### type="password" 속성

##### 예시 : Password 입력 창에서 'visible' 처리하는 방법

```html

```

<br />

#### type="search" 속성

<br />

###### 2025-02-19

#### type="email" 속성

<br />

#### type="submit" 속성

<br />

#### type="tel" 속성

<br />

#### type="checkbox" 속성

#### checked 속성

#### value 속성

<br />

#### type="radio" 속성

name 속성으로

#### checked 속성

#### value 속성

<br />

#### type="range" 속성

#### min, max 속성

#### step 속성

<br />

#### type="url" 속성

#### type="date" 속성

#### type="datetime" 속성

#### type="month" 속성

#### type="week" 속성

#### type="datetime-local" 속성

<br />

#### type="number" 속성

#### min, max 속성

#### step 속성

<br />

#### type="color" 속성

<br />

#### required 속성

required 속성을 input 태그 안에 넣어, 사용자에게 입력을 받고 싶은 특정 요소를 필수로 설정할 수 있다. 예를 들면, 회원가입을 할 때 ID, Password 를 필수 입력 값으로 설정할 수 있고, 성별, 생년월일 등은 선택 항목으로 둘 수 있다.

##### div 에 aria- 속성을 이용하여 폼 서식을 만드는 예시

```html
<!-- aria-require="true"를 속성으로 넣어 required 속성을 동작하게 만들 수 있다 -->
<div role="form">
  <div aria-required="true" contenteditable="true"></div>
</div>
```

<br />

#### placeholder 속성

입력값에 대한 힌트를 줄 수 있다.

##### 예시

```html
<!-- 최대 5자리까지 텍스트를 입력하게 할 수 있다 -->
<div>
  <label for="userName">이름</label>
  <input type="text" name="userName" id="userName" placeholder="김민수" maxlength="6" />
</div>
```

<br />

#### maxlength, minlength 속성

값의 최대 길이 _maxlength_ , 최소 길이 _minlength_ 를 지정할 수 있다.

##### 예시

```html
<!-- 최소 8자리 이상으로 비밀번호를 입력하게 할 수 있다 -->
<div>
  <label for="userPwd">비밀번호</label>
  <input type="password" name="userPwd" id="userPwd" placeholder="8자리 이상" minlength="8" />
</div>
```

<br />

#### list 속성과 datalist 요소

<br />

#### pattern 속성

<br />

#### autofocus 속성

<br />

## 19. form (button) 요소

하나의 form 태그에 포함된 input 과 button 은 동일한 속성을 부여하면, 동일한 기능으로 작동한다.

##### 예시

```html
<form>
  <div><label for="user">사용자 이름</label><input type="text" name="user" id="userName" /></div>
  <div><label for="user">사용자 암호</label><input type="password" name="pwd" id="userPwd" /></div>
  <div>
    <input type="submit" value="전송" />
    <input type="reset" value="초기화" />
    <input type="button" value="Clike Me!" />
  </div>
  <div>
    <button type="submit">전송</button>
    <button type="reset">초기화</button>
    <button type="button">클릭!</button>
  </div>
</form>
```

<br />

같은 form 태그에 포함되지 않는 요소를 포함하고 싶은 경우가 있다. 이때, form 의 id 와 바깥에 있는 요소에 form="id" 를 매칭하면 하나의 form 요소처럼 컨트롤 할 수 있다.

##### 예시

```html
<form id="test"><button></button></form>
<button form="test"></button>
```

<br />

## 20. form (select, textarea) 요소

### 20-1. select 요소

select 요소와 option 요소를 사용하여, 셀렉트 박스 _Select box_ 폼을 만들 수 있다.

웹을 최초로 불러왔을 때 리스트 폼 형태의 맨 처음 요소에 `value=""`값을 넣어 리스트를 안내하는 특정 텍스트를 입력할 수 있다. 해당 방법은 추후 CSS 를 통해 디자인적으로 변경하여 활용할 수 있으나, 권하지는 않는다.

##### 예시

```html
<form action="/" method="post">
  <div>
    <label for="petSelect">반려동물</label>
    <select name="petSelect" id="petSelect">
      <option value="">반려동물 선택</option>
      <option value="dog">강아지</option>
      <option value="cat">고양이</option>
      <option value="hamster">햄스터</option>
      <option value="spider">거미</option>
      <option value="goldfish">열대어</option>
      <option value="parrot">패럿</option>
    </select>
  </div>
</form>
```

<br />

option 요소가 많은 경우, optgroup 요소를 부모로 사용하여 그룹핑해줄 수 있다.

##### 예시

```html
<form action="/" method="post">
  <div>
    <label for="petSelect">반려동물</label>
    <select name="petSelect" id="petSelect">
      <optgroup label="포유류">
        <option value="dog">강아지</option>
        <option value="cat">고양이</option>
        <option value="hamster">햄스터</option>
        <option value="parrot">패럿</option>
      </optgroup>
      <optgroup label="기타">
        <option value="spider">거미</option>
        <option value="goldfish">열대어</option>
      </optgroup>
    </select>
  </div>
</form>
```

<br />

### 20-2. textarea 요소

여러 줄에 걸쳐 많은 양의 텍스트를 작성할 때, textarea 요소를 활용할 수 있다.

#### placeholder 속성

&lt;textarea&gt;와 &lt;/textarea&gt; 사이에 값 _value_ 이 있는 경우, placeholder 속성이 중복되어 화면에 나타나지 않는다.

보통 placeholder 의 텍스트는 길게 작성하지 않는다. 만약, placeholder 를 여러 줄에 걸쳐 길게 작성하고 싶다면, CSS 로 textarea 위에 텍스트를 올리고, JavaScript 를 통해 동적으로 작동할 수 있도록 만든다.

<br />

## 21. dialog 요소, popover 속성

참고 링크 : [W3C modal guide](https://www.w3.org/WAI/ARIA/apg/patterns/dialog-modal/examples/dialog/)

### 21-1. dialog 요소

### 21-2. popover 속성

button 요소와 div 요소를 사용하여 JavaScript 없이 팝업 창을 만들 수 있다.

```html
<button class="button-popover" type="button" popovertarget="popoverContent">팝오버 보기</button>
<div id="popoverContent" popover>
  <p>팝오버 내용</p>
</div>
```

#### popovertarget="" 속성

#### popover 속성

<br />

## 22. details, summary 요소

### 22-1. details 요소

#### open 속성

### 22-2. summary 요소

<br />

## 23. script 요소
