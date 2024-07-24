# Using the jerVNC JavaScript library

This document describes how to make use of the jerVNC JavaScript library for
integration in your own VNC client application. If you wish to embed the more
complete jerVNC application with its included user interface then please see
our [embedding documentation](EMBEDDING.md).

## API

The API of jerVNC consists of a single object called `RFB`. The formal
documentation for that object can be found in our [API documentation](API.md).

## Example

jerVNC includes a small example application called `vnc_lite.html`. This does
not make use of all the features of jerVNC, but is a good start to see how to
do things.

## Conversion of Modules

jerVNC is written using ECMAScript 6 modules. This is not supported by older
versions of Node.js. To use jerVNC with those older versions of Node.js the
library must first be converted.

Fortunately jerVNC includes a script to handle this conversion. Please follow
the following steps:

 1. Install Node.js
 2. Run `npm install` in the jerVNC directory

The result of the conversion is available in the `lib/` directory.
