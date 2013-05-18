---
layout: page
title: Getting started
tagline: 
---
{% include JB/setup %}

This document will get you up and running to use Threft.

### Installation
There are no binary distributions in this point of development. With go, installation from source is very easy.
#### Install from source with go get
Make sure you have a go1.1 compiler and the go tool installed.
Execute the following commands in a terminal:

 - `go get -u github.com/threft/threft`
 - `go get -u github.com/threft/threft-gen-go`
 - `go get -u github.com/threft/threft-gen-html`

Use the same commands to update to the latest version.

### Usage
Simple usage:
`threft -i yourFile.thrift -g go -o outputDirectory`

For more information, execute `threft --help`
