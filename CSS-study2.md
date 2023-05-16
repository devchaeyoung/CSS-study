# CSS 박스모델

![CSS박스모델](https://velog.velcdn.com/images/xiu_8/post/d15929d3-0909-42a3-b690-8f5496ab6e7e/image.png)

## margin과 padding

- margin과 padding은 border를 기점으로 나눠진다.

### margin과 padding 표기방법

```css
div {
  margin: 30px 0 0 10px;
}
```

- 위 코드와 같이 top에서 부터 시계방향으로 한 줄에 작성이 가능하다.
- top > right > botton > left
- left에만 속성값을 넣을 경우 `margin-left: 100px;`로 입력 가능하다.
- 만약 상하/좌우 같게하려면 상하/ 좌우 값만 적어주면 된다.
  ```css
  div {
    padding: 10px 0;
  }
  ```
- 상하 padding값을 10px로 지정하고 좌우 padding값을 0으로 지정한다.

# Block과 Inline

- block과 inline은 css 속성의 width와 height를 적용할 수 있냐없냐로 나뉘는 요소이다.
- 대표적으로 block요소에는 `<p>`태그, inline요소에는 `<a>`태그가 있다.

## Block 요소의 특징

- 줄바꿈 현상이 일어난다.
- Y축으로 나열된다.
- width와 heigh 같은 공간 관련 속성값이 사용 가능하다.
- margin과 padding 같은 상하 배치 작업도 가능하다.

### 대표적인 Block 요소 태그

- `<p>`, `<div>`, `<article>`

## Inline 요소의 특징

- 줄바꿈 현상이 없다.
- X축으로 나열된다.
- width/height, margin/padding 과 같은 속성값은 사용할 수 없다.
- 만약 공간관련 속성값을 사용하려면 `display: block;`으로 변경해줘야 사용할 수 있다.

### 대표적인 Inline 요소 태그

- `<a>`, `<span>`

# 마진 병합 현상 이해하기

- 마진 병합 현상은 CSS에서 상하관계에 있는 마진값이 병합되는 현상을 말한다.
- **형제지간의 태그**나, **부모자식 지간의 태그**에서 나타난다.
- margin-top과 margin-botton 사이에서 일어난다.

## 형제지간의 마진 병합

- 형제지간의 코드가 `margin-bottom`과 `margin-top`영역이 맞닿아 있으면 숫자가 큰 값으로 적용된다.
- 마진 bottom과 top 속성값이 합해진 150이 출력되는게 아니라 숫자가 큰 `margin-bottom`값만 적용되어 출력된다.

```html
<style>
  .a {
    background-color: yellow;
    margin-bottom: 100px;
    width: 200px;
    height: 200px;
  }
  .b {
    background-color: pink;
    margin-top: 50px;
    width: 200px;
    height: 200px;
  }
</style>
<div>
  <p class="a">Hello. I'm box 'a'.</p>
  <p class="b">Hello. I'm box 'b'.</p>
</div>
```

![형제지간 코드 예시 출력사진](https://velog.velcdn.com/images/xiu_8/post/917ec55d-b123-4b2b-bea4-fb98b39294cb/image.png)

## 부모자식지간의 마진 병합

- 자식태그에 margin상하 값을 지정하는 경우 자식태그에만 따로 적용되는 게 아니라 부모태그도 같이 적용되는 현상을 말한다.

```html
<style>
  article {
    width: 100px;
    height: 200px;
    margin-top: 50px;
  }
</style>
<main role="main">
  <article></article>
</main>
```

## 마진 병합현상을 없애려면?

- `position :absolute;` 속성을 이용할 수 있다.

# 레이아웃을 움직이는 속성

## display

- Block과 Inline, grid 요소 등 성격을 바꿀 때 사용한다.
- `display: inline-block;`을 사용하면 두 요소의 성격을 모두 가진다. X축 정렬이면서 공간에 대한 개념을 다루고 상하 배치 작업까지 가능하게 만든다.

## float

- 지금은 잘 안쓰는 개념이지만 후에 flex를 배우기전 기초 베이스라 생각하고 알아두자.
- 선택된 요소를 좌측 또는 우측 끝에서 정렬시키고자 할 때 사용하며 이름 그대로 선택자를 띄워서 새로운 레이어층을 만든다.
- 레이어가 겹치지않게 좌측 차례로 정렬시키려면 `float: left;`를 순차적으로 선언해줘야 한다.

```html
<style>
  .a {
    float: left;
  }
  .b {
    float: left;
  }
</style>

<h2 class="a">Hello. I'm box 'a'.</h2>
<h2 class="b">Hello. I'm box 'b'.</h2>
```

- 아래의 코드는 부모태그의 `width: 800px;`안에서 `float`이 적용되어있다. 자식태그보다 부모태그에 적용된 값이 작은 경우에는 레이아웃이 틀어지게 된다.

```html
<div style="width: 800px;">
  <div class="a">left</div>
  <div class="a">right</div>
</div>
```

## clear

- clear는 float과 세트!
- float 을 사용하면 다음 선택자가 종속되어 위쪽으로 따라 올라오는 특성이있는데 이런 float속서을 제어하려면 clear를 사용해줘야한다.
- clear는 float을 마지막으로 사용한 지점 다음에 사용해주면 된다.

## 레이아웃 값 초기화하기

- 브라우저와 공간 사이에는 기본적으로 여백이 존재하는 경우가 있는데 웹 사이트를 만들기전 초기화를 시켜주는 편이 좋다
- html내 모든 태그 초기화 하는 법은 모든 HTML 태그를 선택하는 `*`선택자를 사용해주면 된다.

```css
* {
  margin: 0;
  padding: 0;
}
```

- 위 태그를 항상 디폴트값으로 적용해줄 것!

# 디폴트 CSS코드

```css
* {
  margin: 0;
  padding: 0;
}
img {
  vertical-align: middle;
}
a {
  text-decoration: none;
  color: #000;
}
ul,
ol {
  list-style: none;
}
```
