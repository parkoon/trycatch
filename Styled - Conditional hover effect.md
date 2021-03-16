# Styled - Conditional hover effect

```javascript
const AnimationContainer = styled.div`
  transform: translate(0%);
  transition: 0.3s ease-out;

  &:hover {
    // apply hover only when $(props.animated) is paased
    position: fixed;
    transform: translate(0%, -30%);
    transition: 0.3s ease-out;
  }
`;
```

> `hover` 를 `animated` 값에 따라 적용하고 싶다면 어떻게 해야할까?

💡`styled-component` 의 `css` 를 이용한다.

```javascript
const AnimationContainer = styled.div`
  transform: translate(0%);
  transition: 0.3s ease-out;

  ${(props) =>
    props.animated &&
    css`
      &:hover {
        position: fixed;
        transform: translate(0%, -30%);
        transition: 0.3s ease-out;
      }
    `}
`;
```
