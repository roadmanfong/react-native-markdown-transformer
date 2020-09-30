# React Native Markdown Transformer

[![Build Status](https://travis-ci.org/roadmanfong/react-native-markdown-transformer.svg?branch=master)](https://travis-ci.org/roadmanfong/react-native-markdown-transformer) [![npm version](https://img.shields.io/npm/v/react-native-markdown-transformer.svg?style=flat-square)](https://www.npmjs.com/package/react-native-markdown-transformer) [![npm downloads](https://img.shields.io/npm/dm/react-native-markdown-transformer.svg?style=flat-square)](https://www.npmjs.com/package/react-native-markdown-transformer)

## Usage

```js
import Markdown from 'react-native-markdown-display';
import article from 'article.md';

export default function App() {
  return <Markdown>{article}</Markdown>;
}
```

## Setup

```shell
yarn add --dev react-native-svg-transformer
```

### For React Native v0.57 or newer

`metro.config.js`

```js
const { getDefaultConfig } = require('metro-config');

module.exports = (async () => {
  const {
    resolver: { sourceExts },
  } = await getDefaultConfig();
  return {
    transformer: {
      babelTransformerPath: require.resolve(
        './scripts/react-native-markdown-transformer'
      ),
      getTransformOptions: async () => ({
        transform: {
          experimentalImportSupport: false,
          inlineRequires: false,
        },
      }),
    },
    resolver: {
      sourceExts: [...sourceExts, 'md'],
    },
  };
})();
```

### Typescript

```ts
declare module '*.md' {
  const content: string;
  export default content;
}
```

## Todo

* Unit Test