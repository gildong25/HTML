# 10. HTML5와 시맨틱 태그

## 10-1. HTML4 문서 vs HTML5 문서

### HTML4 문서

```
<div id="header">
    <!-- 헤더와 메뉴 -->
<div id="content">
    <!-- 본문 내용 -->
<div id="footer">
    <!-- 푸터 -->
```

> 문제점 

- 구조 이해 어려움
- 본문 섹션 파악 어려움
- 개발자별 표준화 되어있지 않은 태그

### 시맨틱 태그가 사용된 HTML5 문서

> 시맨틱 태그(semantic tag) - 문서 구조에서의 역할을 알수있다. 

- ex) 헤더(header),  본문(content), 사이드바(sidebar), 푸터(footer)

```
<!DOCTYPE html>
<html lang="ko">
<head>
    ...
</head>

<body>
    <header>
         ...
    </header>

    <section>
        ...
    </section>

    <footer>
        ...
    </footer>
</body>
</html>
```

> 시맨틱 태그를 활용한 레이아웃

- 내용 구분 용이
- 내용 검색이 용이
- 웹접근성 향상
- 문서 해석의 표준화


## 10-2. 문서 구조를 위한 HTML5 시맨틱 태그 (실습)

```
1. <header> - 머리말 지정
2. <nav> - 문서 연결 내비게이션 링크
3. <section> - 주제별 콘텐츠 영역
4. <article> - 콘텐츠 내용
5. <aside> - 본문 이외의 내용
6. <footer> - 제작 정보와 저작권 정보
7. CSS 파일 연결
    <link rel="stylesheet" href="css/layout.css">

* <address> - 사이트 제작자 정보, 연락처 정보
* <iframe> - 외부 문서 삽입
* <div> - 콘텐츠에 CSS를 적용할때
```

## [10-3. IE8 이하 버전 처리](https://www.w3schools.com/html/html5_browsers.asp)

### [시맨틱 태그 지원 사항](https://caniuse.com/#search=form)

#### html5shiv 이용

```
<head>
  <!--[if lt IE 9]>
    <script src="/js/html5shiv.js"></script>
  <![endif]-->
</head>
```

#### CSS 블록 레벨로 정의 - 영역 설정

```
header, section, nav, article, footer {
    display:block;;
}
```

#### 시맨틱 태그 직접 정의

```
<script>
    document.createElement("article")
    document.createElement("section")
    document.createElement("aside")
    document.createElement("nav")
    document.createElement("footer")
        ...
</script>
```

### 폴리필(pollyfill)- 파편화 해소

파편화가 생기는 브라우저에 삽입하는 자바스크립트, 브라우저를 스스로 진단해 필요한 shim을 자동으로 생성해줌.

# 11. HTML5와 멀티미디어

## 11-1. 웹과 멀티미디어

### [플러그인 프로그램](https://www.youtube.com/html5)

> 대부분 HTML5 플레이어가 사용됨.

### \<object> 태그와 \<embed> 태그

#### \<object> 태그 - 외부파일 삽입

ex) 자바 애플릿, PDF, 플래시무비, 타 HTML ...


```
<object data="경로" type="유형" [name="이름" width="너비" height="높이"]></object>
```

#### \<embed> 태그 - object 태그 지원하지 않는 브라우저

```
<!-- 닫는 태그 없음 -->
<embed src="경로" width="너비" height="높이">
```

### 멀티미디어의 웹 표준화

> 비디오 : .mp4

> 오디오 : .mp3

#### HTML와 비디오 코덱 - 인코딩, 디코딩

- 인코딩(encoding) : 원본 비디오를 압축하여 컴퓨터에서 사용할 수 있는 비디오 파일로 변환

- 디코딩(decoding) : 비디오 파일에 저장되어 있는 비디오 정보를 가져와 비디오 플레이어에 보여주는 과정

- ex) H.264/AVC(.mp4), v8/v9(webm-크롬), 오그테오라(ogv-파이어폭스)

#### HTML와 오디오 코덱

- ex) MPEG-1 AUDIO Layer3(.mp3), Ogg Vorbis(.ogg/.oga, 오픈소스)

### HTML5 비디오 변환하기
[카카오인코더 : mov->webm](https://blog.naver.com/cacaotools)


## 11-2. 오디오 & 비디오 재생하기

### \<audio>태그 - 오디오 파일 삽입

```
<audio src="오디오 파일경로" [속성] [속성="속성 값"]></audio>
```

|속성|설명|
|--:|:--|
|autoplay| 자동 재생|
|controls| 컨트롤 막대 표시(재생/멈춤/진행바/볼륨)|
|loop| 반복 재생|
|muted| 재생 및 소리 끔|
|preload| 재생 전 다운로드(none,metadata,auto)|
|poster| 문제 상황 표시|

### \<video> 태그 - 비디오 파일 삽입

```
<video src="비디오 파일경로" [속성] [속성="속성 값"]></video>
```

### \<source> 태그 - 여러 미디어 파일 한꺼번에 지정

```
<video controls>
    <source src="Fireworks.mp4" type="video/mp4">
    <source src="Fireworks.webm" type="video/webm">
    <source src="Fireworks.ogv" type="video/ogg">    
</video>
```

### 이전 브라우저

- 대체 텍스트 표시

```
<video controls>
    <source src="media/Fireworks.mp4" type="video/mp4">
    <source src="media/Fireworks.webm" type="video/webm">
    <source src="media/Fireworks.ogv" type="video/ogg"> 
    이 영상을 보기위해서는 HTML5를 지원하는 브라우저가 필요합니다.   
</video>
```

- \<object> 태그와 \<embed> 태그

```
<video controls>
    <source src="media/Fireworks.mp4" type="video/mp4">
    <source src="media/Fireworks.webm" type="video/webm">
    <source src="media/Fireworks.ogv" type="video/ogg"> 
    <object data="media/Paining.swf" type="application/x-shockwave-flash"></object>   
</video>
```

### \<track> 태그 - 비디오 화면에 자막 추가

```
<track kind="subtitles" src="Wildlife.vtt" srclang="ko" label="korean" default>
```

- ex) smi - 자막 내용만, srt - 시간 정보 포함
- WebVTT(.vtt) - 공식 표준

#### \<track> 속성

|속성 값|설명|
|--:|:--|
|subtitles*| 자막|
|captions| 캡션|
|descriptions| 콘텐츠 설명|
|chapters| 탐색 - 장 제목|
|metadata| 콘텐츠 정보|

