## GraphQL 하면서 느낀점

---

1. `User` 객체에서 `password` 라는 값을 숨기기 위해서 전달하기 전에 `User` 객체에 접근해 `delete User.password` 를 하는 것이 아닌 `Query` 에서 `password` 필드만 제거하면, 클라이언트는 `password` 를 가져 갈 수 없다.

2. 정말 쉽게 데이터를 조작 할 수 있다. [Find Operator 예시](https://github.com/typeorm/typeorm/blob/master/docs/find-options.md)
