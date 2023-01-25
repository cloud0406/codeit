# CSS 시작하기

## CSS 기본 문법

### style 속성

태그에 CSS를 적용하려면 style 이라는 속성을 사용

```html
<div style="...">...</div>
```

### CSS 속성과 CSS 속성 값

CSS 코드를 추가할 때는 `CSS 속성: CSS 속성값` 형태로 적는다.

```html
<div style="color: #272928">...</div>
```

### 여러 개의 CSS 속성 사용하기

여러 개의 CSS 속성을 사용할 때는 세미콜론(;)으로 구분.

```html
<div style="color: #272928; background-color: #eeeeee">...</div>
```

## CSS 기본 단위

### 색 이름

- red, green, yellow처럼 색상을 이름으로 사용하는 방식.
- 다양한 색을 표현하는데 한계가 있기 때문에 거의 사용하지 않느나.
- CSS 이름 목록: https://www.w3.org/wiki/CSS/Properties/color/keywords

### 색상 코드

- 색상을 HEX(16진수)로 표현한 값.
- 보통 이 값으로 색상을 사용.
- 모든 색깔들을 펼쳐 놓고 하나씩 코드를 부여한 것인데 구글 검색에서 `‘Color Picker’` 같은 걸 검색해서 색상 코드를 확인해 볼 수 있다.
- 주로 이미지 편집 프로그램 같은 데서 디자인을 하면서 색상 코드를 정하게 된다.

### 픽셀(px)

- CSS에서는 크기를 설정할 때 픽셀이라는 단위.
- 화면에서 그려지는 가장 작은 정사각형을 말한다.
- 이미지의 일부를 확대해서 보면 작은 정사각형 단위로 되어 있는데,
  이때 각 정사각형을 픽셀(Pixel)이라고 부른다.
- 이 정사각형을 화면에서 크기의 단위로 쓰기도 하는데, 코드에서 크기의 단위로 쓸 때는 px라고 쓰고 픽셀이라고 읽으면 된다.
- 만약 어떤 이미지의 너비가 100px이라고 한다면, 가로로 저 작은 정사각형 100개만큼 있다는 것.
- 글자의 크기도 픽셀로 설정하는 경우가 많은데, 글자 크기가 24px라고 하면 글자의 세로 길이가 24px이라는 뜻.

## CSS 속성

### 배경색

```css
background-color: #272928;
```

### 글자색

```css
color: #ffffff;
```

### 글꼴

- 우선 적용할 글꼴 이름부터 차례대로 적어 주면 된다.
- 글꼴 이름이 띄어쓰기가 있는 경우엔 따옴표로 감싸 준다.
- `sans-serif` 나 `serif` 를 사용하면 산 세리프나 세리프 타입의 글꼴을 웹 브라우저가 알아서 적용해 준다.

```css
font-family: Poppins, "Noto Sans KR", sans-serif;
```

### 정렬

```css
// 가운데 정렬
text-align: center

// 오른쪽 정렬
text-align: right

// 가운데 정렬
text-align: left
```

### 글자 크기

```css
font-size: 16px;
```

### 글자 굵기

- 100에서부터 900까지, 100 단위로 올라간다.
- 중간이 되는 font-weight 값은 400.

```css
font-weight: 400;
```

### 너비

```css
width: 560px;
```

### 높이

```css
height: 380px;
```

### 안쪽 여백

- 세로, 가로 10px 예시

```css
padding: 10px;
```

- 세로 10px, 가로 20px 예시

```css
padding: 10px 20px;
```

### 바깥 여백

- 세로, 가로 10px 예시

```css
margin: 10px;
```

- 세로 10px, 가로 20px 예시

```css
margin: 10px 20px;
```

- 세로 10px, 가로 자동(알아서 채워 넣기) 예시

```css
margin: 10px auto;
```

**참고: auto는 바깥 여백(margin)의 가로에서만 동작**
