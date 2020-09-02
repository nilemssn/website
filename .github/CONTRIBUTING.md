# Guidelines for Contributing

Bismillah ar-Rahman ar-Raheem.

The following guidelines should help you get started contributing to the Nile MSSN website.To keep this repo organised and make contibuting easier here are a set of helpful links and information along with guidlines that will hopefully make help this happen.
These guidelines area work in progress and may be subject to change.

## Table of Contents

- [What to Know Before Getting Started](#what-to-know-before-getting-started)
- [Set up the Project on Your Computer](#set-up-the-project-on-your-computer)
- [Workflow](#workflow)
- [Style Guide](#style-guide)
  - [Code Style](#code-style)
  - [Comments](#comments)
  - [Folder Structure](#folder-structure)
  - [Commit Messages](#commit-messages)
  - [Miscellaneous](#miscellaneous)

## What to Know Before Getting Started

TODO

<!--

Mention the tech stack of the project first (including Netlify).

Then mention what you need to know and assumptions made in this document.

 TODO: Basic HTML, CSS, JS, Terminal

Bootstrap, React

Gatsby, Git ...

Add Git Handbook (https://guides.github.com/introduction/git-handbook/), GitHub guide here perhaps

-->

## Set up the Project on Your Computer

1. Install [Node.js](https://nodejs.org/). It comes with a JavaScript package manager called [NPM](https://www.npmjs.com/). (Also, install [Git](https://git-scm.com/) if you haven't already.)

2. Open your terminal and navigate to a folder where you would like to download the repository. Next, type the following command to install the Gatsby <abbr title="Command-Line Interface">CLI</abbr>. The Gatsby CLI lets you develop Gatsby sites.

   ```shell
   npm install -g gatsby-cli
   ```

3. Run the following Git command to get a local copy of this repository.

   ```shell
   git clone https://github.com/nilemssn/website.git
   ```

4. You should now find a new "website" folder. Navigate into it and install its dependencies. Note that this might take a while and use over 100MB of data.

   ```shell
   cd website/ && npm install
   ```

5. Start the development server with the following command.

   ```shell
   gatsby develop
   ```

6. The site should now be running at http://localhost:8000. You'll also see a second link: http://localhost:8000/___graphql. This is a tool you can use to experiment with querying data. Learn more about using this tool in the [Gatsby GraphiQL tutorial](https://www.gatsbyjs.com/tutorial/part-five/#introducing-graphiql).

7. Open the "website" folder in your code editor of choice and start editing the files. Save your changes and the browser will update in real time!

## Workflow

A typical workflow might be something like the following.

1. Look for [an open issue](https://github.com/nilemssn/website/issues) on the GitHub repository (aka the "remote"), or [create one](https://docs.github.com/en/github/managing-your-work-on-github/creating-an-issue). You can use issues to discuss changes to the site with the team.

2. Open your terminal, navigate to the local repository and pull in changes from the `master` branch. The `master` branch is the default branch and contains the source code for the website ready to be deployed. If you're not already in the `master` branch, run the following to switch to it:
   ```shell
   git checkout master
   ```
   Then run the following to update your `master` branch with the remote's.
   ```shell
   git pull
   ```

3. Before you start working on the code, you need to create a branch from the `master` branch. You can think of a branch as an environment where you can work separately, and later merge with other branches. The code below would create a new branch `layout` and switch to it. You can give your branch a name that identifies what you want to work on.
   ```shell
   git checkout -b layout
   ```

4. Now you can start working on the site in your editor! As you work, you should regularly tell Git to "save" your changes. To do this, first, you'll have to "add" your changes:
   ```shell
   git add .
   ```
   (Note the space between add and the dot.) This informs Git of your new changes.
   Next, you'll commit your changes to create a "checkpoint". Your commits should have a message describing the changes you made:
   ```shell
   git commit -m "Make the navbar responsive"
   ```
   See the [commit messages style guide section](#commit-messages) on writing good commit messages. How often should you commit? It's up to you! A simple rule is to [commit whenever you create something that you're satisfied with](https://softwareengineering.stackexchange.com/a/74893), or [something you would like to go back to](https://softwareengineering.stackexchange.com/a/83842). Remember, a commit is like a checkpoint.

5. When you're ready to share your work, push it to the remote. If you're pushing a new branch (in this case `layout`) to the remote for the first time, do
   ```shell
   git push -u origin layout
   ```
   If it's not the first time you're pushing the branch to the remote, then this suffices:
   ```shell
   git push
   ```
   (Note: You don't have to de done with your work before pushing.)

6. Share your changes with the team! Go to the GitHub website and [create a pull request](https://docs.github.com/en/github/collaborating-with-issues-and-pull-requests/creating-a-pull-request#creating-the-pull-request). This allows you to discuss your changes with the team and request reviews. When your changes are approved, [merge your pull request](https://docs.github.com/en/github/collaborating-with-issues-and-pull-requests/merging-a-pull-request#merging-a-pull-request-on-github).

7. You can return to your terminal and delete your branch. Switch to a different branch:
   ```shell
   git checkout master
   ```
   Then delete the branch you created earlier (`layout` in this case):
   ```shell
   git branch -d layout
   ```
   (Note that the remote branch would be deleted automatically when you merged the pull request.) That's it!

<!--

(Use this to explain working with Git and GitHub)

Look for an issue, or create one

Pull the master

Checkout a new branch

Work on the issue

Stage changes and commit

Work more, commit more

Push the new branch

Create PR on GitHub (and all the fancy stuff) (Mention Skip CI, and Netlify)

Merge PR

(Documenting changes to package.json)

 -->

## Style Guide

The style guide describes how your code, commit messages, etc. should be written. The goal of the style guide is to ensure readability and consistency. You should try to follow the guide as much as you can. Note however that the guidelines are not hard-and-fast rules.

<!-- TODO: Style Guide for CSS is missing -->

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

There are some things that Prettier would not fix however. For example, variable names. In JavaScript, write your identifiers (variable names, function names, etc.) in `camelCase`. React component names and class names should be in `PascalCase`. It goes without saying that identifiers should describe what they identify.

So, write:
```js
let name = "Musty";

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
// What does "x" identify?
let x = "Musty";

// No underscore should be in the middle of variable name
const new_posts = [];

// Function name should not start with capital letter
function Arraysum() {
  // ...
}

// React Component name should not contain underscore
function Button_Group() {
  return <div>{/* ... */}</div>
}
```

### Comments

Comments help everyone understand your code. Make sure to use them where appropriate. Try to write in clear, simple language. If you find yourself writing lots of comments to explain a small piece of code, consider rewriting the code. Also, avoid redundant comments like:

```js
// z is the sum of x and y
const z = x + y
```

When you write functions, React components etc., it is helpful to document them. Use [JSDoc](https://jsdoc.app/) comments for that. JSDoc is a tool for documenting JavaScript code. When documenting a function, for example, make sure you describe enough of it so that someone who hasn't looked at the function's implementation can use it with ease.

Now, how do you use JSDoc comments?

#### Simple JSDoc example

Let's say you wrote a function that returns the sum of an array of numbers:
```js
function sum(numbers) {
  let result = 0
  for (const num of numbers) {
    result += num
  }
  return result
}
```
You can easily document this like so:
```js
/** Return the sum of an array of numbers. */
function sum(numbers) {
  // ...
}
```
Anyone reading this should understand what the function does, without seeing its body.

Though unnecessary for this function, you may go further by describing the parameters and return value using [JSDoc tags](https://jsdoc.app/#block-tags):
```js
/**
 * Return the sum of an array of numbers.
 * @param {number[]} numbers
 * @return {number}
 */
function sum(numbers) {
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

### Folder Structure

#### How to name files and folders?

The files and folders of the Gatsby default starter (which this project is based on) are written `like-this` (i.e. lowercase letters and hyphens), so you should follow that.

<!-- TODO: What's in the project? -->

### Commit Messages

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

In either case, keep the first line of the message reasonably short. You can avoid some unnecessary pronouns. For example, instead of
```sh
git commit -m "I increased the margin-bottom on the main heading"
```
do
```sh
git commit -m "Increase the margin-bottom on the main heading"
```

### Miscellaneous

#### Links

[Gatsby recommends using its `Link` component for links to pages within a site](https://www.gatsbyjs.com/docs/gatsby-link/). The usual HTML `<a>` tag should be used for external links. For example:

```js
// Internal link
<Link to="/about/">...</Link>

// External link
<a href="https://twitter.com/nilemssn">...</a>
```

You need to import the `Link` component to use it:

```js
import { Link } from "gatsby"
```

Certain React Bootstrap components render as links. For example, the following renders an `<a>` element styled as a button:

```js
<Button href="/about/">...</Button>
```

The React Bootstrap components have an `as` prop that you can use to specify which React component or HTML element to render as. So, the example above with Gatsby's `Link` becomes:

```js
<Button as={Link} to="/about/">...</Button>
```
