### REPLACE TYPE CODE WITH STATE/STRATEGY (PATTERN)
As you start working with more complex system  you will find yourself end up with classes which has type-code and then logic around it. Like the following example
```java
public class Appointment{
    private int type;
    public static final int VIRTUAL_CONFERENCE = 0;
    public static final int FACETOFACE = 1;
    public static final int TELE_CONFERENCE = 2;
    //.....
    public Appointment(int type){
        this.type = type;
    }
    public String getInformation(int type){
        switch (type){
            case VIRTUAL_CONFERENCE:
                return conferenceRoom +"\n" + conferenceNum + "\n" + conferenceTime.toString();
            case FACETOFACE:
                return conferenceRoom + "\n" + conferenceTime.toString();
            case TELE_CONFERENCE:
                return conferenceRoom + "\n" + conferenceTime.toString(); +"\n" +conferenceTele + "\n" + conferenceCode;
        }
                
    }
    
}
```

This does seem like a great case where we can convert type code to State/Strategy pattern. Here you can also establish that Virtual_Conference is an appointment!
Have we just found an opportunity to use inheritance? Let's try it.

Assuming once an appointment is created it can not be converted to other type, we can directly use subclassing.

```java
abstract class Appointment{
    private ConferenceTime conferenceTime;
    abstract String getInformation();   
    
}

class FaceToFaceAppointment extends Appointment{
    
}

class VirtualAppointment extends Appointment{
    
}

class TeleAppointment extends Appointment{
    
}


``` 

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
In a simpler world, we start with representing programming concepts with  data types like Strings and integers.  But in some cases you will realize a simple string does not suffice all the logic we may want, for example, a string that represents full name may need it’s own method to render names. Ex: “firstName LastName”, or “Last, fullName” or names with title etc. 

### REPLACE ARRAY WITH OBJECT 
### REPLACE MAGIC NUMBER WITH CONSTANT 

### REPLACE TYPE CODE WITH SUBCLASSES
If you have a class where final type codes exist, for example, in a class named “Appointment” if you have a “private int appointmentType;” which can have values associated with “face to face”, “conf call” etc then you may want to create a superclass called appointment and create subclasses of it like ConferenceCall, and FaceToFaceAppointment which extends Appointment class. 





