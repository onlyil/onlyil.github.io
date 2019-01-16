---
title: A Vue multiple-pages Project Template
date: 2018-12-03 21:32:00
tags: vue
icon: fa-file-text
---

# A Vue multiple-pages Project Template

> This project template is configured based on vue cli 2

For modify config of webpack, we need generate some configs in a new js: `config/multiple.js`.
Directory:

``` text
├── build
├── config
│   ├── dev.env.js
│   ├── index.js
│   ├── multiple.js         // generate multiple entries webpack dev, pro related config
│   └── prod.env.js
├── package.json
├── src
│   ├── assets
│   ├── components
│   └── pages               // divide pages by multiple modules
│       ├── admin
│       │   ├── App.vue
│       │   ├── index.html  // the template html of this module
│       │   ├── main.js
│       │   ├── vuepage
│       │   └── router
│       └── user
│           ├── App.vue
│           ├── index.html
│           ├── main.js
│           ├── vuepage
│           └── router
└── static
```

## Entry

- Firstly get the dir names in `src/pages`, use node `fs` module.
- Generate entries object by the `main.js` of every module dir.

``` javascript
const fs = require('fs')
const path = require('path')
const pagesPath = path.resolve(__dirname, '..', 'src/pages')
const dirs = fs.readdirSync(pagesPath)

const createMultipleEntries = function () {
  const entries = {}
  dirs.forEach(dir => {
    entries[dir] = `${pagesPath}/${dir}/main.js`
  })
  return entries
}
```
