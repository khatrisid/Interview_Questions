.. contents::
   :local:
   :depth: 3


Encaptulation:
===============================================================================
Encapsulation in Java is a process of wrapping code and data together into a single unit.

Advantage of Encapsulation in Java:

.. code:: JAVA

      *By providing only a setter or getter method, you can make the class read-only or write-only. In other words, you can skip the getter or setter methods.
      *It provides you the control over the data. Suppose you want to set the value of id which should be greater than 100 only, you can write the logic inside         the setter method. You can write the logic not to store the negative numbers in the setter methods.
      *It is a way to achieve data hiding in Java because other class will not be able to access the data through the private data members.
 

Java Package:
===============================================================================

A java package is a group of similar types of classes, interfaces and sub-packages.

Package in java can be categorized in two form, built-in package and user-defined package.

There are many built-in packages such as java, lang, awt, javax, swing, net, io, util, sql etc.

Advantage of Java Package

1) Java package is used to categorize the classes and interfaces so that they can be easily maintained.

2) Java package provides access protection.

3) Java package removes naming collision.


Describe and compare fail-fast and fail-safe iterators. Give examples:
===============================================================================

The main distinction between fail-fast and fail-safe iterators is whether or not the collection can be modified while it is being iterated. Fail-safe iterators allow this; fail-fast iterators do not.

Fail-fast iterators operate directly on the collection itself. During iteration, fail-fast iterators fail as soon as they realize that the collection has been modified (i.e., upon realizing that a member has been added, modified, or removed) and will throw a ConcurrentModificationException. Some examples include ArrayList, HashSet, and HashMap (most JDK1.4 collections are implemented to be fail-fast).

Fail-safe iterates operate on a cloned copy of the collection and therefore do not throw an exception if the collection is modified during iteration. Examples would include iterators returned by ConcurrentHashMap or CopyOnWriteArrayList.

Java is Strictly Pass by Value!:
===============================================================================

Java creates a copy of the variable being passed in the method and then do the manipulations. Hence the change is not reflected in the main method.

.. code:: JAVA

      public class Main {
          public static void main(String[] args)
          {
              int x = 5;
              change(x);
              System.out.println(x);
          }
          public static void change(int x) { x = 10; }
      }

      Output: 5
      
                           How about objects or references?
                           
In Java, all primitives like int, char, etc are similar to C/C++, but all non-primitives (or objects of any class) are always references.
  
.. code:: JAVA
  
        // A Java program to show that we can change members using
      // reference if we do not change the reference itself.
      class Test {
          int x;
          Test(int i) { x = i; }
          Test() { x = 0; }
      }

      class Main {
          public static void main(String[] args)
          {
              // t is a reference
              Test t = new Test(5);

              // Reference is passed and a copy of reference
              // is created in change()
              change(t);

              // New value of x is printed
              System.out.println(t.x);
          }

          // This change() doesn't change the reference, it only
          // changes member of object referred by reference
          public static void change(Test t) { t.x = 10; }
      }

      Output: 10

