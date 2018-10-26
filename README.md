
class: center, middle

# Webpack for Backend

### Author: José Miguel Colella
### Email: <jose.colella@dynatrace.com>
### Github: https://github.com/josecolella

---

# Agenda

1. Why use Webpack for backend applications?

2. Getting Started

3. Advantages

4. Disadvantages

5. My webpack config

5. Q&A

---

# Why use Webpack for backend applications?

* Optimizations

- Remove comments, unreachable code, uglify, minify, resulting in faster load and parsing of production build artifact.

- Code Analysis when builing, using tslint. For example: tslint-loader

```ts
rules: [
      // all files with a '.ts' or '.tsx' extension will be handled by 'ts-loader'
      {
        test: /\.ts$/,
        enforce: 'pre',
        use: [
          {
            loader: 'tslint-loader'
          }
        ]
      },
      { test: /\.tsx?$/, loader: ['ts-loader', 'shebang-loader'] }
    ]
```

- Aliases (tsconfig-paths) to end '../../../' path *hell*. Code is more legible

---

# Getting Started

- To get started using webpack for backend applications

```sh
npm install webpack-node-externals --save-dev
```

- This will notify webpack what external modules are - modules that should not be bundled

```ts
const config: webpack.Configuration = {
  ...
  externals: [nodeExternals()],
  ...
  target: 'node',

};
```

---

- Some node_modules can be bundled with the build to allow for smaller final build.

**Example: Oauth-client**

```ts
externals: [
    nodeExternals(),
    {
      simpleoauth2: {
        commonjs: 'simple-oauth2',
        commonjs2: 'simple-oauth2',
        amd: 'simple-oauth2',
        root: 'simple-oauth2'
      }
    },
    {
      got: {
        commonjs: 'got',
        commonjs2: 'got',
        amd: 'got',
        root: 'got'
      }
    }
  ],
```

---

# Advantages

- Great documentation

- Vibrant plugin community to fit the needs of your project

- Optimizations

- Allows for enforcement of rules at the build stage


---

# Disadvantages

- Steep beginners learning curve.
    * Many websites had shown up to help create a beginning config file based on project configurations
      - [Webpack config tool](https://webpack.jakoblind.no/)
      - [Webpack config generator](https://doug2k1.github.io/webpack-generator/)

- Add additional development dependencies to your project

---
class: center, middle

# My webpack config

## Live Demo

---

class: center, middle

#Q&A
