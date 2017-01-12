---
layout: page
title: "Example"
category: deepdancer-darkmagic
date: 2017-02-01 20:17:00
order: 2
---

**deepdancer has a
[demo project](https://github.com/deepdancer/deepdancer-demo), you will not see
much code here but link to this project.**

From scratch
===

The [master branch](https://github.com/deepdancer/deepdancer-demo/tree/master)
does not use dependency injection, the
[deepdancer-darkmagic
branch](https://github.com/deepdancer/deepdancer-demo/tree/deepdancer-darkmagic)
uses deepdancer-darkmagic.

By comparing the two branches you can get the essence of what
deepdancer-darkmagic brings to your project. We suggest that you at read
first [deepdancer example](/documentation{% post_url 2017-01-04-deepdancer-example %}) before
diving here.

From deepdancer
===

If you have already understood deepdancer.

The [master branch](https://github.com/deepdancer/deepdancer-demo/tree/deepdancer)
uses deepdancer, the
[deepdancer-darkmagic
branch](https://github.com/deepdancer/deepdancer-demo/tree/deepdancer-darkmagic)
uses deepdancer-darkmagic.

Quickly check how configuring deepdancer is affected by deepdancer-darkmagic
comparing
[`dependencies.js@deepdancer`](https://github.com/deepdancer/deepdancer-demo/blob/deepdancer/src/deepdancer-demo/dependencies.js)
and
[dependencies.js@deepdancer-darkmagic](https://github.com/deepdancer/deepdancer-demo/blob/deepdancer-darkmagic/src/deepdancer-demo/dependencies.js):

* deepdancer-darkmagic literraly replaces deepdancer.
* We need to register dependencies's alias, this enables us to treat
`deepdancer-demo/service/user/upsertUser` as `upsertUser`. Note that this is
 a suitable function parameter name.
* Similarily, we alias also external dependencies to potential function
parameter names, for example `fs-promise` to `fsPromise`.

Now this all start to makes sense when we look at one service
[upsertUser.js@deepdancer-darkmagic](https://github.com/deepdancer/deepdancer-demo/blob/deepdancer-darkmagic/src/deepdancer-demo/service/user/upsertUser.js)
(for reference here is
[upsertUser.js@deepdancer](https://github.com/deepdancer/deepdancer-demo/blob/deepdancer/src/deepdancer-demo/service/user/upsertUser.js)):

* The `__dependencies` array is not required anymore.
* The functions parameters names are used as dependencies name in the container.
