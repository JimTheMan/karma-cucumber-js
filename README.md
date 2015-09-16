# karma-cucumber-js

This is yet another Cucumber.js adapter for Karma. It supports latest version of Cucumber.js. 
This adapter does not include Cucumber.js. Cucumber.js and jQuery (required by Cucumber.js) are peer dependencies.

## Getting Started
``` Shell
npm install jquery --save-dev
npm install cucumber --save-dev
npm install karma-cucumber-js --save-dev
```

### Configuring karma.conf.js
``` JavaScript
...
frameworks: ['cucumber-js'],
...
files: [
  // Feature files to test
  { pattern: 'features/*.feature', included: false },
  ... // Include JS files with step definitions and any other files they require
],
...
client: { // Specify this if you want to test features/scenarios with certain tags only
  args: ['--tags', '@frontend']
},
...
```

## Step Definitions
``` JavaScript
__adapter__.addStepDefinitions(function (scenario) {
    scenario.Given(/^there is a test step$/, function () { });
    scenario.When(/^it is executed$/, function () { });
    scenario.When(/^it is not executed$/, function (callback) { return callback.pending(); });
    scenario.Then(/^test succeeds$/, function () { });
    scenario.Then(/^test fails$/, function (callback) { return callback.fail(new Error('Step failed')); });
});
```

## License
Copyright (c) 2015 Eugene Shalyuk.
This project is licensed under the terms of the MIT license.