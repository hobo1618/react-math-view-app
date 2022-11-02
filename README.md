# Example of customized shared keyboard with react-math-view 
This is a simple example of how to implement a shared keyboard with a custom layout using the [react-math-view](https://github.com/arnog/react-mathlive) package in `create-react-app`. (If you are using NextJS, check out [this sample repo](https://github.com/hobo1618/next-math-view-app))

**These instructions assume you've set up a react app with `create-react-app`**

## Shared Virtual Keyboard
 1. install `react-math-view` and `mathlive` packages through npm or equivalent:
 
 ```bash
 npm install mathlive react-math-live
 ```
 
 2. Import `MathView` component and the `makeSharedVirtualKeyboard` function from their respective packages:
 
 ```javascript
import MathView, { MathViewRef } from "react-math-view";
import { makeSharedVirtualKeyboard } from "mathlive";
 ```
 
 3. Create a component in `App.tsx` that wraps two or more `<MathView/>` components:
 
  ```javascript
  ...
  
function App() {

  return (
    <div>
      <MathView/>
      <MathView/>
    </div>
  );
}

export default App;
 ```
 
 4. Add a `useSharedVirtualKeyboard` prop to the `MathView` fields that will share a keyboard and set `virtualKeyboardMode` equal to `onfocus` or `auto`:
 
   ```javascript
  ...
  
function App() {

  return (
    <div>
      <MathView
        useSharedVirtualKeyboard
        virtualKeyboardMode="onfocus"
      />
      <MathView
        useSharedVirtualKeyboard
        virtualKeyboardMode="onfocus"
      />
    </div>
  );
}

export default App;
 ``` 
 
 
