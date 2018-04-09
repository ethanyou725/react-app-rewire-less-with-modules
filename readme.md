# Installation

```
yarn add react-app-rewire-less-with-modules -D
```
or use npm

# Example

 my-procejt/config-overrides.js

```
const rewireLessWithModule = require('react-app-rewire-less-with-modules')

module.exports = function override (config, env) {
  config = rewireLessWithModule(config, env)
  return config
}

```

 work with antd, customize the deault theme,  modifyVars to override the default values.

```
const { injectBabelPlugin } = require('react-app-rewired')
const rewireLessWithModule = require('react-app-rewire-less-with-modules')

module.exports = function override (config, env) {
  config = injectBabelPlugin(['import', {
    libraryName: 'antd',
    libraryDirectory: 'es',
    style: true
  }], config)
  config = rewireLessWithModule(config, env, {
    modifyVars: {
      '@primary-color': 'red',
      '@link-color': '#1DA57A',
      '@border-radius-base': '2px',
      '@font-size-base': '16px',
      '@line-height-base': '1.2'
    },
  })
  return config
}

```