---
layout: page
title: Design & project
tagline: 
---
{% include JB/setup %}

<p>
	<span class="label label-info">Note!</span>
	This page describes the general design and project-setup for Threft.io. As the project is still in it's early stages a lot of what is described here is not actually finished yet or not even in development! More information will become available gradually on subpages under /design, which will be linked from this page.
</p>

<p>
	<span class="label label-success">Contribute?</span>
	Contributions are very welcome! Join <a target="_blank" href="https://groups.google.com/forum/?fromgroups#!forum/threft-dev" >threft-dev</a> and/or find out how to help with <a href="/develop.html" >development</a>.
</p>

## Design
Rather than creating new idea's and solutions: the Threft.io design borrows the best idea's from other projects such as Protobuf, Thrift and Go. For instance, even though compromises must be made to stay compatible. 

### IDL: Interface Definition Language
##### `.thrift` and `.threft`
The Threft.io parser can parse two types of files.
The first is the existing <a target="_blank" href="http://thrift.apache.org/docs/idl/" title="Thrift Interface Definition Language" >Thrift IDL</a>, with the `.thrift` file extension.
The second is the more strict <a href="/design/threft-idl" >Threft.io IDL</a>, with the `.threft` file extension.

### Parser & Generators
<img src="/images/parser_generator_large.png" alt="Parse and Generator" />
The parser and generators are seperated. The parser checks and parses input files to the Threft Interface Definition Model (TIDM). The TIDM is then marshalled to tidm-json, which is simply json following a specific structure. The parser executes the generator and sends the tidm-json on stdin. The generator creates code and writes files. A generator doesn't have to be written in Go because it is separated from the parser. Anyone can create a generator for any language in any language.

### Generated code and support libraries
<img src="/images/code_libraries.png" alt="Generated code, Threft support library and Language standard library." />
Since everyone can create a generator, this project cannot controll the design of the generated code. Since the Go generator (threft-gen-go) is part of this project a set of design principles are defined:
 - Minimal runtime reflection and type assertion in generated code.
 - Threrefore: code for serialisation/de-serialisation is to be generated, not support library.
 - Support library should only complement the standard libraries with small functionality such as networking helpers.

<br/>

## Project

### Commands
The Threft.io project consists of multiple commands.
<dl>
	<dt>threft</dt>
	<dd>
		Reads <i>.thrift</i> files and  executes a generator with tidm-json.<br/>
		<a target="_blank" href="http://github.com/threft/threft" >source</a>
	</dd>
</dl>
<dl>
	<dt>threft-gen-go</dt>
	<dd>
		Generates Go code from given tidm-json.<br/>
		<a target="_blank" href="http://github.com/threft/threft-gen-go" >source</a>
	</dd>
</dl>
<dl>
	<dt>threft-gen-html</dt>
	<dd>
		Generates HTML documentation from given tidm-json.<br/>
		<a target="_blank" href="http://github.com/threft/threft-gen-html" >source</a>
	</dd>
</dl>

### Packages
The project commands are backed by packages.
<dl>
	<dt>threft/tidm</dt>
	<dd>
		Threft Interface Definition Model. Datastructure that can be marhsalled to/from tidm-json. Also contains IDL parsing code.<br/>
		<a target="_blank" href="https://github.com/threft/threft/tree/master/tidm" >source</a> | <a target="_blank" href="http://godoc.org/github.com/threft/threft/tidm" >godoc</a>
	</dd>
</dl>
<dl>
	<dt>threft-gen-go/gog</dt>
	<dd>
		Actual Go generator code. Is being used by the threft-gen-go command.<br/>
		<a target="_blank" href="https://github.com/threft/threft-gen-go/tree/master/gog" >source</a> | <a target="_blank" href="http://godoc.org/github.com/threft/threft-gen-go/gog" >godoc</a>
	</dd>
</dl>
<dl>
	<dt>threft-gen-html/htmlg</dt>
	<dd>
		Actual HTML generator code. Is being used by the threft-gen-html command.<br/>
		<a target="_blank" href="https://github.com/threft/threft-gen-html/tree/master/htmlg" >source</a> | <a target="_blank" href="http://godoc.org/github.com/threft/threft-gen-html/htmlg" >godoc</a>
	</dd>
</dl>