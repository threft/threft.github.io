---
layout: page
title: Threft.io IDL
tagline: 
---
{% include JB/setup %}

The Threft.io <abbr title="Interface Definition Language">IDL</abbr> is based on the thrift IDL, but is a lot stricter.
Some un-used features are removed.

My current approach to this is to implement the thrift parser into the <a target="_blank" href="https://github.com/threft/threft/tree/master/tidm" >tidm package</a> and write down all things I like/dislike.

### Basic definitions

#### Characters
```
newline        = /* the Unicode code point U+000A */ .
unicode_char   = /* an arbitrary Unicode code point except newline */ .
unicode_letter = /* a Unicode code point classified as "Letter" */ .
unicode_digit  = /* a Unicode code point classified as "Decimal Digit" */ .
```

#### Identifier
An identifier can contain letters, digits, dots and underscores. It must start with a letter or underscore.
```
identifier = ("a" … "z" | "A" … "Z" | "_") {"a" … "z" | "A" … "Z" | "_" | "-" | "." } .

lowercase
Uppercase
camelCase
_fooBar
foo-bar
fooBarÆ   // illegal: contains invalid character 'Æ'
-fooBar   // illegal: does not start with letter or underscore
0fooBar   // illegal: does not start with letter or underscore
```

#### String literal
```
string_literal = `"` { unicode_char | `\"` | "\n" } `"`

"foobar"
"foo"bar"    // illegal: " should be escaped
"foo\"bar"   // \" is escaped to "
"foo\nbar"   // \n is escaped to a newline (unicode code point U+000A)
```

