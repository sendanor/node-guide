node-guide
==========

Sendanor's Node.js and JavaScript Quick Reference Guide.

******************************************************************************

Project Files
-------------

### `README.md`

The main documentation for this project in [the Github Flavored Markdown 
format](https://help.github.com/articles/github-flavored-markdown).

******************************************************************************

### `package.json`

The NPM package configuration file.

See also: 

* [Documentation for package.json](https://npmjs.org/doc/json.html)
* [An interactive guide to package.json](http://package.json.nodejitsu.com/)
* [Developers Guide to NPM](https://npmjs.org/doc/developers.html)

******************************************************************************

#### Automate tasks using `npm run` ####

See [Task automation with npm run by substack](http://substack.net/task_automation_with_npm_run).

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
OurImplementation.prototype.print_foo = function() {
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

******************************************************************************
