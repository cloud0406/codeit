# 자주 쓰는 CSS 속성

## 배경 이미지 `background-image`

`url(...)`이라는 문법으로 배경 이미지를 넣는다.

```css
background-image: url("flowers.png");
```

참고로 배경 이미지는 여러 개 넣을 수 있다.

아래처럼 이미지를 배경으로 넣으면 `a.png` 아래에 `b.png`가 깔리고, 맨 밑에는 `c.png`가 깔린다.

```css
background-image: url("a.png"), /* 제일 위에 보이는 이미지 */ url("b.png"), url("c.png");
```

## 배경의 위치 `background-position`

기본값은 `left top`(왼쪽 위)이고, 가운데 정렬을 하려면 아래처럼 `center`를 쓰면 된다.

```css
background-position: top; /* 위 */
background-position: right; /* 오른쪽 */
background-position: bottom; /* 아래 */
background-position: left; /* 왼쪽 */
background-position: left top; /* 왼쪽 위 (지정하지 않았을 때 기본값) */
background-position: center;
```

## 배경의 반복 `background-repeat`

기본값은 `repeat(반복)`이고, `no-repeat`으로 하면 반복되지 않게 할 수 있다. (`no-repeat`을 자주 사용)

```css
background-repeat: repeat; /* 반복하기 (지정하지 않았을 때 기본값) */
background-repeat: no-repeat; /* 반복 안 함 */
```

## 배경의 크기 `background-size`

직접 가로 세로 크기를 지정할 수도 있고, **비율을 유지하면서 영역에 꽉 차게(cover)하거나, 영역 안에서 최대한 크게(contain)할 수도 있다.** (`cover`를 자주 사용)

```css
background-size: cover; /* 비율 유지하면서 꽉 차게. 이미지 잘릴 수 있음 */
background-size: contain; /* 비율 유지하면서 최대한 크게. 이지미 잘리지 않음 */
background-size: 40px 30px; /* 가로 40px 세로 30px */
```

## 그라디언트 `linear-gradient()`

기본적으로 시작 색상과 종료 색상으로 사용할 수 있다.

```css
background-image: linear-gradient(#000000, #ffffff);
```

기본 방향의 각도는 180도인데, (위에서 아래로 내려오는 방향)
이 각도를 바꾸고 싶다면 맨 앞에다가 각도를 써 주면 된다. 각도의 단위는 `deg`이다.

```
background-image:
  linear-gradient(45deg, rgba(0, 0, 0, 0.8), rgba(0, 0, 0, 0.2));
```

- 아래 링크 참고하면서 사용
- https://cssgradient.io/

팁으로 아래와 같이 이미지 위에 gradient를 같이 사용 가능 (이미지만 사용할 경우 텍스트가 잘 안보일 수 있는데 이렇게 사용하면 좀 더 깔끔하게 보일 수 있다.)

```css
background-image: linear-gradient(
    90deg,
    rgba(0, 0, 0, 1) 40%,
    rgba(0, 0, 0, 0)
  ), url("pizza.png");
```

이미지 위에 반 투명한 gradient를 겹쳐놓는다고 생각하면 됨.

## 그림자 box-shadow

가로, 세로 위치, 흐린 정도(Blur), 퍼지는 정도(Spread), 색상의 순서로 쓴다.

```css
box-shadow: 5px 10px 15px 8px rgba(0, 0, 0, 0.6);
/*
  가로: 5px
  세로: 10px
  흐린 정도(Blur): 15px
  퍼지는 정도(Spread): 8px
  색상: rgba(0, 0, 0, 0.6)
*/
```

- 아래 링크 참고하면서 사용
- https://cssgenerator.org/box-shadow-css-generator.html

## 불투명도 opacity

요소 전체의 불투명도를 조절할 때 사용. 0에서 1 사이의 소수 값으로 단위 없이 쓰면 된다.

```css
opacity: 0; /* 투명 */
opacity: 0.6;
opacity: 1; /* 불투명 */
```
