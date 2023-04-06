## 23-React3-1 오유정

react : 사용자 인터페이스를 만들기 위한 자바스크립트 라이브러리
https://github.com/soaple/first-met-react-practice/tree/master/src

### 2023/4/6


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

``
class Hello extends React.Component {
  render() {
    return <div>HeUo {this. props. toWhat}</div>;
    }
 }

 ReactDOM.render(
  <Hello toWhat=1,World" /》,
  document.getElementById('root')
 )；

``
   

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





