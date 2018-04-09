# ICOnator Docker Compose

This git repo provides a easy way on how to easily bootstrap the ICOnator services.

## Setting an .env file

First, you need to create an `.env` file on the root of this repository. This file is not provided since it should contain credentials.

Add the following to your `.env` file:

```
MONITOR_ETHEREUM_NODE_URL=<YOUR_ETHEREUM_NODE_URL>
GMAIL_USER=<YOUR_GMAIL_USERNAME_TO_SEND_EMAILS_FROM>
GMAIL_PASSWORD=<YOUR_GMAIL_PASSWORD>
EMAIL_SEND_FROM_ADDRESS=<YOUR_EMAIL_ADDRESS>
```

where:

* `<YOUR_ETHEREUM_NODE_URL>`: the full node URL with enabled JSON-RPC API. 
* `<YOUR_GMAIL_USERNAME_TO_SEND_EMAILS_FROM>`, `<YOUR_GMAIL_PASSWORD>`: username and password of an GMail account.
* `<EMAIL_SEND_FROM_ADDRESS>`: the email address to send emails from -- usually the same as `<YOUR_GMAIL_USERNAME_TO_SEND_EMAILS_FROM>`.

## The `docker-compose.yml`

The `docker-compose.yml` has the description of all the ICOnator application, the services (e.g., database, smtp server), and such dependencies between them.

Also, for each application and service there are environment variables set. Change it according to yoru own needs.

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

