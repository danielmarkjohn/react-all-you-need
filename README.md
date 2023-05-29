# All You Need to Know React Cheat Sheet

1. **Components:**

```jsx
javascriptCopy code
import React from 'react';

class MyComponent extends React.Component {
  render() {
    return <div>Hello, World!</div>;
  }
}

```

1. **Functional Components:**

```jsx
javascriptCopy code
import React from 'react';

function MyComponent() {
  return <div>Hello, World!</div>;
}

```

1. **Props:**

```jsx
javascriptCopy code
<MyComponent name="John" age={25} />

```

1. **State:**

```jsx
javascriptCopy code
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = { count: 0 };
  }

  render() {
    return <div>Count: {this.state.count}</div>;
  }
}

```

1. **Lifecycle Methods:**

```jsx
javascriptCopy code
componentDidMount() {
  // Executed after the component is mounted
}

componentDidUpdate(prevProps, prevState) {
  // Executed after the component is updated
}

componentWillUnmount() {
  // Executed before the component is unmounted
}

```

1. **Event Handling:**

```jsx
javascriptCopy code
<button onClick={handleClick}>Click Me</button>

function handleClick() {
  // Event handling logic
}

```

1. **Conditional Rendering:**

```jsx
javascriptCopy code
render() {
  return (
    <div>
      {isLoggedIn ? <UserGreeting /> : <GuestGreeting />}
    </div>
  );
}

```

1. **Lists and Keys:**

```jsx
javascriptCopy code
<ul>
  {items.map(item => <li key={item.id}>{item.name}</li>)}
</ul>

```

1. **Forms:**

```jsx
javascriptCopy code
<input type="text" value={this.state.text} onChange={this.handleChange} />

handleChange(event) {
  this.setState({ text: event.target.value });
}

```

1. **React Router:**

```jsx
javascriptCopy code
import { BrowserRouter as Router, Route, Link } from 'react-router-dom';

function App() {
  return (
    <Router>
      <nav>
        <Link to="/">Home</Link>
        <Link to="/about">About</Link>
      </nav>
      <Route exact path="/" component={Home} />
      <Route path="/about" component={About} />
    </Router>
  );
}

```

1. **Hooks:**

```jsx
javascriptCopy code
import React, { useState, useEffect } from 'react';

function MyComponent() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    document.title = `Count: ${count}`;
  }, [count]);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}

```

1. **Context API:**

```jsx
javascriptCopy code
import React, { createContext, useContext } from 'react';

const MyContext = createContext();

function MyComponent() {
  const data = useContext(MyContext);
  return <div>{data}</div>;
}

function App() {
  return (
    <MyContext.Provider value="Hello, World!">
      <MyComponent />
    </MyContext.Provider>
  );
}

```

1. **PropTypes:**

```jsx
javascriptCopy code
import PropTypes from 'prop-types';

MyComponent.propTypes = {
  name: PropTypes.string.isRequired,
  age: PropTypes.number
};

```

1. **Default Props:**

```jsx
javascriptCopy code
MyComponent.defaultProps = {
  age: 18
};

```

1. **React Fragments:**

```jsx
javascriptCopy code
import React, { Fragment } from 'react';

function MyComponent() {
  return (
    <Fragment>
      <h1>Title</h1>
      <p>Content</p>
    </Fragment>
  );
}

```

1. **CSS-in-JS (Styled Components):**

```jsx
javascriptCopy code
import styled from 'styled-components';

const Button = styled.button`
  background-color: ${props => (props.primary ? 'blue' : 'gray')};
  color: white;
`;

function MyComponent() {
  return (
    <div>
      <Button primary>Primary Button</Button>
      <Button>Secondary Button</Button>
    </div>
  );
}

```

1. **Higher-Order Components (HOC):**

```jsx
javascriptCopy code
function withLogger(WrappedComponent) {
  return class extends React.Component {
    componentDidMount() {
      console.log('Component mounted');
    }

    render() {
      return <WrappedComponent {...this.props} />;
    }
  };
}

const EnhancedComponent = withLogger(MyComponent);

```

1. **Render Props:**

```jsx
javascriptCopy code
class MouseTracker extends React.Component {
  render() {
    return (
      <div onMouseMove={this.handleMouseMove}>
        {this.props.render(this.state)}
      </div>
    );
  }
}

function MyComponent() {
  return (
    <MouseTracker render={({ x, y }) => (
      <p>Mouse position: {x}, {y}</p>
    )} />
  );
}

```

1. **Error Boundaries:**

```jsx
javascriptCopy code
class ErrorBoundary extends React.Component {
  constructor(props) {
    super(props);
    this.state = { hasError: false };
  }

  componentDidCatch(error, info) {
    this.setState({ hasError: true });
    console.error(error, info);
  }

  render() {
    if (this.state.hasError) {
      return <div>Something went wrong.</div>;
    }
    return this.props.children;
  }
}

<ErrorBoundary>
  <MyComponent />
</ErrorBoundary>

```

1. **React Hooks:**

```jsx
javascriptCopy code
import React, { useState, useEffect } from 'react';

function MyComponent() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    document.title = `Count: ${count}`;
  }, [count]);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}

```

1. **React Context with useContext and useReducer:**

```jsx
javascriptCopy code
import React, { createContext, useContext, useReducer } from 'react';

const MyContext = createContext();

const initialState = { count: 0 };

function reducer(state, action) {
  switch (action.type) {
    case 'INCREMENT':
      return { count: state.count + 1 };
    case 'DECREMENT':
      return { count: state.count - 1 };
    default:
      return state;
  }
}

function MyComponent() {
  const { state, dispatch } = useContext(MyContext);

  return (
    <div>
      <p>Count: {state.count}</p>
      <button onClick={() => dispatch({ type: 'INCREMENT' })}>Increment</button>
      <button onClick={() => dispatch({ type: 'DECREMENT' })}>Decrement</button>
    </div>
  );
}

function App() {
  const [state, dispatch] = useReducer(reducer, initialState);

  return (
    <MyContext.Provider value={{ state, dispatch }}>
      <MyComponent />
    </MyContext.Provider>
  );
}

```

1. **React Router with Route Parameters:**

```jsx
javascriptCopy code
import { BrowserRouter as Router, Route, Link } from 'react-router-dom';

function User({ match }) {
  return <div>User ID: {match.params.id}</div>;
}

function App() {
  return (
    <Router>
      <nav>
        <Link to="/users/1">User 1</Link>
        <Link to="/users/2">User 2</Link>
      </nav>
      <Route path="/users/:id" component={User} />
    </Router>
  );
}

```

1. **React Hooks with Custom Hooks:**

```jsx
javascriptCopy code
import React, { useState, useEffect } from 'react';

function useDocumentTitle(title) {
  useEffect(() => {
    document.title = title;
  }, [title]);
}

function MyComponent() {
  const [count, setCount] = useState(0);
  useDocumentTitle(`Count: ${count}`);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}

```

1. **React Performance Optimization with useMemo and useCallback:**

```jsx
javascriptCopy code
import React, { useState, useMemo, useCallback } from 'react';

function ExpensiveComponent({ data }) {
  // Expensive computation
  const result = useMemo(() => {
    // Some time-consuming calculation using data
    return /* result */;
  }, [data]);

  const handleClick = useCallback(() => {
    // Callback function logic
  }, []);

  return (
    <div>
      <p>Result: {result}</p>
      <button onClick={handleClick}>Click Me</button>
    </div>
  );
}

```

1. **React Hooks for Form Handling with useState:**

```jsx
javascriptCopy code
import React, { useState } from 'react';

function Form() {
  const [name, setName] = useState('');
  const [email, setEmail] = useState('');

  const handleSubmit = (e) => {
    e.preventDefault();
    // Form submission logic
  };

  return (
    <form onSubmit={handleSubmit}>
      <input type="text" value={name} onChange={(e) => setName(e.target.value)} placeholder="Name" />
      <input type="email" value={email} onChange={(e) => setEmail(e.target.value)} placeholder="Email" />
      <button type="submit">Submit</button>
    </form>
  );
}

```

1. **Error Boundaries with componentDidCatch:**

```jsx
javascriptCopy code
class ErrorBoundary extends React.Component {
  constructor(props) {
    super(props);
    this.state = { hasError: false };
  }

  componentDidCatch(error, errorInfo) {
    console.error('Error:', error);
    console.error('Error Info:', errorInfo);
    this.setState({ hasError: true });
  }

  render() {
    if (this.state.hasError) {
      return <div>Something went wrong.</div>;
    }
    return this.props.children;
  }
}

<ErrorBoundary>
  <MyComponent />
</ErrorBoundary>

```

1. **React Context with Redux-like State Management:**

```jsx
javascriptCopy code
import React, { createContext, useContext, useReducer } from 'react';

const MyContext = createContext();

const initialState = { count: 0 };

function reducer(state, action) {
  switch (action.type) {
    case 'INCREMENT':
      return { count: state.count + 1 };
    case 'DECREMENT':
      return { count: state.count - 1 };
    default:
      return state;
  }
}

function MyComponent() {
  const { state, dispatch } = useContext(MyContext);

  return (
    <div>
      <p>Count: {state.count}</p>
      <button onClick={() => dispatch({ type: 'INCREMENT' })}>Increment</button>
      <button onClick={() => dispatch({ type: 'DECREMENT' })}>Decrement</button>
    </div>
  );
}

function App() {
  const [state, dispatch] = useReducer(reducer, initialState);

  return (
    <MyContext.Provider value={{ state, dispatch }}>
      <MyComponent />
    </MyContext.Provider>
  );
}

```

1. **Server-side Rendering (SSR) with React and Next.js:**

```jsx
javascriptCopy code
// pages/index.js
import React from 'react';

function Home() {
  return <div>Welcome to the home page!</div>;
}

export default Home;

```

1. **React Portals for Modal Dialogs or Modals:**

```jsx
javascriptCopy code
import React from 'react';
import ReactDOM from 'react-dom';

function Modal({ children }) {
  return ReactDOM.createPortal(
    children,
    document.getElementById('modal-root')
  );
}

function App() {
  return (
    <div>
      <h1>My App</h1>
      <Modal>
        <div>Modal Content</div>
      </Modal>
    </div>
  );
}

ReactDOM.render(<App />, document.getElementById('root'));

```

1. **React Testing Library for Unit Testing React Components:**

```jsx
javascriptCopy code
import React from 'react';
import { render, screen } from '@testing-library/react';
import MyComponent from './MyComponent';

test('renders MyComponent correctly', () => {
  render(<MyComponent />);
  const element = screen.getByText(/Hello, World!/i);
  expect(element).toBeInTheDocument();
});

```

1. **React Hooks for Context with useReducer:**

```jsx
javascriptCopy code
import React, { createContext, useContext, useReducer } from 'react';

const MyContext = createContext();

const initialState = { count: 0 };

function reducer(state, action) {
  switch (action.type) {
    case 'INCREMENT':
      return { count: state.count + 1 };
    case 'DECREMENT':
      return { count: state.count - 1 };
    default:
      return state;
  }
}

function MyComponent() {
  const { state, dispatch } = useContext(MyContext);

  return (
    <div>
      <p>Count: {state.count}</p>
      <button onClick={() => dispatch({ type: 'INCREMENT' })}>Increment</button>
      <button onClick={() => dispatch({ type: 'DECREMENT' })}>Decrement</button>
    </div>
  );
}

function App() {
  const [state, dispatch] = useReducer(reducer, initialState);

  return (
    <MyContext.Provider value={{ state, dispatch }}>
      <MyComponent />
    </MyContext.Provider>
  );
}

```

1. **React Performance Optimization with memo:**

```jsx
javascriptCopy code
import React, { memo } from 'react';

const MyComponent = memo(({ value }) => {
  return <div>{value}</div>;
});

```

1. **React.lazy and Suspense for Code Splitting:**

```jsx
javascriptCopy code
import React, { lazy, Suspense } from 'react';

const MyComponent = lazy(() => import('./MyComponent'));

function App() {
  return (
    <Suspense fallback={<div>Loading...</div>}>
      <MyComponent />
    </Suspense>
  );
}

```

1. **React Hooks for Debouncing and Throttling:**

```jsx
javascriptCopy code
import React, { useState, useEffect } from 'react';

function DebouncedInput() {
  const [value, setValue] = useState('');

  useEffect(() => {
    const timer = setTimeout(() => {
      // Perform action after debounce time
    }, 500);

    return () => clearTimeout(timer);
  }, [value]);

  return (
    <input
      type="text"
      value={value}
      onChange={(e) => setValue(e.target.value)}
    />
  );
}

```

1. **React Fragments with Short Syntax:**

```jsx
javascriptCopy code
import React from 'react';

function MyComponent() {
  return (
    <>
      <h1>Title</h1>
      <p>Content</p>
    </>
  );
}

```

1. **React.memo with Custom Equality Function:**

```jsx
javascriptCopy code
import React, { memo } from 'react';

const MyComponent = memo(
  ({ value }) => {
    return <div>{value}</div>;
  },
  (prevProps, nextProps) => {
    // Custom equality check logic
    return prevProps.value === nextProps.value;
  }
);

```

1. **React Testing Library with user Event:**

```jsx
javascriptCopy code
import React from 'react';
import { render, screen } from '@testing-library/react';
import userEvent from '@testing-library/user-event';
import MyComponent from './MyComponent';

test('handles button click correctly', () => {
  render(<MyComponent />);
  const button = screen.getByRole('button');
  userEvent.click(button);
  expect(screen.getByText('Clicked!')).toBeInTheDocument();
});

```
