
# 源码分析

## 文件结构

``` bash
/Users/liufang/openSource/FunnyLiu/color-thief
├── LICENSE
├── README.md
├── async.html
├── build
|  └── build.js
├── cypress
|  ├── fixtures
|  |  └── example.json
|  ├── integration
|  |  ├── api_spec.js
|  |  ├── cors_spec.js
|  |  └── module_spec.js
|  ├── plugins
|  |  └── index.js
|  ├── support
|  |  ├── commands.js
|  |  └── index.js
|  └── test-pages
|     ├── cors.html
|     ├── es6-module.html
|     ├── img
|     |  ├── black.png
|     |  ├── rainbow-horizontal.png
|     |  ├── rainbow-vertical.png
|     |  ├── red.png
|     |  ├── transparent.png
|     |  └── white.png
|     ├── index.html
|     ├── index.js
|     └── screen.css
├── cypress.json
├── dist
|  ├── color-thief.js
|  ├── color-thief.min.js
|  ├── color-thief.mjs
|  ├── color-thief.umd.js
|  └── color-thief.umd.js.map
├── examples
|  ├── css
|  |  └── screen.css
|  ├── img
|  |  ├── image-1.jpg
|  |  ├── image-2.jpg
|  |  └── image-3.jpg
|  └── js
|     └── demo.js
├── index.html
├── package-lock.json
├── package.json
└── src
|  ├── color-thief-node.js
|  ├── color-thief.js
|  └── core.js

directory: 14 file: 40

ignored: directory (1)

```

## 外部模块依赖

![img](./outer.svg)

## 内部模块依赖

![img](./inner.svg)
  

## 原理说明

通过给canvas给image拿到像素数组，然后通过第三方库quantize，从像素数组中拿到用的最多的颜色值。该库也是基于图像处理中的某个算法来得出颜色最多的分布。

# Color Thief

Grab the color palette from an image using just Javascript.Works in the browser and in Node.

### View the [demo page](https://lokeshdhakar.com/projects/color-thief/) for examples, API docs, and more.

---

## Contributing

### Project structure

+ `build/` - Simple script that copies and renames files into the /dist folder.
+ `cypress/` - Browsers tests.
+ `dist/` - Generated distribution files created by [microbundle](https://github.com/developit/microbundle) package and a couple of files copied via build script.
+ `examples/` - CSS, JS, and Images for the index.html example page.
+ `src/color-thief-node.js` - Source for the Node (commonjs) compatible version of the script.
+ `src/color-thief.js` - Source for the browser (ES6, AMD, Global var) compatible version of the script.
+ `src/core.js` - Functions shared between the node and browser versions of the script.
+ `test/` - Node integration tests. Uses Chai.
+ `index.html` - Example page.

### Running tests

There are two sets of tests:

1. Browser tests run with [Cypress](https://www.cypress.io)
2. Node tests run with [Karma](https://karma-runner.github.io/latest/index.html) and utilizing [Mocha](https://mochajs.org/)

To run both the browser and Node tests:

- `npm run dev` to start local server.
- `npm run test`

To run just the browser tests with the Cypress UI:

- `npm run dev` to start local server
- `npm run test:browser`

To run just the Node tests:

- `npm run test:node`


### Adding tests

- Update `cypress/test-pages/index.html` as needed or create a new test page if you need new examples.
- Add new tests in `cypress/integration/apis_spec.js`

### Making a new release

- Merge `dev` into `master`
- Pull down `master`
- Update version number in `src/color-thief.js` and `package.json`
- Run `npm run build`
- Commit and push built files back up to `master`
- Create a new Github release along with tag. Naming convention for both ```v2.8.1```
- `npm publish`
