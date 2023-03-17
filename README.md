
Copyright (c) 2023 SURF bv

All rights reserved. This software is distributed under the Apache 2.0 license. For more information, see LICENSE

## INTRODUCTION

These test scripts were created for the development and testing of the eduID Wallet PoC. The scripts leverage IRMA CLI commands to quickly issue or verify credential statements for use with an IRMA/YiVi wallet or the demo wallet created as part of this PoC.

## PREREQUISITES
To use these scripts you need to install the IRMA CLI client, as described in the IRMA documentation (see below).

Depending on your OS, you may also need to install 'jq' and 'qrencode'.

## USING THE TOOL

### IRMA CLI Instructions

#### Step 1

Download and install the IRMA CLI
from [here](https://gitlab.science.ru.nl/irma/github-mirrors/irmago/-/jobs/artifacts/master/download?job=binaries)
using the instruction from [this docs page](https://irma.app/docs/irma-cli/).

#### Step 2

Clone the custom `irma-demo` scheme and revoke the write permissions to the `schemes` directory (to
prevent automatic scheme updates).

```shell
$ mkdir schemes
$ cd schemes
$ git clone 'https://github.com/surfnet-niels/irma-demo-schememanager.git' niels-irma-demo
$ cd ..
$ chmod -R -w schemes
```

#### Step 3

Make sure to have `jq` installed seeing as it's used to one-line the session JSON using the `-c` flag.

Start an issuance request:

```shell
$ irma session --disable-schemes-update --schemes-path ~/your/path/to/schemes --request "$(cat irmacli/sessions/issuance_session_eduid.json | jq -c)"
```

#### Step 4

Start a disclosure request:

```shell
$ irma session --disable-schemes-update --schemes-path ~/your/path/to/schemes --request "$(cat irmacli/sessions/disclosure_session_eduid.json | jq -c)"
```



## CONTACT

Questions/remarks/suggestions/praise regarding this tool can be sent to:

Niels van Dijk  - <niels.vandijk@surf.nl>

