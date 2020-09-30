# React Native Markdown Transformer

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
