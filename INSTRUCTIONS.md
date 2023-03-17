# IRMA CLI Instructions

## Step 1

Download and install the IRMA CLI
from [here](https://gitlab.science.ru.nl/irma/github-mirrors/irmago/-/jobs/artifacts/master/download?job=binaries)
using the instruction from [this docs page](https://irma.app/docs/irma-cli/).

## Step 2

Clone the custom `irma-demo` scheme and revoke the write permissions to the `schemes` directory (to
prevent automatic scheme updates).

```shell
$ mkdir schemes
$ cd schemes
$ git clone 'https://github.com/surfnet-niels/irma-demo-schememanager.git' niels-irma-demo
$ cd ..
$ chmod -R -w schemes
```

## Step 3

Make sure to have `jq` installed seeing as it's used to one-line the session JSON using the `-c`
flag.

Start an issuance request:

```shell
$ irma session --disable-schemes-update --schemes-path ~/your/path/to/schemes --request "$(cat irmacli/sessions/issuance_session_eduid.json | jq -c)"
```

## Step 4

Start a disclosure request:

```shell
$ irma session --disable-schemes-update --schemes-path ~/your/path/to/schemes --request "$(cat irmacli/sessions/disclosure_session_eduid.json | jq -c)"
```
