# ES6Rocks Code Style

This is fork from [jQuery Code Style] and follows the same licensing.
[jQuery Code Style]: http://contribute.jquery.org/style-guide/js/

This style guide should be applied to all ES6Rocks code to improve readability and consistency.

## Spacing

- Indentation: 4 spaces, no tabs.
- No whitespace at the end of line or on blank lines.
- Lines should be no longer than 100. There are 2 exceptions:
    - If the line contains a comment with a long URL.
    - If the line contains a regex literal. This prevents having to use the regex constructor which requires otherwise unnecessary string escaping.
- `if`/`else`/`for`/`while`/`try` always have braces and always go on multiple lines.

    ```js
    // Bad
    if ( condition ) return;

    // Good
    if ( condition ) {
        return;
    }
    ```

- Unary special-character operators (e.g., `!`, `++`) must not have space next to their operand.
- Any `,` and `;` must not have preceding space.
- Any `;` used as a statement terminator must be at the end of the line.
- Any `:` after a property name in an object definition must not have preceding space.
- No filler spaces in empty constructs (e.g., `{}`, `[]`, `fn()`)
- New line at the end of each file.

## Objects

Object and array declarations can be made on a single line if they are short. When an object declaration is too long to fit on one line, there must be one property per line.

Property names only need to be quoted if they are reserved words or contain special characters.

```js
// Bad
var map = { ready: 9,
    when: 4, "you are": 15 };

// Good
var map = { ready: 9, when: 4, "you are": 15 };

// Good as well
var map = {
    ready: 9,
    when: 4,
    "you are": 15
};
```

## Filler spaces

- No filler spaces around one-line object and array elements neither function arguments list.
- There should be a single space after each object/array element or function argument, preceded by `,`.
- No filler space between the function name and its arguments parenthesis.
- Unnamed expressions shouldn't have a filler space between `function` and its arguments parenthesis.
- Braces should be preceded by a filler space when opening functions and blocks.

### Examples:
```js
// Bad
foo = [ a, b ];

// Good
foo = [a, b];
```

```js
// Bad
function foo ( a, b, c ) {
    /* magic */
}

// Good
function foo(a, b, c) {
    /* magic */
}
```

```js
// Bad
function (){
    /* magic */
}

// Good
function() {
    /* magic */
}
```

## Multi-line statements

When a statement is too long to fit on one line, line breaks must occur after an operator.

```js
// Bad
html = "<p>The sum of " + a + " and " + b + " plus " + c
    + " is " + (a + b + c);

// Good
html = "<p>The sum of " + a + " and " + b + " plus " + c +
    " is " + (a + b + c);
```

Lines should be broken into logical groups if it improves readability, such as splitting each expression of a ternary operator onto its own line even if both will fit on a single line.

```js
var baz = firstCondition( foo ) && secondCondition( bar ) ?
    qux( foo, bar ) :
    foo;
```

When a conditional is too long to fit on one line, successive lines must be indented one extra level to distinguish them from the body.

```js
if ( firstCondition() && secondCondition() &&
        thirdCondition() ) {
    doStuff();
}
```

## Chained method calls

When a chain of method calls is too long to fit on one line, there must be one call per line, with the first call on a separate line from the object the methods are called on. If the method changes the context, an extra level of indentation must be used.

```js
// Bad
parser.start().then(parser.clean).then(parser.getConfig)
.then(parser.createPublicFolder).then(parser.compileCSS);

// Good
parser
    .start()
    .then(parser.clean)
    .then(parser.getConfig)
    .then(parser.createPublicFolder)
    .then(parser.compileCSS);
```

## Assignments

Assignments in a declaration must be on their own line. Declarations that don't have an assignment must be listed together at the start of the declaration.

Declarations must be on the top of its scope.

```js
// Bad
var foo = true;
var bar = false;
var a;
var b;
var c;

// Good
var a, b, c,
    foo = true,
    bar = false;
```

## Equality

Strict equality checks (`===`) must be used in favor of abstract equality checks (`==`). The _only_ exception is when checking for `undefined` and `null` by way of `null`.

```js
// Check for both undefined and null values, for some important reason.
undefOrNull == null;
```

## Comments

Comments are always preceded by a blank line and must go over the line they refer to.

There must be a single space between the comment token and the comment text.

Multi-line comments - also named block level comments - are only used for file and function headers.

```js
// We need an explicit "bar", because later in the code foo is checked.
var foo = "bar";

// Even long comments that span
// multiple lines use the single
// line comment form.
```

## Quotes

Use single quotes: `'`. Strings that require inner quoting must use single outside and double inside.

## Semicolons

Use them. Never rely on ASI.

## Naming Conventions

Variable and function names should be full words, using camel case with a lowercase first letter. Names should be descriptive but not excessively so. Exceptions are allowed for iterators, such as the use of i to represent the index in a loop.

Constructors need a capital first letter, but modules do not.

## Switch statements

The usage of switch statements is generally discouraged.

## Linting and checking

- Use JSHint to detect errors and potential problems. JSHint options should be stored in a `.jshintrc` file.
- Use JSCS to detect code style issues. JSCS options should be stored in a `.jscsrc` file.
