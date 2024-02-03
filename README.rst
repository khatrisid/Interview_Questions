.. contents::
   :local:
   :depth: 3


Encapsulation:
===============================================================================
Encapsulation in Java is a process of wrapping code and data together into a single unit.

Advantages of Encapsulation in Java:


1) By providing only a setter or getter method, you can make the class read-only or write-only. In other words, you can skip the getter or setter methods.
2) It provides you the control over the data. Suppose you want to set the value of id which should be greater than 100 only, you can write the logic inside the setter method. You can write the logic not to store the negative numbers in the setter methods.
3) It is a way to achieve data hiding in Java because other classes will not be able to access the data through the private data members.
 

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

Java creates a copy of the variable being passed in the method and then does the manipulations. Hence the change is not reflected in the main method.

.. code:: JAVA

      public class Main {
          public static void main(String[] args)
          {
              int x = 5;
              change(x);
              System.out.println(x);
          }
          public static void change(int x) 
          {
              x = 10; 
          }
      }

      Output: 5
      
                           
How about objects or references?
                           
In Java, all primitives like int, char, etc are similar to C/C++, but all non-primitives (or objects of any class) are always references.
  
.. code:: JAVA
  
        // A Java program to show that we can change members using
      // reference if we do not change the reference itself.
      class Test {
          int x;
          Test(int i) { 
            x = i; 
         }
          Test() {
            x = 0; 
         }
      }

      class Main {
          public static void main(String[] args)
          {
              // t is a reference
              Test t = new Test(5);

              // Reference is passed and a copy of the reference is created in change()
              change(t);

              // New value of x is printed
              System.out.println(t.x);
          }

          // This change() doesn't change the reference, it only
          // changes member of the object referred by reference
          public static void change(Test t) { 
            t.x = 10; 
         }
      }

      Output: 10

We learned that parameter passing in Java is always Pass-by-Value. However, the context changes depending upon whether we’re dealing with Primitives or Objects:

For Primitive types, parameters are pass-by-value
For Object types, the object reference is pass-by-value


Access Modifiers in Java:
===============================================================================

The access modifiers in Java specify the accessibility or scope of a field, method, constructor, or class. We can change the access level of fields, constructors, methods, and classes by applying the access modifier to it.

There are four types of Java access modifiers:

1) Private: The access level of a private modifier is only within the class. It cannot be accessed from outside the class.
2) Default: The access level of a default modifier is only within the package. It cannot be accessed from outside the package. If you do not specify any access level, it will be the default.
3) Protected: The access level of a protected modifier is within the package and outside the package through the child class. If you do not make the child class, it cannot be accessed from outside the package.
4) Public: The access level of a public modifier is everywhere. It can be accessed from within the class, outside the class, within the package, and outside the package.

Java Access Modifiers with Method Overriding

If you are overriding any method, the overridden method (i.e. declared in a subclass) must not be more restrictive.

.. code:: JAVA

      class A{  
         protected void msg() {
            System.out.println("Hello java");
         }  
      }  

      public class Simple extends A {  
         void msg() {
            System.out.println("Hello java");
         }//C.T.Error  

         public static void main(String args[]) {  
            Simple obj=new Simple();  
            obj.msg();  
         }  
      }  
      

The default modifier is more restrictive than protected. That is why, there is a compile-time error.



ArrayList, LinkedList, and Vector are all implementations of the List interface. Which of them is most efficient for adding and removing elements from the list? Explain your answer, including any other alternatives you may be aware of:
===============================================================================

Of the three, LinkedList is generally going to give you the best performance. Here’s why:

ArrayList and Vector each use an array to store the elements of the list. As a result, when an element is inserted into (or removed from) the middle of the list, the elements that follow must all be shifted accordingly. Vector is synchronized, so if a thread-safe implementation is not needed, it is recommended to use ArrayList rather than Vector.

LinkedList, on the other hand, is implemented using a doubly linked list. As a result, an inserting or removing an element only requires updating the links that immediately precede and follow the element being inserted or removed.


Why would it be more secure to store sensitive data (such as a password, social security number, etc.) in a character array rather than in a String?
===============================================================================

In Java, Strings are immutable and are stored in the String pool. What this means is that, once a String is created, it stays in the pool in memory until being garbage collected. Therefore, even after you’re done processing the string value (e.g., the password), it remains available in memory for an indeterminate period of time thereafter (again, until being garbage collected) which you have no real control over. Therefore, anyone having access to a memory dump can potentially extract the sensitive data and exploit it.

In contrast, if you use a mutable object like a character array, for example, to store the value, you can set it to blank once you are done with it with confidence that it will no longer be retained in memory.


volatile keyword in java
===============================================================================

The volatile keyword in Java is used to mark a Java variable as “being stored in main memory”. Every thread that accesses a volatile variable will read it from main memory, and not from the CPU cache. This way, all threads see the same value for the volatile variable.

The volatile keyword is often used with flags that indicate that a thread needs to stop running. For example, a thread might have a boolean flag called “done”, and when another thread sets this flag to “true”, the first thread will know to stop running. Without the volatile keyword, the first thread might keep running indefinitely, because it would never see the updated value of the “done” flag.

Compare the sleep() and wait() methods in Java, including when and why you would use one vs. the other.
===============================================================================

Sleep(): This Method is used to pause the execution of the current thread for a specified time in Milliseconds. Here, Thread does not lose its ownership of the monitor and resumes its execution

Wait(): This method is defined in the object class. Simply pauses the thread until either (a) the specified number of milliseconds have elapsed or (b) it receives a desired notification from another thread (whichever is first).
                                                                                                OR
It tells the calling thread to wait until another thread invokes the notify() or notifyAll() method for this object, The thread waits until it reobtains the ownership of the monitor and Resume Execution.

sleep() is most commonly used for polling, or to check for certain results, at a regular interval. wait() is generally used in multithreaded applications, in conjunction with notify() / notifyAll(), to achieve synchronization and avoid race conditions.

Java program to demonstrate the difference between wait and sleep 

.. code:: JAVA

   class GfG{
   
   private static Object LOCK = new Object();
 
   public static void main(String[] args) 
     throws InterruptedException {
  
       Thread.sleep(1000);
   
       System.out.println("Thread '" + Thread.currentThread().getName() +
         "' is woken after sleeping for 1 second");
  
       synchronized (LOCK) 
       {
           LOCK.wait(1000);
       
           System.out.println("Object '" + LOCK + "' is woken after" +
             " waiting for 1 second");
       }
   }
   }

