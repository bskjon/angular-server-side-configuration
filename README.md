# angular-server-side-configuration

Configure an angular application at runtime on the server or in a docker container via environment variables.

## Motivation

The Angular CLI provides build time configuration (via environment.ts).
In a Continuous Delivery environment this is sometimes not enough.

## How it works

Environment variables are used for configuration.
This package provides an Angular CLI builder to search for usages at build time.
A [native CLI](#on-host-server-or-in-dockerfile) can be used to insert populated
environment variables into index.html file(s) into the head tag or by replacing `<!--CONFIG-->`
(Missing environment variables will be represented by `null`). This should be done
on the host serving the bundled angular files.

Starting with version 13, there are experimental builders for the `build` and `serve` commands.
To install the experimental builders run `ng add angular-server-side-configuration` and answer
`Would you like to use the experimental builders for build and serve?` with `y(es)`.

## Getting Started

```
ng add angular-server-side-configuration
```

or, if you have a previous version of this library installed

```
ng update angular-server-side-configuration@latest
```

This will configure the appropriate files.

Alternatively, if you want to configure the files yourself:

```
npm install --save angular-server-side-configuration
```

### angular.json

Ensure you have an `ngsscbuild` entry in your project `architect` section.
To use the builder run `ng run your-project-name:ngsscbuild:production`.
You can add additional configurations in angular.json, which can be executed
by replacing `production` with your configuration name in the previous command.

The builder will analyze the configured `ngsscEnvironmentFile` to detect
used environment variables and generate an [ngssc.json](#ngsscjson) in the defined
`outputPath` in the referenced `browserTarget`.

```json
...
  "projects": {
    ...
    "your-project-name": {
      ...
      "architect": {
        ...
        "ngsscbuild": {
          "builder": "angular-server-side-configuration:ngsscbuild",
          "options": {
            "additionalEnvironmentVariables": ["MANUAL_ENTRIES"],
            "browserTarget": "your-project-name:build",
            "ngsscEnvironmentFile": "src/environments/environment.prod.ts",
            // Optional
            // (Defaults to the basename of the index option of the browser target)
            "filePattern": "index.html"
          },
          "configurations": {
            "production": {
              "browserTarget": "your-project-name:build:production"
            }
          }
        }
        ...
      }
      ...
    }
    ...
  }
...
```

To run the ngssc build, run the command `ng run your-project-name:ngsscbuild:production`.

### environment.prod.ts

angular-server-side-configuration supports two variants for using environment variables:
process.env._ or NG_ENV._ (_Deprecated_)

#### process.env.\*

Use process.env.NAME in your environment.prod.ts, where NAME is the
environment variable that should be used.

```typescript
import 'angular-server-side-configuration/process';

export const environment = {
  production: process.env.PROD !== 'false',
  apiAddress: process.env.API_ADDRESS || 'https://example-api.com',
};
```

#### NG\_ENV.\* *Deprecated*

Import NG_ENV from `angular-server-side-configuration/ng-env`
and use NG_ENV.NAME in your environment.prod.ts, where NAME is the
environment variable that should be used.

```typescript
import { NG_ENV } from 'angular-server-side-configuration/ng-env';

export const environment = {
  production: NG_ENV.PROD !== 'false',
  apiAddress: NG_ENV.API_ADDRESS || 'https://example-api.com',
};
```

### index.html (Optional)

Add `<!--CONFIG-->` to index.html. This will be replaced by the configuration script tag.
This is optional, as the environment variables can be configured to be inserted in the head tag.
It is however the safest option.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <title>Angular Example</title>
    <!--CONFIG-->
    <base href="/" />

    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <link rel="icon" type="image/x-icon" href="favicon.ico" />
  </head>
  <body>
    <app-root></app-root>
  </body>
</html>
```

### On host server or in Dockerfile

This library provides a Node.js and a native implementation for inserting the environment variables into your html.
Either use the `insert` function from the package (`import { insert } from 'angular-server-side-configuration';`)
or the `insert` command of the CLI.
For the native CLI, go to [Releases](https://github.com/kyubisation/angular-server-side-configuration/releases)
and download the appropriate executable for your server environment.
(See [build.sh](https://github.com/kyubisation/angular-server-side-configuration/blob/master/cli/build.sh) for
build details of the native CLI. Please open an [Issue](https://github.com/kyubisation/angular-server-side-configuration/issues/new)
if you need an additional environment.)

#### ngssc insert

Insert environment variables. Looks for an ngssc.json file inside the current or
given directory. Directory defaults to current working directory.

Usage: ngssc insert [options] [directory]

| Options           | Description                                                                                                                                |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| `--recursive, -r` | Recursively searches for ngssc.json files and applies the contained configuration.                                                         |
| `--nginx`         | Applies default configuration for ngssc insert to work with nginx. Sets working directory to /usr/share/nginx/html/ and recursive to true. |
| `--dry`           | Perform the insert without actually inserting the variables.                                                                               |

#### ngssc substitute

Substitutes the variable \$\{NGSSC_CSP_HASH\} in files ending with ".template"
and copies the file while removing the ".template" extension.

\$\{NGSSC_CSP_HASH\} represents the CSP hash value of the IIFE generated/inserted by the
insert command, wrapped by single quotes.

By default looks for "\*.template" files in the current working directory. Specify another
directory to search for "\*.template" files via argument.
(e.g. `ngssc substitute /path/to/template/files`)

When applying the variable(s), the file is copied to the same directory without the
".template" extension with the substituion applied.
(e.g. `ngssc substitute`: /a/my.conf.template => /a/my.conf)

Use the "--out" flag to define a different output directory.
(e.g. `ngssc substitute --out=/b`: /a/my.conf.template => /b/my.conf)

Optionally supports substituting environment variables with the --include-env flag.
The format \$\{EXAMPLE\} must be used (\$EXAMPLE will not work). Additionally only
alphanumeric characters and \_ are allowed as variable names (e.g. \$\{EXAMPLE_KEY\}).
(e.g. `ngssc substitute --include-env`)

**ATTENTION**: Since the official nginx container image already provides a similar mechanism
with substitution, it is recommended **not** to use the `/etc/nginx/templates` directory.
Instead use the directory `/etc/nginx/ngssc-templates`.

Usage: ngssc substitute [options] [directory]

| Options                | Description                                                                                                                                                                                                                                 |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `--ngssc-path`         | Path to the ngssc.json file or containing directory to be used for the generated IIFE. Supports glob. Defaults to [current working directory]/\*\*/ngssc.json. Throws if multiple ngssc.json with different variant or variables are found. |
| `--hash-algorithm, -a` | The hash algorithm to be used. Supports sha256, sha384 and sha512. Defaults to sha512.                                                                                                                                                      |
| `--out, -o`            | The directory into which the updated files should be copied.                                                                                                                                                                                |
| `--include-env, -e`    | Substitute all variables in the format of \$\{VARIABLE_NAME\}.                                                                                                                                                                              |
| `--nginx`              | Applies default configuration for ngssc substitute to work with nginx. Sets ngssc-path to /usr/share/nginx/html/, template directory to /etc/nginx/ngssc-templates/ and out directory to /etc/nginx/conf.d/.                                |
| `--dry`                | Perform the insert without actually inserting the variables                                                                                                                                                                                 |

##### Minimal Example

Dockerfile

```Dockerfile
FROM nginx:alpine

# Install ngssc binary
ADD https://github.com/kyubisation/angular-server-side-configuration/releases/download/v14.0.1/ngssc_64bit /usr/sbin/ngssc
RUN chmod +x /usr/sbin/ngssc

# Add ngssc init script
COPY ngssc.sh /docker-entrypoint.d/ngssc.sh
RUN chmod +x /docker-entrypoint.d/ngssc.sh

# Copy app
COPY dist /usr/share/nginx/html
```

ngssc.sh

```bash
#!/bin/sh
ngssc insert /usr/share/nginx/html
# Substitute CSP variable (and optionally environment variables)
# See documentation above
#ngssc substitute --ngssc-path=/usr/share/nginx/html -o=/etc/nginx/conf.d/ /etc/nginx/ngssc-templates/
```

### ngssc.json

The ngssc.json will be generated by the ngsscbuild builder.

```javascript
{
  "variant": "process",           // Either "process" or "NG_ENV".
  "environmentVariables": [],     // Detected environment variables.
  "filePattern": "**/index.html"  // File pattern in which environment variables should be inserted.
}
```

## License

Apache License, Version 2.0
