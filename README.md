# roe-cli

[![PyPI version](https://badge.fury.io/py/roe.svg)](https://badge.fury.io/py/roe)
[![pypi supported versions](https://img.shields.io/pypi/pyversions/roe.svg)](https://pypi.python.org/pypi/roe)

This utility helps you deploy your code as an API locally on your machine
using [Docker](https://www.docker.com/products/docker-desktop). It is a python based package that can be installed via
pip.

## Quickstart

1. Install roe: `pip install roe`

2. Deploy your package : `roe deploy -l path/to/package/folder`

   eg: `roe deploy -l /Users/abcdef@ghi.com/Documents/git/myProject`

   Note: you will be prompted to enter your **docker hub username, password, and email**

You can find a sample project [here.](https://github.com/chainopt/roe-cli/tree/main/samples/myProject)

----

#### - Deploy Package Arguments and Options

`roe deploy -l path/to/package/folder`

* `-l` is for local deployment (only local is available for now).
* `-n` is for specifying a package name. If left out, the folder name is chosen as package name.
* `-p` is a port you specify for it to be spun up on(The valid range is 1024-65535). If left out, a port will be
  assigned.
* `-q` is to deploy with no extra prompts to affirm redeployments and no webpage opening when finishing the deployment.

#### - Re-deploying a package.

`roe deploy -l path/to/package/folder`

#### If you used a custom name for your package, you will have to specify it with the package name (-n) flag just like you did initially.

e.g. `roe deploy -l /Users/abcdef@ghi.com/Documents/git/myUpdatedProject`
or

`roe deploy -l -n myCustomName /Users/abcdef@ghi.com/Documents/git/myUpdatedProject`

>Note: It will re-use the port from the first deployment.
---
### Other commands:

| Description                 | Command                                 |
| ----------------------------|-----------------------------------------|
| Verify package configuration| `roe verify -l path/to/package/folder`  |
| List packages deployed      | `roe list -l`                           |
| Stop a package ¹            | `roe stop -l myProject`                 |
| Stop all packages           | `roe stop -l --all`                     |
| Start a package             | `roe start -l myProject`                |
| Start all packages          | `roe start -l --all`                    |
| Undeploy a package          | `roe undeploy -l myProject`             |
| Undeploy all packages       | `roe undeploy -l --all`                 |
| Begin ROE session ² ³       | `roe begin -l`                          |
| End ROE session             | `roe end -l`                            |

¹ If a model API associated with this package is running, you will be asked to enter 'Y' to stop it and proceed with
deleting the package.

² A ROE Session begins automatically upon running `roe deploy` or `roe list`.

³ You can also point to a yaml file like this:
`roe begin -l -f /Users/myUser/Documents/docker-creds.yaml`. Download a sample credential
file [here.](https://github.com/chainopt/roe-cli/tree/main/samples/credentials.yaml)

##### You can use the `--help` command in front of any command from within the CLI for help with options and arguments.

##### Eg: `roe deploy --help`
----