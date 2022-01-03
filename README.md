# heroku-buildpack-node-preinstall
Heroku buildpack used for running commands before installing Node. 

Currently used for overriding the .npmrc file in the build directory with the contents of a config var for authorizing with npm when installing private packages.

## Add Buildpack
Add the buildpack to your Heroku app either using the CLI or the Heroku dashboard. 

**The `heroku-buildpack-node-preinstall` needs to run before any buildpack using npm**. In the following example, it runs before the `heroku/nodejs` buildpack:
```bash
$ heroku buildpacks:set --index 1 https://github.com/offerzen/heroku-buildpack-node-preinstall.git
$ heroku buildpacks:add heroku/nodejs
```

## Configure Config Var
Add the NPMRC config var in Heroku with the contents of your .npmrc file.

Environment variable Name:
```
NPMRC
```
Environment variable Value: 
```
@offerzen:registry=https://npm.pkg.github.com
//npm.pkg.github.com/:_authToken=<secret auth token>
```
