# `yarn-3-link-step-regression`

This reproduces a performance regression in "Link step" when installing with Yarn 3.

There are two directories in this codebase: one with Yarn 2.4.1 and one with Yarn 3.0.1. Each has three workspaces with a long list of the [most popular NPM dependencies](https://gist.github.com/anvaka/8e8fa57c7ee1350e3491).

To reproduce the issue:

1. `cd yarn-2.4.1 && yarn install` to warm the cache. This will take some time.
2. Run `yarn install` a few times and notice how long the "Link step" and total install time takes.
3. `cd ../yarn-3.0.1 && yarn install` to warm that cache. This will take some time.
4. Run `yarn install` a few times and notice that the "Link step" takes about 2x longer for Yarn 3.0.1 than it does for 2.4.1.
