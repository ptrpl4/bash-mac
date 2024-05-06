---
description: JavaScript Object Notation
---
# JSON

#### links

https://www.json.org/

## Description

JSON is a syntax for serialising objects, arrays, numbers, etc. 
It is based on JavaScript syntax.

## Basic syntax and structure

JSON text can be built on one of two structures:

- a collection of the **key:value** pairs (associative array);
- an orderly set of values (array or list).

### Example

Keys in an object are always strings, but values can be any of seven types of values, including another object or array.

JSON does not support comments.

```json
{
  "firstName": "John",
  "lastName": "Smith",
  "isAlive": true,
  "age": 27,
  "address": {
    "streetAddress": "21 2nd Street",
    "city": "New York",
    "state": "NY",
    "postalCode": "10021-3100"
  },
  "phoneNumbers": [
    {
      "type": "home",
      "number": "212 555-1234"
    },
    {
      "type": "office",
      "number": "646 555-4567"
    },
    {
      "type": "mobile",
      "number": "123 456-7890"
    }
  ],
  "children": [],
  "spouse": null
}
```

## JSON + Python

JSON to Python

| JSON          | Python |
| ------------- | ------ |
| object        | dict   |
| array         | list   |
| string        | str    |
| number (int)  | int    |
| number (real) | float  |
| true          | True   |
| false         | False  |
| null          | None   |

Python to JSON

| Python                                 | JSON   |
| -------------------------------------- | ------ |
| dict                                   | object |
| list, tuple                            | array  |
| str                                    | string |
| int, float, int- & float-derived Enums | number |
| True                                   | true   |
| False                                  | false  |
| None                                   | null   |
