"# Redux-cheatList" 

### ACTION

  1/Make Action Folder
  2/index.jsx to write Action Type.. for example 

  export const IncAction = () => {
     return { type: "INCRIMENT" };
  };

        export const DicAction =()=>{
                return {type : "DICRIMENT"}
        }

        export const Div =()=>{
                return {type : "DIVIDET"}
        }
        export const Mul =()=>{
                return {type : "MULTIFICATION"}


### REDUCE 

  1/Make Reduce Folder
  2/Make 2 File  
    (i) index.jsx
    (ii) Reduce.jsx

  Write in reducer File ---

     const initialState = {
        count : 0,
        divMul : 5,
   }

   const countMath=(state = initialState,action)=>{
        switch(action.type){
                case "INCRIMENT" : {
                       
                        return {...initialState,  count : state.count + 1}
                };
                case "DICRIMENT" : {
                        const newCount = state.count >= 1 ? state.count - 1 : state.count
                        return {...initialState ,count : newCount}
                };
                case "DIVIDET" : {
                       
                        const newState = state.divMul === 1 ? state.divMul  : state.divMul / 5
                        return {...initialState,divMul : newState}
                };
                case "MULTIFICATION" : {
                        const newState = state.divMul >=  1 ? state.divMul * 5 : state.divMul
                        return {...initialState,divMul : newState}
                };
                default : return state
        }
   }
    export default countMath;


    2 > Conbaind This Reduce File in Reduce Folder of index.jsx

        import Reducer from "./Reducer"

        import {combineReducers} from "redux"

        const RootReducer = combineReducers({
                Reducer
        })

        export default RootReducer;


### STORE Data


  make Store.jsx file and store dataa

        import {createStore} from "redux"
        import RootReducer from "./Reducer/Index"

        const Store = createStore(RootReducer)
        export default Store;


### Store DATa Provide ROOT project
     stap - 1 

        import Store from "./Store"
        import {Provider} from "react-redux"

   step -2

      <Provider store={Store}>
        <App/>
        </Provider>


### STORE DATA inplement  any File


        import {IncAction,DicAction,Div,Mul} from "./Action/Index"
        import { useDispatch,useSelector } from "react-redux"

   write in file example const app=()=> {
        const CountCarrentState = useSelector((state)=> state.Reducer.count)
        const DivMulCarrentState = useSelector((state)=> state.Reducer.divMul)
        const disPatch = useDispatch()

   return (

  


         <div style={{display: "flex",margin : "50px"}}>
        <button style={customCss.button} onClick={()=> disPatch(IncAction())} > + </button>
        <h1 style={customCss.button}>{CountCarrentState}</h1>
        <button style={customCss.button}  onClick={()=> disPatch(DicAction())}> - </button>
        </div>

        <div style={{display: "flex", margin : "50px"}}>
        <button style={customCss.button}  onClick={()=> disPatch(Div())}> / </button>
        <h1 style={customCss.button}>{DivMulCarrentState}</h1>
        <button style={customCss.button} onClick={()=> disPatch(Mul())} > * </button>
        </div>
        </div>
         )

        }