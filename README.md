# Introduction
Light and fast **JSON** library, compliant to https://www.ietf.org/rfc/rfc4627.txt

This library provides comprehensive **JSON** support, including both encoding and decoding. 
The ``JSONValue`` abstract class serves as the foundation for parsing **JSON** values. 
Its ``parse()`` method takes a **JSON** string as input and returns the corresponding parsed object. 

The ``JSONObject`` class specifically handles **JSON** objects, offering a ``toString()`` method to convert them back into human-readable **JSON** strings.

The class ``TestSuite`` performs automatic tests of **JSON** parser.

# JSON encoding
in case of JSON object, you can use Java oriented constructor ``JSONObject`` followed by ``toString()`` method invocation, e.g.:
```
new JSONObject("{\"a\":\"123\",\"b\":true}").toString()
```
in case of JSON array, you can use Java oriented constructor ``JSONArray`` followed by ``toString()`` method invocation, e.g.:
```
new JSONArray("[\"a\":\"123\",\"b\":true]").toString()
```
# JSON decoding
use ``parse()`` method followed by ``toJava()`` method invocation, e.g.:
```
JSONValue.parse("{\"a\":[[[1,2,3],[false,true],[null]],{\"a\":{}}]}").toJava()
```
# TestSuite
Class ``TestSuite`` performs automatic tests of json parser.
```
compile: javac -encoding UTF-8 json\TestSuite.java

run: java json.TestSuite [json file]
- in case optional argument json file is provided, it parses the file and returns the string from the JSONValue
- if no optional argument is provided, it performs built in automatic tests of json parser.
```

# JSON Syntax
JSON syntax is based on RFC4627
```
JSON-text ::= object | array
object ::= '{' [ member ( ',' member )* ] '}'
member ::= string ':' value
array ::= '[' [ value ( ',' value )* ] ']'
value ::= 'false' | 'null' | 'true' | object | array | number | string
number ::= [ '-' ] int [ frac ] [ exp ]
int ::= '0' | ( digit1-9 digit* )
frac ::= '.' digit+
digit ::= '0' | '1' | '2' | '3' | '4' | '5' | '6' | '7' | '8' | '9'
exp ::= ('e' | 'E') [ '+' | '-' ] digit+
string ::= '"' char* '"'
char ::= unescaped | '\' ('"' | '\' | '/' | 'b' | 'f' | 'n' | 'r' | 't' | 'u' <hex><hex><hex><hex>)
unescaped ::= %x20-21 | %x23-5B | %x5D-10FFFF

note: symbol * indicates 0 or more instances while symbol + indicates 1 or more instances
```
# Classes
```
JSONValue
JSONObject extends JSONValue
JSONArray extends JSONValue
JSONString extends JSONValue
JSONNumber extends JSONValue
JSONBoolean extends JSONValue
JSONException extends Exception
Scanner
TestSuite
```
Useful public methods in JSONValue and related classes:
```
Object toJava();//return Java value
String toString();//return JSON value
boolean equals(Object o)//check equality
```
