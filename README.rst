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
 

.. code:: JAVA

    //A Java class which is a fully encapsulated class.  
    //It has a private data member and getter and setter methods.  
    package com.javatpoint;  
    public class Student{  
    //private data member  
    private String name;  
    //getter method for name  
    public String getName(){  
    return name;  
    }  
    //setter method for name  
    public void setName(String name){  
    this.name=name  
    }  
    }  


