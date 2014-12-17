StringBuilder for PHP
=====================

[![Version](http://img.shields.io/packagist/v/bit3/string-builder.svg?style=flat-square)](https://packagist.org/packages/bit3/string-builder)
[![Stable Build Status](http://img.shields.io/travis/bit3/string-builder/master.svg?style=flat-square&label=stable build)](https://travis-ci.org/bit3/string-builder)
[![Upstream Build Status](http://img.shields.io/travis/bit3/string-builder/develop.svg?style=flat-square&label=dev build)](https://travis-ci.org/bit3/string-builder)
[![License](http://img.shields.io/packagist/l/bit3/string-builder.svg?style=flat-square)](http://spdx.org/licenses/LGPL-3.0+)
[![Downloads](http://img.shields.io/packagist/dt/bit3/string-builder.svg?style=flat-square)](https://packagist.org/packages/bit3/string-builder)

The benefit of StringBuilder for PHP is to provide a mutable, object oriented string and all required methods to manipulate the string, following the Java StringBuilder.

How to use
----------

Basic usage:
```php
$stringBuilder = new StringBuilder();
$stringBuilder->append('Hello world!');
echo $stringBuilder;
```

Work with encoding:
```php
// set encoding on initialisation
$stringBuilder = new StringBuilder(null, 'ISO-8859-1');

// set encoding after initialisation (will not convert contents)
$stringBuilder->setEncoding('ISO-8859-15');

// change encoding and convert contents
$stringBuilder->changeEncoding('UTF-16');
```

Check contents:
```php
// string start with...
if ($stringBuilder->startsWith('Hello')) { ... } // bool(true)

// string ends with...
if ($stringBuilder->endsWith('world!')) { ... } // bool(true)

// string contains...
if ($stringBuilder->contains('Hello')) { ... } // bool(true)

// search substring from the beginning
$pos = $stringBuilder->indexOf('o w'); // int(4)

// search substring from the ending
$pos = $stringBuilder->lastIndexOf('o w'); // int(4)

// get a char from a specific position
$char = $stringBuilder->charAt(6); // string("w")

// get a substring
$substring = $stringBuilder->substring(6, 10); // string("world")

// get length of the current sequence
$length = $stringBuilder->length(); // int(11)
```

Manipulate contents:
```php
// append content
$stringBuilder->append('The end is near!'); // string("Hello world!The end is near!")

// insert content
$stringBuilder->insert(12, ' I know: '); // string("Hello world! I know: The end is near!")

// replace partial content
$stringBuilder->replace(13, 14, 'You'); // string("Hello world! You know: The end is near!")

// delete substring
$stringBuilder->delete(13, 22); // string("Hello world! The end is near!")

// delete single character
$stringBuilder->deleteCharAt(11); // string("Hello world The end is near!")

// limit the length of the string
$stringBuilder->setLength(11); // string("Hello world")

// extend string to a specific length
$stringBuilder->setLength(14, '!'); // string("Hello world!!!")

// trim contents
$stringBuilder->trim('!'); // string("Hello world")
$stringBuilder->trimLeft('He'); // string("llo world")
$stringBuilder->trimRight('dl'); // string("llo wor")

// reverse content
$stringBuilder->reverse(); // string("row oll")
```
