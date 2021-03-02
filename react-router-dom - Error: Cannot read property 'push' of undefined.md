## react-router-dom - Error: Cannot read property 'push' of undefined

---

`next.js` 만 사용하다 오랜만에 `react-router-dom` 을 사용하려고 하니, 생각지도 못한 에러가 발생했다.

```javascript
import { BrowserRouter as Router, Switch, Route, Link } from "react-router-dom";

function App() {
  return (
    <Router>
      <Switch>
        <Route path="/register">
          <Register />
        </Route>
        <Route path="/login">
          <Login />
        </Route>
        <Route path="/">
          <Home />
        </Route>
      </Switch>
    </Router>
  );
}
```

위와 같이 라우팅을 해주고 각 컴포넌트에서 `props.history.push('/somewhere')` 를 호출하는데 `Cannot read property 'push' of undefined` 에러가 발생했다.

리액트 라우터에서 `props` 에 `history` 객체를 주입하지 못한거 같다.

찾아보니 해결책은 2가지가 있다.

1. 각 컴포넌트에서 `react-router-dom` 에서 제공하는 `useHistory`를 사용한다.
2. **compound pattern** 이 아닌 **prop injection** 으로 변경한다.

```javascript
function App() {
  return (
    <Router>
      <Switch>
        <Route path="/register" component={Register} />
        <Route path="/login" component={Login} />
        <Route path="/" component={Home} />
      </Switch>
    </Router>
  );
}
```
