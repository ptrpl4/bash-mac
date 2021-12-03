---
description: JavaScript Object Notation
---

# JSON

## Description

JSON является синтаксисом для сериализации\* объектов, массивов, чисел, строк логических значений и значения [`null`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global\_Objects/null). Он основывается на синтаксисе JavaScript, однако всё же отличается от него.

\*_процесс перевода какой-либо_ [_структуры данных_](https://ru.wikipedia.org/wiki/%D0%A1%D0%BF%D0%B8%D1%81%D0%BE%D0%BA\_%D1%81%D1%82%D1%80%D1%83%D0%BA%D1%82%D1%83%D1%80\_%D0%B4%D0%B0%D0%BD%D0%BD%D1%8B%D1%85) _в последовательность_ [_битов_](https://ru.wikipedia.org/wiki/%D0%91%D0%B8%D1%82)__

JSON основан на двух структурах данных:

* Коллекция пар ключ/значение. В разных языках, эта концепция реализована как объект, запись, структура, словарь, хэш, именованный список или ассоциативный массив.
* Упорядоченный список значений. В большинстве языков это реализовано как массив, вектор, список или последовательность.

{% embed url="https://www.json.org/" %}

## Example

```javascript
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
