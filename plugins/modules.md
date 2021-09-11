---
title: Modules
description: Using javascript and typescript modules for data, pages, and layouts
docs: plugins/modules.ts
---

Because Lume is built for Deno, it has native support for JavaScript and
TypeScript. This plugin is **enabled** by default.

## Creating _data files

Create `_data.js` or `_data/*.js` (or the TypeScript equivalent `_data.ts` or
`_data/*.ts`) files to save shared data.

```js
export const users = [
  {
    name: "Oscar",
    surname: "Otero",
  },
  {
    name: "Michael",
    surname: "Jackson",
  },
];
```

## Creating pages

To create pages using JavaScript or TypeScript, create a file with the extension
`.tmpl.js` or `.tmpl.ts` (the `.tmpl` subextension is required to differentiate
HTML pages created from a JavaScript file from the JavaScript files to execute
in the browser). To export the variables, use named exports and to export the
main content you can use the default export.

```js
export const title = "Welcome to my page";
export const layout = "layouts/main.njk";

export default "This is my first post using lume. I hope you like it!";
```

The default export can be a function, so it will be executed passing all the
available data in the first argument and the filters in the second argument:

```js
export const title = "Welcome to my page";
export const layout = "layouts/main.njk";

export default (data, filters) =>
  `<h1>${data.title}</h1>
  <p>This is my first post using lume. I hope you like it!</p>
  <a href="${filters.url("/")}">Back to home</a>`;
```

JavaScript/TypeScript allows to generate multiple pages from the same file, see
[Pagination](/creating-pages/pagination/) for more info.

## Creating layouts

It's possible to create layouts using JavaScript/TypeScript. Just create
`.tmpl.js` or `.tmpl.ts` files inside the `_includes` directory.

```js
export default ({ title, content }, filters) =>
  `<html>
    <head>
      <title>${title}</title>
    </head>
    <body>
      ${content}
    </body>
  </html>`;
```
