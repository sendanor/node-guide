**Table of Contents**  *generated with [DocToc](http://doctoc.herokuapp.com/)*

- [node-guide](#node-guide)
	- [Project Files](#project-files)
		- [`README.md`](#readmemd)
		- [`package.json`](#packagejson)
			- [Automate tasks using `npm run`](#automate-tasks-using-npm-run)
		- [`.gitignore`](#gitignore)
		- [`.sublime-project` and `.sublime-workspace`](#sublime-project-and-sublime-workspace)
		- [`~/.netrc`](#~netrc)
		- [Example `~/.netrc` for Github](#example-~netrc-for-github)
		- [NODE_ENV](#node_env)
	- [The environment](#the-environment)
		- [Tabs to indent, spaces to align](#tabs-to-indent-spaces-to-align)
	- [Sendanor Style Guide](#sendanor-style-guide)
		- [Use Semicolons](#use-semicolons)
		- [No universal characters per line limit](#no-universal-characters-per-line-limit)
			- [Line break after semicolons](#line-break-after-semicolons)
			- [Documentation blocks](#documentation-blocks)
			- [Splitting objects in code](#splitting-objects-in-code)
			- [Splitting arrays in code](#splitting-arrays-in-code)
		- [Opening braces go on the same line](#opening-braces-go-on-the-same-line)
		- [Declare one variable per var statement](#declare-one-variable-per-var-statement)
		- [Lower or upper case](#lower-or-upper-case)
		- [Use the === Operator](#use-the-===-operator)
		- [Write small functions](#write-small-functions)
		- [Return early from functions](#return-early-from-functions)
		- [Example of difference with `new String` and `""`](#example-of-difference-with-new-string-and-)
		- [JSON](#json)
		- [JSON-Schema](#json-schema)
		- [JSON-Patch and JSON-Diff](#json-patch-and-json-diff)
		- [Iterate over arrays and objects](#iterate-over-arrays-and-objects)
	- [Promises](#promises)
	- [Creating objects and arrays](#creating-objects-and-arrays)
	- [JSON and tools](#json-and-tools)

node-guide
==========

Sendanor's Node.js and JavaScript Quick Reference Guide.

******************************************************************************

Project Files
-------------

### `README.md`

The main documentation for a project in [the Github Flavored Markdown 
format](https://help.github.com/articles/github-flavored-markdown).

******************************************************************************

### `package.json`

The NPM package configuration file.

Take a look at:

* `npm help json`
* `npm help scripts`
* `npm help config`

See also: 

* [Documentation for package.json](https://npmjs.org/doc/json.html)
* [An interactive guide to package.json](http://package.json.nodejitsu.com/)
* [Developers Guide to NPM](https://npmjs.org/doc/developers.html)

******************************************************************************

#### Automate tasks using `npm run` ####

See [Task automation with npm run by substack](http://substack.net/task_automation_with_npm_run) 
and `npm help scripts`.

******************************************************************************

### `.gitignore` ###

This file lists all files and directories (one by line) that should be ignored 
by git.

It is also used by the NPM if `.npmignore` file does not exists.

******************************************************************************

### `.sublime-project` and `.sublime-workspace` ###

`.sublime-project` is the project file for [Sublime Text Editor](http://www.sublimetext.com/).

`.sublime-workspace` contains the user specific data, such as the open files 
and the modifications to each. It ***should not*** be in the repository.

See also [Projects in Sublime Text 3](http://www.sublimetext.com/docs/3/projects.html).

******************************************************************************

### `~/.netrc` ###

You can use oauth services like Github directly with `curl`, `git`, or any other tool in shell.

  1. Get oauth token
    1. Using a web browser, see [Creating a token for CLI at Github](https://help.github.com/articles/creating-an-access-token-for-command-line-use/)
    2. You can also create it using [Github API](https://developer.github.com/v3/oauth_authorizations/#create-a-new-authorization)
  2. Create the file: `touch ~/.netrc && chmod 600 ~/.netrc`
  3. Save the token to `~/.netrc` file, see example below.

### Example `~/.netrc` for Github

```
machine github.com
  login s5WaTA9nMuHtoTn56CnC2hqfwCGTpHNm
  password x-oauth-basic

machine raw.github.com
  login s5WaTA9nMuHtoTn56CnC2hqfwCGTpHNm
  password x-oauth-basic

machine git.github.com
  login s5WaTA9nMuHtoTn56CnC2hqfwCGTpHNm
  password x-oauth-basic

machine api.github.com
  login s5WaTA9nMuHtoTn56CnC2hqfwCGTpHNm
  password x-oauth-basic
```

... where `s5WaTA9nMuHtoTn56CnC2hqfwCGTpHNm` is your Github oauth token.

******************************************************************************

The environment
---------------

### NODE_ENV

Make sure your development shell has `NODE_ENV=development` set when 
developing. Some apps that use it do not correctly fallback to it if it is 
undefined.

```
NODE_ENV=development
export NODE_ENV
```

This is actually just a convention used by (at least) 
[Express](http://expressjs.com/) and some hosting platforms. Not a real 
standard.

******************************************************************************

Sendanor Style Guide
--------------------

We use a bit different style than [Node.js Style 
Guide](https://github.com/felixge/node-style-guide) and we don't demand all of 
it.


******************************************************************************

### Tabs to indent, spaces to align

The "smart tabs" scheme, where tabs are used **only** for indentation and 
spaces for everything else.

```javascript
function example() {
<TAB> console.log("Hello World");
<TAB> var foo = "bar",
<TAB>     bar = "foo";
<TAB> return [foo, bar];
}
```

This style makes it possible for everyone to setup their editor to show tabs as 
they prefer. We would officially use four (4) spaces but of course that's 
insignificant when using tabs to indent.

See also [Indent with tabs, align with spaces](http://vim.wikia.com/wiki/Indent_with_tabs,_align_with_spaces).


******************************************************************************

### Use Semicolons

Even though Node.js usually does not break when semicolons are ommited, the 
ECMAScript specification is still badly designed relating to auto placement of 
semicolons and implementations are free to implement that functionality in 
multiple surprising ways.

It also seems to be the community standard, see [Use 
Semicolons](https://github.com/felixge/node-style-guide#use-semicolons).


******************************************************************************

### No universal characters per line limit

We do not insist on splitting your lines to some specific magic or legacy 
character limit.

Exception to this is a content like longer blocks of text in a documentation.

This does not mean you should write long lines of code. Split them when it's 
best for readability. Preferably after each instruction.


******************************************************************************

#### Line break after semicolons

Use line break after each semicolon. This is probably very self-evident.

```
console.log("Hello");
console.log("World");
```


******************************************************************************

#### Documentation blocks

For documentation blocks we use 79 characters per line unless the line has very 
long links, tables or other Markdown content that cannot be split on multiple 
lines.

```
/**
 * Travel time to the nearest starbase? Besides, you look good in a dress. 
 * Well, I'll say this for him - he's sure of himself. Wait a minute - you've 
 * been declared dead. You can't give orders around here. Damage report! I'd 
 * like to think that I haven't changed those things, sir. Sorry, Data.
 */
```


******************************************************************************

#### Splitting objects in code

Objects can be splitted on multiple lines by each property on its own 
line:

```
var o = {
	"name": "Oulu",
	"latitude": 65.016667,
	"longitude": 25.466667
};
```


******************************************************************************

#### Splitting arrays in code

Arrays can be splitted on multiple lines by each item on its own 
line:

```
var arr = [
	"Oulu",
	"Kalajoki",
	"Helsinki"
};
```

******************************************************************************

### Opening braces go on the same line

See [Opening braces go on the same line](https://github.com/felixge/node-style-guide#opening-braces-go-on-the-same-line).

******************************************************************************

### Declare one variable per var statement

See [Declare one variable per var statement](https://github.com/felixge/node-style-guide#declare-one-variable-per-var-statement).

******************************************************************************

### Lower or upper case

Use underscores for variables, properties and normal function names:

```
var hello_world = "Hello World";
```

Use leading underscore for private local variables:

```
var _hello_world = "Hello World";
```

Use lower case for normal functions:

```
function print_foo() {
	console.log("foo");
}
```

Use UpperCamelCase for object constructor functions:

```
function OurImplementation() {
	this.foo = "bar";
}
```

Use camelCase for method names:

```
OurImplementation.prototype.printFoo = function() {
	console.log(this.foo);
}
```

...but ***prefer*** not to use names with multiple words in the first place.

Use [UPPERCASE for Constants](https://github.com/felixge/node-style-guide#use-uppercase-for-constants):

```
var SECOND = 1 * 1000;
```

******************************************************************************

### Use the === Operator

See more [Use the === operator](https://github.com/felixge/node-style-guide#use-the--operator).

******************************************************************************

### Write small functions

See more [Write small functions](https://github.com/felixge/node-style-guide#write-small-functions).

******************************************************************************

### Return early from functions

See more [Return early from functions](https://github.com/felixge/node-style-guide#return-early-from-functions).

******************************************************************************

Promises
--------

On Node.js side we prefer using [Q promises](https://github.com/kriskowal/q) 
with our own [chainable method extension from nor-extend](https://github.com/sendanor/nor-extend#example-usage).

On browser side we prefer using [jQuery 
promises](http://api.jquery.com/category/deferred-object/).

Creating objects and arrays
---------------------------

* Do not use `var o = new Object()`, use `var o = {};`.
* Do not use `var a = new Array()`, use `var a = [];`.
* Do not use `var s = String("hello")`, use `var s = "hello";`.

### Example of difference with `new String` and `""`

Here's a demostration of the difference in `node` shell:

```
> var a = new String("hello");
undefined
> typeof a
'object'
> var b = "hello";
undefined
> typeof b
'string'
```

JSON and tools
--------------

### JSON

[JSON specification](http://json.org) is pretty simple single page standard and available online.

JavaScript standard also has support for handling JSON.

Convert JavaScript to JSON:

```
> JSON.stringify([1,2,3])
'[1,2,3]'
```

Convert JSON to JavaScript:

```
> JSON.parse('[1,2,3]')
[ 1, 2, 3 ]
```

### JSON-Schema

We use [JSON-Schema version 4](http://json-schema.org) and [tv4 library](https://github.com/geraintluff/tv4) in all environments (browser, node.js and PostgreSQL database servers).

It seems to be production ready.

### JSON-Patch and JSON-Diff

JSON-patch and JSON-diff libs are not yet very production ready. There is also more than one different implementation with quite interesting bugs.

### Iterate over arrays and objects

For Arrays use `.forEach()` (or `.map()`):

```
[1, 2, 3].forEach(function(i) {
	// do something with i ...
});
```

For Objects use compination of `Object.keys()` and `.forEach()` (or `.map()`):

```
var obj = {"foo":"bar", "bar":"foo"};
Object.keys(obj).forEach(function(key) {
	var value = obj[key];
	// do something with value and key ...
});
```

***Never*** use JavaScript `in` operator. Most times it's not what you want. See [stackoverflow #500504](http://stackoverflow.com/questions/500504/why-is-using-for-in-with-array-iteration-such-a-bad-idea).


******************************************************************************
