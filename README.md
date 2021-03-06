[![CircleCI](https://circleci.com/gh/DAB0mB/graphql-tag-pluck/tree/master.svg?style=svg)](https://circleci.com/gh/DAB0mB/graphql-tag-pluck/tree/master)

# GraphQL Tag Pluck

`graphql-tag-pluck` will take JavaScript code as an input and will pluck all template literals provided to `graphql-tag`.

Input:

```js
import gql from 'graphql-tag'

const fragment = gql`
  fragment Foo on FooType {
    id
  }
`

const doc = gql`
  query foo {
    foo {
      ...Foo
    }
  }

  ${fragment}
`
```

Output:

```graphql
fragment Foo on FooType {
  id
}

query foo {
  foo {
    ...Foo
  }
}
```

Originally created because of https://graphql-code-generator.com/.

### Usage

`graphql-tag-pluck` is installable via NPM (or Yarn):

    $ npm install graphql-tag-pluck

Once installed you can pluck GraphQL template literals using one of the following methods:

```js
import gqlPluck, { gqlPluckFromFile, gqlPluckFromCodeString } from 'graphql-tag-pluck'

gqlPluck.fromFile(filePath, { sync: false, ...mergeBabelConfig })
gqlPluck.fromFile.sync(filePath, mergeBabelConfig)

gqlPluck.fromCodeString(codeString, { sync: false, ...mergeBabelConfig })
gqlPluck.fromCodeString.sync(codeString, mergeBabelConfig)
```

supported file extensions are: `.js`, `.jsx`, `.ts`, `.tsx`, `.graphqls`, `.graphql`, `.gql`.

### License

MIT
