## AJAX

**Asynchronous JavaScript and XML** is an outdated term for doing HTTP requests using JavaScript.

The name comes from the pre-JSON era, when people still used XML to transfer data:

```xml
<employees>
    <employee>
        <name>Vimal</name>
        <email>vjaiswal1987@gmail.com</email>
    </employee>
    <employee>
        <name>Jai</name>
        <email>jai87@gmail.com</email>
    </employee>
</employees>
```

<!-- break -->

## AJAX

Nowadays JSON is used pretty much everywhere, so it should really be called AJAJ. But that doesn't have an "X" in it.

In any case, people still say "AJAX" when they're talking about JavaScript making HTTP requests.

<!-- break -->

## `fetch`

AJAX is a bit antiquated, and is honestly a bit of a hack - if you tried to write code to fetch data with the `XMLHttpRequest` (XHR) object API, you'd quickly want to run away.

For this reason, a new kid on the block has arrived, known simply as `fetch`. It 'promises' to use modern concepts making data fetching a bit easier.

In reality, though, it's still a bit of a pain to work with, and has a number of gotchas. For this reason, we'll be sticking to AJAX, but without the headaches of the XHR object...

<!-- break -->

## Axios

We'll be using [Axios](https://github.com/mzabriskie/axios) for our HTTP requests. It's a handy library that makes doing HTTP requests with JavaScript really easy (especially compared to using XHR).

It's a third party library, which we can install with:

```shell
npm install axios
```

<!-- break -->

## Axios

Axios provides us with methods for the various HTTP methods:

```js
import axios from "axios";

axios.get("/articles");

axios.post("/articles", {
    title: "Hello",
    article: "Blah blah blah",
});

axios.put("/articles/5", {
    title: "Hello Again",
    article: "Blah blah blah!",
});

axios.delete("/articles/4");
```

<!-- break -->

## Asynchronous Programming

When we make a request to the API we don't get a response straight away. Even on a fast connection it can take 100ms or more to get a response. That might not sound like a long time, but for a computer that's ages.

So, JavaScript doesn't just stop doing everything until you get a response back: it keeps on doing whatever else needs to be done until it gets a response.

When we don't get back a response immediately, we need to deal with the response **asynchronously**: in other words, the code that runs when the response comes back could run at any time in the future.

<!-- break -->

## Promises

So, when we make a request with Axios, we can't be given back the response in a variable, as the response doesn't exist yet. What we get back instead is a **Promise**.

A promise is an object containing various methods. All of these methods allow you to be notified when the data is ready (or an error has occurred).

It's easiest to visualise how a promise works via a scenario.

<!-- break -->

Here, a 'consumer' (in our case, the app) is asking the 'originator' (the server) for some data. The server responds with a promise object. Later on, when the data is ready, the server 'fulfils' it.

![Promises work by the client asking the server to perform some asynchronous operation. The server gives a 'promise' object to the client, which the client can then use to be notified when the operation has been completed.](/notes/assets/promises.png)

<small><em>Credit: https://blogs.msdn.microsoft.com/windowsappdev/2013/06/11/all-about-promises-for-windows-store-apps-written-in-javascript/</em></small>

<!-- break -->

## Working with Axios via promises

```js
let promise = axios.get("/articles");

promise.then(response => {
    console.log(response.data);
});
```

Generally we use chaining with Promises:

```js
axios.get("/articles").then(({ data }) => {
    // data was destructured from the response object
    console.log(data);
});
```

**Note:** be aware that there's no guarantee the promises will resolve in the order you wrote them. `GET` requests are generally quicker than other types of request as they generally involve less server activity.

<!-- break -->

## Promises: Errors

Sometimes thing will go wrong: your might sent invalid data, the API server might be down, or any number of other issues.

The `.catch()` method will be called if something goes wrong:

```js
axios.get("/articles")
  .then(response => {
    console.log("Everything has worked");
  })
  .catch(error => {
    console.log("Something has gone wrong");
    console.log(error); // logs an error message
  });
```

It's outside the scope of the course, but you could use the above methods to handle form validation errors and the like.

<!-- break -->

## CRUD

Now that we know how to fetch data, where in our app should the code live to perform the fetching?

Normally, we can split API actions into 4 groups:

- *Create* some new data on the server
- *Retrieve* some existing data from the server
- *Update* some existing data on the server
- *Delete* some existing data on the server

These four operations are so common they are often grouped as an acronym **CRUD**.

<!-- break -->

## React Lifecycle Methods

Three of the four operations listed above (Create, Update and Delete) are normally executed after some user interaction, e.g. filling in a form. Data retrieval, however, can often happen automatically - on app start, or periodically in the background.

To achieve this, we can hook into React **lifecycle methods**. These are methods on React class components, called at particular times in the lifetime of a component.

You've already used two lifecycle methods: `constructor` and `render`. We'll be introducing three new lifecycle methods here.

<!-- break -->

![React lifecycle events](/notes/assets/lifecycle.png)

<small><em>Credit: http://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/</em></small>

<!-- break -->

``` js
class ExampleComponent extends React.Component {
  constructor(props) {
    // Called when the component is first created.
  }

  render() {
    // Should return the JSX to display to the screen.
  }

  componentDidMount() {
    // Component was mounted (attached) to the DOM.
  }

  componentWillUnmount() {
    // Component is about to be unmounted from the DOM.
  }

  componentDidUpdate(oldProps, oldState) {
    // Component was re-rendered.
  }
}
```

<!-- break -->

## Fetching data on screen load

Of these lifecycle events, which is best suited for fetching data when the app is first loaded?

- `render` ❌ this _must_ be a synchronous method, returning JSX to display to the screen (remember, fetching data is always async).
- `componentDidUpdate` ❌ this is run every time the app renders - we only want to fetch data once.
- `componentWillUnmount` ❌ this is run when the screen is about to be hidden/removed from view.
- `constructor` ❌ seems like a good candidate, but we should not perform 'side effects' in a component constructor.

This leaves: `componentDidMount` ✅ this is run once, after the component has mounted. It's the best place for first-run logic such as data fetching.


<!-- break -->

## Key Terms

- **AJAX**: the catch-all term for making HTTP requests using JavaScript
- **Asynchronous**: code that doesn't immediately return a value
- **Promise**: a nice way to deal with asynchronous code
- **Lifecycle methods**: called at certain times in the component lifecycle.

<!-- break -->

## Additional Resources

- [Axios](https://github.com/axios/axios)
- [MDN: Promises](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)
- [Promises: A Technical Look](http://exploringjs.com/es6/ch_promises.html)
- [MDN: `async` functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function)
- [Understanding React Class Component Lifecycle Methods](https://medium.com/@nancydo7/understanding-react-16-4-component-lifecycle-methods-e376710e5157)
