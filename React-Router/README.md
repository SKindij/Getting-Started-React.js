## 📚 React Router

### <a name="introduction"></a>📖 Introduction to React Router

&emsp;In a single-page application (SPA), all the necessary HTML, CSS, and JavaScript are loaded initially, and subsequent interactions with the application are handled dynamically without requiring full page reloads.\
&emsp;Routing is essential in SPAs to handle different views or pages within the application without actually navigating to a new HTML page.

&emsp;React Router is a library that allows you to add routing functionality to your React applications. 
It helps to create URLs for different pages or components in your application, allowing the user to navigate between them using the browser's address bar or links.

React Router offers several features and benefits, including:
+ Component-based routing: 
  - _you can associate specific components with different routes, making it easy to render appropriate component based on current URL._
+ Nested routing: 
  - _it allows you to nest routes within each other, creating hierarchical structure for your application's views._
+ Programmatic navigation: 
  - _you can programmatically navigate between routes, either in response to user actions or as result of certain conditions being met._
+ URL parameter handling: 
  - _it provides built-in support for extracting and utilizing URL parameters in your components._
+ Query parameter handling: 
  - _it allows you to parse and retrieve query parameters from the URL, enabling more dynamic behavior in your application._
+ Route guards and authentication: 
  - _features for implementing route guards, allowing you to control access to certain routes based on authentication or other conditions._
 
&emsp;React Router v6, the latest major version, introduces a more intuitive and simplified API compared to previous versions. It provides improved nesting, route matching, and streamlined navigation methods.

> To install the React Router:\
> ```bash
>  npm install react-router-dom \
>    localforage \
>    match-sorter \
>    sort-by
> ```
> >  - _package, which provides the necessary components and functionality for routing_
> >  - _JavaScript library that simplifies usage of web browser's IndexedDB API for storing data;_
> >  - _It provides simple API for storing and retrieving data in a key-value format._
> >  - _utility for sorting and filtering arrays or collections based on given search query_
> >  - _package for sorting array of objects based on given property or properties;_


### <a name="setting-routes"></a>📖 Setting up Routes

&emsp; Once installed, you can import necessary components from react-router-dom and define your routes. 

> _Let's say we have **pages** folder with attached files. It contains **index.js** file, through which we can organize general export of our pages._
> > ```javascript
> >  import MainPage from "./MainPage";
> >  import ResidentialGates from "./ResidentialGates";
> >  import IndustrialGates from "./IndustrialGates";
> >  import Page404 from './404';
> > 
> > export {MainPage, ResidentialGates, IndustrialGates, Page404};
> > ```
> _Here's an example of setting up routes:_
> > ```javascript
> >  import React from 'react';
> >  import { BrowserRouter as Router, Route, Switch } from 'react-router-dom';
> >  
> >  import AppHeader from "../appHeader/AppHeader";
> >  import { MainPage, ResidentialGates, IndustrialGates, Page404 } from '../pages';
> >    
> >  function App() {
> >    return (
> >      <Router>
> >        <div className="app">
> >          <AppHeader />
> >          <main>
> >            <Switch >
> >            {/* ensures that only one route is rendered at a time */}  
> >              <Route exact path="/" component={MainPage} />
> >              <Route path="/residential" component={ResidentialGates} />
> >              <Route path="/industrial" component={IndustrialGates} />
> >              <Route path="*" component={Page404} />
> >            </Switch>
> >          </main>
> >        </div>
> >      </Router>
> >    );
> >  }
> >  
> >  export default App;
> > ```

&emsp; `<Route>` component has several configuration options. Here are some commonly used ones:
+ **path**: _specifies URL pattern to match for route;_
+ **component**: _specifies component to render for matched route;_
+ **exact**: _matches route exactly (without it, partial matches will also render component);_
+ **render**: _allows rendering inline function as component instead of separate component file;_
+ **children**: _similar to render, but always renders, regardless of URL match._

&emsp; `useParams` hook allows you to access the dynamic parameters from the URL. 

> _For example, if you have route like `/products/:id`, you can use useParams to access id parameter:_
> > ```javascript
> >  // Product component retrieves productId parameter from URL using useParams hook
> >  import React from 'react';
> >  import { useParams } from 'react-router-dom';
> >  
> >  function Product() {
> >    const { productId } = useParams();
> >    // Fetch product details based on productId or perform any other logic
> >    return <div>Product ID: {productId}</div>;
> >  }
> >  
> >  export default Product;
> > ```
> _To set up the route for products, you can add a new <Route> component in your route configuration:_
> > ```javascript
> >  <Route path="/products/:productId" component={ Product } />
> >  // when you access URL like /products/123, Product component will be rendered, and 
> >  // productId parameter will be available for use through useParams hook
> > ```















