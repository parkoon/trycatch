## Nullish coalescing operator

---

**널 병합 연산자(??)** 는 왼쪽 피연산자가 `null` 또는 `undefined` 일 경우에 오른쪽에 있는 값을 반환한다.

```javascript
const foo = null ?? "bar"; // expected value: 'bar'
const zero = 0 ?? "not zero"; // expected value: 0
```

**논리 연산자(||)** 와 잘 구분해서 써야 한다. **널 병합 연산자** 와는 달리 왼쪽에 있는 값이 `null`, `undefined` 뿐만 아니라 `falsy` 한 값인 `0` 또는 `''` 일 때도 오른쪽에 있는 값을 반환한다.

상황은 아래와 같다.

금액이 0이 아닌 경우 "결재 할 금액이 있습니다" 라는 문구를 띄운다면

```javascript
const price = getPrice();

price || <span>결재 할 금액이 있습니다</span>; // (O)

price ?? <span>결재 할 금액이 있습니다</span>; // (X)의도하지 않은 0 이 출력 될 수 있다.
```
