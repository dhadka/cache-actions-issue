# The issue

This repo demonstrates an issue related to [`actions/cache`](https://github.com/actions/toolkit/tree/main/packages/cache) and binary files produced from C++ compilation. It seems that `actions/cache` is not able to restore some build artifacts in such a way that they can be reused from the second build.

# Repro steps

1. Build nodejs. The compilation produces `out` folder
2. Cache whole nodejs source along with `out` folder
3. Run second build
* Actual: An error is thrown - `/bin/sh: /Users/runner/work/cache-actions-issue/cache-actions-issue/nodejs/out/Release/mksnapshot: cannot execute binary file
make[1]: *** [ffb81844d4b5e90f0e9727f409709bbedd426bc1.intermediate] Error 126`. More info can be found [here](https://github.com/Fatme/cache-actions-issue/runs/1401957672?check_suite_focus=true).
* Expected: Green build that reuses cached nojes binaries

# How to run the project ?

1. Go to `Actions` tab
2. Run `nodejs-ci` workflow