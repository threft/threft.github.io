---
layout: page
title: Why Threft
tagline: 
---
{% include JB/setup %}

TODO: intro text naming other serialisation protocols that generate code. (*thrift*, protobuf, etc.)

#### Threft has a decoupled design, seperating parser and generator.
The *thrift* compiler/generator is designed to generate code for multiple languages, by one binary. This might lead to problems when compiling the *thrift* binary for someone trying to generate java code, the build might fail on an other generator.  
**Threft seperates parser and generator, allowing you to write a generator without having to care about anything else.**


#### Threft allows anyone to contribute in their own language
The *thrift* code generators are written in c++. As a result of this, erlang or python experts might find it hard writing or improving a generator that produces best-practice code for the language they are working with.  
**Threft allows programmers to write the code generator in the language of their own. This will lead to **


#### Threft encourages independent projects
As the *thrift* project consists of a single repository and a cenralized project management it hardens (and for some people discourages) patching bugs or creating new features.  
**Thrift aims to create a thriving community and "social coding" as seen on github.**