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

Rather we will see these pattern from Maintainability/ Flexibility/ Testibility point of view which will mostly depend on how we decouple components.

## Simple Factory

it abstract the creation details of the product from our caller. 

<p> Let's understand it with help of an problem. Suppose you represent Ford from “Ford vs Ferrari” and want to write a class which will represent Cars for some races</p>

![problem_simple_factory1](https://user-images.githubusercontent.com/4917774/87854839-30a6b180-c932-11ea-8da5-2c48004850ff.png)

<p> Note that the Ford class(creational class) will be creating actual class(Product class(s)) based on type of race passed to it. We will run LMPCar in LeMans race and Formula1 Car in grand prix. SO we want to add more kind of cars.</p>

![problem_simple_factory2](https://user-images.githubusercontent.com/4917774/87854841-32707500-c932-11ea-89c2-1ff971102252.png)


<p> So if more cars are added/deleted, you need to modify code. Suppose we want to close classes for modification. What should we do?  > </p>

> Extra thought: Closed for modification?? why ??? suppose it is a library which takes any type of car and library do certain operation on it.

<p> Introducing Simple factory</p>

![simple_factory](https://user-images.githubusercontent.com/4917774/87854851-44521800-c932-11ea-9e07-b9cfe6524a79.png)

By encapsulating the car creation in one class, we now have only one place to make modifications when the implementation changes.

## Factory Method Pattern

it provides an interface for creating objects but allows subclasses to provide implementation of the type of an object that will be created.

<p> To understand above statement, we go ahead with our previous ford example. Now Ford have become famous in car racing. Everybody wants to partner with Ford like Lotus and Cooper. As a good car producer, you want to ensure the quality of the car and you want them to use your time tested code. But even then allow them to create their own car.</p>

<p>Introducing Factory Method Pattern</p>

![factory_with_simple](https://user-images.githubusercontent.com/4917774/87855411-b37d3b80-c935-11ea-8ff2-d873696a9ada.png)

<p>To checkout difference, consider User hierarchy, Creational class(s) and Product class(s). Factory method design pattern is one that provides an interface for creating objects but allows subclasses to alter the type of an object that will be created.</p>

## Abstract Factory Pattern

it encapsulate all simple factories that have common theme without specifying their name.
<p>Suppose we want to put a little control on how factories can work</p>

![abstract_factory_pattern](https://user-images.githubusercontent.com/4917774/87855406-aeb88780-c935-11ea-911a-d1c302c80ca8.png)

## What’s next

- https://python-patterns.guide/gang-of-four/factory-method/
- https://python-patterns.guide/gang-of-four/abstract-factory/
- abstractmethod decorator in abc package
- Dynamic Import with Python
- [python entry points](https://amir.rachum.com/blog/2017/07/28/python-entry-points/)

## License
[MIT](https://choosealicense.com/licenses/mit/)
