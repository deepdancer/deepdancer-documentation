---
layout: page
title: "Intentions"
category: deepdancer
date: 2017-02-01 20:17:00
order: 0
---

A dependency injections system that:

* Requires only a light configuration
* Fallbacks to loading a module when a key is not declared
* Has its dependencies declared inside the modules (to reduce the probability
to miss an update)
* Support the overriding of the dependencies (for the purpose of testing)
* In my usecase, most if not all of my dependencies are named according to the
path of the module they contain. So far you should be able to name your
dependencies the way you want.

[http://xkcd.com/927/](http://xkcd.com/927/)

Similar project: [knit](https://github.com/nicocube/knit)

### Pros


* The above **Intentions**.
* High test coverage.
* Tested and improved since more than nine months before release on the backend
of https://konnectr.co/ , a coverage of more than 90% on the core of the
application (we probably have your use cases covered).

### Cons

* The library being resolving dependency recursively, the callstack may
be quite long when an error occures while loading an object.