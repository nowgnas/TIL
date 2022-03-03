# React

## Props와 State

- Props는 읽기 전용이고 State는 쓰기 기능을 한다.
- Props와 State가 변경되면 App()이 다시 렌더링 된다.

## useState와 useEffect

### useState

```jsx
const [text, setText] = useState("");
```

- useState는 상태를 변경하고 싶을 때 사용한다.
- `text`를 `setText('changeText')`를 사용해 변경 가능하다.
- `setText()`를 호출하게되면 `App()`이 다시 렌더링 된다.

### useEffect

```jsx
useEffect(()=>{
    if(text === 'someText'){
        ...action
    }
}, [text])
```

- useEffect는 최초 한 번 실행되어야 하는 코드이다.
- useEffect는 생성 되었을 경우 실행된다.
- useEffect의 두 번째 인자는 해당 변수가 변화했을 때 실행되는 함수이다.
