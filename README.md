## 23-React3-1 오유정

react : 사용자 인터페이스를 만들기 위한 자바스크립트 라이브러리
https://github.com/soaple/first-met-react-practice/tree/master/src

### 2023/5/23

#### 컨텍스트 API

1.  React.createContext
``` const MyContext = React.createContext（기본값）; ```
2. Context.Provider
```  <MyContext.Provider value={ some value }> ```
3. Class.contextType
  
``` class MyClass extends React.Component {
 componentDidMountO {
 let value = this.context;

 }
 componentDidUpdateO {
 let value = this.context;
 /* ... */
 }

componentWillUnmoumt() {
 let value = this.context;
 /... *
 }
 render() {
 let value = this.context;
 /* MyContexto| 값에 따라서 컴포넌트들을 렌더링 /*
 }
 }
 MyClass.contextType = MyContext; ```

 4. Context.Consumer
 ```
  <MyContext .Consumeo
 {value => /* 컨텍스트의 값에 따라서 컴포넌트들을 렌더링 */}
 </MyContext.Consumer>  
 ```

 #### userContext

- 함수형 컴포넌트에서 컨텍스트를 사용하기 위해 컴포넌트를 매번  Consumer 컴포넌트로 감싸주는 것보다 Hook을 사용하면 됨

- useContext()  또는 React.createContext() 함수 호출로 생성된 컨텍스트 객체를 인자로 받아서 현재 컨텍스트의 값을 리턴한다


```
function MyComponent(props) {
 const value = useContext(MyContext);

 return (

 )
 } ```


------------------------------------------------------------------

### 2023/5/18 12주차

#### Specialization (특수화, 전문화)

- 웰켐다이얼로그는 다이얼로그의 특별한 케이스이다
- 범용적인 개념을 구변이 되게 구체화하는 것을 특수화라고 한다
- 객체지향 언어에서는 상속을 사용하여 특수화를 구현한다.
- 리액트에서는 합성을 사용하여 특수화를 구현한다.

```
function Dialog(props) {
 return (
 <FancyBorder color="blue">
 <hl className="Dialog-title">
 {props.title}
 </hl>
 <p className="Dialog-message">
 {props.message}
 </p>
 소플의처음 만난 리액트
 </FancyBorder>
 );
 }

 function WelcomeDialog(props) {
 return (
 <Dialog
 title="어서 오세요“
 message="우리 사이트에 방문하신 것을 환영합니다!”
 />
 )；
 }
```

다음 예와 같이 특수화는 범용적으로 쑬 수 있는 컴포넌트를 만들어 놓고 이를 특수한 목적으로 사용하는 합성 방식이다.



---------------------------------------------------

### 2023/5/11 11주차

하위 컴포넌트에서  state 공유하기
- 물이 끓는지 알려주는 컴포넌트
```
 function BoilingVerdict(props) {
        if (props.celsius >= 100) {
            return <p>물이 끓습니다.</p>;
        }
        return <p>물이 끓지 않습니다.</p>;
    }
```
- Calculator
```
    function Calculator(props) {
        const [temperature, setTemperature] = useState('');

        const handleChange = (event) => {
            setTemperature(event.target.value);
        }
        
        return (
            <fieldset>
                <legend>섭씨 온도를 입력하세요:</legend>
                <input
                    value={temperature}
                    onChange={handleChange} />
                <BoilingVerdict
                    celsius={parseFloat(temperature)} />
            </fieldset>
        )
    }
     
```
추출한 컴포넌트 사용하도록 Calculator 컴포넌트 변경
```
    function Calculator(props) {
        return (
            <div>
                <TemperatureInut sclae="c" />
                <TemperatureInut sclae="f" />
            </div>
        );
    }
```

- 온도 변환 함수
- TemperatureInput 컴포넌트
```
function TemperatureInput(props) {
    const handleChange = (event) => {
        props.onTemperatureChange(event.target.value);
    }


    return (
        <fieldset>
            <legend>온도를 입력해주세요(단위:{scaleNames[props.scale]}):</legend>
            <input value = {props.temperature} onChange={handleChange} />
        </fieldset>
    )
}
```
- Calculator  컴포넌트 변경하기
```
function Calculator(props) {
    const [temperature, setTemperature] = useState("");
    const [scale, setScale] = useState("c");

    const handleCelsiusChange = (temperature) => {
        setTemperature(temperature);
        setScale("c");
    };

    const handleFahrenheitChange = (temperature) => {
        setTemperature(temperature);
        setScale("f");
    };

    const celsius =
        scale === "f" ? tryConvert(temperature, toCelsius) : temperature;
    const fahrenheit =
        scale === "c" ? tryConvert(temperature, toFahrenheit) : temperature;

    return (
        <div>
            <TemperatureInput
                scale="c"
                temperature={celsius}
                onTemperatureChange={handleCelsiusChange}
            />
            <TemperatureInput
                scale="f"
                temperature={fahrenheit}
                onTemperatureChange={handleFahrenheitChange}
            />
            <BoilingVerdict celsius={parseFloat(celsius)} />
        </div>
    );
}
```



-------------------------------------------------------

### 2023/5/4 10주차

#### 리스트와 키란 무엇인가
- 리스트는 js 변수나 객체를 하나의 변수로 묶어놓은 배열과 같은 것이다
- 키는 각 객체나 아이템을 구분할 수 있는 고유한 값을 의미
- 리액트에서는 배열과 키를 사용하는 반복되는 다수의 앨리먼트를 쉽게 렌더링할 ?수 있음


|태그|설명
|----------|---------
|File input | 값이 읽기 전용이다.
|select | 목록에서 다중으로 선택이 되도록 하기 위해 multiple 속성값을 true로 변경
|textarea | html에서는 textarea의 childred으로 텍스트가 들어간다. state를 통해 벨루의 attribute변경하여 텍스트 표시



------------------------------------------------------------------

### 2023/4/13 7주차

#### 훅이란 무엇인가

기존 함수 컴포넌트는 클래스 컴포넌트와는 다르게 코드도 간결하고, 별도로
state를 정의해서 사용하거나 컴포넌트의 생명주기에 맞춰 어떤 코드가 실행
되도록 할 수 없었다. 따라서 이런 기능을 지원하기 위해 나온 것이 훅이다.

- 클래스형 컴포넌트는 생성자에서 state를 정의하고, setState()함수를
 통해 state를 업데이트 한다.
- 함수형 컴포넌트에서   state너 생명주기 함수의 기능을 사용하게 해주기 위해
추가된 기능이 바로 훅이다.


#### useState
- useState는 함수형 컴포넌트에서 state를 사용하기 위한 Hook이다.
- 증가는 시킬 수 있지만 증가할 때마다 재 렌더링은 일어나지 않는다.
-> 그럴 경우 useState() 를 사용한다.

1. 첫번째 항목은  state의 변수 이름
2. 두번째 항목은  state의 set함수(state를 업데이트 하는 함수)
3. 함수를 호출 할 때  state의 초기값을 설정
4. 함수의 리턴 값은 배열의 형태

##### useEffect

- useState와 함께 가장 많이 사용하는 Hook
- side effect(리액트에서는 '영향'의 의미) 를 수행하기 위한 것
ex) 서버에서 데이터를 받아오거나 수동으로  Dom을 변경하는 등의 작업
(렌더링 중에 작업이 완료될 수 없고 다른 컴포넌트에 영향을 줄 수 있기 때문에)
- 클래스 컴포넌트의 생명주기 함수와 같은 기능을 하나로 통합한 기능을 제공

- 첫번째 파라미터는 이펙트 함수가 들어가고, 두번째 파라미터로는 의존성 배열
```  userEffect(이펙트 함수, 의존성 배열); ```
- 이때 의존성 배열을 생략하는 경우는 업데이트될 때마다 호출된다.


```
useEffect(() => {
  // 컴포넌트가 마운트 된 이후
  // 의존성 배열에 있는 변수들 중 하나라도 값이 변경되었을 때 실행됨
  // 의존성 배열에 빈 배열을 넣으면 마운트와 언마운트시에 단 한번씩만 실행됨
  // 의존성 배열 생략 시 컴포넌트 업데이트 시마다 실행됨

  return() => {
    // 컴포넌트가 마운트 해제되기 전에 실행됨
  }
}, [의존성 변수1, 의존성 변수2]);

``` 
#### useMemo
- useMemo()혹은 Memorized value를 리턴하는 훅
- 이전 계산값을 갖고 있기 때문에 연산량이 많은 작업의 반복을 피할 수 있음
- 이 훅은 렌더링이 일어나는 동안 실행됨
- 예를 들면 useEffect 사이드 이펙트와 같은 것

```
const memoizedValue = 니seMemo(
 () => computeExpensiveValue(a, b) // (의존성 변수1, 의존성 변수2)
 );
 ```

#### useCallback

- useCallback() 혹은 useMemo()와 유사한 역할
- 차이점은 값이 아닌 함수를 반환한다는 것


#### useRef()

- 래퍼런스란 특정 컴포넌트에 접근할 수 있는 객체를 의미
- useRef() 훅은 이 래퍼런스 객체를 반환
- 객체에는 .current라는 속성이 있는데, 이것은 현재 참조하고 있는 엘리먼트를 의미
``` const refContainer = useRef(초깃값);
```
- 이렇게 반환된 레퍼런스 객체는 컴포넌트의 라이프타임 전체에 걸쳐서 유지
- 즉, 컴포넌트가 마운트 해제 전까지는 계속 유지된다는 의미

#### 훅의 규칙

1. 무조건 최상의 레벨에서만 호출해야 함
-> 반복문이나 조건문 또는 중첩된 함수 안에서 절대 호출 안됨
-> 컴포넌트가 렌더링 될 때마다 같은 순서로 호출되어야만 한다.
2. 리액트 함수 컴포넌트에서만 훅을 호출해야 함
-> 일반 자바스크립트 함수에서 훅 호출 안된다.
-> 훅은 리액트 함수 컴포넌트 혹은 직접 만든 커스텀 훅에서만 호출 가능

```
// isOnline이라는  state에 따라 사용자의 상태가 온라인인지 보여주는 컴포넌트
 
 import React, { useState, useEffect } from "react";

 function UserStatus(props) {
 const [isOnline, setlsOnline] = useState(nuU);

 useEffect(() => {
 function handleStatusChange(status) {
 setIsOnline(status.isOnline);
 }

 ServerAPI.subscribeUserStatus(props.user.id, handleStatusChange);
 return () => {
 ServerAPI.니nsubscribeUserStatus(props.user.id, handleStatusChange);
 };
 });

 if (isOnline === null) {
 return '대기중…';
 }
 return isOnline ? '온라인 ' : '오프라인 ';
 }

```

---------------------------------------------

### 2023/4/6 6주차


#### 컴포넌트 추출
- 복잡한 컴포넌트를 쪼개서 여러 개의 컴포넌트로 나눌 수 있음
- 큰 컴포넌트에서 일부를 추출하여 새로운 컴포넌트를 만듬



#### status란
- status는 리액트 컴포넌트의 상태를 의미
- 컴포넌트의 데이터를 의미
- 컴포넌트의 변경가능한 데이터를 의미
- status가 변하면 다시 렌더링 되기 때문에 렌더링과 관련된 앖만 status에 포함시켜야 함

#### 6.2 생명주기에 대해 
- 생명주기는 컴포넌트의 생성 시점, 사용 시점, 종료 시점을 나타냄
- constructor가 실행 되면서 컴포넌트가 생성
- 생성 직후 componentDidMount()함수가 호출
- 컴포넌트가 소멸하기 전까지 여러 번 렌더링
- 렌더링은 props. setStatus(), forceUpdate()에 의해 상태가 변경되면서 이루어짐
- 렌더링이 끝나면 conponentWillUnmount() 함수가 호출

-----------------------------------------
### 2023/3/30 5주차

#### 엘리먼트

- 엘리먼트는 리액트 앱을 구성하는 요소를 의미
- 공식페이지에는 엘리먼트는 리랙트 앱의 가장 작은 빌딩 블록들 이라고 설명함
- 웹 사이트의 경우 DOM 엘리먼트이며 HTML요소를 의미함

#### 앨리먼트 특징

- 리액트 엘리먼트의 가장 큰 특징은 불변성
- 즉 한 번 생성된 엘리먼트의 children이나 속성(attributes)을 바꿀 수 없음

#### 컴포넌트에 대해
- 리액트는 컴포넌트 기반의 구조를 갖는다.
- 컴포넌트 재사용이 가능하기 깨문에 전체 코드의 양을 줄일 수 있어 개발 시간과 유지 보수 비용도 줄일 수 있다.
- 컴포넌트는 자바스크립트 함수와 입력과 출력이 있다는 면에서 유사
- 다만 입력과 출력은 입력은 Props가 담당하고 출력은 리액트 엘리먼트 형태로 출력
- 엘리먼트를 필요한 만큼 만들어 사용한다는 면에서는 객체 지향의 개념과 비슷

#### Props의 특징
- 읽기 전용, 변경 불가함
- 속성이 다른 엘리먼트를 생성하려면 새로운 props를 컴포넌트에 전달하면 됨

#### pure 함수 vs impure 함수
  pure함수는 인수로 받은 정보가 함수 내부에서도 변하지 않는 함수
  inpure함수는 인수로 받은 정보가 함수 내부에서 변하는 함수
--------------------------------------------------------------------

###  2023/3/23 4주차 

#### JSX (A syntax extention to JavaScript) 
- 자바스크립트 확장 문법
- 자바스크립트와 xml/html을 합친 것이라고 봐도 가능
1. 속성 
  const element = <a href="http://www.reactjs~></a>

2. 자식 정의
jsx태그는 자식을 포함할 수 있음
  const element = {
    <div>
      <h1>hello</h1>
    </div>
  }
  3. 객체 포함

>> * jsx는 내부적으로 xml/tml코드를 자바스크립트로 변환하는 과정을 거치는데 이 변환하는 역할을 하는 것이 리액트의 `` createElemnet()``라는 것이다.

```
class Hello extends React.Component {
  render() {
    return <div>HeUo {this. props. toWhat}</div>;
    }
 }

 ReactDOM.render(
  <Hello toWhat=1,World" /》,
  document.getElementById('root')
 )；

```
   

#### jsx의 장점
1. 코드의 가독성이 좋다
2. injection Attack이라 불리는 해킹 방법을 방어함으로써 방어에 강하다.

----------------------------------------------------------------

### 2023/3/16 3주차

<리액트의 장점>

1. 빠른 업데이트와 렌더링 속도

2. 컴포넌트 기반 구조

- 리액트의 모든 페이지는 컴포넌트로 구성한다.
- 하나의 컴포넌트는 다른 여러 개의 컴포넌트의 조합으로 구성 가능
  (컴포넌트를 조합해 웹사이트 개발)

3.  재사용성

- 반복적인 작업을 줄여주기 때문에 생사성을 높여준다
- 유지보수가 용이하다
- 재사용이 가능하려면 해당 모듈의 의존성이 없어야 한다.

4. 든든한 지원금

- 메타에서 오픈소스 프로젝트로 관리하고 있어 계속 발전하고 있다.

5. 모바일 앱 개발기능

- 리액트 네이티브라는 모바일 환경 ui프레임워크를 사용하면 크로스 플랫폼 모바일 앱을 개발할 수 있다.





