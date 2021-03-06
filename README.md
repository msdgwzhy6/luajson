## LuaJSON
JSON Parser/Constructor for Lua

### Author:
Thomas Harning Jr. <harningt@gmail.com>

### Source code:
http://repo.or.cz/luajson

### Bug reports:
http://github.com/harningt/luajson
harningt@gmail.com

### Requirements
Lua 5.1, 5.2, 5.3, LuaJIT 2.0, or LuaJIT 2.1
LPeg (Tested with 0.7, 0.8, 0.9, 0.10, 0.12rc2, 1.0)
For regressionTest:
	lfs (Tested with 1.6.3)
### For lunit-tests:
lunitx >= 0.8

### NOTE:
LPeg 0.11 may not work - it crashed during my initial tests,
it is not in the test matrix.

### Lua versions tested recently:
* Lua 5.1.5
* Lua 5.2.4
* Lua 5.3.2
* LuaJIT-2.0.4
* LuaJIT-2.1.0-beta2

### License
All-but tests: MIT-style, See LICENSE for details
tests/*:       Public Domain / MIT - whichever is least restrictive

### Module/Function overview:
### json.encode (callable module referencing json.encode.encode)
___encode ( value : ANY-valid )___

Takes in a JSON-encodable value and returns the JSON-encoded text
Valid input types:
* table
* array-like table (spec below)
* string
* number
* boolean
* 'null' - represented by json.util.null

Table keys (string,number,boolean) are encoded as strings, others are erroneus
Table values are any valid input-type
Array-like tables are converted into JSON arrays...
Position 1 maps to JSON Array position 0

___isEncodable ( value : ANY )___

Returns a boolean stating whether is is encodeable or not
NOTE: Tables/arrays are not deeply inspected

### json.decode (callable module referencing json.decode.decode)
___decode (data : string, strict : optional boolean)___

Takes in a string of JSON data and converts it into a Lua object
If 'strict' is set, then the strict JSON rule-set is used

### json.util
___printValue (tab : ANY, name : string)___

recursively prints out all object values - if duplicates found, reference printed

___null___

Reference value to represent 'null' in a well-defined way to
allow for null values to be inserted into an array/table

___merge (t : table, ... : tables)___

Shallow-merges a sequence of tables onto table t by iterating over each using
pairs and assigning.

### Attribution
parsing test suite from JSON_checker project of http://www.json.org/
No listed license for these files in their package.
