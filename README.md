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
 
 ## Customizing the virtual keyboard
I recommend you first read through the official docs, which offer pretty clear examples of how to customize the keyboard. The only difficulty I faced was determining within which css selectors I should assign values to the css variables. The docs specify that: 

> To customize the appearance of the virtual keyboard panel set the following CSS variables on a selector that applies to the container of the virtual keyboard panel, which is the <body> element by default:
> ```css
 > body {
 > --keyboard-zindex: 3000;
> }
 >```
 
However this doesn't seem to work in react. In the end I found the classnames of the virtualKeyboard's layers and assigned values to css variables there directly:
 
 ```css
 body {
  /* this has no effect */
  /* --keyboard-background: rgb(23, 23, 200); */
}

 /* this worked */
.ML__keyboard--plate {
  --keyboard-background: rgb(23, 23, 23);
  --keyboard-text: rgb(230, 230, 230);
  --keycap-background: rgb(40, 40, 40);
  --keycap-text: rgb(230, 230, 230);
  --keycap-background-border: rgb(20,20,20)
  --keycap-background-active: rgb(30,30,30)
}

.action {
  --keycap-modifier-background: rgb(100,100,100)
}

.keycap {
  --keycap-text-active: rgb(23, 230, 23);
  --keycap-background-active: rgb(100,100,100)
}
 
 ```

 The rest was of the instructions in the docs worked perfectly, and the sample code above should be pretty self explanatory. 
 
 
 
 
 
 
 
 
 
 
