JavaScript Webpack "mjs" Import Issue Demo
==========================================

如果一个package同时提供了两种格式的bundle:

```
"main": "index.js",
"module": "index.mjs"
```

那么webpack在引入它时，到底会选择哪一个？

如果没有经过特别设置，对于

```
require('javascript-webpack-mjs-import-issue-demo--to-upper')
```

将会选择`index.mjs`。

所以，如果我们想让它引用`.js`时，需要写成：

```
require('javascript-webpack-mjs-import-issue-demo--to-upper/index.js')
```

或者在webpack.config.js中指定mainFields的查找顺序：

```
resolve: {
  mainFields: ['main', 'module']
}
```

如果把`main`放在前面的话，那么就会先找`main`对应的`index.js`

运行：

```
npm install
npm run demo
```

