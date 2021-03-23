# React - Key 의 중요성

상황은 이렇다.

특정 버튼을 누르면 배열에 값을 넣고 그 값은 순회하면서 컴포넌트를 생성하고 그 컴포넌트는 3초후에 없애야 하는 상황이었다.

```javascript
function App() {

    const [values, setValues] = useState();

    const add = () => {
        const newValue = {...}
        setValues(prev => [...prev, newValue])
    }

    return <>
        {values.map(v => <Timer />)}
    </>
}
```

```javascript
function Timer() {

    const timerId = useRef()

    useEffect(() => {
        startTimer()
        return () => stopTimer()
    }, [])

    const startTimer = () => {
        if (timerId.current)
            timerId.current = setTimeout(() => {...}, 3000)
    }
    const stopTimer = () => {

        if (timerId.current)
            clearTimeout(timerId.current)
    }
}
```

클릭 한 번은 동작하는데, 클릭 한 번 이상했을 때 첫 번째 클릭한게 없어지지 않았다.

이유는 `map` 돌 때 키를 안넣어줘서 그렇다.

컴포넌트는 지우는 상황이 아니라면 리액트에서 `key` 를 입력하지 않아도 큰 문제는 없다. (추가하는 상황에서는 성능 이슈가 발생할 수는 있다.)

지울 땐 아예 동작이 달라진다. 리액트 이 녀석이 어떤 놈을 지워야 하는지 모르는것 같다.
