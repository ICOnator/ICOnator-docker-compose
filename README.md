# ICOnator Docker Compose

This repository provides an easy way to bootstrap the ICOnator services. It serves as the example to better understand
the project, learn about its dependencies, and on how to deploy it. 

> **IMPORTANT:** this repo requires `docker-compose` version 1.13.0 or higher. Run `docker-compose --version` to check if
yours is compatible.

## Setting an .env file

First, you need to create an `.env` file on the root of this repository. This file is not provided since it should 
contain external credentials. You should get your own credentials to run the demo.

Add the following to your `.env` file:

```
MONITOR_ETHEREUM_NODE_URL=<YOUR_ETHEREUM_NODE_URL>
GMAIL_USER=<YOUR_GMAIL_USERNAME_TO_SEND_EMAILS_FROM>
GMAIL_PASSWORD=<YOUR_GMAIL_PASSWORD>
EMAIL_SEND_FROM_ADDRESS=<YOUR_EMAIL_ADDRESS>
CORE_RECAPTCHA_ENABLED=<SUPPORT_TO_RECAPTCHA_AUTH>
CORE_RECAPTCHA_SECRET_KEY=<YOUR_RECAPTCHA_SECRET_KEY>
```

where:

* `<YOUR_ETHEREUM_NODE_URL>`: the full node URL with enabled JSON-RPC API. 
* `<YOUR_GMAIL_USERNAME_TO_SEND_EMAILS_FROM>`, `<YOUR_GMAIL_PASSWORD>`: username and password of an GMail account.
* `<EMAIL_SEND_FROM_ADDRESS>`: the email address to send emails from -- usually the same as `<YOUR_GMAIL_USERNAME_TO_SEND_EMAILS_FROM>`.
* `<SUPPORT_TO_RECAPTCHA_AUTH>`: a boolean that specifies whether the registration of a new investor requires recaptcha authentication.
* `<YOUR_RECAPTCHA_SECRET_KEY>`: the secret key from the ReCaptcha.

> **Note 1:**
> If you are not familiar with Google ReCaptcha, you can obtain more info [here](https://developers.google.com/recaptcha/)
> and get an account [here](https://www.google.com/recaptcha/).

> **Note 2:**
> Google GMail is not strictly required to run ICOnator. You can directly connect to any SMTP server (e.g., Amazon SES).
> We used Google GMail because it's easier for a demo showcase, and everyone can obtain an account. 

## The `docker-compose.yml`

The `docker-compose.yml` has the description of all the ICOnator application, the services (e.g., database, smtp server), and dependencies between them.

Also, for each application and service there are environment variables set. Change it according to your own needs.

## Run 

Simply run everything with:

```
$ docker-compose up -d
```

Check the logs with:

```
$ docker-compose logs -f
```

If you want to check the logs for one specific application or service (specified on the `docker-compose.yml`), run:

```
$ docker logs <SERVICE_NAME>
```

where `<SERVICE_NAME>` can be, e.g., `iconator-core` or `smtp-service`.

