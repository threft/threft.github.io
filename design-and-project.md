---
layout: page
title: Design & project
tagline: 
---
{% include JB/setup %}

## Design
### Parser & Generator
Parser and generators are seperated. The parser checks and parses input files (.thrift, .threft) to the Threft Interface Definition Model (TIDM). The TIDM is then handed to a generator in the form of tidm-json. The generator creates code. This means that the generator doesn't have to be written in Go and thus a python generator can be written in python and a java generator can be written in java, etc. This also means that you only need to install the generators that you use.

<br/>

## Project
### Commands
This project consists of multiple commands.
<dl>
	<dt>threft</dt>
	<dd>Reads <i>.thrift</i> files and  executes a generator with tidm-json.</dd>
</dl>
<dl>
	<dt>threft-gen-go</dt>
	<dd>Generates Go code from given tidm-json</dd>
</dl>
<dl>
	<dt>threft-gen-html</dt>
	<dd>Generates HTML documentation from given tidm-json</dd>
</dl>

### Directory structure
<dl>
	<dt>threft</dt>
	<dd>Code for the <i>threft</i> command</dd>
</dl>
<dl>
	<dt>threft/tidm</dt>
	<dd>Go package for the Threft Interface Definition Model. Datastructure that can be marhsalled to/from tidm-json. Also contains parsing and reading methods.</dd>
</dl>
<dl>
	<dt>threft-gen-go</dt>
	<dd>Code for the <i>threft-gen-go</i> command.</dd>
</dl>
<dl>
	<dt>threft-gen-go/gog</dt>
	<dd>Go package with the actual Go generator. Uses threft/tidm. Is being used by the threft-gen-go command.</dd>
</dl>
<dl>
	<dt>threft-gen-go-tests</dt>
	<dd>Contains tests and golden code to verify/develop the go generator with.</dd>
</dl>
<dl>
	<dt>threft-gen-html</dt>
	<dd>Code for the <i>threft-gen-html</i> command.</dd>
</dl>
<dl>
	<dt>threft-gen-htmlg</dt>
	<dd>Go package with the actual HTML generator. Uses threft/tidm. Is being used by the threft-gen-html command.</dd>
</dl>