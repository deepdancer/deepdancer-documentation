---
layout: page
title: "Example"
category: deepdancer-callgraph
date: 2017-01-12 20:17:00
order: 2
---

deepdancer has a
[demo project](https://github.com/deepdancer/deepdancer-demo). Code here is
based on this demo project on the
[deepdancer-darkmagic](https://github.com/deepdancer/deepdancer-demo/tree/deepdancer-darkmagic)
branch.

### Install deepdancer-callgraph

```bash
npm install --save-dev deepdancer-callgraph
```

### Create a script enabling the graph generation

For the example we have call it callgraph.js:

```js
var dependencies = require('deepdancer-demo/dependencies');
var dependenciesCallgraph = require('deepdancer-callgraph');

dependencies.eagerLoad();
console.log(dependenciesCallgraph(dependencies));
```

Not the console.log is actually making the ouput.

### Visualize the graph

You need to have `graphviz` installed in order to have the `dot` command
available.

```bash
node callgraph.js > callgraph.dot
dot -Tsvg callgraph.dot > callgraph.svg
```

And here you go:

<div class="callgraph-container">
    <img class="callgraph" src="/documentation/res/deepdancer-demo-callgraph.svg" alt="deepdancer demo callgraph">
</div>

A clear view of your dependencies and a nice way to identify design problems.