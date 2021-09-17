---
title: Base path
description: Add automatically a base path to all urls
docs: plugins/base_path.ts
---

The `base_path` plugin fixes all URLs in your HTML documents by prepending the
path of the location settings. It's useful if your site can be hosted in a
subdirectory and you don't want to use the [`url` filter](../core/url.md)
everywhere.

This plugin **is disabled by default** so to enable it you have to import and
use it in the `_config.js`. After that, any element with the attribute `href`,
`src`, `srcset` and `imagesrcset` will be automatically fixed.

Note that if the path of your [location setting](../getting-started/config-file.md)
is `/`, **it won't have any effect.**

```js
import lume from "lume/mod.ts";
import basePath from "lume/plugins/base_path.ts";

const site = lume({
  location: "https://my-site.com/blog/", // ← Note the path /blog/
});

site.use(basePath());
```

All **absolute** URLs of your site will be fixed. For example:

```html
<a href="/articles/my-second-article/">Go to the second article</a>
```

The `base_path` plugin will convert this HTML code to:

```html
<a href="/blog/articles/my-second-article/">Go to the second article</a>
```
