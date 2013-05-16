---
layout: page
title: Design & project
tagline: 
---
{% include JB/setup %}

<p>
	<span class="label label-info">Note!</span>
	This page describes the general design and project-setup for Threft. As the project is still in it's early stages a lot of what is described here is not finished yet or not even in development! More information will become available gradually on subpages linked from this page.
</p>

<p>
	<span class="label label-success">Care to help?</span>
	If you have an idea/thought, or want to help out with the code. Please let us know, <a target="_blank" href="https://groups.google.com/forum/?fromgroups#!forum/threft-dev" >leave a message</a>!
</p>

## Design
Rather than creating new idea's and solutions: the Threft design tries to borrow the best idea's from other projects such as Protobuf, Thrift and Go. For instance, even though compromises must be made to stay compatible. 
### Interface Definition Language: .thrift vs .threft
The Threft parser can parse two types of files. The first is the existing <a target="_blank" href="http://thrift.apache.org/docs/idl/" title="Thrift Interface Definition Language" >Thrift IDL</a>, with the .thrift file extension. The second is the more strict <a href="/design/threft-idl" >Threft IDL</a>, with the .threft file extension.
### Parser & Generators
The parser and generators are seperated. The parser checks and parses input files to the Threft Interface Definition Model (TIDM). The TIDM is then handed to a generator in the form of tidm-json. The generator then creates code. Because it is not directly included into the parser binary a generator doesn't have to be written in Go. So if you want to create a generator that creates code for the language you love, then you can do that in your own language!
### Generated code and libraries
The Threft project puts the generator to work! The libraries only contain minimal code to help generated code during runtime. Serialisation code and networking services are generated. The use of runtime reflection or generics is kept to a minimum.

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
	<dt>threft-gen-html/htmlg</dt>
	<dd>Go package with the actual HTML generator. Uses threft/tidm. Is being used by the threft-gen-html command.</dd>
</dl>