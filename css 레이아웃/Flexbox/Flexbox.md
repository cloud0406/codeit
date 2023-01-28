# Flexbox

## 플렉스 박스 만들기

```css
display: flex;
```

## 기본 축과 교차 축

<img src="image1.png">

## 배치 방향

`flex-direction`을 사용하면 **기본 축**의 방향을 정할 수 있다. 이때 기본 값은 `row`입니다. (기본 축이 가로)

<img src="image2.png">

## 기본 축 정렬: justify-content

`justify-content`를 사용하면 **기본 축 방향으로 정렬**할 수 있다. 기본 값은 `flex-start`.

<img src="image3.png">

<img src="image4.png">

<img src="image5.png">

<img src="image6.png">

## 교차 축 정렬: align-items

**교차 축 방향으로 정렬**할 때는 `align-items`를 사용. 기본 값은 `stretch`(늘려서 배치하기).

<img src="image7.png">

<img src="image8.png">

<img src="image9.png">

<img src="image10.png">

## 요소가 넘칠 때: flex-wrap

요소가 넘치는 경우 `flex-wrap: wrap`을 지정해주면 교차 축 방향으로 넘어가서 배치.

<img src="image11.png">

## 간격: gap

<img src="image12.png">

숫자를 하나만 쓰면, 모든 방향의 간격을 지정할 수 있다.

<img src="image13.png">

세로, 가로 순서대로 숫자를 두 개 쓰면 세로 간격, 가로 간격을 지정할 수 있다. **이때 세로와 가로는 기본 축 방향이랑은 상관없다.**

## 요소 늘려서 채우기: flex-grow

기본 값은 0입니다. `flex-grow` 값이 클수록 많이 늘어난다.

<img src="image14.png">

<img src="image15.png">

<img src="image16.png">

<img src="image17.png">

## 요소 줄여서 채우기: flex-shrink

만약 요소들의 크기가 커서 넘치는 경우, 요소의 크기를 줄여서 플렉스박스 안에 가득 채운다. `flex-shrink`의 기본 값이 1이기 때문에 기본적으로 요소를 줄여서 배치하고, 0으로 지정하면 크기가 줄어들지 않는다. 그리고 `flex-shrink` 값이 클수록 상대적으로 많이 줄어든다.

<img src="image18.png">

<img src="image19.png">

<img src="image20.png">

## inline-flex

flex를 사용할 경우 그 안에서는 플렉스박스의 규칙에 따라 배치되고, 그 바깥에서 플렉스박스 전체에 대해서는 마치 `display: block`처럼 위에서 아래로 배치된다.

`display: inline-flex`를 사용하면 플렉스박스를 만들면서 동시에 플렉스박스 전체를 마치 `display: inline`처럼 배치한다. (즉, 인라인 안에서 플렉스박스를 만들고 싶을 때 사용)
