# Guidelines for Contributing

TODO

<!-- Intro talk -->

## Table of Contents

- [What to Know Before Getting Started](#what-to-know-before-getting-started)
- [Workflow](#workflow)
- [Style Guide](#style-guide)
  - [Code Style](#code-style)
  - [Comments](#comments)
  - [Folder structure](#folder-structure)
  - [Commit messages](#commit-messages)

## What to Know Before Getting Started

TODO

<!-- Basic HTML, CSS, JS, Git

Bootstrap, React

Gatsby, ... -->

## Workflow

TODO

## Style Guide

The style guide describes how your code, commit messages, etc. should be written. The goal of the style guide is to ensure readability and consistency. You should try to follow the guide as much as you can. Note however that the guidelines are not hard-and-fast rules.

<!-- Style Guide for CSS is missing -->

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
const new_posts = [];

function Arraysum() {
  // ...
}

function Button_Group() {
  return <div>{/* ... */}</div>
}
```

### Comments

Comments help everyone understand your code. Make sure to use them as much as you can. Try to write in clear, simple language. If you find yourself writing lots of comments to explain a small piece of code, consider rewriting the code. Also, avoid redundant comments like:

```js
// z is the sum of x and y
const z = x + y
```

<!-- How about the usual comments? Any need to mention them? -->

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

#### Regular comments

It's important to note that JSDoc comments don't necessarily replace the usual JavaScript line comments (`//`). You should use JSDoc comments for interfaces and _not_ implementations. Use the regular comments elsewhere.

For example, to describe the internals of the `Button` component from above, you could do:

```js
/**
 * ...
 */
function Button(props) {
  const {
    color = "primary",
    outline,
    size,
    className = "",
    ...rest
  } = props;

  // Create the button color class from the outline and color props.
  const colorClass = `btn-${outline ? "outline-" : ""}${color}`
  // Add the size suffix if the size is given
  const sizeClass = size ? `btn-${size}` : ""
  // Combine the button classes with the custom ones.
  const classes = `${className} btn ${colorClass} ${sizeClass}`

  return <button className={classes} {...rest} />
}
```

### Folder structure

#### How to name files and folders?

The files and folders of the Gatsby default starter (which this project is based on) are written `like-this` (i.e. lowercase letters and hyphens), so you should follow that.

<!-- TODO: What's in the project? -->

### Commit messages

A single-line commit message should suffice for commits with small changes. For example:
```sh
git commit -m "Rename abc.js to xyz.js"
```

Commits with larger changes may require longer messages. In such a case, you can do:
```sh
git commit -m "Create a Slider component

Long text here describing why you created a Slider component
and whatever else is important to know about it.
"
```

In either case, keep the first line of the message _reasonably_ short. You can avoid some unnecessary pronouns. For example, instead of
```sh
git commit -m "I increased the margin-bottom on the main heading"
```
do
```sh
git commit -m "Increase the margin-bottom on the main heading"
```

<!-- TODO: Stuff about semantics and accessibility? -->