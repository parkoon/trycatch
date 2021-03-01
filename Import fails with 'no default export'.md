`export default` 로 작성되어 있지 않은 모듈을 `import module from 'module'` 과 같이 가져오려고 하면 아래와 같은 에러 메세지가 발생한다.

_Module '"/Users/parkjonghyeok/Workspace/graphql-course/node_modules/@types/bcrypt/index"' has no default export._

이를 해결 할 수 있는 방법은 2가지가 있다.

1. `import * as module from 'module'` 을 사용한다.
2. `tsconfig.json` 에 `"allowSyntheticDefaultImports": true` 와 `"esModuleInterop": true` 를 준다.

> 참고: https://github.com/microsoft/TypeScript-React-Starter/issues/8
