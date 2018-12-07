# NPM Package Setup with [Verdaccio](https://verdaccio.org/docs/en/what-is-verdaccio) private npm registry

**Why ?** 
- publish package/module in the growing npm ecosystem 
- reusability of code/components throughout projects
- easy to share between developers/departments

## Windows Setup  
1. Install [Node LTS version](https://nodejs.org/en/) & test in terminal: `node -v`
2. If you don't have Python in PATH: one way (that worked for me) is to start Powershell as Administrator & run [`npm install -g windows-build-tools`](https://www.npmjs.com/package/windows-build-tools)
3. Install Verdaccio, again (I used) Powershell as Administrator & run [`npm install -g verdaccio`](https://www.npmjs.com/package/verdaccio) 

- **Remember** - in order to run npm modules/packages (that where installed globally (-g) as above) in the terminal/cmd/powershell, the **npm folder** (e.g. my npm folder is located in `C:\Users\ropo\AppData\Roaming\npm`) needs to be added to Windows PATH variable !

## Getting started to publish package
0. We want to run verdaccio -> make a package directory -> initialize npm package -> add user -> publish package 
1. Open the **first terminal** & run: `verdaccio` - this will show information about the config file & [http address](http://localhost:4873) of the verdaccio npm private server
2. Open a **second terminal** & run: `mkdir demo-package` & go into it `cd demo-package`
3. In the same terminal run: `npm init` - this will create package.json which can be modified later on, so just press enter all the way
4. Set the npm registry to the verdaccio server: `npm set registry http://localhost:4873`
5. Afterwards, register a user: `npm adduser --registry http://localhost:4873`
6. Lastly, publish npm package: `npm publish --registry http://localhost:4873`
7. [Now, check it out](http://localhost:4873)

- **Beware** - in order to re-publish the same package you will need to update/increment the package "version" in package.json
- **Useful** - If you want to delete a package or only a version of it, you can delete it from the `storage` of verdaccio on the server that hosts the package

## Setup on a server to pull package [to do]
0. We want to pull and use our package through `npm install --save package_name` in other projects for code reusability

## References & other useful links
- [Verdaccio installation](https://verdaccio.org/docs/en/installation)
- [Verdaccio github](https://github.com/verdaccio/verdaccio)
- [Publish your own npm package](https://hackernoon.com/publish-your-own-npm-package-946b19df577e)
- [NPM module boilerplate](https://github.com/flexdinesh/npm-module-boilerplate)
- [Host your own private npm repository with verdaccio](https://medium.com/devopslinks/host-your-own-private-npm-repository-with-verdaccio-e8a3202b97c5)
- [bitsrc - alternative to Verdaccio may be a commecial & better solution](https://bitsrc.io/)
