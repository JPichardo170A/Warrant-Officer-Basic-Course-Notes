# 🏗️ Objects and Classes

*Module 01 — Python | Day 8*

---

## 🎯 Learning Objectives

- Understand objects as instances of classes
- Use `isinstance()` for type checking
- Create custom classes with `class` keyword
- Implement `__init__` and `__str__` magic methods
- Apply inheritance and polymorphism
- Use `super()` to call parent class methods

---

# Objects and Classes

## Object Review
- In Python every value is some kind of object.  More specifically, an object is an instance of a class
   - We have seen multiple classes in this course and instances of those classes:

| class | object |
| :--- | ---: |
| int | 7 |
| float | 3.14 |
| str | 'hello" |
| bool | True |
| list | [1,2,3,4] |
| tuple | (1,2,3,4) |
| set | {1,2,3} |
| dict | {'a':1} |

##### An object is an instance of a class

```python
someData = [0, 0.0, True, 'hello', (1,2), [3,4], {5,6}, {'a':1}]
for data in someData:
    print(f'{str(repr(data)).ljust(8)} is an instance of {type(data)}')

# repr is a built-in function that returns a printable representation of an object; useful for distinguishing numbers from strings in output
# and showing non-printable characters such as '\n' and '\t'
```

- ```isinstance``` is a built-in function that returns ```True``` if an object is an instance of a specific type and ```False``` otherwise

##### isinstance Function

```python
x = 0
if isinstance(x, int):
    print(f'{(repr(x))} is an instance of an integer.')
else:
    print(f'{repr(x)} is not an instance of an integer.')


if isinstance(x, float):
    print(f'{repr(x)} is an instance of a float.')
else:
    print(f'{repr(x)} is not an instance of a float.')

if isinstance(x, str):
    print(f'{repr(x)} is an instance of a string.')
else:
    print(f'{repr(x)} is not an instance of a string.')
```

## Object Properties: 
- Programmers speak of an 'OO style', or paradigm, of software development. The style involved organizes apps by creating modules called objects.
- An **object** in OO style is a code module that models an entity identified in the problem domain.
- The model stresses that the object is a happy amalgam of data and procedure, often expressed as object attributes and object behaviors.
- **Object attributes** are coded as Python names bound to values.
- **Object behaviors** are coded as Python functions (called methods in OO-speak).
- The OO methodology calls for breaking problems into code modules (objects!) that represent things (entities) in the problem domain.

- The different modules (each one representing something) communicate with each other during the app’s execution.
- One module may send a message to another module which may cause the other module to react (execute a method corresponding to a behavior) which may change data in the object and/or send a message to another object, and so one.
- The objects changing their data, executing methods in accordance to their designed behaviors result in an end state of the completion of the application’s work (the reason the app was developed in the first place).

### Object Properties Examples
- We have seen many examples of object properties in this course, however all of the examples we have seen are methods (object behaviors).

| class | methods (not exhaustive) |
| :-- | --: |
| str | isdigit, upper, title |
| list | append, insert, sort |
| set | add, intersection, difference |
| dict | update, keys, items |

## Creating Objects 

- In Python (and other OO languages) the programmer can use a special function called the class **constructor** (often referred to as the CTOR) to create objects.
   - The classes we have seen in this course have constructors
   - For example, to create an empty set, we use the constructor ```set()```, to create an empty dictionary we use the constructor ```dict()```.

## Creating Custom Classes
- Python provides the programmer the ability to make custom classes.  This is important since Python's built-in classes are not versatile enough to handle everything a programmer might want to include in an app.
### ```class``` keyword
- We use the ```class``` keyword to create custom classes.
- The syntax is ```class Classname:``` with at least one indented line underneath the class declaration.  The name of the class should follow variable naming rules, however by convention most programmers capitalize the first letter of class names.
### A simple class with no attributes or methods

```python
class Useless:
   pass
```

This above class ```Useless``` has a valid class declaration, but it is not very useful.  To create an instance of ```Useless``` we call the constructor ```Useless()```

```python
a = Useless()
print(type(a))
```

### A simple class with one attribute and one method
To make a class meaningful we should give the class attributes and methods

```python
class Pet:
   petType = 'dog'

   def speak(self):
      print(f'I am a {self.petType}.')
```

- In the class ```Pet``` we have one attribute ```petType``` and one method ```speak```.  All instances of ```Pet``` will begin with the attribute ```petType``` which will be assigned the value ```'dog'``` and all instances will have the method ```speak```.
- As described in the section 'Object Properties' above, methods (object behaviors) are functions, hence we use a function definition statement. Note the parameter called ```self```. Every method definition must have at least one parameter.  The first parameter is always used to refer to the object.  The programmer can use any name for this parameter, but by convention programmers name this parameter ```self``` (note that ```self``` is not a keyword).
We can create an instance of ```Pet``` with the constructor ```Pet()```.

```python
a = Pet()
print(type(a))
```

Like other objects we have seen in this course, we can access its properties using dot-notation.

```python
print(a.petType)  # retrieve the value stored in the attribute petType for this instance of Pet
a.speak()         # call the method speak for this instance of Pet
```

In addition to retrieving values stored in attributes, we can assign a new value to an attribute

```python
a.petType = 'cat' # assign a new value to petType for this instance of Pet
print(a.petType)
```

We can add an arbitrary attribute ```name``` to an instance of ```Pet``` that will not exist for other instances of ```Pet```

```python
# Create an arbitrary attribute 'name' for only this instance of Pet
a.name = 'Kitty'
print(a.name)

# Create another instance of Pet
b = Pet()
print(b.petType)

# This instance of Pet does not have a 'name' attribute
print(b.name)    # this will cause a runtime error
```

Without creating a new declaration of ```Pet``` we can add the attribute ```name``` to ```Pet```

```python
# Make 'name' an attribute for Pet
Pet.name = 'unknown'

# Note this will not overwrite already created instances that have an arbitrary name attribute
print(a.name)

# If the already created instance did not yet have a name attribute, it now has one with the default value
print(b.name)

# Create a new instance of Pet - this instance will have the 'name' attribute with the default value
c = Pet()
print(c.name)
```

We can change the value of the attribute ```petType``` for all instances of ```Pet```.

```python
# All instances should be cats
Pet.petType = 'cat'

# Create a new instance of Pet
d = Pet()
print(d.petType)

# Since petType was never an arbitrary attribute for any instances, all instances now have petType with the new value
print(a.petType)
print(b.petType)
print(c.petType)
```

### A more complicated class that has Magic Methods
- Magic Methods are known in Python Documentation as [Special Methods](https://docs.python.org/3/reference/datamodel.html#specialnames).
- Every class inherits (more on this later) from the built-in class ```object```.  Both classes we created ```Useless``` and ```Pet``` inherit from ```object```.  This means that ```Useless``` and ```Pet``` have all the attributes and methods that ```object``` has.  We can see this if we call the function ```dir``` on ```Useless``` or ```Pet```.

```python
print(dir(Useless))
print(dir(Pet))
```

- We see there are many methods that begin with two underscores.  We refer to this as *dunder* (double underscore).  All of these dunder methods are what we call *Magic Methods*.  The two magic methods that we focus on in this course are ```__init__``` and ```__str__```
- ```__init__``` is used to add additional functionality to the class constructor. For example, we can pass in arguments to the constructor to assign these values to attributes.
- ```__str__``` is used to tell Python how to represent an object as a string.  When we call the ```print``` function, behind the scenes Python calls the ```__str__``` magic method to know how to represent the object as a string.

```python
class balloon:
    def __init__(self):
        self.altitude = 0
    
    def __str__(self):
        return f'Current altitude: {self.altitude}'

    def climb(self):
        self.altitude += 1

    def dive(self):
        if self.altitude > 0:
            self.altitude -= 1
        else:
            print('The balloon is at ground level.')

    def crashland(self):
        self.altitude = 0

    def setaltitude(self,newaltitude):
        if newaltitude >= 0:
            self.altitude = newaltitude

    def getaltitude(self):
        return self.altitude
```

- Here the `__init__` method does not take any additional parameters beyond `self`.  Inside the method we must refer to `self` to access the attribute `altitude`.
- Note the `__str__` method **returns** a f-string
- Using the `balloon` class:

```python
b = balloon()
print(b.getaltitude())     # output 0
b.setaltitude(10000)
print(b.getaltitude())     # output 10000
b.climb()
b.climb()
b.climb()
b.dive()
b.climb()
b.climb()
b.climb()
print(b)                   # output 'Current altitude: 10005'
b.crashland()
b.dive()                   # output 'The balloon is at ground level.'
print(b)                   # output 'Current altitude: 0'
```

### A ```Dog``` Class Example with More Magic Methods

```python
class Dog:
    def __init__(self, aName, level):       # magic method that initializes the values of dogName 
        self.dogName = aName              # and goodDogLevel for instance of Dog
        if level < 0:                       # Includes some error checking to make sure goodDogLevel is only between 0 and 10 inclusive
            self.goodDogLevel = 0
        elif level > 10:
            self.goodDogLevel = 10
        else:
            self.goodDogLevel = level
    
    def __del__(self):                      # magic method that performs an action prior to destruction
        print(f'{self.dogName} says, "Goodbye!"')
    
    def __str__(self):                      # magic method called when str or print is called on object instance
        return f'<Dog object named {self.dogName} with level {self.goodDogLevel}>'
    
    def __eq__(self, aDog):                 # magic method called when == comparison made between two dog objects
        return self.goodDogLevel == aDog.goodDogLevel
    
    def __ne__(self, aDog):                 # magic method called when != comparison made between two dog objects
        return self.goodDogLevel != aDog.goodDogLevel
    
    def __lt__(self, aDog):                 # magic method called when < comparison made between two dog objects
        return self.goodDogLevel < aDog.goodDogLevel
    
    def __le__(self, aDog):                 # magic method called when <= comparison made between two dog objects
        return self.goodDogLevel <= aDog.goodDogLevel

    def __gt__(self, aDog):                 # magic method called when > comparison made between two dog objects
        return self.goodDogLevel > aDog.goodDogLevel
    
    def __ge__(self, aDog):                 # magic method called when >= comparison made between two dog objects
        return self.goodDogLevel >= aDog.goodDogLevel
    
    def setName(self, aName):               # change value of dogName without user referencing dogName
        self.dogName = aName
    
    def setLevel(self, level):              # change value of goodDogLevel without user referencing goodDogLevel
        if level < 0:
            self.goodDogLevel = 0
        elif level > 10:
            self.goodDogLevel = 10
        else:
            self.goodDogLevel = level
    def query(self):
        print(f'The name of this dog is {self.dogName} and its level of goodness is {self.goodDogLevel}.')
```

Using the `Dog` class:

```python
a = Dog('Lucky',8)
b = Dog('Bailey',8)
a.query()                                                         # output 'The name of this dog is Lucky and its level of goodness is 8.'
b.query()                                                         # output 'The name of this dog is Bailey and its level of goodness is 8.'
a.setName('Smilla')
a.query()                                                         # output 'The name of this dog is Smilla and its level of goodness is 8.'
b.setName('Buddy')
b.query()                                                         # output 'The name of this dog is Buddy and its level of goodness is 8.'
print((a))                                                        # output '<Dog object named Smilla with level 8>'
print((b))                                                        # output '<Dog object named Buddy with level 8>'
print(f'Are these dogs equal: {a == b}')                          # output 'Are these dogs equal: True'
a.setLevel(9)
print((a))                                                        # output '<Dog object named Smilla with level 9>'
print((b))                                                        # output '<Dog object named Buddy with level 8>'
print(f'Are these dogs equal: {a == b}')                          # output 'Are these dogs equal: False'
print(f'Is the first dog more good than the second dog: {a > b}') # output 'Is the first dog more good than the second dog: True'
del a                                                             # output 'Smilla says, "Goodbye!"'
del b                                                             # output 'Buddy says, "Goodbye!"'
# the 'del' statement is used to delete an object from memory
```

#### What does help say about the Dog class?

```python
help(Dog)
```

### Inheritance
- As mentioned above all classes inherit from the built-in class ```object```. This means that every class has all the attributes and methods that ```object``` has.  We can choose to overwrite the inherited attributes and methods by implementing our own version.  We see in the two previous examples that we overwrote some inherited magic methods by implementing our own versions.
- Besides inheriting from the built-in class ```object```, we can inherit from any class we want.  To do this in our class declaration we include parentheses after the class name and before the colon.  Inside the parentheses we type the name of the class we want our class to inherit from.
- For example, we could use inheritance to create a class called ```myList``` that inherits from ```list``` and add some functionality that ```list``` does not have.

```python
class myList(list):
    def cnt(self):
        return len(self)

aList = myList((1,2))
print(aList.cnt())      # output 2
aList.append(3)         # myList inherits the append method from list
print(aList.cnt())      # output 3
```

#### Another example of inheritance
- We have a base class called ```Shape``` that has attributes ```shapeName``` and ```area``` and the methods ```printArea``` and ```getArea```
- We have a class called ```Rectangle``` that inherits from ```Shape``` and overwrites the ```__init__``` and ```getArea``` methods. It also has two attributes of its own ```width``` and ```height```.
- We have a class called ```Square``` that inherits from ```Rectangle``` and overwrites the ```__init__``` method.
- We have a class called ```Circle``` that inherits from ```Shape``` and overwrites the ```__init__``` and ```getArea``` methods. It also has one attribute of its own ```radius```

```python
from math import pi

class Shape:
    area = 0
    def printArea(self):
        shapeName = str(self.__class__.__name__).lower()
        print(f'The area of this {shapeName} shape is {self.area:.2f}.')
    
    def getArea(self):
        print('This method is a placeholder that should be overrided in a subclass.')

class Rectangle(Shape):

    def __init__(self, w, h):
        self.width = w
        self.height = h
        self.getArea()

    def getArea(self):
        self.area = self.width * self.height

class Square(Rectangle):
    def __init__(self, side):
        self.width = side
        self.height = side
        self.getArea()

class Circle(Shape):

    def __init__(self, r):
        self.radius = r
        self.getArea()

    def getArea(self):
        self.area = pi * self.radius**2
```

Using these classes:

```python
MainShape = Shape()
MainShape.printArea()     # output 'The area of this shape shape is 0.00.'
MainShape.getArea()       # output 'This method is a placeholder that should be overrided in a subclass.'

R = Rectangle(5,10)
R.printArea()             # output 'The area of this rectangle shape is 50.00.'

C = Circle(5)
C.printArea()             # output 'The area of this circle shape is 78.54.'

S = Square(5)
S.printArea()             # output 'The area of this circle shape is 78.54.'
```

### Polymorphism
- Polymorphism in object oriented programming is having multiple classes that all inherit from one class, but each modifies its inherited methods to do something different.
- In this example we have a class called ```Base``` and three classes ```A```, ```B```, and ```C``` which inherit from ```Base```.  In turn the classes ```A```, ```B```, and ```C``` each modify its inherited ```behavior``` method differently.

```python
class Base:
    def behavior(self):
        print('Base behavior')

class A(Base):
    def behavior(self):
        print('A behavior')

class B(Base):
    def behavior(self):
        print('B behavior')

class C(Base):
    def behavior(self):
        Base.behavior(self)
        print('C behavior')
```

Using these classes:

```python
l = []
l.append(A())
l.append(B())
l.append(C())

for i in l:
    i.behavior()
```

### A military example that uses polymorphism and interitance
- We have a base class called ```Soldier```. All Soldiers should know the Army Song, the Soldier Creed, be able to be promoted and change ETS date
- We have three classes called ```NCO```, ```Warrant```, and ```Officer``` that all inherit from ```Solider```.
- All NCOs should do everything a Soldier can do and also know the NCO Creed.
- All Warrants should do everything a Soldier can do and also know the Warrant Officer Creed.
- All Officers should do everything a Soldier can do and also be able to Administer the Oath.  Additionally Officers have the attribute ```degree```

```python
class Soldier:
    
    def __init__(self, lname, fname, dodid, rank, etsdate):
        self.lname = lname
        self.fname = fname
        self.dodid = dodid
        self.etsdate = etsdate
        self.rank = rank
    
    def __str__(self):
        return f'{self.__class__.__name__}: {self.rank} {self.fname} {self.lname}'

    def armySong(self):
        print('March along, sing our song, with the Army of the free ...')
    
    def soldierCreed(self):
        print('I am an American Solider. I am a warrior ...')
    
    def setRank(self, rank):
        self.rank = rank
    
    def setEtsDate(self, etsdate):
        self.etsdate = etsdate

class NCO(Soldier):
    
    def ncoCreed(self):
        print('No one is more professional than I. I am a Non-Commissioned Officer ...')

class Warrant(Soldier):
   
    def warrantCreed(self):
        print('Willingly render loyal services to superiors, subordinates and peers ...')

class Officer(Soldier):
    
    def __init__(self, lname, fname, dodid, rank, etsdate, degree):
        self.degree = degree
        super().__init__(lname, fname, dodid, rank, etsdate)
    
    def admininsterOath(self):
        print('Raise your right hand and repeat after me ...')
```

Using these classes:

```python
s = Soldier('Doe', 'James', '1234', 'SPC', '1-1-1')
n = NCO('Doe', 'Jane', '2345', 'SSG', '1-1-1')
w = Warrant('Doe', 'John', '3456', 'CW2', '1-1-1')
o = Officer('Doe', 'Jill', '4567', 'CPT', '1-1-1', 'Bachelors')

print(s)               # output 'Soldier: SPC James Doe' 

print(n)               # output 'NCO: SSG Jane Doe'
n.armySong()           # output 'March along, sing our song, with the Army of the free ...'
n.ncoCreed()           # output 'No one is more professional than I. I am a Non-Commissioned Officer ...'

print(w)               # output 'Warrant: CW2 John Doe'
w.soldierCreed()       # output 'I am an American Solider. I am a warrior ...'
w.warrantCreed()       # output 'Willingly render loyal services to superiors, subordinates and peers ...'

print(o)               # output 'Officer: CPT Jill Doe'
o.setRank('MAJ')
print(o)               # output 'Officer: MAJ Jill Doe'
o.admininsterOath()    # output 'Raise your right hand and repeat after me ...'
```


---

[⬆️ Back to Module Index](../README.md)
