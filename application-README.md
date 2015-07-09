# Application Name Goes Here

This is brief summary of what this application does. If this application is deprecated, here is a good place to say that.

[![Build Status](https://magnum.travis-ci.com/goodeggs/garbanzo.svg?token=6spuidFAaP6eRzSXeuza&branch=master)](https://magnum.travis-ci.com/goodeggs/<project>)

## Getting started

### Running

```
gulp
```

Will start up an express server listening at
[example.goodeggs.dev:80015](http://example.goodeggs.dev:80015/). This command
will also start another process listening for domain events.

### External dependencies

In order for this app to run, you'll need to have the following services
available:

- Mongodb (Connection string can be configured with the `MONGO_URL` env
  variable. By default, uses `mongodb://localhost:27107/kale_development`.)
- Redis (Environment variables: `REDIS_URL`, `REDIS_DB_NUM`, and `REDIS_PASSWORD`)
- RabbitMQ (Connection string can be configured with `AMQP_URL` env variable.)
- Algolia (Required for search. By default, points to a dev index at algolia.com.)
- Garbanzo API (To get `User` data.)

### Setup

You'll need to add `example.goodeggs.dev` to your `/etc/hosts` file:

```
example.goodeggs.dev  127.0.0.1
```

Before your first run (and after you do a `git pull` for the latest updates),
run:

```
npm install
```

To populate your development machine with fake data, you can use the
[`dump-and-restore`](https://github.com/goodeggs/dump-and-restore) utility:

```
dump-and-restore kale
```

## API endpoints

This app provides the following API endpoints, for use with anyone that can
authenticate with a token from
[`goodeggs-ops-tokens`](https://github.com/goodeggs/goodeggs-ops-tokens):

- `GET /v1/customer_events`: Returns an array of customer events

## Common problems and how to fix them

**I can search for users, but I'm not getting their information after I click
into a result.**
The user search is populated by a shared Algolia instance. If you don't have
local data matching what's in algolia, the system won't know anything about the
customer you've clicked on. Also, when the system encounters a user id it
doesn't know about, it attempts to request information about that user ID from
the garbanzo API, so make sure that's running.
