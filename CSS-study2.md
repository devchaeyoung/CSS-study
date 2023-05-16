# CSS 박스모델

![CSS박스모델]()

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
