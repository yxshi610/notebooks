# JavaScript

https://javascript.info/

## Intro

Today, JavaScript can execute not only in the browser, but also on the server, or actually on any device that has a special program called the JavaScript engine.

The browser has an embedded engine sometimes called a “JavaScript virtual machine”.

Different engines have different “codenames”. For example: V8 in Chrome, Opera and Edge.

There are many languages that get “transpiled” to JavaScript and provide certain features. e.g. TypeScript & kotlin.

## Fundamentals

### script

JavaScript programs can be inserted almost anywhere into an HTML document using the `<script>` tag.

The `<script>` tag contains JavaScript code which is automatically executed when the browser processes the tag.

If we have a lot of JavaScript code, we can put it into a separate file. Script files are attached to HTML with the `src` attribute:

`<script src="./script.js"></script>`

As a rule, only the simplest scripts are put into HTML. More complex ones reside in separate files.

The benefit of a separate file is that the browser will download it and store it in its cache.

Other pages that reference the same script will take it from the cache instead of downloading it.
