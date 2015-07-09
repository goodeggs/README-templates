# Module name goes here

This is brief summary of what this module does. If this module is deprecated, here is a good place to say that.

[![Build Status](https://magnum.travis-ci.com/goodeggs/garbanzo.svg?token=6spuidFAaP6eRzSXeuza&branch=master)](https://magnum.travis-ci.com/goodeggs/<project>)

## Code example

```coffeescript
m = require 'module-name'
result = m.doStuff()
```

## Philosophy

A discussion of why this module is necessary. Provides a big benefit to people
who are considering adding features, or who are considering whether or not it's
something worth including in the project they are working on.

You can find good examples of this sort of information in the following modules:

- [Goodeggs Domain Events](https://github.com/goodeggs/goodeggs-domain-events#best-practices)
- [Goodeggs Money](https://github.com/goodeggs/goodeggs-money#why)

## Configuration

Information about how to set up and configure your module goes here.

## API documentation

- `doStuff()`: does x and returns a `result`

## Common problems and how to fix them

**I can search for users, but I'm not getting their information after I click
into a result.**
The user search is populated by a shared Algolia instance. If you don't have
local data matching what's in algolia, the system won't know anything about the
customer you've clicked on. Also, when the system encounters a user id it
doesn't know about, it attempts to request information about that user ID from
the garbanzo API, so make sure that's running.
