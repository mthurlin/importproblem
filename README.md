## Minimal repro of problem with ES6 import hoisting and circular dependencies

In https://github.com/mthurlin/importproblem/blob/master/src/prefix.js I would expect that ```prefix``` is always set to ```"foo"``` when the function ```addPrefix``` is run.

However, if ```prefix.js``` itself imports other files, and somewhere along the import chain another file imports ```prefix.js``` and uses ```addPrefix``` on the module level, the ```prefix``` will be undefined.

In this contrived example, the circular dependency is easily spotted, but in bigger code bases it is impossible to find manually.

1. Is this expected? (I kind of suspect it might be, due to import/export hoisting)
2. If it is expected, is there any way to warn about it or otherwise detect it?
