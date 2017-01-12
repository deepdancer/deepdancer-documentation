---
layout: page
title: "Reference"
category: deepdancer-darkmagic
date: 2017-02-01 20:17:00
order: 3
---

The key feature of deepdancer-darkmagic is to prevent you from declaring
manually the `__dependencies` attribute of your module. If the module is of
`__type` `factory` or `class`. deepdancer-darkmagic will infer the missing
`__dependencies` from the arguments names.

### Container methods

#### registerAliasByRootPath(rootPath, rootModule, ignore = [])


Arguments:

* `rootPath`: the path to scan for files.
* `rootModule`: the root module existing inside this path.
* `ignore` (optional): an array of regular expressions or strings to ignore.


Automatically registers an alias under the given `rootPath` containing the
`rootModule` modules.

For example, if you wish to register alias for the module `mylibrary` stored in
`./src/mylibrary`, it contains modules like 'mylibrary/alpha', 'mylibrary/beta',
'mylibrary/gamma'. `registerAliasByRootPath('./src/mylibrary', 'mylibrary')`
will scan for files `./src/mylibrary` either ending with a `coffee` or `js`
extension, and for files it found an alias and let you require `gamma` instead
of `mylibrary/gamma`.

This makes leveraging the dependencies inference easy.


