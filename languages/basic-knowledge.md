# 🤓 Basic Knowledge

## Statically v. dynamically v. strongly v. weakly typed languages

#### Links

{% embed url="https://hexlet.io/courses/intro_to_programming/lessons/types/theory_unit" %}

[https://www.educative.io/answers/statically-v-dynamically-v-strongly-v-weakly-typed-languages](https://www.educative.io/answers/statically-v-dynamically-v-strongly-v-weakly-typed-languages)

### Type checking

<figure><img src="../.gitbook/assets/изображение (3) (1).png" alt=""><figcaption></figcaption></figure>

Static type-checking - checking types during compilation process.

Dynamc type-checking - checking types at run time.

### Strong and weak typing <a href="#firstheading" id="firstheading"></a>

<figure><img src="../.gitbook/assets/изображение (1) (1).png" alt=""><figcaption></figcaption></figure>

Strong versus weak is about HOW SERIOUS DO YOU GET while checking the types.

JS example: weak typing

```javascript
4 + '7';      // '47'
4 * '7';      // 28
2 + true;     // 3
false - 3;    // -3
```

Python example: strong typing

```python
var = 21;            #type assigned as int at runtime.
var = var + "dot";   #type-error, string and int cannot be concatenated.
print(var);
```

<figure><img src="../.gitbook/assets/изображение (9) (2).png" alt=""><figcaption></figcaption></figure>
