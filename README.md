## Demo of jest --init failing

Followed the instructions at https://jestjs.io/docs/en/getting-started.html

```bash
yarn add --dev jest
```

Create the:

- `sum.js`
- `sum.test.js`

And updated:

- `package.json` as specified

Then executed the additional configuration:

```
% jest --init
yarn run v1.22.19
$ /Volumes/Projects/demo-jest-failure/node_modules/.bin/jest --init

The following questions will help Jest to create a suitable configuration for your project

✔ Would you like to use Jest when running "test" script in "package.json"? … yes
✔ Would you like to use Typescript for the configuration file? … no
✔ Choose the test environment that will be used for testing › jsdom (browser-like)
✔ Do you want Jest to add coverage reports? … no
✔ Which provider should be used to instrument code for coverage? › babel
✔ Automatically clear mock calls, instances, contexts and results before every test? … no

✏️  Modified /Volumes/Projects/demo-jest-failure/package.json

📝  Configuration file created at /Volumes/Projects/demo-jest-failure/jest.config.js
✨  Done in 25.77s.
```

But after running:

```
% yarn test
yarn run v1.22.19
$ jest
 FAIL  src/index.test.js
  ● Test suite failed to run

    SecurityError: localStorage is not available for opaque origins

Test Suites: 1 failed, 1 total
Tests:       0 total
Snapshots:   0 total
Time:        0.305 s
Ran all test suites.
```

Even if we add the `testEnvironmentOptions.url` to the `jest.config.js`:

```js
// The test environment that will be used for testing
testEnvironment: "jsdom",

// Options that will be passed to the testEnvironment
testEnvironmentOptions: {
    url: "http://localhost/"
},
```
