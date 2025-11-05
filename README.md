<p align="center">
  <img align="center" src="logo.png" width="150px" height="150px" />
</p>
<h1 align="center">ProsperaSheet</h1>
<p align="center">ProsperaSheet is a fork of FortuneSheet: for experimental features, faster bug fixes and optimizations.</p>

<div align="center">

[![xiemala](https://img.shields.io/badge/maintained%20by-corbe30-cc00ff.svg)](https://corbe30.github.io)

</div>


English | [简体中文](./README-zh.md)

## Purpose

ProsperaSheet encourages faster SDLC, pushing newer versions quicker. Due to this, testing may not be as thorough as in FortuneSheet. Here, ProsperaSheet depends on the community to bring the developers to its attention for quicker error resolution!

ProsperaSheet cannot promise backward compatibility with FortuneSheet, but promises an optimized experience in edit operations with fewer P0/P1 issues.
FortuneExcel will always be compatible with both ProsperaSheet and FortuneSheet.

Moreover, due to its access limitations and new changes to npm token expiration, we won't be able to maintain FortuneSheet further.

## Upcoming Improvements to FortuneSheet

- [ ] Special Paste Support [ctrl/cmd + shift + v]
- [ ] Updated documentation
- [ ] Updated Storybooks
- [ ] Dark theme
- [ ] NaN in Selected Cell/ Range box
- [ ] Optimized Edit Cell operation
- [ ] Optimized Load by deferring caching
- [ ] Optimized Memory Usage to reduce craches

## Get started (react)

### Download and install the library

<details open>
<summary>Using npm</summary>

```shell
npm install @prospera-sheet/react
```
</details>

<details>
<summary>Using pnpm</summary>

```shell
pnpm install @prospera-sheet/react
```
</details>

<details>
<summary>Using yarn</summary>

```shell
yarn add @prospera-sheet/react
```
</details>

### Create an HTML placeholder
```html
<style>
  html, body, #root {
    width: 100%;
    height: 100%;
  }
</style>
<div id="root"></div>
```

**NOTE**: `width` and `height` doesn't have to be 100%, but should at least have a value. If set to `auto`, table area may not show.

### Render the sheet

```js
import React from 'react';
import ReactDOM from 'react-dom';
import { Workbook } from "@prospera-sheet/react";
import "@fortune-sheet/react/dist/index.css"

ReactDOM.render(
  <Workbook data={[{ name: "Sheet1" }]} />,
  document.getElementById('root')
);
```

### Backend storage and collabration

Each time a user operates on the sheet, an array of `Op` will be emiited through `onOp` callback. An op describes how to modify the current data to reach the new data after the user's operation. For example, here is an op when user sets the cell font to be bold on cell A2.

```json
[
    {
        "op": "replace",
        "index": "0",
        "path": ["data", 1, 0, "bl"],
        "value": 1
    }
]
```

The op is useful for database modification and syncing state in online collabration.

A working example with `Express` (backend server) and `MongoDB` (data persistence) is avaiable in `backend-demo` folder.

Run it with `node index.js` and visit [Collabration example](https://ruilisi.github.io/fortune-sheet-demo/?path=/story/collabration--example) (initialize data by visiting http://localhost:8081/init)

For detailed doc about `Op`, refer to [fortune-sheet-doc](./docs/guide/op.md)

## Contributing
Expected workflow is: Fork -> Patch -> Push -> Pull Request

Please make sure to read the [Contributing Guide](./docs/guide/contribute.md) before making a pull request.

## Development
### Installation
```shell
yarn
```

### Development
```shell
yarn dev
```

### Packaging
```shell
yarn build
```

## License
This project is licensed under the MIT License. See [MIT](http://opensource.org/licenses/MIT) for the full license text.
