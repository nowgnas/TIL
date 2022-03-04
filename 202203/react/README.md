# React

### **2022 03 03**

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

---

### **2022 03 04**

### useMemo

```jsx
const App = () => {
  const [first, setfirst] = useState(second);
  const [second, setsecond] = useState(second);
  const sumNum = useMemo(() => first + second, [first, second]);
  return <div></div>;
};
```

- 지정한 State나 Prop가 변경될 때 해당 값을 사용하는 다른 값을 저장하기 위해 사용한다.
- useMemo의 연산은 렌더링 단계에서 이뤄지기 때문에 시간이 오래 걸리는 로직은 작성하지 않도록 한다.

### useCallback

```jsx
const App = () => {
  const [first, setfirst] = useState(second);
  const [second, setsecond] = useState(second);

  const getSum = useCallback(() => {
    return first + second;
  }, [first, second]);

  return <div>{getSum()}</div>;
};
```

- 함수를 메모이제이션하기 위해 사용된다.
- 컴포넌트가 재렌더링 될 때 불필요하게 함수가 다시 생성되는 것을 방지한다.
- `useMemo(()=>func, deps)`와 `useCallback(func, deps)`는 동일하다.

### useRef

```jsx
const App = () => {
  const first = useRef(null);
  const onButtonClick = () => {
    first.current.focus();
  };
  return (
    <div>
      <input ref={first} />
      <button onClick={onButtonClick}>first로 포커스</button>
    </div>
  );
};
```

- 컴포넌트 생애 주기 내에서 유지할 ref 객체를 반환한다.
- ref는 `.current`라는 속성을 가지며 이 값을 자유롭게 변경 가능하다.
- React에서 DOM Element에 접근할 때 사용한다.
- `useRef`에 의해 반환된 ref 객체가 변경되어도 컴포넌트는 재렌더링 되지 않는다.

## useState 사용 방법

```jsx
const App = () => {
  const [first, setFirst] = useState(0);
  setFirst((curr) => {
    return curr + 1;
  });
};
```

- setState를 사용할 때 위 코드와 같이 함수형으로 작성하는 방법이 좋다.

## 많이 사용하는 DOM 이벤트

### onClick

- Element를 클릭했을 때

### onChange

- Element의 내용이 변경되었을 때(input의 텍스트를 변경, 파일 선택 등)

### onKeyDown, onKeyUp, onKeyPres

- 키보드 입력이 일어났을 때

### onDoubleClick

- Elemet를 더블 클릭했을 때

### onFocus

- Element가 Focus되었을 때

### onBlur

- Element가 Focus를 잃었을 때

### onSubmit

- Form Element에서 submit 했을 때

---
