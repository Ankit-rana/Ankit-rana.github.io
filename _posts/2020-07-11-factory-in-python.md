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


<p> So if more cars are added/deleted, you need to modify code. Suppose we want to close classes for modification. What should we do?
Extra thought: Closed for modification?? why ??? suppose it is a library which takes any type of car and library do certain operation on it.</p>
<p> Introducing Simple factory</p>

![simple_factory](https://user-images.githubusercontent.com/4917774/87854851-44521800-c932-11ea-9e07-b9cfe6524a79.png)

By encapsulating the car creation in one class, we now have only one place to make modifications when the implementation changes.

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
