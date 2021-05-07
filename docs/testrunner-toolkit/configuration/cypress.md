---
id: cypress
title: "Configuration Syntax: Cypress"
sidebar_label: Cypress
---
import Common from './common.md'


## Example Configuration

```yaml reference
https://github.com/saucelabs/saucectl-cypress-example/blob/master/.sauce/config.yml
```

## Common Configuration Parameters

<Common />

## Cypress Configuration Parameters

### `cypress`

__Description__: Details specific to the `cypress` configuration.

__Type__: *object*

__Example__:
```yaml
cypress:
  version: 6.6.0
  configFile: "cypress.json"
```

#### `version`

__Description__: Version of `cypress` to use during tests.

__Type__: *string*

__Example__:
```yaml
  version: ##VERSION##
```

#### `configFile`

__Description__: The designated `cypress` configuration file. `saucectl` determines related files based on the location of the config file. By default `saucectl` defers to the test file location defined in `cypress.json`.

__Type__: *string*

__Example__:
```yaml
  configFile: "cypress.json"
```

> For further information regarding cypress configurations, please consult the [Cypress documentation](https://docs.cypress.io/guides/references/configuration.html#Options).

#### `record`

__Description__: Record video of tests running.

__Type__: *boolean*

__Example__:
```yaml
  record: true
  key: $MY_SECRET_KEY
```

#### `key`

__Description__: Secret record key.

__Type__: *string*

__Example__:
```yaml
  record: true
  key: $MY_SECRET_KEY
```

In order for the `record` and `key` fields to work you must add the cypress `"projectId"` in your `cypress.json` file.

The value of your `projectId` correlates directly with the value of the `key` field; in this case `$MY_SECRET_KEY`.

:::note
Please refer to [this Cypress Documentation page](https://docs.cypress.io/guides/dashboard/projects.html#Project-ID) for further information about how to configure/retrieve the cypress `projectId`.

For more information about the cypress __Record Key__, please consult this [Cypress Documentation page](https://docs.cypress.io/guides/guides/command-line.html#cypress-run-record-key-lt-record-key-gt).
:::

### `suites`

__Description__: The set of parameters providing details about the test suites to run. You may include multiple suite definitions.

__Type__: *object*

__Example__:
```yaml reference
https://github.com/saucelabs/saucectl-cypress-example/blob/master/.sauce/config.yml#L23-L29
```


#### `name`

__Description__: Name of the test suite.

__Type__: *string*

__Example__:
```yaml
suites:
  - name: "saucy test"
```

#### `mode`

__Description__: Allows you to specify whether the individual suite will run on `docker` or `sauce`, potentially overriding the default project mode setting.

__Type__: *string*

__Example__:
```yaml
  mode: "sauce"
```

#### `env`

__Description__: Any ephemeral/environment variables needed to run cypress tests.

__Type__:  *string* | *int* | *float* | *boolean*

__Example__:

```yaml
      env:
        hello: world
```

#### `browser`

__Description__: Name of the browser in which the test runs.

__Type__: *string*

__Example__:
```yaml
    browser: "chrome"
```

#### `browserVersion`

<p><small><Highlight color="#ad1415">sauce cloud only</Highlight></small></p>

__Description__: Version of the browser in which the test runs.

__Type__: *string*

__Example__:
```yaml
    browserVersion: "85.0"
```

#### `platformName`

<p><small><Highlight color="#ad1415">sauce cloud only</Highlight></small></p>

__Description__: Operating system on which the browser and test runs. This value is optional and will be defaulted to a sensible platform. Set this value explicitly if you'd like to have greater control over where your tests should run.

__Type__: *string*

__Example__:
```yaml
    platformName: "Windows 10"
```

#### `screenResolution`

<p><small><Highlight color="#ad1415">sauce cloud only</Highlight></small></p>

__Description__: Field where you can change the browser window screen resolution. For a list of supported resolutions, see [Sauce Labs Custom Testing Options](https://wiki.saucelabs.com/display/DOCS/Test+Configuration+Options#TestConfigurationOptions-SauceLabsCustomTestingOptions).

__Type__: *string*

__Example__:
```yaml
    screenResolution: "1920x1080"
```

#### `config`

__Description__: Details specific to the cypress test configuration

__Type__: *object*

__Example__:
```yaml {5}
  suites:
    - name: "Hello"
    browser: "firefox"
    platformName: "Windows 10"
    config:
      env:
        hello: world
      testFiles: [ "**/*.*" ]
```

##### `testFiles`

__Description__: The specific location of the cypress test files (if not otherwise specified explicitly in `cypress.json`).

__Type__:  *string array* | *string* | *regex*

__Example__:

```yaml
      testFiles: [ "**/*.*" ]
```
