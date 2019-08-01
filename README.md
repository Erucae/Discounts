## Collenda Contents
- [Intro](#Intro)
	- [Redux](#redux-reducers)
	- [Data Flow](#data-flow)
	- [Eslint](#eslint)
	- [Flow](#flow)
	- [Routing and lazy loading](#routing-lazy-load)
	- [Project structure](#project-structure)
	- [Material-ui and styled components](#material-ui-styled)
	- [API Calls](#api-calls)
	- [Auth](#auth)
	- [Theme](#theme)
- [Requirements](#Requirements)
- [Installation](#Installation)
- [Documentation](#Documentation)
	- [Form Controls](src/components/formControls/FormControlsDocumentation.md)
	- [Components](#components)
        - [Search Box](#search-box)
        - [List](#list)
        - [Loader](#loader)
        - [Tab Component](#tab-component)
        - [Accordion Component](#tab-component)
        - [Step Component](#step-component)
    - [Frameset](src/views/frameBox/readme.md)
    - [Middleware](src/middlewares/readme.md)

<a name="Intro"></a>
## Intro


<a name="redux-reducers"></a>
## redux - action, reducers
[redux](https://redux.js.org/) as storage represent application state

1. component fire actions

2. reducers check actions and modify storage

3. on storage change components are rerendered



<a name="data-flow"></a>
##### Video about unidirectional Data Flow and why we should use it
[![About Unidirectional Data Flow](http://img.youtube.com/vi/i__969noyAM/0.jpg)](http://www.youtube.com/watch?v=i__969noyAM)



<a name="eslint"></a>
## eslint
[eslint](https://eslint.org/) is used for basic style checking



<a name="flow"></a>
## flow
[flow](https://flow.org/en/) is used as static style checker

examples:
```
// @flow
function square(n: number): number {
  return n * n;
}
```
`//@flow` should be added for each file which should be checked by flow

`n: number` inform flow about type of `n`

js class example:
```
class FLowExample<{n: number}> {}
``` 




<a name="routing-lazy-load"></a>
## routing and lazy loading
Default react functions and component are used for lazy loading and react-router for routing
```
import React, { Component, Suspense, lazy } from 'react';
import { Route, Switch } from 'react-router-dom';

const Dashboard = lazy(() => import('../views/dashboard/dashboard'));

class Example extends Component {
  render() {
    return (
        <Suspense fallback={<LoadingBox />}>
          <Switch>
            <Route exact path="/" component={Dashboard}/>
            <Route exact path="/dynamic/:template/:objectType/:objectId" component={DynamicPage}/>
          </Switch>
        </Suspense>
    );
  }
}
```



<a name="project-structure"></a>
## Project structure
* /app - basic app code - storage, middleware, config, routes, auth functions
* /components - all UI components we use (containers, controls etc.)
   * /components/styled - custom styling (not regular material ui) is here
* /jsxParse - everything about parsing generated pages
* /views - applications pages
   * /view/example - example page dir
   * /view/example/example.js - example page logic
   * /view/example/exampleTemplate.js - example page template rendered by component in example.js
   * /view/example/exampleReducer.js - example page reducer




<a name="material-ui-styled"></a>
## material-ui and styled components
[material-ui](https://material-ui.com) is used as UI framework

[styled components](https://www.styled-components.com/) is used for custom styling (no css files in project)

styled components examples:

```$xslt
// Static object
const Box = styled.div({
  background: 'palevioletred',
  height: '50px',
  width: '50px'
});

// Adapting based on props
const PropsBox = styled.div(props => ({
  background: props.background,
  height: '50px',
  width: '50px'
}));

render(
  <div>
    <Box />
    <PropsBox background="blue" />
  </div>
);
```


<a name="api-calls"></a>
## API calls
REST api is user for backed

All API requests are handler by
[redux-rest-middleware](https://github.com/rednetio/redux-rest-middleware)

To make api call - component should fire event with `meta` property:
```$xslt
const listTodos = () => ({
  type: 'LIST_TODOS',
  meta: {
    rest: '/todos',
  },
});
```

<a name="auth"></a>
## auth
[JWT](https://jwt.io/) is used for authorization

auth middleware store JWT token in locaStorage remove it when token is expired


<a name="theme"></a>
## theme
custom theme parameters is stored in `src/public/config` 
```
palette: {
      type: "light",
      primary: {
        light: '#42a5f5',
        main: '#0d1d41', // used as background-color for top Navigation, primary Buttons, main right side Menu, DatePicker header and Primary icons
        dark: '#24ce7b', // used as background-color for :hover primary Buttons
        contrastText: '#fff', // color for text in top Navigation, primary Buttons, main right side Menu items text
      },
      secondary: {
        light: '#66bb6a',
        main: '#388e3c', // used as background-color for secondary Buttons, color for Loader
        dark: '#2e7d32', // used as background-color for :hover secondary Buttons
        contrastText: '#fff', // color for text in secondary Buttons
      },

      background: {
        default: '#f1f5f6',// used as page background-color
        paper: "#ffffff", // used as background-color for content blocks in application
      },

      action: {
        active: '#0d1d41',
        hover: '#24ce7b', // used as :hover background-color for items in main right side Menu
        hoverOpacity: "0.1",
        selected: '#37D287', // used as background-color for active items in main right side Menu
      }
```

all parameters can be redefined there, or few other themes can be added.

Parameters are set:
* `palette` - colors for theme elements:
    *  `type` - default type of theme ("dark" or "light")
    *  `background` - default for all application and paper inside Paper component 
    *  `primary` - colors for primary elements (headers, checkboxes and buttons)
    *  `secondary` - colors for secondary elements (headers, checkboxes and buttons)
    *  `action` - styles for menu items, links and buttons on Hover, Active

More details about using MAtherial UI Theme can be found here [material-ui-themes](https://material-ui.com/customization/themes/) 



<a name="Requirements"></a>
## Requirements
NodeJS, yarn


<a name="Installation"></a>
## Installation

Go to project path
run `npm install`
run `yarn && yarn start`



<a name="Documentation"></a>
## Documentation


## [Form Controls](src/components/formControls/FormControlsDocumentation.md)

<a name="components"></a>
## Components

<a name="search-box"></a>
### [Search Box](src/components/SearchBoxComponent/readme.md)

<a name="list"></a>
### [List](src/components/ListComponent/readme.md)

<a name="loader"></a>
### [Loader](src/components/LoadingBox/readme.md)

<a name="tab-component"></a>
### [Tab Component](src/components/TabComponent/readme.md)

<a name="accordion-component"></a>
### [Accordion Component](src/components/AccordionComponent/AccordionComponent.md)

<a name="step-component"></a>
### [Step Component](src/components/StepComponent/readme.md)

## [Frameset](src/views/frameBox/readme.md)



