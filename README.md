# Jest Mock Module

[![Dependabot badge](https://badgen.net/dependabot/iamogbz/jest-mock-module/?icon=dependabot)](https://app.dependabot.com)
[![Dependencies](https://david-dm.org/iamogbz/jest-mock-module.svg)](https://github.com/iamogbz/jest-mock-module)
[![Build Status](https://github.com/iamogbz/jest-mock-module/workflows/Build/badge.svg)](https://github.com/iamogbz/jest-mock-module/actions)
[![Coverage Status](https://coveralls.io/repos/github/iamogbz/jest-mock-module/badge.svg)](https://coveralls.io/github/iamogbz/jest-mock-module)
[![NPM Version](https://img.shields.io/npm/v/jest-mock-module.svg)](https://www.npmjs.com/package/jest-mock-module)

Extends jest to allow deep auto mocking of a module by spying on all functions and properties.

## Introduction

### Getting Started

Install the extension using [npm](https://docs.npmjs.com/cli/install.html) or [yarn](https://yarnpkg.com/en/docs/usage)

```sh
npm install -D "jest-mock-module"
```

### Example Usage

```js
// src/example.js
module.exports = {
  testing: "123";
  nested: {
    test: () => true;
    testing: "456";
  }
}
```

```js
import * as mock from "jest-mock-module";
mock.extend(jest);

jest.spy("src/example");

const spied = require("src/example");

jest.isMockProp(spied, "testing"); // true
jest.isMockMethod(spied.nested.test); // true
jest.isMockProp(spied.nested, "testing"); // true
```

It keeps the same structure of the module but replaces all functions and properties with jest mocks.

#### References

- [`jest-spy-on`][jest-spyon-method] - Guide to spying on module methods
- [`jest-mock-props`][jest-spyon-props] - Guide to spying on object properties

[jest-spyon-method]:https://jestjs.io/docs/en/jest-object#jestspyonobject-methodname]
[jest-spyon-props]:https://ogbizi.com/jest-mock-props/
