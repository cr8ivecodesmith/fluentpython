Python Data Model
=================

Describes Python as a framework where the special methods referred as `dunder methods` are what
makes everything in Python consistent.

We wrote a class the represents a deck of cards to demonstrate the Python Data Model (PDM) at work.

Implementing the `__len__` and `__getitem__` methods allows this class to behave like any other
iterable. This means it can be sliced, looped over, indexed, _(custom)_ sorted, etc.

Using the `len()` function on a class that implements the `__len__` method standardizes how we get
the number of items in a sequence. Otherwise we'll have to figure out if its via calling
`.length()`, `.size()`, etc.

Just like a framework, where the core features behaves consistenly as long as you implement certain
things it looks out for. You also benefit from using the standard library instead of reinventing the
wheel.

Examples explored:

- Getting the number of items via the `len()` function
- Using `random.choice` to pick a random card
- Looping over the deck with for loop
- Checking for existing cards via the `in` operator
- Slicing
- Accessing individual cards via its index

#### how special methods are used

You don't call the dunder methods directly. The Python interpreter is the one to call the `__len__`
method for example when you use the `len()` function. If it checks that the object instance is from
a user defined class, it looks for the implementation of `__len__`.

The call to dunder methods are implicit in most cases. For example, if the `__iter__` method is
implemented, the Python interpreter will call that, otherwise it'll just call a default
implementation of that method.

The only dunder method you would normally call is the `__init__` to invoke the initializer of the
super class in your own initializer. For the other dunder methods, its better to use the equivalent
built-in functions such as:

built-in     | dunder
:------------|:------------
len()        | `__len__`
iter()       | `__iter__`
str()        | `__str__`

#### emulating numeric types


###### footnotes

- See carddeck.py for the FrenchDeck class.
- In Python 2, you'll have to explicitly write `FrenchDeck(object)` but in Python 3, this is the
  default.
- At this point the deck cannot be shuffled because its immutable. This can be changed by violating
  encapsulation and handling the `_cards` attribute directly. This will be addressed in chapter 11
  by implementing the `__setitem__` method.
- If we implement the `__contains__` method, we can customize how the `in` operator would behave.
- If we implement the `__iter__` method, we can customize how the `for .. in` loop would behave.
- The Python interpreter call for the `__iter__` method actually is an invocation of the `iter()`
  function.
- Avoid naming your methods with dunders as they may acquire special meaning in the future.


###### exercise ideas

- Implement the `__contains__` method on the card deck to _..do what?_
- Implement the `__iter__` method on the card deck to _..do what?_
- Create a dict-like class that implements the `__len__`, `__contains__`, `__iter__`, `__getitem__`
  methods. The dict-like class will _..do what?_
- Observe the method calls in the FrenchDeck class with `pdb`. What happens if those are just
  implementing from the super class?
