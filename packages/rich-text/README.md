# Rich Text

This module contains helper functions to convert HTML or a DOM tree into a rich text value and back, and to modify the value with functions that are similar to `String` methods, plus some additional ones for formatting.

## Installation

Install the module

```bash
npm install @wordpress/rich-text
```

_This package assumes that your code will run in an **ES2015+** environment. If you're using an environment that has limited or no support for ES2015+ such as lower versions of IE then using [core-js](https://github.com/zloirock/core-js) or [@babel/polyfill](https://babeljs.io/docs/en/next/babel-polyfill) will add support for these methods. Learn more about it in [Babel docs](https://babeljs.io/docs/en/next/caveats)._

## API

<!-- START TOKEN(Autogenerated API docs) -->

### applyFormat

[src/index.js#L6-L6](src/index.js#L6-L6)

Apply a format object to a Rich Text value from the given `startIndex` to the
given `endIndex`. Indices are retrieved from the selection if none are
provided.

**Parameters**

-   **value** `Object`: Value to modify.
-   **format** `Object`: Format to apply.
-   **startIndex** `[number]`: Start index.
-   **endIndex** `[number]`: End index.

**Returns**

`Object`: A new value with the format applied.

### concat

[src/index.js#L8-L8](src/index.js#L8-L8)

Combine all Rich Text values into one. This is similar to
`String.prototype.concat`.

**Parameters**

-   **values** `...Object`: Objects to combine.

**Returns**

`Object`: A new value combining all given records.

### create

[src/index.js#L9-L9](src/index.js#L9-L9)

Create a RichText value from an `Element` tree (DOM), an HTML string or a
plain text string, with optionally a `Range` object to set the selection. If
called without any input, an empty value will be created. If
`multilineTag` is provided, any content of direct children whose type matches
`multilineTag` will be separated by two newlines. The optional functions can
be used to filter out content.

**Parameters**

-   **$1** `[Object]`: Optional named arguments.
-   **$1.element** `[Element]`: Element to create value from.
-   **$1.text** `[string]`: Text to create value from.
-   **$1.html** `[string]`: HTML to create value from.
-   **$1.range** `[Range]`: Range to create value from.
-   **$1.multilineTag** `[string]`: Multiline tag if the structure is multiline.
-   **$1.multilineWrapperTags** `[Array]`: Tags where lines can be found if nesting is possible.

**Returns**

`Object`: A rich text value.

### getActiveFormat

[src/index.js#L10-L10](src/index.js#L10-L10)

Gets the format object by type at the start of the selection. This can be
used to get e.g. the URL of a link format at the current selection, but also
to check if a format is active at the selection. Returns undefined if there
is no format at the selection.

**Parameters**

-   **value** `Object`: Value to inspect.
-   **formatType** `string`: Format type to look for.

**Returns**

`(Object|undefined)`: Active format object of the specified type, or undefined.

### getTextContent

[src/index.js#L13-L13](src/index.js#L13-L13)

Get the textual content of a Rich Text value. This is similar to
`Element.textContent`.

**Parameters**

-   **value** `Object`: Value to use.

**Returns**

`string`: The text content.

### insert

[src/index.js#L21-L21](src/index.js#L21-L21)

Insert a Rich Text value, an HTML string, or a plain text string, into a
Rich Text value at the given `startIndex`. Any content between `startIndex`
and `endIndex` will be removed. Indices are retrieved from the selection if
none are provided.

**Parameters**

-   **value** `Object`: Value to modify.
-   **valueToInsert** `(Object|string)`: Value to insert.
-   **startIndex** `[number]`: Start index.
-   **endIndex** `[number]`: End index.

**Returns**

`Object`: A new value with the value inserted.

### insertObject

[src/index.js#L24-L24](src/index.js#L24-L24)

Insert a format as an object into a Rich Text value at the given
`startIndex`. Any content between `startIndex` and `endIndex` will be
removed. Indices are retrieved from the selection if none are provided.

**Parameters**

-   **value** `Object`: Value to modify.
-   **formatToInsert** `Object`: Format to insert as object.
-   **startIndex** `[number]`: Start index.
-   **endIndex** `[number]`: End index.

**Returns**

`Object`: A new value with the object inserted.

### isCollapsed

[src/index.js#L14-L14](src/index.js#L14-L14)

Check if the selection of a Rich Text value is collapsed or not. Collapsed
means that no characters are selected, but there is a caret present. If there
is no selection, `undefined` will be returned. This is similar to
`window.getSelection().isCollapsed()`.

**Parameters**

-   **value** `Object`: The rich text value to check.

**Returns**

`(boolean|undefined)`: True if the selection is collapsed, false if not, undefined if there is no selection.

### isEmpty

[src/index.js#L15-L15](src/index.js#L15-L15)

Check if a Rich Text value is Empty, meaning it contains no text or any
objects (such as images).

**Parameters**

-   **value** `Object`: Value to use.

**Returns**

`boolean`: True if the value is empty, false if not.

### join

[src/index.js#L16-L16](src/index.js#L16-L16)

Combine an array of Rich Text values into one, optionally separated by
`separator`, which can be a Rich Text value, HTML string, or plain text
string. This is similar to `Array.prototype.join`.

**Parameters**

-   **values** `Array<Object>`: An array of values to join.
-   **separator** `[(string|Object)]`: Separator string or value.

**Returns**

`Object`: A new combined value.

### registerFormatType

[src/index.js#L17-L17](src/index.js#L17-L17)

Registers a new format provided a unique name and an object defining its
behavior.

**Parameters**

-   **name** `string`: Format name.
-   **settings** `Object`: Format settings.
-   **settings.tagName** `string`: The HTML tag this format will wrap the selection with.
-   **settings.className** `[string]`: A class to match the format.
-   **settings.title** `string`: Name of the format.
-   **settings.edit** `Function`: Should return a component for the user to interact with the new registered format.

**Returns**

`(WPFormat|undefined)`: The format, if it has been successfully registered; otherwise `undefined`.

### remove

[src/index.js#L19-L19](src/index.js#L19-L19)

Remove content from a Rich Text value between the given `startIndex` and
`endIndex`. Indices are retrieved from the selection if none are provided.

**Parameters**

-   **value** `Object`: Value to modify.
-   **startIndex** `[number]`: Start index.
-   **endIndex** `[number]`: End index.

**Returns**

`Object`: A new value with the content removed.

### removeFormat

[src/index.js#L18-L18](src/index.js#L18-L18)

Remove any format object from a Rich Text value by type from the given
`startIndex` to the given `endIndex`. Indices are retrieved from the
selection if none are provided.

**Parameters**

-   **value** `Object`: Value to modify.
-   **formatType** `string`: Format type to remove.
-   **startIndex** `[number]`: Start index.
-   **endIndex** `[number]`: End index.

**Returns**

`Object`: A new value with the format applied.

### replace

[src/index.js#L20-L20](src/index.js#L20-L20)

Search a Rich Text value and replace the match(es) with `replacement`. This
is similar to `String.prototype.replace`.

**Parameters**

-   **value** `Object`: The value to modify.
-   **pattern** `(RegExp|string)`: A RegExp object or literal. Can also be a string. It is treated as a verbatim string and is not interpreted as a regular expression. Only the first occurrence will be replaced.
-   **replacement** `(Function|string)`: The match or matches are replaced with the specified or the value returned by the specified function.

**Returns**

`Object`: A new value with replacements applied.

### slice

[src/index.js#L25-L25](src/index.js#L25-L25)

Slice a Rich Text value from `startIndex` to `endIndex`. Indices are
retrieved from the selection if none are provided. This is similar to
`String.prototype.slice`.

**Parameters**

-   **value** `Object`: Value to modify.
-   **startIndex** `[number]`: Start index.
-   **endIndex** `[number]`: End index.

**Returns**

`Object`: A new extracted value.

### split

[src/index.js#L26-L26](src/index.js#L26-L26)

Split a Rich Text value in two at the given `startIndex` and `endIndex`, or
split at the given separator. This is similar to `String.prototype.split`.
Indices are retrieved from the selection if none are provided.

**Parameters**

-   **value** `Object`: Value to modify.
-   **string** `[(number|string)]`: Start index, or string at which to split.
-   **endStr** `[number]`: End index.

**Returns**

`Array`: An array of new values.

### toggleFormat

[src/index.js#L29-L29](src/index.js#L29-L29)

Toggles a format object to a Rich Text value at the current selection.

**Parameters**

-   **value** `Object`: Value to modify.
-   **format** `Object`: Format to apply or remove.

**Returns**

`Object`: A new value with the format applied or removed.

### toHTMLString

[src/index.js#L28-L28](src/index.js#L28-L28)

Create an HTML string from a Rich Text value. If a `multilineTag` is
provided, text separated by a line separator will be wrapped in it.

**Parameters**

-   **$1** `Object`: Named argements.
-   **$1.value** `Object`: Rich text value.
-   **$1.multilineTag** `[string]`: Multiline tag.
-   **$1.multilineWrapperTags** `[Array]`: Tags where lines can be found if nesting is possible.

**Returns**

`string`: HTML string.

### unregisterFormatType

[src/index.js#L31-L31](src/index.js#L31-L31)

Unregisters a format.

**Parameters**

-   **name** `string`: Format name.

**Returns**

`(WPFormat|undefined)`: The previous format value, if it has been successfully unregistered; otherwise `undefined`.


<!-- END TOKEN(Autogenerated API docs) -->

<br/><br/><p align="center"><img src="https://s.w.org/style/images/codeispoetry.png?1" alt="Code is Poetry." /></p>
