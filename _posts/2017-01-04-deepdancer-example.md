---
layout: page
title: "Example"
category: deepdancer
date: 2017-02-01 20:17:00
order: 2
---

**deepdancer has a [demo project](https://github.com/deepdancer/deepdancer-demo),
you will not see much code here but link to this project.**

The [master branch](https://github.com/deepdancer/deepdancer-demo/tree/master)
does not use dependency injection, the
[deepdancer
branch](https://github.com/deepdancer/deepdancer-demo/tree/deepdancer) uses
deepdancer.

By comparing the two branches you can get the essence of what deepdancer brings
to your project.

### Tests without dependency injection

We are only able to [test some high level usage of our
service](https://github.com/deepdancer/deepdancer-demo/blob/master/test/deepdancer-demo/service/user/upsertUserTest.js).
The test in the master branch tests that our service is doing its job, we give
it an ip address, it retrieves the location from this address and stores
everything somewhere.

This is a nice test to have because it tests all components integrated, but it
lacks of specificity. If the location service fails the test will obviously fail
but we will not if the problem comes from the inside or the outside of our
service.

### Tests with deepdancer

We can see that [our test is now
expanded](https://github.com/deepdancer/deepdancer-demo/blob/deepdancer/test/deepdancer-demo/service/user/upsertUserTest.js),
and it contains true unit tests as we are mocking dependencies.

### Initialization

The [initialization code fits in four
lines](https://github.com/deepdancer/deepdancer-demo/blob/deepdancer/src/deepdancer-demo/dependencies.js).

### Impact on modules

Before deepdancer integration:
[upsertUser.js@master](https://github.com/deepdancer/deepdancer-demo/blob/master/src/deepdancer-demo/service/user/upsertUser.js).

After: [upsertUser.js@deepdancer](https://github.com/deepdancer/deepdancer-demo/blob/deepdancer/src/deepdancer-demo/service/user/upsertUser.js).

Mostly the service is wrapped in a function that serves as a factory, the
dependencies are passed are parameters of this function. The `__dependencies`
informs deepdancer about the dependencies to inject.

If you find this too verbose deependancer-darkmagic is here to solve your
problem.

Note that if you leave dependencies, like
[getLocationFromIp.js](https://github.com/deepdancer/deepdancer-demo/blob/deepdancer/src/deepdancer-demo/service/location/getLocationFromIp.js),
unchanged it will work. **deepdancer does not force you to migrate all your code,
dependencies can be plain normal node modules, of course if you depend on a
deepdancer factory or class, your old code will obviously fail.**