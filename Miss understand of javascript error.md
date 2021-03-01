## Miss understand of javascript error

---

`try { ... } catch (err) { ... }` 구문을 맹목적으로 사용하다보니 `err` 객체에 대한 이해가 굉장히 짧았다.

### Case 1

```javascript
try {
  if (error) {
    throw new Error("error occurred");
  }
} catch (err) {
  // type of err
}
```

### Case 2

```javascript
try {
  if (error) {
    throw "error occurred";
  }
} catch (err) {
  // type of err
}
```

**Case 1** 의 타입은 `Error` 객체이고 `Case 2` 의 타입은 `string` 이다.

자바스크립트를 아무것도 모르던 시절 (아마 타입스크립트를 썼다면 에러가 타입 에러가 발생했겠지만...) `catch` 문에서 `err.message` 를 당연하게 접근해서 쓰려고 했던 나를 떠올리며 반성한다.

이 개념을 알고 있다면 [커스텀 에러와 에러 확장](https://ko.javascript.info/custom-errors) 을 쉽게 이해 할 수 있을 것이다.
