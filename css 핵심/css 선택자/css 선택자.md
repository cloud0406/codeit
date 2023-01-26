# CSS 선택자

## CSS 선택자(CSS Selector)

CSS 규칙에서 맨 앞에 적어 주는 걸 CSS 선택자라고 부른다. 선택자를 사용해서 이 규칙을 어떤 요소들에 적용할지 선택할 수 있다.

```
선택자 {
  선언;
  선언;
  선언;
}
```

## 선택자 목록

콤마(`,`)로 선택자를 연결하면 여러 선택자에 같은 규칙을 적용할 수 있다.

```
선택자1,
선택자2 {
  ...
}
```

## 선택자 붙여 쓰기

**여러 조건을 동시에 만족하는 요소를 선택하고 싶다면** 선택자를 붙여서 쓸 수 있다. 예를 들어서 아래 HTML 코드에 있는 태그를 선택해보면,

```html
<h2 id="mongolia" class="large title">몽골 대자연으로 떠나는 여행</h2>
```

### 예시 1. 아이디 + 클래스

```css
#mongolia.title
```

### 예시 2. 클래스 + 클래스

```css
.large.title
```

### 예시 3. 태그 + 아이디 + 클래스

```css
h2#mongolia.large.title
```

- 위 조건을 모두 만족하는 요소들의 css를 선택 (h2태그 이면서 'mongolia' id값을 가지고 class 속성으로 large와 title을 모두 가지고 있는 요소)

## 자식 결합자 (Child Combinator)

자식이란 요소의 바로 하위 요소를 말한다. (바로 하위 요소만 적용되고 하위의 하위 요소부터는 적용 x)

오른쪽 꺾쇠로 선택자를 이어 준다. 예를 들어서 아래 코드에서 `tesla-y-2025.png`를 보여 주는 이미지 태그를 선택하려면 `.article > img`로 선택할 수 있다.

```html
<div class="article">
  <img src="tesla-y-2025.png" />
  ...
</div>
```

```
.article > img {
  width: 100%;
}
```

- `article` class의 자식 요소인 `img`태그를 선택

## 자손 결합자 (Descendant Combinator)

자손이란 요소의 하위 요소들을 말한다. 자식 결합자와는 다르게 바로 직계 자식뿐만 아니라 하위의 하위 요소까지 모두 찾아서 적용한다.

스페이스(띄어쓰기)로 선택자를 이어 준다. 예를 들어서 아래 코드에서 `tesla-w-2025.png`를 보여주는 이미지 태그를 선택하려면 `.article img`로 선택할 수 있다.

```html
<div class="article">
  <p>
    이번에 리뷰해 볼 차량은 테슬라 모델 W 입니다.
    <img src="tesla-w-2025.png" />
  </p>
  ...
</div>
```

```css
.article img {
  width: 100%;
}
```

- `article` class의 자손인 `img` 태그를 선택

## 가상 클래스 (Pseudo-class)

가상 클래스는 의사 클래스, 가짜 클래스라고도 부른다. **요소의 상태 같은 걸 선택할 때 사용하는 클래스**이다. 정해진 이름 앞에 콜론(:)을 붙여서 사용합니다. 대표적으로 `:hover`(마우스를 올렸을 때), `:active`(클릭한 상태) `visited`(방문한 적이 있는 링크), `focus`(포커싱 됐을 때)등이 있다. 예를 들어서 밑줄이 없는 링크에 마우스를 올렸을 때 밑줄이 생기도록 하려면 `:hover`를 활용하면 된다.

```css
a {
  text-decoration: none;
}

a:hover {
  text-decoration: underline;
}
```

- 마우스를 올리지 않았을때는 밑줄이 없지만 마우스를 링크에 올리면 밑줄이 생긴다.

## 전체 선택자 (Universal Selector)

`*` 라는 선택자는 모든 요소를 선택하는 선택자.

### 모든 요소를 선택하기

```css
* {
  box-sizing: border-box;
}
```

### `.gallery`의 모든 자식 요소 선택하기

```css
.gallery > * {
  width: 120px;
  height: 90px;
}
```

## n번째 자식 선택자(n-th child Selector)

`:nth-child()`를 사용. 괄호 안에는 숫자나 `even`, `odd`, `2n` 같은 값이 들어갈 수 있는데, 숫자는 1부터 시작 (첫 번째 자식은 1이고, 세 번째 자식은 3)

### .gallery의 세 번째 자식

```css
.gallery :nth-child(3) {
  ...;
}
```

### .gallery의 짝수 번째 자식

```css
.gallery :nth-child(even) {
  ...;
}
.gallery :nth-child(2n) {
  ...;
}
```

### .gallery 의 홀수 번째 자식

```css
.gallery :nth-child(odd) {
  ...;
}
.gallery :nth-child(2n + 1) {
  ...;
}
```

### 특히 첫 번째 자식, 마지막 자식은 아래처럼 선택

```css
.gallery :first-child {
  ...;
}
.gallery :last-child {
  ...;
}
```

## 팁

### 선택자는 최대한 단순하게

클래스, 가짜 클래스 한 두 개만 조합해서 최대한 단순하게 쓰시는 걸 추천. 복잡하게 조합하다 보면 나중에 코드를 고칠 때마다 어디서 뭐가 바뀔지 알기 힘들어지기때문

그래도 선택자를 조합해서 쓰면 정말 유용한 경우가 있는데, 선택자 조합을 어떻게 쓰면 좋을지 몇 가지 예시를 확인해보자.

### 모든 곳에서 border-box를 쓰고 싶을 때

앞에서 박스 모델의 크기는 기본적으로 콘텐트(`content-box`)를 기준으로 정해진다고 배웠는데, 모든 요소의 크기를 테두리(`border-box`)를 기준으로 하고 싶다면, 아래처럼 추가하고 쓰면 된다. 항상 이 코드를 추가하는 것도 좋다.

```css
* {
  box-sizing: border-box;
}
```

### 같은 클래스지만 변화를 주고 싶을 때

똑같은 상품 버튼이지만, 품절된 상품의 버튼을 보여줄 때나 똑같은 이미지이지만 유저가 선택한 이미지를 보여줄 때처럼 같은 클래스지만 살짝 다른 경우에 쓰면 좋다.

### 클래스를 넣어 줄 태그가 너무 많을 때

자손 조합자는 적용해야 할 태그가 너무 많아서, 일일이 적용하기 어려울 때 쓰면 좋다.
