# CSS

- CSS: cascading style sheet

## CSS란?

- 정보(HTML)과 디자인(CSS)의 분리
- 문서의 레이아웃과 스타일 정릐
- HTML로 작성된 정보를 꾸며주는 언어
- 색상, 공간에 대한 크기지정, 상하 배치 작업

[CSS 개구리게임](https://flexboxfroggy.com/#ko)

## CSS 구성요소

- CSS전체 구조를 rule set이라한다. CSS rule set구조를 알아보자.

```css
selector {
  property: property value;
}
/*declaration*/
```

- CSS는 선택자(selecor)과 선언(declaration)의 속성(property), 속성값(property value)으로 구성 되어있다.

### 선택자(selector)

- 디자인을 적용할 HTML 영역

### 속성(property)

- 어떤 디자인을 적용할지 정의

```CSS
h1 {
    font-size:16px;
    font-family: Times sans-serif;
    color:blue;
    text-align: center;
}
```

### 속성값(property value)

- 어떤 역할을 수행할지 구체적으로 명령. 세미콜론`;` 필수입력

### 선언 (declaration)

- 꾸미기 원하는 요소의 속성을 명시하는 것

```css
h1 {
  color: blue;
}
```

- 선언을 하고난 후 다음 속성과 속성값을 위해 세미콜론`;` 값을 입력해줘야한다.

## CSS 연동 방법 세 가지

- Inline style sheet
- Internal style sheet
- External style sheet

### Inline style sheet

- 태그 안에 직접 원하는 스타일 적용

```html
<h1 style="color:red;">Inline Style sheet</h1>
```

### Internal style sheet

- `<head>`태그 자식인 `<style>`태그 안에 넣기

```html
<head>
  <style>
    h1 {
      color: fff;
    }
  </style>
</head>
```

### External style sheet

- `<head>`태그의 `<link>`태그로 불러오기

```html
<head>
  <link rel="stylesheet" href="style.css" />
</head>
```

- 여기서 `rel`은 정보에 대한 성격을 지정할 때 쓰는 태그
- `.css`확정파일을 만들어서 아래 link tag로 파일을 연동시켜준다.

#### External style sheet의 장점

- html, css 각각의 문서 안에서 따로 관리하여 상대적으로 가독성이 높고 유지보수가 쉽다.

# CSS 선택자

- CSS 디자인을 적용할 HTML의 어떤 요소(elements)

## 선택자 종류 3가지

- **타입(Type)** : 태그
  ```css
  h1 {
    color: yellow;
  }
  ```
- **클래스(Class)** : 태그 별명
  ```html
  <style>
    .class {
      color: orange;
    }
  </style>
  <h1 class="class">Hello World</h1>
  ```
- **아이디(ID)** : 태그이름
  ```html
  <style>
    #class {
      color: orange;
    }
  </style>
  <h1 id="class">Hello World</h1>
  ```

### 여러 요소 선택하는 법

```css
h1,
h2,
p {
  color: #fff;
}
```

- 태그명 사이에 콤마`,`로 나열해 준다.

### 부모 자식 태그 선택하는 법

- 먼저 원하는 지역에만 css 속성을 적용하기 위해 HTMl에서 부모를 구체적으로 표기
  ```html
  <header>
    <h1>Hello World</h1>
    <nav>
      <ul>
        <li>a</li>
        <li>b</li>
      </ul>
    </nav>
  </header>
  <main>
    <h2>c</h2>
    <p>Lorem ipsum dolor sit amet consectetur adipisicing elit</p>
  </main>
  <footer>
    <p>Lorem ipsum dolor sit amet consectetur adipisicing elit.</p>
  </footer>
  ```
- 부모 자식 태그 표기방법
  ```css
  header {
    width: 100%;
  }
  header h1 {
    backgroung-color: yellow;
  }
  header ul.li {
    grid: 1fr 1fr;
  }
  ```

# 캐스케이딩

- CSS를 적용할 때의 우선순위
- 우선순위를 사용해서 수정하는 것이 원본 코드를 유지하는 방법이다.

## CSS의 우선순위를 결정하는 세가지 요소

- 선언된 **순서**
  - 나중에 적용한 속성값이 우선순위가 높음
- 표기된 **디테일** : 얼마나 상세하게 CSS선택자를 표기했는지
  - 더 구체적으로 작성된 선택자의 우선순위가 높음
- **선택자** : Type class ID등에 따른 우선순위
  - style > id > class > type 순으로 우선순위가 높음

# CSS 주요 속성

- 아래 정리된 속성외에 필요한 속성이 있다면 `구글링`을 적극적으로 하며 보강할 수 있다.

## width, height

- 특정 영역에 공간을 설정할 때 사용
- block 속성의 display에만 적용되므로 inline 속성 태그에 적용시킬려면 먼저 `display : block;`으로 속성값을 변경시켜 준 후에 적용이 가능하다.
- `width` : 선택한 요소의 넓이를 설정 (고정값 px, 가변값 %)
- `height` : 선택한 요소의 높이를 설정

## font-

- 폰트 관련 속성

```html
<p id="paragraph">폰트관련 속성</p>
<style>
  .paragraph {
      font-size: 15px;
      font-family: Arial, sans-serif;
      font-style: italic
      font-weight: bold;
  }
</style>
```

- `font-family` : 브라우저마다 지원하는 폰트가 다름으로 여러개의 폰트를 입력 후 마지막에 `sans-serif`를 입력해준다. 입력한 순서대로 우선순위가 적용된다.
- `font-style` : 글자 기울기
- `font-weight` : 100~900 사이로 100단위씩 숫자를 입력할 수 있다. 숫자가 클수록 폰트가 굵어진다. `bold`가 가장 두꺼운 속성값이다.

## border

- CSS 박스 모델의 border부분을 수정한다.
- 아래 두가지 방법으로 표기할 수 있는데 주로 파일 용량을 줄이기 위해 한줄로 작성하는 걸 권장한다. 이때, 쉼표는 작성하지 않고 띄어쓰기로 순서는 상관없이 표기한다.

```css
.paragraph {
  border: solid 5px red;
}

.paragraph {
  border-style: solid;
  border-width: 5px;
  border-color: red;
}
```

## background

### background 특징

-

# CSS 주석처리 방법

```css
/* 주석입니다 */
```
