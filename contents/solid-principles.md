So good morning
We will be talking today about the SOLID principles
The S here stands for the Single responsibility principle
This principle states that, a class should have a single responsility, and thus should have only one reason to change
So as a bad example, lets assume we have a class:
```
class Employee:
def init ... # create an employee with the given data
...
def calculate_salary(...
...
def generate_employee_report(...)
...

def save(...
    ...
```
So this class, despite that everything it does is related to an employee, yet, it does a lot of things
so it doesn't only create an employee, but also, calculate its salary, generate a report about him etc.

What we need to do here, is to defer other things to other classes/utils
So we should have another class for example that is responsible for calculating the employee salary as well as another one for generating a report etc.

Now lets move to the next principle, which is the letter O
which stands for Open closed principle
This principle states that,  a class should be open for extension, and closed for modification
So as a bad example, we have a shape class
```
class Shape:
    def init(...):
    ...
def calculate_area(...):
    if self.type == 'Square':
        return self.height
    elif self.type == 'Circle':
        return self.radius * 3.14
    elif ...
```
Here the calculate area method, needs to be modified every time we define a new shape type, what we need to do instead, is to have an interface with an abstract `calculate_area` method, and each shape type will implement it
```
class Shape:
    def calculate_area(...):
        pass

class Square(Shape):
    def calculate_area(..):
        return self.height**2

class Circle(Shape):
    # etc..
```

Now for the next principle, which is liskov subsititution principle, it states that a subclasses should be subistitutable with their super classes without needing to change the code.
So as a bad example,
```
class Rectangle:
    def set_height(
        ...
    def set_width(
        ...
class Square(Rectangle):
    def set_height()
        self.set_width = height
```
Here the square inherits from the rectangle, and in order for it to function as a square, it overides the rectangle set height and set width to have the same effect
In this case, if we decide to use a rectangle instance in some place, and we were expecting it to behave same like the square, the code will break.
(The unit test example)
So instead of that, we should have an interface that caters for both and define the required method in the subclasses instead.

Moving on, the Interface seggregation principle, states that, a client should not be forced to implement an interface it doesn't use, or a client should never depend on methods it doesn't use
So for example, lets assume we have a class:
```
class Animal
    def make_sound()
        ...
    def groom()
        ...


class Dog(Animal):
    def make_sound
        ...
    
    def groom()
        ...

class Zebra(Animal)
    def make_sound
        ...

    def groom # dummy implementation that is not needed
        pass
```
Instead we should have two interfaces instead of one, Animal and Pet, the Zebra inherits from Animal, The Pet also inherits from Animal, and defines the groom method there, later we can define Dog/Cat/Bunny to inherit from Pet

Finally, The dependency inversion principle, states that high level modules should depend on abstractions rather than concrete implementations
In another definition:
- high level modules should not depend on low level modules, rather, both should depend on Abstractions
- Abstractions should not depend on details, Details should depend on abstractions
so as a bad example:
```
class SalaryCalculator:
    def calculate

class Employee:
    def calculate_salary
        calculator = SalaryCalculator()
        calculator.calculate()
```
Here is the Employee depends on the SalaryCalculator, but we don't need to do this, we need to decouple
So basically we define a new interface:
```
class Calculator:
    # Interface

class SalaryCalculator(Calculator)
    ...

class Employee:
    def __init__
        self.calculator = Calculator()
        self.calculator.calculate()
# main
calculator = SalaryCalculator()
employee = Employee(calculator=calculator)
```
Here the SalaryCalculator as well as the Employee both depend on the Calculator interface