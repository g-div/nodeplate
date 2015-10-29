# nodeplate

![](https://david-dm.org/g-div/nodeplate/status.svg)
![](https://david-dm.org/g-div/nodeplate/dev-status.svg)

A boilerplate for your rock-solid node.js projects. Includes static code analysis, development and building tools.

## What's included ?

- **Babel transpiling** ```npm start``` (using [babel](https://babeljs.io/))

  Write your code in [ES6](https://babeljs.io/docs/learn-es2015/).

- **Watch files and reload** ```npm run dev``` (using [nodemon](https://github.com/remy/nodemon))

  Run your script and watch for changes.

- **Debugging** ```npm run debug``` (using [babel-node-debug](https://github.com/crabdude/babel-node-debug))

  Debug your application using a babel-compatible version of [node-inspector](https://github.com/node-inspector/node-inspector).

- **Test runner** ```npm test``` (using [lab](https://github.com/hapijs/lab))

  Write your tests in the ```test``` folder and run them with ```npm test```.

- **Code coverage** ```npm run coverage``` (using [lab](https://github.com/hapijs/lab))

  Lab can also calculate the code coverage.

- **Code linting** ```npm run lint``` (using [xo](https://github.com/sindresorhus/xo))

  Lint your code (even **ES6/7** and **JSX**).

- **Code format** ```npm run format``` (using [esformatter](https://github.com/millermedeiros/esformatter))

  Beautify and format you code.

- **Recognize duplicate code** ```npm run inspect``` (using [jsinspect](https://github.com/danielstjules/jsinspect))

  Recognize duplicate, copy-pasted and similar code.

- **License checker** ```npm run licenses``` (using [license-checker](https://github.com/davglass/license-checker))

  Print the link and the license type of each dependency

- **Package building** ```npm run build``` (using [nar](https://github.com/h2non/nar))

  You can build an executable file out of your project including all dependencies.

  Please refer to *nar*'s documentation if you like to include a custom *node.js* version or to build a package for a different system-architecture/OS. You should simple edit the ```build```property in the ```scripts``` section of ```package.json``` to something like:
```sh    
    nar create --executable --os darwin --arch x64 --node 0.12.0
```

- **Find vulnerabilities** ```npm run deps:sec``` (using [nsp](https://github.com/nodesecurity/nsp))

  *nsp* (*Node Security Project*) will check if any dependency is affected by a known vulnerability.

- **Keep dependencies up-to-date** ```npm run deps:updates``` (using [david](https://github.com/alanshaw/david))

  David keeps dependencies up-to-date and will help you to [update](https://github.com/alanshaw/david#update-to-latest) them.

- **README generator** ```npm run readme``` (using [node-readme](https://github.com/revolunet/node-readme))

    Generate a README like this from an ES6 template extracting data from ```package.json```.
    Edit the ```.README.md``` template and run the command. Check the [node-readme documentation](https://github.com/revolunet/node-readme#custom-template) for all available variables/functions.

    **Do not edit the ```README.md```** in your project folder, since this will be **overwritten** running the ```npm run readme``` command.

- **Git hooks** (using [husky](https://github.com/typicode/husky))

  Custom ```precommit``` and ```prepush``` are defined in order to run tests (and vulnerabilities discovery) on commit and push. You can define your own in the ```package.json```


- **[npm-run-all](https://github.com/mysticatea/npm-run-all)**

## Install

```sh
git clone https://github.com/g-div/nodeplate
cd nodeplate
npm install
```

## Usage
Use ```npm``` commands listed above as following:
```sh
npm run lint
npm run test:deps
```

or use [npm-run-all](https://github.com/mysticatea/npm-run-all):
```sh
npm-run-all --parallel lint test:deps test --sequential build
```

## Scripts

 - **npm run readme** : `node-readme`
 - **npm run precommit** : `npm test`
 - **npm run prepush** : `npm-run-all lint test test:deps`
 - **npm run start** : `babel-node $npm_package_main`
 - **npm run dev** : `nodemon --exec babel-node -- $npm_package_main`
 - **npm run debug** : `babel-node-debug $npm_package_main`
 - **npm run lint** : `xo`
 - **npm run inspect** : `jsinspect`
 - **npm run test** : `lab`
 - **npm run covreage** : `lab -r lcov`
 - **npm run format** : `esformatter -i '**/*.js'`
 - **npm run build** : `nar create --executable`
 - **npm run deps:sec** : `nsp audit-package`
 - **npm run deps:updates** : `david`
 - **npm run test:deps** : `npm-run-all deps:sec deps:updates`
 - **npm run licenses** : `license-checker`

## Dependencies

Package | Version | Dev
--- |:---:|:---:
[babel](https://www.npmjs.com/package/babel) | ^5.8.29 | ✔
[babel-node-debug](https://www.npmjs.com/package/babel-node-debug) | ^1.3.0 | ✔
[david](https://www.npmjs.com/package/david) | ^6.4.0 | ✔
[esformatter](https://www.npmjs.com/package/esformatter) | ^0.8.1 | ✔
[husky](https://www.npmjs.com/package/husky) | ^0.10.1 | ✔
[jsinspect](https://www.npmjs.com/package/jsinspect) | ^0.7.0 | ✔
[lab](https://www.npmjs.com/package/lab) | ^7.0.0 | ✔
[license-checker](https://www.npmjs.com/package/license-checker) | ^4.2.0 | ✔
[nar](https://www.npmjs.com/package/nar) | ^0.3.20 | ✔
[node-readme](https://www.npmjs.com/package/node-readme) | ^0.1.9 | ✔
[nodemon](https://www.npmjs.com/package/nodemon) | ^1.8.0 | ✔
[npm-run-all](https://www.npmjs.com/package/npm-run-all) | ^1.2.12 | ✔
[nsp](https://www.npmjs.com/package/nsp) | ^1.1.0 | ✔
[xo](https://www.npmjs.com/package/xo) | ^0.10.1 | ✔


## TODOs:
- [ ] Documentation tool (JSDoc, dox, ...)
- [ ] Aggregate commands using npm-run-all
- [ ] Use a scaffolding system (init)
- [ ] Consider [standard](https://github.com/feross/standard) instead of **xo**
- [ ] Fix **nar**: should be able to use $npm_package_main variable
- [ ] Consider [strong-build](https://github.com/strongloop/strong-build) instead of **nar**
- [ ] Consider [semantic-release](https://github.com/semantic-release/semantic-release)
- [ ] Consider [hotel](https://github.com/typicode/hotel) and [minihost](https://github.com/typicode/minihost)

## Contributing

Contributions welcome; Please submit all pull requests the against master branch.

## Author

g-div <undefined> http://github.com/g-div

## License

 - **ISC** : http://opensource.org/licenses/ISC
