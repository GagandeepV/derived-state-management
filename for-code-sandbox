//-react-begginers-most-likely-to-make-mistake-[wds]
//Every Beginner React Developer Makes This Mistake With State

import { useState } from "react";
import "./styles.css";
const data = [
  { id: 1, name: 'a', value: 10 },
  { id: 2, name: 'b', value: 20 },
  { id: 3, name: 'c', value: 30 },
]

const Header = ({ id, list }) => {
  const selected = list.find(({ id: listId }) => listId === id)
  return id ? <h1>Selected : {selected.name} with {selected.value}</h1> : 'NONE'
}

const List = ({ list, incrementFunc, selectFunc }) => {
  return list.map(({ id, name, value }) => {
    return (<div key={id}>
      <span>----{name}----{value}---</span>
      <button onClick={() => incrementFunc(id)} >Increment</button>---
      <button onClick={() => selectFunc(id)} >Select</button>
    </div>)
  })

}

export default function App() {
  const [state, setState] = useState({ listData: data, selectId: 0 })
  const { listData, selectId } = state

  const incrementer = (idFromButton) => {
    const toChange = listData.map(({ id, value, ...rest }) => {
      if (id === idFromButton) return { id, ...rest, value: value + 1 }
      return { id, value, ...rest }
    })

    setState(prevState => ({ ...prevState, listData: toChange }))
  }

  const selector = (idFromButton) => {
    const selected = listData.find(({ id }) => id === idFromButton)
    setState(prevState => ({ ...prevState, selectId: selected.id }))
  }

  return (
    <div className="App">
      <Header id={selectId} list={listData} />
      <hr />
      <List list={listData} incrementFunc={incrementer} selectFunc={selector} />
    </div>
  );
}
