Ruby's answer to the multiple inheritance problem is not, strictly
speaking, multiple inheritance at all, but rather the use of modules as
"mix-ins". Mix-ins allow one class to be "mixed into" another class,
thereby bringing all of it's instance methods into the new class. You
can mix-in as many modules as you need in your class. By doing this, you
are able to easily leverage the functionality of any existing mix-in in
your new class. The strength of this approach is that you avoid the
potential problem of inheriting from two classes who themselves inherit
from one base class, and the namespace collisions that can ensue
(commonly referred to as the "diamond problem"). If you are careful and
attentive to the order in which you "include" modules in your class, you
will always know which version of a method will be called from a
mixed-in module. Another strength of this approach is perhaps more
abstract, but in modeling your classes, mix-ins allow you think of your
class as "having" certain behavior, instead of "being" a certain thing.
My class "has" Comparable functionality, but is not primarily a
Comparable child class.

One of the weaknesses of this approach is that it's easy for your
classes to become huge in a hurry before you write any code. Some
modules, in Rails core for example, already contain hundreds of methods.
However, I think with attentive planning, this can be avoided.

Having worked with Java and C++ before, overall I find Ruby's approach
to the multiple inheritance problem to be easier to work with, more
elegant, and more powerful than other approaches.
