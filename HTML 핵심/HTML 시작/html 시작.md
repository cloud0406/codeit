# HTML 시작

## HTML 이란?

HTML이란 'Hypertext Markup Language'의 약자로 **서로 링크로 연결된 문서(Hypertext)를 만들 때 사용하며 내용 뿐만 아니라 추가적인 정보(구조와 의미)도 표시(Markup)하는**것을 말한다.

## HTML 기본 문법

기본 문법은 '시작 태그'와 '종료 태그' 사이에 내용을 넣는 방식으로 사용된다.

```html
<a href="reservation.html>예약</a>
```

참고로 위에 예시에서 `href`은 속성 이름, `"~"` 따옴표 내부 부분으 속성 값이라 한다.

## HTML 기본 구조

```html
<!DOCTYPE html>
<html>
  <head>
    페이지에 대한 기본 정보가 들어가는 부분 (페이지에 표시 x)
  </head>
  <body>
    화면에 보이는 내용이 들어가는 부분
  </body>
</html>
```

## 코멘트 시작

코멘트는 프로그램에 영향을 주지 않으며 간단히 메모를 남길때 혹은 잠시 해당 코드를 지우기위해 사용한다.

- 단축키는 윈도우에서는 `ctrl + /`, 맥에서는 `cmd + /`

```html
<!DOCTYPE html>
<html>
  <head>
    <!-- 헤드 태그 -->
  </head>
  <body>
    <!-- 바디 태그 -->
  </body>
</html>
```
