## Cache Clearing

```shell
 npm cache clean --force
```

###  Initial bug: `expect` function from vitest throws type error in TS

```
This expression is not callable.
  Type 'ExpectStatic' has no call signatures. ts(2349)
```
When running `npm test`, this would result in tests passing and the `expect` 
functioning as expect. My IDE (IntelliJ IDEA) would flag this as a type error.

Deleting `node_modules` and reinstalling with `npm i` did not work.

Clearing the cache after deleting `node_modules` and reinstalling removed 
the type error and fixed the problem.

This fixed the issue since `npm` was installing from previous the cache.

#### Resources that helped resolve the issue
[Type Error: ExpectStatic](https://github.com/vitest-dev/vitest/issues/5670)

[Clearing Cache](https://www.javatpoint.com/npm-clear-cache#:~:text=How%20to%20clear%20cache%3F&text=To%20clear%20a%20cache%20in,cache%20is%20not%20cleared%20simply.)