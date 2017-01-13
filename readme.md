# connect-docco

Bringing the literate programing tool [Docco] to [Connect][].

The idea is just to generate documentation dynamically upon request,
which is quite handy during development.

[docco]: http://jashkenas.github.com/docco/
[connect]: http://senchalabs.github.com/connect/

## Installation

    npm install connect-docco -g

If you don't intend to use the `connect-docco` program, you can omit
the `-g` flag.

## Command-Line Usage

The arguments below are the defaults and can be omitted.

    connect-docco --port 8082 --dirname .

## Middleware Usage

Here is an example of a basic server setup:

    connect.createServer()
        .use(connect.logger())
        .use(require("docco")(__dirname))
        .use(connect.directory(__dirname))
        .use(connect.static(__dirname))
        .listen(process.env.PORT);

The middleware handles any Docco-compatible extension (`.coffee`,
`.js`, `.json`, `.rb`, `.py`). You can still view the raw version of the file
when the `?raw` query string parameter is given, should you wish to use it:

    http://localhost:8082/some/file.js?raw
