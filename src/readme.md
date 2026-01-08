# Why React?

- We can use states which means that once we update the state variable, it changes across the page, because we can use on feature multiple time
- We can split our app into multiple components and reuse those components
- React uses a virtual DOM to efficiently update the UI which is better than updating content using DOM Manipulation
- Debugging and maintainance is easy

# 1. props in react

- ek se dusre component me data pass karna props kahlata hai `(props)` (props.title/ props.desc)

- in Card file

```
const Card = (props) => {
    return (
        <div className='card'>
           <h1>{props.title}</h1>
            <p>{props.description} desc</p>
        </div>
    )
}
```

- in main `App.jsx` file

```
  <div className="cards">
  <Card title="card 1" description="card 1" />
  <Card title="card 2" description="card 2" />
  <Card title="card 3" description="card 3" />
  </div>
```

Tip : Don't forget to import card in `App.jsx` like this

```
import Card from './components/Card'
```

# 2. Component
- Component are add in `App.jsx` `return` section
- har component function hota hai par yeh class base bhi ho sakta hai
- component ko main file `App.jsx` me import karte hai this type of syntax use karte hai

```
<Navbar/>
```

and `Navbar.jsx` file me

```
export default Card
import React from 'react'

const Card = () => {
  return (
    <div>

    </div>
  )
}

export default Card
```

# diffrence between library and framework

- library -- target specific functionality deta hai
- framework -- ek app ko create karne ke liye jo bhi chahiye wo framework me hota hai(next.js)

# 3. JSX (JavaScriptReact)

- main use `html` with `js`
- normally use HTML and switch to JS than use `{}`
- in this curly brakate switch into js and only in brakate

```
 {}
```

# 4. Hooks & State
- Hooks & State add in first `function()` 
- React ke function component ki capabilities ko enhance karte hai
- like `usestate()` ek function hai jisme `count` naam ki ek state ho jiski abhi ki value `0` ho and ek aisa function `setCount` ho jo is `count` ki value ko update kar ske
- State are `useState`

```
 const [count, setCount] = useState(0)
```

```
<p>let count is {count} </p>
<button onClick={()=>{setCount(count + 1)}}>click here to + 1</button>
```

- Doubt Solve :- count, setCount are not React inbuild item so we can edit there name Like(counti, setCounti)

# 5. useEffect() Hook

- syntax

```
useEffect(() => {
    first

    return () => {
        second
    }
}, [prop])
```

- this return use for comnditional rendering

Case 1 :- Run on every render

```
useEffect(() => {
    alert("Hey I will run on every render")
})
```

Case 2: Run only on first render

```
useEffect(() => {
    alert("Hey welcome to my page. This is the first render")
}, [])
```

Case 3: Run only when certain values change

```
useEffect(() => {
    alert("Hey I am running because color was changed")
}, [color])
```

- most of use `useEffect()` koi chij (props, component) sirf ek bar ho jab aapka page reload ho and ek ek bhut bar ho sakta hai

# 6. useRef() Hook

- Case: 1
- uses `useRef` is when we use `useEffect()` and normal action on app than whole page are rerender, here is a problem because of rerendering, value was same, in case we think value not change (before was it). than `useRef()` use to not rerender page like value persist hogi and
- it initialize not the value like before we have `0` change into not in `0` it update and without `useRef()` it again and again `0`

```
const a = useRef(0)
```

- use `.current` to avoid error

```
useEffect(() => {
  a.current += 1
  console.log(`rerendering and the value of a is ${a.current}....`)
})
```

- it was counter in console

- Case : 2
- use to reference and it in sort of DOM manupalation using `useRef()` we can edit other items like

```
const btnref = useRef()

useEffect(() => {
  btnref.current.style.backgroundColor = "red"
}, [])
```

- add in button

```
<button ref={btnref} onClick={() => setCount((count) => count + 1)}>
   count is {count}
</button>
```

- button color was red
- another example

```
<button onClick={()=>{btnref.current.style.display = "none"}}>Click Me</button>
```

- hide `btnref` button

# 7. Conditional Rendering

- Conditional Rendering is a basically Rendering with Conditional understand with example
- using `useState` we add to value (showbtn, setshowbtn)
```
const [showbtn, setshowbtn] = useState(false)
```
- this is for toggle
```
{showbtn ? <button>showbtn is true</button> : <button>showbtn is false</button>}
```

```
<button onClick={() => setshowbtn(!showbtn)}>
  Toggle showbtn
</button>
```
