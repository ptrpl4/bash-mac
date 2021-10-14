---
description: язык с неявной сильной динамической типизацией
---

# Python

![](<../../.gitbook/assets/изображение (5).png>)

## About

[https://docs.python.org/3/genindex-all.html](https://docs.python.org/3/genindex-all.html) 

[https://docs.python.org/3/reference/index.html](https://docs.python.org/3/reference/index.html)

[https://www.w3schools.com/python/python_reference.asp](https://www.w3schools.com/python/python_reference.asp)

[https://repl.it/languages/python3](https://repl.it/languages/python3) - виртуалка

[https://devpractice.ru/python/](https://devpractice.ru/python/) - статьи

PEP - Python Enhancement Proposal

[https://docs.python.org/3.8/reference/index.html](https://docs.python.org/3.8/reference/index.html) - прочитать

## Основные типы данных

### immutable/mutable

К неизменяемым (**immutable**) типам относятся: \
целые числа (**int**), числа с плавающей точкой (**float**), комплексные числа (**complex**), логические переменные (**bool**), кортежи (**tuple**), строки (**str**) и неизменяемые множества (**frozen set**).\
К изменяемым (**mutable**) типам относятся: \
списки (**list**), множества (**set**), словари (dict).

#### Неопределенное значение (None)

### _Boolean Type_

There are three built-in boolean operators in Python: `and`, `or` and `not`. The first two are **binary** operators which means that they expect two arguments. `not` is a **unary** operator, it is always applied to a single operand.

**and** is a binary operator, it takes two arguments and returns True if both arguments are True, otherwise, it returns False.

`x and y` returns x if x is falsy, otherwise, it evaluates and returns y.

**or** is a binary operator, it returns True if at least one argument is True, otherwise, it returns False.

`x or y` returns x if x is truthy, otherwise, it evaluates and returns y.

**not** is a unary operator, it reverses the boolean value of its argument.

```python
game_active = True
can_edit = False
to_be = True           # to_be is True
not_to_be = not to_be  # not_to_be is False
```

**Приоритет** исполнения: not, and, or

```python
a = False or not False  
# True, because `not False` is evaluated first
```

False in Python:

* constants defined to be false: `None` and `False`.
* zero of any numeric type: `0`, `0.0`.
* empty sequences and collections: `''`, `[]`, `{}`.

Anything else generally evaluates to True.

### Числа (_Numeric Type_)

#### Целые числа (int)

`с = 10`

#### Вещественные числа (float)

`d = 12.9`

#### комплексное число (complex)

?

### Списки (list)

[https://docs.python.org/3/tutorial/datastructures.html](https://docs.python.org/3/tutorial/datastructures.html)

```python
listname = ['one','two','three']
different_objects = ['a', 1, 'b', 2]
numbers = [1, 2, 3, 4, 5]
print(len(numbers))  # 5
 
empty_list = list()
print(len(empty_list))  # 0
```

В нумерации списка 'one' - будет под номером \[0]

Последний элемент списка можно запросить как \[–1], предпоследний \[-2]

```
pet = "cat"
 
first_char = pet[0]   # 'c'
second_char = pet[1]  # 'a'
third_char = pet[2]   # 't'
```

`print(listname[0]) // обращение к элементу`\
`listname [0] = 'dimka' // переназначения`

Strings, unlike lists, are immutable, so you can't modify their contents with indexes:

```
pet = "cat"
 
pet[0] = "b"
# TypeError: 'str' object does not support item assignment
```

append() - добавление элементов в список

There is also `list.extend(another_list)` operation which adds all the elements from another iterable to the end of a list.

insert(1, 'elementname') - добавление в список на определенное место. остальные элементы сдвигаются на 1 вправо

pop() - удаляет последний элемент списка, но позволяет к нему обратиться. Если элемент еще может понадобиться  - не использовать команду del

The following example demonstrates the difference between using `list` and `[]` when creating a list:

```python
multi_elements_list = list('danger!')
print(multi_elements_list)  # ['d', 'a', 'n', 'g', 'e', 'r', '!']
 
single_element_list = ['danger!']
print(single_element_list)  # ['danger!']
```

`len()` - функция для возврата длинны списка

### _Slices (срезы/подмножества)_

`listname[0:5] # от 1 до 4`

`listname[:5] # от "начала" до 4`

`listname[2:] # от 3 до "конца"`

listname \[-2:]

`listname[:]# обращение ко всем элементам списка (для копирования)`

`listone = listtwo # создает связь между списками и дублирует изменения для каждого`

### Кортеж (tuple)

tuple - неизменяемый список (кортеж)\
кортеж не меняется, но может быть заново переопределен

```python
>>> t = 12345, 54321, 'hello!'
>>> t[0]
12345
>>> t
(12345, 54321, 'hello!')
>>> # Tuples may be nested:
... u = t, (1, 2, 3, 4, 5)
>>> u
((12345, 54321, 'hello!'), (1, 2, 3, 4, 5))
>>> # Tuples are immutable:
... t[0] = 88888
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'tuple' object does not support item assignment
>>> # but they can contain mutable objects:
... v = ([1, 2, 3], [3, 2, 1])
>>> v
([1, 2, 3], [3, 2, 1])
```

```python
# another empty tuple
empty_tuple = tuple()
print(empty_tuple)        # ()
print(type(empty_tuple))  # <class 'tuple'>
 
# a list turned into a tuple
bakers_dozen = tuple([12, 1])
print(bakers_dozen == (12, 1))  # True
 
# a tuple from a string
sound = tuple('meow')
print(sound)  # ('m', 'e', 'o', 'w')
```

A tuple can be used as a **dictionary key**, whereas lists as keys will result in `TypeError`.

```python
name_and_age = ('Bob', 42)

(name, age) = name_and_age
name  # 'Bob'
age   # 42
```

Именно таким способом принято получать и сразу разбирать значения

Благодаря тому, что кортежи легко собирать и разбирать, в Python удобно делать такие вещи, как множественное присваивание. Смотрите:

```
(a, b, c) = (1, 2, 3)
a  # 1
b  # 2
c  # 3
```

Используя множественное присваивание, можно провернуть интересный трюк: обмен значениями между двумя переменными. 

```
a = 100
b = 'foo'

(a, b) = (b, a)
a  # 'foo'
b  # 100
```

### Строки (_Text Sequence Type_)

#### Строки (str)

`"This is a string." `\
`'This is also a string.'`

#### **The str. format() method**

```python
print('Mix {}, {} and a {} to make an ideal omelet.'.format('2 eggs', '30 g of milk', 'pinch of salt'))
print('{0} in the {1} by Frank Sinatra'.format('Strangers', 'Night'))
print('The {film} at {theatre} was {adjective}!'.format(film='Lord of the Rings',
                                                        adjective='incredible',
                                                        theatre='BFI IMAX'))
print('The {0} was {adjective}!'.format('Lord of the Rings', adjective='incredible'))
```

Remember as a Python rule that keyword arguments are always written **after** positional, or non-keyword, arguments.

#### Multiline strings

```python
print('''This
is
a
multi-line
string''')
```

#### Formatted string literals (f-strinngs)

```python
hundred_percent_number = 1823
needed_percent = 16
needed_percent_number = hundred_percent_number * needed_percent / 100
 
print(f'{needed_percent}% from {hundred_percent_number} is {needed_percent_number}')
# 16% from 1823 is 291.68
 
print(f'Rounding {needed_percent_number} to 1 decimal place is {needed_percent_number:.1f}')
# Rounding 291.68 to 1 decimal place is 291.7
```

#### Работа со строками

* **`str.replace(old, new[, count])`** replaces all occurrences of old with the new. The count argument is optional, and if it is specified, only the first count occurrences are replaced.
* **`str.upper()`** converts all characters of the string to the upper case.
* **`str.lower()`** converts all characters of the string to the lower case.
* **`str.title()`** converts the first character of each word to upper case.
* **`str.swapcase()`** converts upper case to lower case and vice versa.
* **`str.capitalize()`** changes the first character of the string to the upper case and the rest to the lower case.
* **`str.lstrip([chars])`** removes the leading characters (i.e. characters from the left side). If the argument `chars` isn’t specified, leading whitespaces are removed.
* **`str.rstrip([chars])`** removes the trailing characters (i.e. characters from the right side). The default for the argument `chars` is also whitespace.
* **`str.strip([chars])`** removes both the leading and the trailing characters. The default is whitespace.

```python
whitespace_string = "     hey      "
normal_string = "incomprehensibilities"
 
# delete spaces from the left side
whitespace_string.lstrip()  # "hey      "
 
# delete "i" or "s" or "is" from the left side
normal_string.lstrip("is")  # "ncomprehensibilities"
 
# delete spaces from the right side
whitespace_string.rstrip()  # "     hey"
 
# delete "i" or "s" or "is" from the right side
normal_string.rstrip("is")  # "incomprehensibilitie"
 
# no spaces from both sides
whitespace_string.strip()  # "hey"
 
# delete trailing "i" or "s" or "is" from both sides
normal_string.strip("is")  # "ncomprehensibilitie"
```

### Словари (_dict)_

Вид:

`someVar = { "color" : "green", "points" : 5}`

название = { "атрибут" : "значение"}

Получить значение атрибута

`someVar["color"]`

Пример из docs:

```python
>>> a = dict(one=1, two=2, three=3)
>>> b = {'one': 1, 'two': 2, 'three': 3}
>>> c = dict(zip(['one', 'two', 'three'], [1, 2, 3]))
>>> d = dict([('two', 2), ('one', 1), ('three', 3)])
>>> e = dict({'three': 3, 'one': 1, 'two': 2})
>>> a == b == c == d == e
True
```

Удаление

```python
del sample_dict["points"] # how to delete 
```

 Один ключ может иметь список(массив?) значений

`dict_example = { "pizza": ["peperoni", "cheese"]}`

\n - разрыв строки\
\t - табуляция

 \# - символ для обозначения комментария в строке

### Набор (set)

Набор который состоит только из уникальных элементов, неупорядоченный.

Only immutable data types can be elements of a set!

```python
string = set('Hello')
print(string)  # {'H', 'e', 'o', 'l'}
states = ['Russia', 'USA', 'USA', 'Germany', 'Italy']
print(set(states))  # {'Russia', 'USA', 'Italy', 'Germany'}
```

полезные функции и методы\
**`len()`**

```
nums = {1, 2, 2, 3}
print(1 in nums, 4 not in nums)  # True True
```

* add a new element to the set with **`add()`** method or `update()` it with another collection
* delete an element from a specific set using **`discard/remove`** methods. The only difference between them operating is a situation when the deleted element is absent from this set. In this case, **`discard`** does nothing and **`remove`** generates a `KeyError` exception.
* remove one random element using **`pop()`** method. As it’s going to be random, you don’t need to choose an argument.
* delete all elements from the set with **`clear()`** method.

## Math + Операторы

* `+` сложение
* `-` вычитание
* `*` умножение
* `**` возведение в степень
* `/` деление
* `//` [целочисленное деление](https://ru.wikipedia.org/wiki/%D0%94%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5\_%D1%81\_%D0%BE%D1%81%D1%82%D0%B0%D1%82%D0%BA%D0%BE%D0%BC#%D0%92\_%D0%BF%D1%80%D0%BE%D0%B3%D1%80%D0%B0%D0%BC%D0%BC%D0%B8%D1%80%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B8)
* `%` [остаток от деления](https://ru.wikipedia.org/wiki/%D0%94%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5\_%D1%81\_%D0%BE%D1%81%D1%82%D0%B0%D1%82%D0%BA%D0%BE%D0%BC)

\+= \
_увеличение на 1_

Naturally, similar assignment forms exist for the rest of arithmetic operations:\
`-=`, `*=`, `/=`, `//=`, `%=`, `**=`. 

### Операторы сравнения

* `<` strictly less than
* `<=` less than or equal
* `>` strictly greater than
* `>=` greater than or equal
* `==` equal
* `!=` not equal
* `is` object identity
* `is not` negated object identity
* `in` membership
* `not in` negated membership.

The result of applying these operators is always `bool`.

\+= \
_обьединяет строки_

```python
prompt = "If you tell us who you are, we can personalize the messages you see." 
prompt += "\nWhat is your first name? "
```

## Команды

`del` - удаление

`break` - выход из цикла (while, for ...)

`continue` - возвращает цикл к началу

## Функции 

_именованный блок кода с одной определенной задачей_

использование - `function(element.method())`

### Импорт функций в файл

для импортирования функции 

`import filename`\
`filename.funcName(arg1, arg2)`\
`#alternative`\
`from filename import funcName1, funcName2`\
`#adding alias`\
`from filename import funcName as aliasName`\
`#import all func`\
`from fileName import *`

### **built-in**

[https://docs.python.org/3/library/functions.html](https://docs.python.org/3/library/functions.html)  -полный список

![in Python 3.8.2](../../.gitbook/assets/image.png)

`print()`

`sorted() `- временно сортирует a-z

`len()` - определение длинны (для списка кол-во элементов)

`range()` - перебор 

`str()` - преобразование числовых значений в строку

`range(start, stop[, step])`

`list()` - представляет в виде списка

`min()`\
`max()`\
`sum()` - для работы с числовыми списками

`set()` - извлечение уникальных значений 

`input()` - ввод пользовательских данных. все полученные данные преобразует в `str`

```python
message = input('some text--> ')
print(message)
```

To read several inputs, you should call the function more than once:

```python
day = int(input())  # 4
month = input()     # October
```

`int()` - преобразует строковое представление числа в само число:

```python
age = input("How old are you? ")
How old are you? 21
age = int(age)
age >= 18 
True
```

`lstrip() `\
`lstrip()`\
_стирает пробелы слева, справа_

`strip()`\
_стирает все пробелы_

`type()`\
_определяет тип переменной_

`abs()`  \
__It pertains to Python built-ins and returns the absolute value of a number (that is, value regardless of its sign)

`set()`

A **set** is an **unordered **container of **hashable** objects**. **

удаляет дубликаты и выводит набор в произвольном порядке

```
set1 = {'A', 'B', 'C', 'B'}
set2 = {'B', 'C', 'A'}
print(set1 == set2)  # True
```

### user-defined

`def` - определение функции

```python
def func_name():
    """some docks"""
    func body
#funck + 
def greet_user(username, nickname = "lox"):
    """нужно задать имя и ник. ник по дефолту задан"""
    print("Hello! " + username.title() + nickname + "!")
#вызов №1 аргумента
greet_user("jesse")
#вызов аргумента по названию параметра
greet_user(username = "jesse")

#username - параметр
#jesse - аргумент
```

```python
#пример с опциональным аргументом
def get_formatted_name(first_name, last_name, middle_name=''): 
    """Возвращает аккуратно отформатированное полное имя."""
    if middle_name:
    full_name = first_name + ' ' + middle_name + ' ' + last_name
    full_name = first_name + ' ' + last_name
return full_name.title()
musician = get_formatted_name('jimi', 'hendrix') print(musician)
musician = get_formatted_name('john', 'hooker', 'lee')
print(musician)
```

```python
#пример с получением функцией списка
def greet_users(names):
    """Вывод простого приветствия для каждого пользователя в списке.""" for name in names:
        msg = "Hello, " + name.title() + "!" 
        print(msg)
usernames = ['hannah', 'ty', 'margot']
greet_users(usernames)
```

#### кол-во агрументов функции может быть заранее не обьявлено

def make_pizza(\*toppings):

Звездочка в имени параметра \*toppings приказывает Python создать пустой кортеж с именем toppings и упаковать в него все полученные значения.

### Методы (Methods)

Метод - функция принадлежащая классу.

синтаксис - `function(element.method())`

```python
print(name.title()) // функция(обьект.метод(параметры метода))
print(listname[0,1].title()) //
```

title() - первые буквы меняются на заглавные\
upper() - все буквы бульшие\
lower() - все буквы маленькие

lstrip(), strip(), rstrip() - удаление пропусков слева/с обоих концов/справа в строке

append() - добавление элемента в список (последним)

insert() - добавление элемента на конкретное место в списке

remove() - удаляет выбранное значение

sort() - сортирует a-z элементы в списке. исходный порядок перезаписывается

reverse() - меняет текущий порядок на противоположный

За именем переменной в команде print() следует вызов метода title(). Точка (.) после name в конструкции name.title() приказывает Python применить метод title() к переменной name.\
За именем метода всегда следует пара круглых скобок, потому что методам для выполнения их работы часто требуется дополнительная информация.

items() - в словарях возвращает пары: ключ, значение

keys() - возвращает только ключи, без значений (словарь)

values() - возвращает только значения (словарь)

`split()` - делит на части строку/слово, записывает результат как список. по дефолту разделитель - пробел

### Дефолтные методы классов

```python
#создание основных атрибутов класса
__init__(self, make, model, year):
```

```python
#задача атрибутов для child Класса
super().__init__(make,model,year)
```

## Классы (ООП)

Основы ООП

Each object can be characterized by a state and behavior. An object keeps the current state in the **fields** and the behavior in the **methods**.

**Инкапсуляция** - разбивка на самодостаточные детали с возможностью изменить одну не сломав структуру. Взаимодействие с данными происходит через публичные методы. Позволяет защитить обьект от несогласованности

**Абстракция** - обьект представляет только необходимые данные. Наиболее простые для понимания и нужные для взаимодейстивия. 

**Наследование** - возможность создания на базе существующих классов новые, с дополнителнительными атрибутами и методами

**Полиморфизм** - возможность переопределения методов у класса наследника

**self** – это ссылка на текущий экземпляр класса

### Создание Класса

```python
#создание класса
class Dog:
    """Описание класса. Название всегда с Большой Буквы"""
    """определяем набор атрибутов класса"""
    def __init__(self, name, age):
        self.name = name
        self.age = age
        #можем создать атрибут без обязательного обращения при создании
        #и задать ему дефотлтное значение
        self.number = 66
        """добавляем методы класса"""
    def sit(self):
        print(self.name.title() + " is now sitting.")
    def roll_over(self):
        print(self.name.title() + " rolled over!")
```

All instances of the class would be identical to one another. Most of the time that is not what we want. To customize the initial state of an instance, the **`__init__`** method is used.

### def \__init\_\_() <a href="def-__init__" id="def-__init__"></a>

The `__init__` method is a **constructor**. Constructors are a concept from the object-oriented programming. A class can have one and only one constructor. If `__init__` is defined within a class, it is automatically invoked when we create a new class instance.

```python
class River:
    # list of all rivers
    all_rivers = []
    
    def __init__(self, name, length):
        self.name = name
        self.length = length
        # add current river to the list of all rivers
        River.all_rivers.append(self)
 
volga = River("Volga", 3530)
seine = River("Seine", 776)
nile = River("Nile", 6852)
 
# print all river names
for river in River.all_rivers:
    print(river.name)
# Output:
# Volga
# Seine
# Nile
```

The `__init__` method specifies what attributes we want the instances of our class to have from the very beginning. In our example, they are **name **and **length. **

Note that when we actually call an object's method we don't write the `self` argument in the brackets. The `self` parameter (that represents a particular instance of the class) is passed to the instance method **implicitly** when it is called. So there are actually two ways to call an instance method: `self.method()` or `class.method(self)`. In our example it would look like this:

```python
# self.method()
volga.get_info()
# The length of the Volga is 3530 km

# class.method(self)
River.get_info(volga)
# The length of the Volga is 3530 km
```

Classes in Python have two types of attributes: class attributes and instance attributes. You should already know what class attributes are so here we'll focus on the instance attributes. **Instance attributes** are defined within methods and they store instance-specific information.

### Class attribute <a href="class-attribute" id="class-attribute"></a>

**Class attributes** are defined within the class but outside of any methods. Their value is the same for all instances of that class so you could consider them as the sort of "default" values for all objects.

```python
# Book class
class Book:
    material = "paper"
    cover = "paperback"
    all_books = []
Book.material  # "paper"
Book.cover  # "paperback"
Book.all_books  # []
```

### Создание Экземпляра от Класса

```python
#создаем экземпляр. Задаем имя и обязательные атрибуты
my_dog = Dog('willie', 6)
#выводим заданные атрибуты
print('My dog`s name is ' + my_dog.name.title() + ".")
print('My dog is ' + str(my_dog.age) + " years old.")
#можем вызвать методы, полученные у родителя
my_dog.sit()
my_dog.roll_over()
```

### Создание потомка от родителя

```python
class ElectricCar(Car):
    #Инициализирует атрибуты класса-родителя.
    #Затем инициализирует атрибуты, специфические для потомка.
    def __init__(self, make, model, year):
        super().__init__(make,model,year)
#создаем экземпляр
my_tesla = ElectricCar('tesla','model s', 2016)
print(my_tesla.get_descriptive_name())
```

методы, полученные от родителя можно переопределить

### Экземпляры как атрибуты

в определении атрибутов можно указать класс

`#предварительно уже имеем созданный класс "ClassName"`\
`#в новом классе "OtherClass" определяем одним из атрибутов другой класс "ClassName"`\
`class OtherClass:`\
`    def...`\
`    ...`\
`    self.atr_name = ClassName()`\
``\
`#после обращаемся к нему как к атрибуту "OtherClass"`\
`OtherClass.ClassName.class_method`\
`#можем обратиться и к атрибуту`\
`OtherClass.ClassName.class_attribute`

### Summary <a href="summary" id="summary"></a>

If classes are an abstraction, a template for similar objects, a **class instance** is a sort of example of that class, a particular object that follows the structure outlined in the class. In your program, you can create as many objects of your class as you need.

To create objects with different initial states, classes have a constructor `__init__` that allows us to define necessary parameters. Reference to a particular instance within methods is done through the `self` keyword. Within the `__init__` method, we define instance attributes that are different for all instances.

### Class methods

When called for the first time, the `name_captain` method creates a new attribute called `captain` and prints the corresponding message. When used next, it just changes the value of the `self.captain` attribute

```python
class Ship:
    def __init__(self, name, capacity):
        self.name = name
        self.capacity = capacity
        self.cargo = 0
        self.captain = None
 
    def name_captain(self, cap):
        self.captain = cap
```

it is recommended to define all possible attributes in the `__init__`. This can not only help you avoid `AttributeError`, but also give a good understanding of the class and its objects from the get-go. If you do want to create the value for the attribute in a method, then list it in the `__init__` as `None`

### "magic" methods (dunders)

**`__new__`**

New objects of the class are in fact created by the **`__new__`** method that in its turn calls the `__init__` method. 

The first argument of the `__new__` method is `cls`. It represents the class itself, similar to how `self` represents an instance of the class. This also makes `__new__` a different kind of method since it doesn't require an instance of the class.

Usually, there is no need to define a special `__new__` method, but it can be useful if we want to return instances of other classes or restrict the number of objects in our class. 

```python
class Sun:
    n = 0
 
    def __new__(cls):
        if cls.n == 0:
            instance = object.__new__(cls)
            cls.n += 1
            return instance
```

`__repr__`

```
class Transaction:
    def __init__(self, number, funds):
        self.number = number
        self.funds = funds
        self.status = "active"
 
    def __repr__(self):
        return "Transaction {}. Amount: {}. Status: {}".format(self.number,
                                                               self.funds,
                                                               self.status)
```

Now if we try to print any transaction we will get a standard readable string:

```
payment = Transaction("000001", 9999.999)
print(payment)
# Transaction 000001. Amount: 9999.999. Status: active
```

## Составные операторы (Compound statements)

### **if**

```python
for device in devices:
    if device == 'etc':
        print(device.upper())
    else:
        print(device.title())
```

```
first_alternative if condition else second_alternative
```

### for

модель:

```python
#общий пример
for variable in iterable:
    statement
---
for x in a[:]:
    if x < 0: a.remove(x)
---
#цикл для заполнения пар ключ-значение
for key, value in user_info.items():
    profile[key] = value
---
#for symbols in word
for char in 'magic':
    print(char)
```

If the loop didn’t encounter the break statement, an **else clause** can be used to specify a block of code to be executed after the loop.

```python
pets = ['dog', 'cat', 'parrot']
for pet in pets:
    print(pet)
else:
    print('We need a turtle!')
```

Importantly, loop `else` runs if and only if the loop is exited normally (without hitting **break**). Also, it is run when the loop is never executed (e. g. the condition of the `while` loop is false right from the start).

[https://docs.python.org/3/reference/compound_stmts.html#the-for-statement](https://docs.python.org/3/reference/compound_stmts.html#the-for-statement)

### **while **

цикл, проверяющий условие. условием к примеру может быть непустой список

![](<../../.gitbook/assets/image (1).png>)

```python
def print_numbers(last_number):
    # i сокращение от index (порядковый номер)
    # используется по общему соглашению во множестве языков
    # как счетчик цикла
    i = 1
    while i <= last_number:
        print(i)
        i = i + 1
    print('finished!')

print_numbers(3)
```

### Операторы _break_ и _continue_

```python
a = 0
while a >= 0:
   if a == 7:
       break
   a += 1
   print("A")
```

```python
a = -1
while a < 10:
   a += 1
   if a >= 7:
       continue
   print("A")
```

### Проверка условий (and) (or)

and\
выдает true если оба условия совпадают 

or\
выдает true если хотябы 1 верно

### Проверка наличия в списке (in) 

in \
`kitty2 in kitty_list`\
`true`

возвращает true если находит

### Проверка остуствия в списке (not in)

not in 

`if user not in banned_users`

возвращает true если не находит в списке

### Генератор списков

listname = \[var+1 for var in range (1,11)]

определяем список, определяем выражение для цикла for определяем цикл for

_Генератор списка объединяет цикл for и создание новых элементов в одну строку и автоматически присоединяет к списку все новые элементы_

##  Scopes

A **scope** is a part of the program where a certain variable can be reached by its name. The scope is a very important concept in programming because it defines the visibility of a name within the code block.

```python
phrase = "Let it be"
 
def global_printer():
    print(phrase)  # we can use phrase because it's a global variable
 
global_printer()  # Let it be is printed
print(phrase)  # we can also print it directly
 
phrase = "Hey Jude"
 
global_printer()  # Hey Jude is now printed because we changed the value of phrase
 
def printer():
    local_phrase = "Yesterday"
    print(local_phrase)  # local_phrase is a local variable
 
printer()  # Yesterday is printed as expected
 
print(local_phrase)  # NameError is raised
```

### LEGB rule <a href="legb-rule" id="legb-rule"></a>

A variable resolution in Python follows the **LEGB rule**. That means that the interpreter looks for a name in the following order:

1. **Locals**. Variables defined within the function body and not declared global.
2. **Enclosing**. Names of the local scope in all enclosing functions from inner to outer.
3. **Globals**. Names defined at the top-level of a module or declared global with a `global` keyword.
4. **Built-in**. Any built-in name in Python.

```python
x = "global"
def outer():
    x = "outer local"
    def inner():
        x = "inner local"
        def func():
            x = "func local"
            print(x)
        func()
    inner()
 
outer()
```

When the `print()` function inside the `func()` is called the interpreter needs to resolve the name x. The search order will be as following: `func()` locals, `inner()` locals, `outer()` locals, globals, built-in names. So if we execute the code above it will print func local.

there is also a special keyword `global` that allows us to declare a variable global inside a function's body.

When `x` is global you can increment its value inside the function.

```python
x = 1
def global_func():
    global x
    print(x)
    x = x + 1
 
global_func()  # 1
global_func()  # 2
global_func()  # 3
```

`nonlocal` keyword lets us assign to variables in the outer (but not global) scope:

```python
def func():
    x = 1
    def inner():
        x = 2
        print("inner:", x)
    inner()
    print("outer:", x)
 
def nonlocal_func():
    x = 1
    def inner():
        nonlocal x
        x = 2
        print("inner:", x)
    inner()
    print("outer:", x)
 
func()  # inner: 2
        # outer: 1
 
nonlocal_func()  # inner: 2
                 # outer: 2
```

### Интерполяция

Способ получения сложной строки из нескольких простых с использованием специальных шаблонов.

```python
first_name = 'Joffrey'
greeting = 'Hello'

template = "{}, {}!"

print(template.format(greeting, first_name))
# => 'Hello, Joffrey!'
# print("{}, {}!".format(greeting, first_name))
# another way ^
```

## Модули

В Python импортировать модули можно несколькими способами:

1.  импортировать сам модуль
2.  импортировать отдельные определения из модуля
3.  импортировать всё содержимое модуля сразу

В модуле (файле) с именем _greeting.py_ определим функцию `say_hi` и переменную `name`:

```
# file: greeting.py
def say_hi():
    print('Hi!')

name = 'Bob'
```

А в модуле с именем _main.py_ сделаем импорт содержимого модуля _greeting.py_:

```
# file: main.py
import greeting  # заметьте, расширение ".py" не указывается!

print(greeting.name)  # => Bob
greeting.say_hi()     # => Hi!
```

К содержимому же модуля можно обратиться, как говорят, "через точку". Причём можно как получать доступ к переменным (`greeting.name`), так и вызывать функции модуля (`greeting.say_hi()`).

### Импортирование отдельных определений

Синтаксис импорта: `from <имя_модуля (без суффикса ".py")> import <список определений>`

Иногда из всего модуля нужна пара функций или переменных, а имя модуля слишком длинное, чтобы писать его каждый раз. Здесь нам может пригодиться следующий вариант использования инструкции `import`:

```
# file: main.py
from greeting import say_hi, name

print(name)  # используем переменную
say_hi()     # вызываем функцию
```

## Пакеты (packages)

#### Простейший пакет

Давайте рассмотрим пример простейшего пакета. Пусть пакет состоит из каталога `package` и модуля `__init__.py` внутри этого каталога:

```
package/
└── __init__.py
```

Файл `__init__.py` пусть содержит код:

```
# file __init__.py
NAME = 'super_package'
```

Это, хотя и небольшой, но уже полноценный пакет. Его можно импортировать так же, как мы импортировали бы модуль:

#### Абсолютные импорты <a href="absolyutnye-importy" id="absolyutnye-importy"></a>

Абсолютный импорт выглядит как указание полного пути до модуля, включающего все пакеты и _подпакеты (subpackages)_ — да, любой пакет может содержать не только модули, но и вложенные пакеты! Полные пути гарантируют однозначность: интерпретатору всегда понятно, что и откуда импортируется, и читать такие импорты проще.

#### Относительные импорты <a href="otnositelnye-importy" id="otnositelnye-importy"></a>

Относительные импорты выглядят так:

```
from . import module
from .module import function
from .subpackage.module import CONSTANT
```
