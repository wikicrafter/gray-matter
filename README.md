# matter [![NPM version](https://badge.fury.io/js/matter.png)](http://badge.fury.io/js/matter)

> A simple to use YAML Front-Matter parsing and extraction Library.

**Why another YAML Front Matter library?**

Because other libraries we tried failed to meet our requirements with [Assemble](http://assemble.io). Some most of the libraries met most of the requirements, but _none had all of them_. Here are the most important:

* Be usable, if not simple
* Allow custom delimiters
* Use a dependable and well-supported library for parsing YAML
* Don't fail if YAML front matter exists, but no content
* Don't fail if content exists, but no YAML front matter
* Have no problem reading YAML files directly
* Have no problem with complex content, including fenced code blocks containing examples of YAML front matter.
* Should return an object that contains the parsed YAML front matter and content, as well as the "original" content.

```bash
npm i matter --save
```
## Usage

```js
var matter = require('matter');
matter(String, Object);
```

## Methods

### matter

By default the `matter()` method expects a string. So this:

```js
matter('---\nTitle: This is matter\n---\n<p>This is content.<p>');
```

results in:

```json
{
  "context": {
    "title": "This is matter"
  },
  "content": "<p>This is content.<p>",
  "original": "---\nTitle: This is matter\n---\n<p>This is content.<p>"
}
```

### matter.read

To read a file from the file system before parsing, use `matter.read`:

```js
matter.read('file.md');
```

### matter.exists

To check for YAML front matter, returning `true` or `false` if it exists, use `matter.exists`:

```js
matter.exists('file.md');
```



## Options

> All methods will accept an options object to be passed as a second paramer

#### delimiters
Type: `object`

Default: `{delims: ['---', '---']}`

Open and close delimiters can be passed in as an array of strings. Example:

```js
matter.read('file.md', {delims: ['~~~', '~~~']});
```

You may also pass an array of arrays, allowing multiple alternate delimiters to be used. Example:


```js
{
  delims: [
    ['---', '~~~'], ['---', '~~~']
  ]
}
```

_However, passing multiple delimiters will yield unpredictable results, so it is recommended that you use this option only for testing purposes._


## Examples

Let's say our page, `foo.html` contains

```html
---
title: YAML Front matter
description: This is a page
---
<h1>{{title}}</h1>
```

then running the following in the command line:

```js
console.log(matter('foo.html'));
```
returns

```json
{
  "context": {
    "title": "YAML Front matter",
    "description": "This is a page"
  },
  "content": "<h1>{{title}}</h1>",
  "original": "---\ntitle: YAML Front matter\n---\n<h1>{{title}}</h1>"
}
```
and

```js
console.log(matter('foo.html').context);
```
returns


```json
{"title": "YAML Front matter", "description": "This is a page"}
```


## Authors

**Jon Schlinkert**

+ [github/jonschlinkert](https://github.com/jonschlinkert)
+ [twitter/jonschlinkert](http://twitter.com/jonschlinkert)

**Brian Woodward**

+ [github/doowb](https://github.com/doowb)
+ [twitter/doowb](http://twitter.com/jonschlinkert)


## License
Copyright (c) 2014 Jon Schlinkert, Brian Woodward, contributors.
Released under the MIT license

***

_This file was generated by [grunt-readme](https://github.com/assemble/grunt-readme) on Monday, January 27, 2014._

[grunt]: http://gruntjs.com/
[Getting Started]: https://github.com/gruntjs/grunt/blob/devel/docs/getting_started.md
[package.json]: https://npmjs.org/doc/json.html
