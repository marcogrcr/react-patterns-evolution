# React patterns evolution

The following repository showcases how [`react`](https://reactjs.org/) application development patterns have evolved over time. `react v16.8` is backwards compatible with all of these patterns, so you can mix and match them within the same application. In other words, if you want to migrate from one pattern to another, you don't have to do an all-or-nothing upgrade, you can gradually migrate parts of the application.

Which pattern to choose depends on your application specific needs, and whether the added overhead of a pattern (e.g. [`redux`](https://redux.js.org/)) provides substantial benefits that justify using the pattern.

## Example application

The example application consinsts of two components:

- `Counter`: This component displays two buttons (`+`/`-`) which increase/decrease a counter and displays the current value on screen.
- `Textbox`: This component displays a textbox which allows the user to type on it and displays the current value on screen. When side-effects are possible (i.e. [class-based components](https://reactjs.org/docs/components-and-props.html#function-and-class-components) with [lifecycle events](https://reactjs.org/docs/state-and-lifecycle.html) and [function-based components](https://reactjs.org/docs/components-and-props.html#function-and-class-components) with [hooks](https://reactjs.org/docs/hooks-intro.html)), it will set the textbox value to `"Done!"` one second after ther component is mounted.

## Patterns

- `1-class-components-with-isolated-state.html`: implements both components using class-based components and no dependencies other than `react`.
- `2-function-components-with-parent-state.html`: the requirements have changed and now the `Textbox` component needs to be hidden when the current count is equal to `1`. Showcases how a component can affect a sibling component in response to events. This implementation moves the common state (i.e. the count value) to the common ancestor, and the value of the state is propagated to children components via props. Mutations to the parent state can be performed by child components by using callbacks passed as props. Because the `Counter` component no longer maintain state (i.e. it only uses props) it's implemented as a function-based component.
- `3-function-components-with-redux.html`: implements the same functionality as `2-function-components-with-parent-state.html` but using `redux`. This results in cleaner components that can now be implemented as function-based components.
- `4-function-components-with-isolated-state-using-hooks.html`: implements the same functionality as `1-class-components-with-isolated-state.html` but with function-based components and `react` hooks. This results in cleaner components.
- `5-function-components-with-redux-using-hooks.html`: implements the same functionality as `3-function-components-with-redux.html` but using `react` hooks provided by `redux`. This removes the complexity of having to `connect` components to the redux store.

## How to run

Download the repository and open any file with a modern web browser. Alternatively, use [jsdelivr](https://www.jsdelivr.com/?docs=gh) to view the files without having to download the repository.
