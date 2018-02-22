# bug-reporter

[![Build Status](https://travis-ci.org/nicholaswmin/bug-reporter.svg?branch=master)](https://travis-ci.org/nicholaswmin/bug-reporter)

Polymer 1.x form for bug reporting in SPA&#39;s

Captures:

- Name of user, email of user and a user provided description of the issue.
- Any stack traces of errors captured by `window.onerror`.
  - These are the same stack traces you would see in the browser console when
    an error is thrown.
- The current date.
- Some basic system info:
  - Browser vendor and version.
  - OS vendor and version.

## Installation

```bash
$ bower install --save bug-reporter
```

## Basic Usage

```html
<button id="report-bug">Report a Bug</button>
<bug-reporter url="https://my-api.com/bug"></bug-reporter>

<script>
  window.onload = () => {
    document.querySelector('report-bug').addEventListener('click', () => {
      document.querySelector('bug-reporter').toggle()        
    })
  }
</script>
```

When the user fills in the required information and clicks "Submit", the form
will issue a `POST` request to the provided `url` in the following format:

```
method: `POST`,
body: '{
  "name": "John Doe",
  "email": "john@doe.com",
  "description": "Lorem ipsum dolor\nsit amet.",
  "datetime": "Thu Feb 22 2018 04:26:05 GMT+0200 (EET)",
  "stackTraces": [],
  "system": {
    "ua": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_6) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/64.0.3282.140 Safari/537.36",
    "browser": {
      "name": "Chrome",
      "version": "64.0.3282.140",
      "major": "64"
    },
    "engine": {
      "name": "WebKit",
      "version": "537.36"
    },
    "os": {
      "name": "Mac OS",
      "version": "10.12.6"
    },
    "device": {},
    "cpu": {}
  },
  "url": "https://foo-app.com"
}'
```

## View documentation

### Install the Polymer-CLI

First, make sure you have the
[Polymer CLI](https://www.npmjs.com/package/polymer-cli) installed.

Then run:

```
$ polymer serve
```

to serve the element documentation.

## Running Tests

```
$ polymer test
```

## Authors

- [@nicholaswmin][nicholaswmin]


[nicholaswmin]: https://github.com/nicholaswmin


## License

- MIT
