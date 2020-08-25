# Guidelines for Contributing

## What to Know Before Getting Started

TODO

<!-- Basic HTML, CSS, JS, Git

Bootstrap, React

Gatsby, ... -->

## Workflow

TODO

## Style Guide

TODO

### Code Style

Most of the coding style would be taken care of by [Prettier](https://prettier.io/). Prettier is a code formatter with built-in support for HTML, CSS, JavaScript and JSX (and more!).

As an example, running Prettier on the following code:
```js
function Hello() {
  return <div><h1>Hello</h1><p>This is supposed to be a very long paragraph of text. It contains a link to <a href="">some other page</a>, and an <em>emphasized piece of text</em></p><p>There's a second paragraph too!</p></div>
}
```
may produce an output like this:
```js
function Hello() {
  return (
    <div>
      <h1>Hello</h1>
      <p>
        This is supposed to be a very long paragraph of text. It contains a link
        to <a href="">some other page</a>, and an{" "}
        <em>emphasized piece of text</em>
      </p>
      <p>There's a second paragraph too!</p>
    </div>
  )
}
```

You can [try Prettier out in its playground](https://prettier.io/playground/).

<!-- TODO: Mention here about the precommit hook? -->

There are some things that Prettier would not format however. For example, variable names. In JavaScript, write your identifiers (variable names, function names, etc.) in `camelCase`. React component names and class names should be in `PascalCase`.

So, write:
```js
let name = "...";

const newPosts = [];

function arraySum() {
  // ...
}

function ButtonGroup() {
  return <div>{/* ... */}</div>
}
```
but not:
```js
let Name = "...";

const new_posts = [];

function Arraysum() {
  // ...
}

function Button_Group() {
  return <div>{/* ... */}</div>
}
```

### Comments

<!-- TODO: Why comment? -->

When you write functions, React components etc., it is helpful to document them. Use [JSDoc](https://jsdoc.app/) comments for that. JSDoc is a tool for documenting JavaScript code. When documenting a function, for example, make sure you describe enough of it so that someone who hasn't looked at the function's implementation can use it with ease.

Now, how do you use JSDoc comments?

#### Simple JSDoc example

Let's say you wrote a function that returns the sum of an array of numbers:
```js
function arraySum(array) {
  let sum = 0
  for (const num of array) {
    sum += num
  }
  return sum
}
```
You can easily document this like so:
```js
/** Return the sum of an array of numbers. */
function arraySum(array) {
  // ...
}
```
Anyone reading this should understand what the function does, without seeing its body.

You may go further by describing the parameters and return value using JSDoc tags:
```js
/**
 * Return the sum of an array of numbers.
 * @param {number[]} array
 * @return {number}
 */
function arraySum(array) {
  // ...
}
```
Now this says that the function expects the `array` parameter to be an array of numbers, and that the function returns a number. The types are specified in the curly braces.

#### Documenting a React component

Let's say you have a `Button` component that renders a Bootstrap button:
```js
function Button(props) {
  const {
    color = "primary",
    outline,
    size,
    className = "",
    ...rest
  } = props;

  const colorClass = `btn-${outline ? "outline-" : ""}${color}`
  const sizeClass = size ? `btn-${size}` : ""
  const classes = `${className} btn ${colorClass} ${sizeClass}`

  return <button className={classes} {...rest} />
}
```

The default color for the rendered button is `"primary"`. Assume that the `color` prop can take one of `"primary"`, `"success"` and `"danger"`, and the `size` prop can take one of `"sm"` and `"lg"`. Then you might use `<Button />` like so:
```js
// 1. A button with the default color (primary) and size
<Button>Click!</Button>
// 2. A large success button
<Button color="success" size="lg">Click!</Button>
// 3. An outline danger button
<Button color="danger" outline>Click!</Button>
```

So, how do you document this? The component takes a single argument, the `props` object. That gives the following:
```js
/**
 * A button component.
 *
 * @param {object} props
 */
function Button(props) {
  // ...
}
```
The next thing to do is to document the properties of the `props` object. Here's how to do that in JSDoc:
```js
/**
 * A button component.
 *
 * @param {object} props
 * @param {"primary"|"success"|"danger"} props.color
 * @param {boolean} props.outline
 * @param {"sm"|"lg"} props.size
 */
function Button(props) {
  // ...
}
```
Notice that each property of `props` is prefixed with "`props.`". Also notice how the expected values of `props.color` and `props.size` are specified.

You can add notes to the properties like this:
```js
/**
 * A button component.
 *
 * @param {object} props
 * @param {"primary"|"success"|"danger"} props.color - The color of the button. Defaults to "primary"
 * @param {boolean} props.outline - Determines whether the button is an outline button or not.
 * @param {"sm"|"lg"} props.size - The size of the button. If absent, the button takes its normal size
 */
function Button(props) {
  // ...
}
```

Finally, you can give examples on using the component:

```js
/**
 * A button component.
 *
 * @param {object} props
 * @param {"primary"|"success"|"danger"} props.color - The color of the button. Defaults to "primary"
 * @param {boolean} props.outline - Determines whether the button is an outline button or not.
 * @param {"sm"|"lg"} props.size - The size of the button. If absent, the button takes its normal size
 * @param {string|function} props.as - The HTML element or React component to render as. Defaults to "button"
 *
 * @example
 * // A button with the default color (primary) and size
 * <Button>Click!</Button>
 * @example
 * // A large success button
 * <Button color="success" size="lg">Click!</Button>
 * @example
 * // An outline danger button
 * <Button color="danger" outline>Click!</Button>
 */
function Button(props) {
  // ...
}
```

<!--

TODO

JSDoc isn't just for functions/classes.

Mention Tip. Editors + JSDoc

More on JSDoc with React https://www.javascriptjanuary.com/blog/autocomplete-in-react-using-jsdoc

Mention that the stuff here about JSDoc with React isn't specific to React

Mention the tags and link to JSDoc's reference site

-->

### Directory structure

TODO

### Commit messages

TODO