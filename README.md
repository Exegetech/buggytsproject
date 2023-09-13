# Buggy Ts Project

Repo for reproduction of stale build in `ts_project`.

## Steps A
This below steps work as expected:
1. Run `bazel clean` to make sure we start from a clean slate
2. Run `bazel build //mypackage/...`
3. Open `bazel-bin/mypackage/build/index.js`
4. Observe that the code is as expected
5. Change `mypackage/src/util.ts`
6. Run `bazel build //mypackage:build`
7. Open `bazel-bin/mypackage/build/index.js`
8. Observe that the code is as expected, i.e, the change in `mypackage/src/util.ts` is included

## Steps B
This below steps don't work as expected:
1. Run `bazel clean` to make sure we start from a clean slate
2. Open `mypackage/BUILD.bazel`
3. Uncomment the `transpiler`
4. Run `bazel build //mypackage/...`
5. Open `bazel-bin/mypackage/build/index.js`
6. Observe that the code is as expected
7. Change `mypackage/src/util.ts`
8. Run `bazel build //mypackage:build`
9. Open `bazel-bin/mypackage/build/index.js`
10. Observe that the code is not as expected, i.e, the change in `mypackage/src/util.ts` is not included

What should happen: the change in `mypackage/src/utils.ts` should be reflected in `bazel-bin/mypackage/build/index.js` in steps B

