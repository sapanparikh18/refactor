

# Refactoring

The are some of my notes I took while reading Martin Fowler's _Refactoring. Improving THE Design of Existing Code_
While refactoring is synonymous to “code clean up”, before you start cleaning a legacy system a good set of test cases is a prerequisite. Having a suit of test cases will keep two things in check.

1. While you refactor code you are not introducing new bugs 
2. As a result of refactoring you are not making your system slower

While you start refactoring the system a slight performance loss is expected but the assumption is that only 10% of the code is the root cause behind the slowness of any system and refactoring will help you identify that 10% as opposed to speculating what’s slow and what’s not.

## CODE IDENTIFICATION
Usually would want to start with a method or class which is irrationally long and complex. In today’s tools the most suitable code fragments will show up with high cyclomatic or cognitive complexity. Or other simpler yard stick to identify code that needs refactoring is simply find all methods which are too long, may be more than 50 to 100 lines.  I have seen system containing single method bodies spanning more than 10000 lines. That being said there is no easy way to define “long methods”. May be you can start with top 10% of your longest methods!

## REFACTORING TECHNIQUES 
There are a few refactoring methodologies which you can use if you are faced with scary long methods



### EXTRACT METHOD
This refactoring method is the easiest to identify and perform. If in your code you are able to find a piece of code that changes only one variable then it may be best to move it to its own method and return the value of that variable. The variables which are not being changed but are part of the logic should be sent as parameters. Usual targets to extracting methods are logical code blocks like if, else, for loop etc. This way not only you are shortening the method but also decreasing the cognitive complexity of overall method. Essentially, in the end your code will be easier to understand, and modify.f
Also, with modern tools it will be very easy to

### MOVE METHOD
You can use Move Method refactoring techniques in one of the following scenarios.
If your code depends too much on data of another class then most probably your method should also be in another class. This means if you are using far too many getters and setters of other class before a logic is executed then the logic should be moved to the class which is being instantiated to invoke getters and setters.
If you are working on a legacy system which does not have a separate data access layer or a proper MVC then you may want to move chunks of code accessing database to DAO. In a nutshell, follow an architecture, move your DB access code to DAO, move your UI related code to UI components, and move your logic to services.

### INTRODUCE PARAMETER OBJECT
Methods with many primitive parameters are the best candidates to introduce parameter objects. In many cases one can observe a few parameter exists together, most common example is a date range. If you have methods which are expecting parameters like `fromDate` and `toDate` it may be a good idea to move them to a class named DateRange with fields fromDate, toDate. Not only number of parameters will decrease in your method they will be easily understandable to a reader of the code. Also, one more crucial benefit is that you get a central place for validation of inputs. Imagine, rather than just passing dates to method what if you could instantiate a DateRange object where the constructor also took the duration for validation and threw exception if date range was more than the duration passed in the constructor!

### INTRODUCE FOREIGN METHOD
When literary class does not have the method you need

### INTRODUCE LOCAL EXTENSION
When literary class does not have methods you need and you create a new class with delegation

### ENCAPSULATE FIELDS
When data classes have public fields
### ENCAPSULATE COLLECTIONS
When data classes return collections they should be changed to return 
### REPLACE INHERITANCE WITH DELEGATION
### REPLACE TYPE CODE WITH STATE/STRATEGY (PATTERN)
### FORM TEMPLATE METHOD (PATTERN)
### INLINE TO TEMP
### SPLIT TEMP VARIABLE
### REMOVE ASSIGNMENTS TO PARAMETERS
### EXTRACT CLASS
### HIDE A DELEGATE 
Instead of `employee.getDepartment().getManager()` it should be `employee.getManager()`

### INTRODUCE A FOREIGN METHOD
What we call helper methods. Used to work with library classes to which we do not have access to edit code.
### Introduce local extension
When a literary class does not provide methods that you frequently need you may want to create a new class that solely extends functionalities of literary class. A good example would be a class that adds functionalities to Date in Java.
### Replace data value with object
In a simple world we start with start representing programming concepts with simple data types like Strings and integers.  But in some cases you will realize a simple string does not suffice all the logic we may want, for example, a string that represents full name may need it’s own method to render names. Ex: “firstName LastName”, or “Last, fullName” or names with title etc. 

### REPLACE ARRAY WITH OBJECT 
### REPLACE MAGIC NUMBER WITH CONSTANT 

### REPLACE TYPE CODE WITH SUBCLASSES
If you have a class where final type codes exists, for example, in a class named “Appointment” if you have a “private int appointmentType;” which can have values associated with “face to face”, “conf call” etc then you may want to create a super class called appointment and create subclasses of it like ConferenceCall, and FaceToFaceAppointment which extends Appointment class. 





