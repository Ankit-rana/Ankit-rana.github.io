# Factory In Python

We will see ways to decouple code namely factory, factory method pattern and abstract factory pattern

## Overview

* Simple Factory
* Factory Method Pattern
* Abstract factory Pattern

The Factory Method  and Abstract Factory patterns was used as an workaround for the lack of first-class functions and classes in less powerful programming languages like cpp and java. That way, It is a poor fit for Python where we can instead simply pass a class or a factory function when a library needs to create objects on our behalf. 

```python
# from wikipedia
from abc import ABC, abstractmethod
from sys import platform


class Button(ABC):

    @abstractmethod
    def paint(self):
        pass


class LinuxButton(Button):
    def paint(self):
        return 'Render a button in a Linux style'


class WindowsButton(Button):

    def paint(self):
        return 'Render a button in a Windows style'


class MacOSButton(Button):

    def paint(self):
        return 'Render a button in a MacOS style'


if platform == "linux":
    factory = LinuxButton
elif platform == "darwin":
    factory = MacOSButton
elif platform == "win32":
    factory = WindowsButton
else:
    raise NotImplementedError(
        f'Not implemented for your platform: {platform}'
    )

button = factory()
result = button.paint()
print(result)
```

Rather we will see these pattern from maintainability point of view - how to decouple components.

## Factory

abstract the creation details of the product from our caller. 

```python
more code
```

## Factory Method Pattern

provides an interface for creating objects but allows subclasses to provide implementation of the type of an object that will be created.

```python
more code
```

## Abstract Factory Pattern

encapsulate all simple factories that have common theme without specifying their name

```python
more code
```

## License
[MIT](https://choosealicense.com/licenses/mit/)
