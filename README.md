# generator-yfiles-app [![NPM version][npm-image]][npm-url]
> A yeoman generator that scaffolds a [yFiles for HTML](https://www.yworks.com/yfileshtml) powered application. Requires a local yFiles for HTML package which can be [obtained and evaluated here](https://www.yworks.com/products/yfiles-for-html/evaluate).

Watch [this Youtube screencast](https://www.youtube.com/watch?v=Pj0yd1iFp9g) to see the generator in action.

## Installation

First, install [Yeoman](http://yeoman.io) and generator-yfiles-app using [npm](https://www.npmjs.com/) or [yarn](https://yarnpkg.com/) (we assume you have pre-installed [node.js](https://nodejs.org/)). 
The current version scaffolds yFiles for HTML 2.0 projects.

```bash
npm install -g yo
npm install -g generator-yfiles-app
```
or
```bash
yarn global add yo
yarn global add generator-yfiles-app
```

Then generate your new project:

```bash
yo yfiles-app
```

Simply answer a few questions and everything you need for your yFiles app is at the right place.

## Scaffold previous yFiles for HTML versions

To scaffold a **yFiles for HTML 1.3** project, please install v0.9.4 of the generator-yfiles-app, i.e:

```bash
npm install -g generator-yfiles-app@0.9.4
```

To scaffold a **yFiles for HTML 1.4** project, please install v0.9.5 of the generator-yfiles-app, i.e:

```bash
npm install -g generator-yfiles-app@0.9.5
```

To scaffold a **yFiles for HTML 2.0** project, please install v1.2.0 of the generator-yfiles-app, i.e:

```bash
npm install -g generator-yfiles-app@1.2.0
```

## About this generator

This generator scaffolds a yFiles for HTML application. It allows you to choose between different build tools and 
programming languages (ECMAScript 5, ECMAScript 6 (+Babel) and TypeScript).

Here is a rundown of the options you have:

#### Application name
The name of the app and of the first class. Only valid JavaScript identifiers (consisting of \[a-zA-Z$_]) are accepted.

#### Path of yFiles for HTML package
The path to the root of a valid yFiles for HTML package (e.g. "path/to/yFilesPackage"). This package must contain the following folders: 
 * "lib/yfiles"
 * "deployment"
 * "ide-support"

#### Path of license file
The path to a yFiles for HTML license.js file. The generator tries to guess the location of the license file
based on the yFiles for HTML package path. You may however want to specify a custom path here ("path/to/license.js").

#### Which kind of yFiles modules do you want to use?
Choose whether you want to consume the yFiles library as ES6 Modules or as UMD modules. 
 * **[UMD](https://github.com/umdjs/umd)** Use the "traditional" modules that work with AMD/require.js, commonjs (NodeJS) and as browser-globals. 
 * **ES6 Modules** Use the yFiles ES6 Modules and access the yFiles API members using [import statements](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import). Selecting this option *skips most of the following prompts*, as these are not applicable when using ES6 Modules. The resulting project will use webpack, so the resulting application will work in most browsers. 

#### Which build tool do you want to use?
You can choose between those build tools:
 * **none**: No build file is provided and you can run your ES5/ES6 app on supported browsers directly without the need of a compile step.
 * **[Grunt](http://gruntjs.com/)**: Adds a production build step (`npm run production`) that obfuscates and minifies the application and library sources. For development, the 
 application can be started directly without a build step. 
 * **[Browserify](http://browserify.org/)** Adds a production build step that obfuscates and minifies all JavaScript sources (using Grunt), 
 and bundles them to a single file using Browserify (`npm run production`). For development, a [Watchify](https://github.com/substack/watchify) build
 script is provided that enables fast turnaround times during development (`npm run watch`).
 * **[Webpack](https://github.com/webpack/webpack)** Adds a production build step that obfuscates and minifies all JavaScript sources (using Grunt), 
and bundles them to a single file using webpack (`npm run production`). For development, a 
[webpack-dev-server](https://webpack.js.org/configuration/dev-server/) configuration is provided that enables fast 
turnaround times during development (`npm start`).

#### Module loading method
Decide whether you want to load the library via
 * [AMD require](http://requirejs.org/docs/whyamd.html),
 * [systemjs](https://github.com/systemjs/systemjs) or
 * \<script\>-tags.
This option will not be available when webpack or Browserify have been selected as build tool, as the resulting bundle is included via \<script\>-tag.

#### Which modules do you want to use?
Choose which yFiles modules your app will need. For an overview of these take a look at the Developer's Guide's [module section](http://docs.yworks.com/yfileshtml/#/dguide/introduction-modules).
The generator will automatically optimize the set of modules to load.

#### Which language variant do you want to use?
Depending on your previous choices not all of the following choices for the source language will be available:
* **Pure ECMAScript 6** Write plain modern JavaScript (version 6) without a transpilation step. Code will not run without a transpile-step in Internet Explorer and other browsers from the stone age. 
* **ECMAScript 6 +[babel](https://babeljs.io/)** Write ECMAScript 6 sources, transpile to ECMAScript 5 with babel.
  If no other build tool (Grunt/Browserify/Webpack) is involved, use the `npm run babel` script for one-time transpiling, or the 
  `npm run dev` script for watch mode.  
* **[TypeScript](http://www.typescriptlang.org/)** Use TypeScript instead of plain JavaScript. Unless you also chose webpack
 (in which case TypeScript compilation will be part of the webpack bundling), use the `npm run build`
 script for one-time compilation, or the `npm run watch` script for watch mode. 
* **ES5** Use old ES5 for writing your code without using ES6 features like `class` etc. 

#### Which webpack version would you like to use?"
If you chose to use webpack, or if the chosen configuration requires webpack, you are
asked whether you want to use webpack 3 or webpack 4. 

#### Which package manager would you like to use?
Decide which package manager you want to use for managing packages and dependencies: 
 * [npm](https://www.npmjs.com/) or
 * [yarn](https://yarnpkg.com/)

This option will not be available for those variants where no third party software is required for transpiling or loading the app.

#### What else do you want?
 * **Use yfiles-typeinfo.js** Includes the yfiles-typeinfo.js file which provides runtime type checking during development time. 
 Remember to remove this file for production releases.
 Further information can be found [here](http://docs.yworks.com/yfileshtml/#/dguide/DevelopmentSupport#DevelopmentSupport-Checks)
 * **Visual Studio Code integration** Creates additional files required for [Visual Studio Codes'](https://code.visualstudio.com/) IntelliSense as well as a task runner if applicable.
 * **WebStorm/PHP-Storm/Intellij IDEA Ultimate Project files** Creates a simple project file structure for [JetBrains' IDEs](https://www.jetbrains.com/)' with libraries and directories set up correctly.


## License
MIT © [yWorks GmbH](http://www.yworks.com)


[npm-image]: https://badge.fury.io/js/generator-yfiles-app.svg
[npm-url]: https://npmjs.org/package/generator-yfiles-app
