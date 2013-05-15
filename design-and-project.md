---
layout: page
title: Design
tagline: 
---
{% include JB/setup %}

### Parser & Generator
The threft project has a decoupled design in that parser and generators are seperated. The parser checks and parses input files (.thrift, .threft) to the Threft Interface Definition Model (TIDM). The TIDM is then handed to a generator in the form of tidm-json. The generator generates code. Anyone can write a generator for any language, without the need to use Go. This means that a python generator can be written in python, a java generator can be written in java, etc.

### Commands
This project consists of multiple commands.
The main command is `threft`. This command reads .thrift/.threft files and creates the TIDM. It also invokes a generator and hands it tidm-json.

### TIDM
The Threft Interface Definition Model is a generalized way to represent data structures and services. It is marshalled to/from tidm-json.

### Directory structure
The 
<strong>/threft</strong>