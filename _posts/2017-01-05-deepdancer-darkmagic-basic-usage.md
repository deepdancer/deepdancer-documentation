---
layout: page
title: "Basic Usage"
category: deepdancer-darkmagic
date: 2017-02-01 20:17:00
order: 1
---

### Declaring dependencies


```js
// This example is the most common use case a factory.

// The myModuleFactory will be called once with your depency as an argument.
var myModuleFactory = function(someOfMyProjectDependency, fs) {

    // This is what will be trully exposed to the rest of the components in
    // deepdancer
    var myModule = function(anArgument) {

    };

    return myModule;
};

// This should be processed as a factory
myModuleFactory.__type = 'factory'

module.exports = myModuleFactory
```

Comparing to deepdancer, you do not need to declare the dependencies, here an
alias can be registered to `someOfMyProjectDependency`

### Using dependencies

In the example above, `myProject/someOfMyProjectDependency` can be a
module declared somewhere in your code under the file name
`someOfMyProjectDependency.js` autoloaded by module inference.

### Running: calling your first dependencies somewhere

```js
// Once in the main file of your application you will need to instantiate the
// container to manage your dependencies.

// You shouldn't do this outside of your main file and your tests.
dependencies = new (require('deepdancer-darkmagic').Container)()

// This is optional but in the nominal case you want to tell that you module is
// composed of modules that are autoloading themselves in deepdancer. This means
// that their dependencies is loaded from the `__type`, `__lifespan`,
`__dependencies`, `__setupCalls` and `__arityCheck` attributes.
dependencies.setModulesAsAutoregistered('myProject')

// This aliases the submodules from myProject. For example `myProject/hello.js`,
// will be available under the alias `hello`. Ahead we are using a dependency
// named `someOfMyProjectDependency` and one named `fs`,
// `someOfMyProjectDependency` could be actually
// `myProject/someDirectory/someOfMyProjectDependency.js` and `fs` not declared
// as an alias, which would load it as a normal node module.
dependencies.registerAliasByRootPath('src/myProject', 'myProject')

dependencies.get('myProject/app').run()
```