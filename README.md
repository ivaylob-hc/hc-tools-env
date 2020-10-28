# HashiCorp Tools Environment

## Overview

HashiCorp Tools Environment is a simple Bash script that helps you manage your local versions of HashiCorp tools like terraform, packer, vault, nomad and consul.


## UseCase

If you need to switch from one version of a tool like terroform to another you should first download the other version, extract it and rename the current version, etc. In other words there are too many actions to make this switch. This script helps you do that with a single command.


## Available options

```sh
$ hc-tools-env help

Usage:
    hc-tools-env <action> <tool> <params>
    hc-tools-env <use|install|use|versions> <terraform|packer|vault|nomad|consul> <remote [number]>

Examples:
    hc-tools-env use terraform-<version>, where <version> looks like terraform-0.12.29
    hc-tools-env install terraform-<version>
    hc-tools-env list terraform
    hc-tools-env list terraform remote <number>, where <number> in of versions to be listed (default is 20)
    hc-tools-env version
```


### The _use_ action

The _use_ action change deefault version of the specified tool to the specified version.

```commandline
$ hc-tools-env use terraform-0.13.3
Unavailable version terraform of 0.13.3
Downloading https://releases.hashicorp.com/terraform/0.13.3/terraform_0.13.3_darwin_amd64.zip
Using terraform-0.13.3
Terraform v0.13.3
```

> You'll get a message if the desired version is not available locally.

```commandline
$ hc-tools-env use terraform-0.12.26
Terraform v0.12.26
```


### The _install_ action

The _install_ action downloads the desired version of the tool and set this version as default.

```commandline
$ hc-tools-env install terraform-0.13.5
Downloading https://releases.hashicorp.com/terraform/0.13.5/terraform_0.13.5_darwin_amd64.zip
Using terraform-0.13.5
Terraform v0.13.5
```


### The _list_ action

* list _local_ versions of the specified tool

```commandline
$ hc-tools-env list terraform
0.12.26
0.12.24
0.12.21
0.12.20
0.12.19
0.12.16
0.12.13
0.12.12
0.12.10
0.12.6
0.11.8
```

* list _remote_ versions of the specified tool

```commandline
$ hc-tools-env list terraform remote
0.13.5
0.13.4
0.13.3
0.13.2
0.13.1
0.13.0
0.12.29
0.12.28
0.12.27
0.12.26
0.12.25
0.12.24
0.12.23
0.12.22
0.12.21
0.12.20
0.12.19
0.12.18
0.12.17
0.12.16
```

* list given _number_ of _remote_ versions of the specified tool

```commandline
$ hc-tools-env list terraform remote 7
0.13.5
0.13.4
0.13.3
0.13.2
0.13.1
0.13.0
0.12.29
```


### The _version_ action

 The _version_ action displays the current versions of all locally installed tools.

```commandline
$ hc-tools-env version
hc-tools-env    1.0.0
consul          1.5.2
nomad           0.9.3
packer          1.6.4
terraform       0.12.26
vault           1.2.1
```
