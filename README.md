## 23-React3-1 오유정

react : 사용자 인터페이스를 만들기 위한 자바스크립트 라이브러리
https://github.com/soaple/first-met-react-practice/tree/master/src
### 2021/3/16 3주차

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


---------------------------------------------------

###  2021/3/23 4주차 

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
