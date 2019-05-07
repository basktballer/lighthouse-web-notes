#Week 6 Day 2 Notes
## Lecture Notes

* This.setState
  * React batches together
  * If call 3 times in a row, 

* Props vs State
  * Props can be passed from parent to child
  * State is local to the component

* Create-react-app

* Controlled component, input
  * Important

* Pass data down, actions communicate back up
  * Pass down as props

* Check version of react (16.8.6)

* Hooks
  * Hook into a functional component or a lifecycle component
  * Hooks are asynchronous
  * useState hook
    * same as this.state.XXX
    * Change it
    * Comes with two variables to manipulate. 
    * Value is the getter, setValue is the setter
  * Effect hook
    * ComponentDidMount and ComponentDidUpdate
    * UseEffect will take over these two functions above
    * Newer React versions, boilerplates we are currently using doesn't support this

``` jsx

// App.js Use State Hook

import React, {useState} from "react";
import logo from "./logo.svg";


function app() {
  return (
    <div className="App">
    <Counter />
    <Counter step={2}/>
    <Counter step={5}/>
    <Counter step={10} onChange={v => console.log("Value Changed", v)} />

  </div>
  )
};

const Counter = ({step = 1, onChange= () => {} }) => {
  const [value, setValue] = useState(0);

const changeValue = (delta) => {
    const newValue = value + delta;
    setValue(newValue;
    onChange(newValue);     
  }

useEffect(() => {
  document.title = `The counter with ${step} updated to ${value}`;
});

  return (
  <div>
    <button onClick={() => changeValue(-1 * step)}>-</button>
    <span>{value}<span>
    <button onClick={() => changeValue(step)}>+</button>
  </div>);
};

export default App;

```


* Search Example

```jsx

function App() {
  
  const [results, setResults] = useState([]);
  // don't use the index element of the array in case array has been resorted, otherwise sorting has no effect
  // find a value that is unique, use the database ID typically

  const searchReddit = async term => {
    const url = `https://www.reddit.com/r/aww/search.json?restrict_sr=true&sort=hot&type=link&q=${term}`;


    // synchronous function now    
    const resp = await fetch(url); // whatever happens in the first then goes here
    const json = await resp.json(); // next promise
    const images = json.data.children.map(child => ({
          key: child.data.permalink,
          url: child.data.thumbnail
        }));
    return images;

    // ORIGINAL ASYNC FUNCTION
    // fetch(url)  // get request, similar to JQuery, 
    //   .then(resp => resp.json())
    //   .then(json => {
    //     const images = json.data.children.map(child => ({
    //       key: child.data.permalink,
    //       url: child.data.thumbnail
    //     }));
    //     setResults(images);
    //   });
  }
  
  const handleSearch = async term => {
    setResults([]);
  
    const images =  await searchReddit(term);
    setResults(images)

    // ORIGINAL ASYNC
    // searchReddit(term);
  }

  return (
    <div className="App">
      <SearchBar onSearch={handleSearch}/>
      <div>
        <ul>
          {results.map((r, i )=> (
            <img src={r.url} key={r.url} />
          ))}
        </ul>
      </div>
    </div>
  );
}e


const SearchBar = ({onSearch = () -> {}) => {

  const [term, setTerm] = useState(""); // this is a string for user to type in, destructure the array, two values held together

  const handleChange = e => setTerm(e.target.value);

  const handleSearch = () => {
    onSearch(term);
    setTerm("");
  }
    // need to define value and onChange for the input field
    // onChange exists on input elements, we needed to define our own for the counter element
  return (
    <div className="search-bar">
      <input type="text" value={term} onChange={handleChange}/>   
      <button onClick={handleSearch}>
        <span role="img" aria-label="search">
          =)
        </span>
      </button>
    </div>
  );
}
export default SearchBar



```