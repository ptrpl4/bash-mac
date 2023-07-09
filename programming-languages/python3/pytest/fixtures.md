# fixtures

## Info

link [https://docs.pytest.org/en/stable/fixture.html](https://docs.pytest.org/en/stable/fixture.html)

### Structure

/project\
\- tests\
\-- conftest.py - for fixtures

## Usage

Example 1

```python
@pytest.fixture
def accum():
  return Accumulator()

def test_accumulator_init(accum):
  assert accum.count == 0

def test_accumulator_add_one(accum):
  accum.add()
  assert accum.count == 1

def test_accumulator_add_three(accum):
  accum.add(3)
  assert accum.count == 3

def test_accumulator_add_twice(accum):
  accum.add()
  accum.add()
  assert accum.count == 2

def test_accumulator_cannot_set_count_directly(accum):
  with pytest.raises(AttributeError, match=r"can't set attribute") as e:
    accum.count = 10
```

fixture should always return something

Example 2

```python
import pytest


# Arrange
@pytest.fixture
def first_entry():
    return "a"


# Arrange
@pytest.fixture
def order():
    return []


# Act
@pytest.fixture
def append_first(order, first_entry):
    return order.append(first_entry)


def test_string_only(append_first, order, first_entry):
    # Assert
    assert order == [first_entry]
```
