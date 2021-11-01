## DESCRIPTION

Excuse me.
I want to build with esbuild including bootstrap-multiselect.

However, I get the following error in browser's js console.

```
index.js:7069 Uncaught TypeError: Cannot read properties of undefined (reading 'fn')
    at index.js:7069
    at index.js:5923
    at node_modules/bootstrap-multiselect/dist/js/bootstrap-multiselect.js (index.js:5925)
    at __require2 (index.js:17)
    at index.js:7099
    at index.js:7101
```

In webpack, I solved it with [imports-loader](https://webpack.js.org/loaders/imports-loader/#wrapper) as below.

```
module.exports = {
  module: {
    rules: [
      {
        test: /bootstrap-multiselect/,
        use: [
          {
            loader: 'imports-loader',
            options: {
              wrapper: 'window',
              additionalCode: 'var define = false;'
            },
          },
        ],
      }
    ],
  }
}
```

I want to do the same with esbuild, is there any way?
