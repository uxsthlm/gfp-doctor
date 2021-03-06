# gfp-doctor
A command-line tool to help identify problems with GFP modules

## Installation

```
npm install gfp-doctor -g
```

## Usage

When in a GFP repository folder, run `gfp-doctor`

```
Usage: gfp-doctor [options]

  Options:

    -V, --version               output the version number
    -v, --verbose
    -s, --silent
    -pp, --package-path <path>  override default path for package.json
    -h, --help                  output usage information
```

## Checks

1. `package.json`
    1. Should use `eslint-config-gfp`
    1. Should use public npm version of `eslint-config-gfp`
    1. Should use public npm version `angular-module-no-deps`
    1. Should use `documentation`
    1. Should use some `lint` script
    1. Should use `phantomjs-prebuilt`, not old `phantomjs`
    1. Should use `karma-phantomjs-launcher` 1 and up
    1. Should use prepush hooks
    1. Should use public `require-polyfill`
    1. Should use `eslint-config-gfp` 3.0.0 and up
    1. Should run `gfp-doctor` as `postinstall`
    1. Should use `karma` 1.7.0 and up
    1. Should use `karma-coverage` 1.1.0 and up
    1. Should use `karma-jasmine` 1.1.0 and up
1. `.eslintrc`
    1. Should use `valid-jsdoc` rule
    1. Should use `require-jsdoc` rule
1. `karma.conf.js`
    1. Should use `angular` and `angular-mocks` from `node_modules`
1. `bower.json`
    1. Should not have `"version"` property


## Contributing

Create a branch or fork, then submit PR.

Remember to:

* Update CHANGELOG.md
* Update README.md
* `npm run lint`
* `npm test`

Please respect the `.editorconfig` and `.eslintrc`. Basically:

* UTF-8
* Unix linebreaks
* 4 space indentation
* Semicolons


### Adding new tests

1. Create a new file in `/lib` and require it in `lib/index.js`
2. The new file should return an array with the following format to the `run` function in `lib/index.js`:
```
[
    {
        desc: 'a description of the test being made',
        errorMsg: 'a descriptive error message and proposed solution',
        passed: Boolean
    },
    {...}
]
```
