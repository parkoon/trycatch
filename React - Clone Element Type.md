# React - Clone Element Type

타입스크립트를 이용해서 리액트의 `cloneElement` 를 사용할 때 타입을 어떻게 처리해야 할 지 난감할 때가 있었다.

이 때마다, 만능 `any` 를 쓰기엔 죄책감이 들어 다른 해결책 2개를 기억하고자 한다.

보통 부모 컴포넌트에서 자식 컴포넌트는 조작할 때 (Compound Pattern) 다음과 같이 코드를 작성한다.

```javascript
return (
  <div>
    {Children.map(children, (child) => {
      return React.cloneElement(child, {});
    })}
  </div>
);
```

여기서 `cloneElement` 의 첫번째 파라미터에서 타입 에러가 발생한다.

> Type 'string' is not assignable to type 'ReactElement<any, string | ((props: any) => ReactElement<any, any>) | (new (props: any) => Component<any, any, any>)>'

## 해결방법 1

child 가 유효한 리액트 컴포넌트인지 확인한다.

```javascript
return (
  <div>
    {Children.map(children, (child) => {
      if (React.isValidElement(child)) {
        return React.cloneElement(child, {});
      }
    })}
  </div>
);
```

## 해결방법 2

타입에러 에서 명시한 타입을 `as` 로 지정해준다.

```javascript
return (
  <div>
    {Children.map(children, (child) => {
        return React.cloneElement(child as React.ReactElement, {})
    })}
  </div>
);
```
