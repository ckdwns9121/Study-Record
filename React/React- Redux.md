## 리덕스

## 1. 리덕스란

   상태관리를 전역에서 할 수 있도록 해주는 모듈


## 2. 리덕스에서 사용되는 키워드

* 액션
 
  상태에 어떠한 변화가 필요하게 될 때 액션타입을 명시해주는것,
  type :INCREMENT


* 액션 생성함수

  액션 생성함수는 액션들 만드는 함수, 파라미터를 받아와서 액션 객체 형태로 return
  export function increment =() =>{type :INCREMENT}


* 리듀서

   변화를 일으키는 함수. 현재 상태와 전달받은 액션을 참고해 새로운 상태를 만들어 리턴


* 스토어

    리덕스에서 한 어플리케이션당 하나의 스토어를 만듦,
    import {createStore} from 'react-redux';
    const store = createStore(reducers)


### 구독

    스토어의 내장함수중 하나, 그러나 리액트에서 직접적으로 사용하는 경우는 거의 없고
    react-redux의 내장함수인 connect를 통해 구독한다.

 
## 3. 스토어 생성방법

    액션타입 선언 -> 액션생성자 -> 리듀서 구현 -> 스토어에 파라미터로 넘김


## 4. Ducks 패턴

    기본적인 디렉터리 구조는 actions, reducers 등등의 디렉토리로 분리되있지만
    프로젝트가 커지고 관리할 소스코드가 많아지면 액션과 리듀서가 분리되어있는 구조는 매우 불편하다.

    그래서 리듀서와 액션, 액션생성자 등 관련 코드를 하나의 파일에 묶어 작성하는 패턴을 Ducks 패턴이라고 한다.


## 5. connect 함수
    
    기본적으로 Container 코드에서 작성  
    import {connect} from 'react-redux';  
    import {hello} from '../mudules;  
    
    const TestContainer =({test,onHello}){  
        return(  
            <Test  
            test={test}  
            onHello={onHello}  
            />  
        )  
    }  
  
    mapToStateProps = (state) =>({  
        test : state.test  
    })  
    mapToDispatchProps = (dispatch) =>({    
        onHello : () => dispatch(hello())    
    })  
    export default connect(mapToStateProps,mapToDispatchProps)(TestContainer);  

