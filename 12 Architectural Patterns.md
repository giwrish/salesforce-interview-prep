# Object Oritented Concepts

## Inheritance
Inheritance is a mechanism in which one object acquires all the properties and behaviours of a parent object.

### Why use inheritance in
-   For [Method Overriding](https://www.javatpoint.com/method-overriding-in-java) (so [runtime polymorphism](https://www.javatpoint.com/runtime-polymorphism-in-java) can be achieved).
-   For Code Reusability.

Inheritance represents the IS-A relationship. SavingsAccount IS-A Account. CurrentAccount IS-A Account. FixedDeposit IS-A Account.

Inheritance can be achieved by extending abstract and virtual class in apex.

<img width="922" alt="image" src="https://github.com/shindegirish/salesforce-interview-prep/assets/32008754/d04861ff-78a0-44a6-84d1-71d49fee423d">


## Polymorphism
- Polymorphism is a concept by which we can perform a single action in different ways.
- There are two types of polymorphism : compile-time polymorphism and runtime polymorphism. We can perform polymorphism by method overloading and method overriding.
- Method overloading - compile time polymorphism.
- Method overriding - run time polymorphism.
- SOQL TYPEOF - Runtime polymorphism exmple : https://developer.salesforce.com/docs/atlas.en-us.soql_sosl.meta/soql_sosl/sforce_api_calls_soql_select_typeof.htm
- 
SELECT Name FROM Account
WHERE CreatedById IN
    (
    SELECT 
        TYPEOF Owner
            WHEN User THEN Id
            WHEN Group THEN CreatedById
        END
    FROM CASE
    )
  SELECT
    TYPEOF What
        WHEN Account THEN Id, LastModifiedDate
        WHEN Opportunity THEN Id
    END
FROM Task
- Why Method Overloading is not possible by changing the return type of method only?
Because of ambiguity, see below exmaple
```
class Adder{  
static int add(int a,int b){return a+b;}  
static double add(int a,int b){return a+b;}
}

@isTest
class TestAdder{  
	static testAdd(){
		Test.startTest();
		
		Adder.add(1,1); // THIS IS AMBIGOUS, PROGRAM WONT KNOW WHICH METHOD IS CALLED
		
		Test.stopTest();
	}
}  
```

## Abstraction
Abstraction is a process of hiding the implementation details and showing only functionality to the user.

### Ways to achieve Abstraction

There are two ways to achieve abstraction
1.  Abstract class (0 to 100%)
2.  Interface (100%)

## Encapsulation
Encapsulation is defined as the wrapping up of data under a single unit. It is the mechanism that binds together code and the data it manipulates. Another way to think about encapsulation is, it is a protective shield that prevents the data from being accessed by the code outside this shield.

-   Technically in encapsulation, the variables or data of a class is hidden from any other class and can be accessed only through any member function of its own class in which it is declared.
-   As in encapsulation, the data in a class is hidden from other classes using the data hiding concept which is achieved by making the members or methods of a class private, and the class is exposed to the end-user or the world without providing any details behind implementation using the abstraction concept, so it is also known as a **combination of data-hiding and abstraction**.
-   Encapsulation can be achieved by Declaring all the variables in the class as private and writing public methods in the class to set and get the values of variables


# [interface vs abstract vs virtual](https://salesforceprofs.com/abstract-virtual-interface-in-apex/)
<table class="s-table">
<thead>
<tr>
<th>Feature</th>
<th>Interface</th>
<th>Abstract</th>
<th>Virtual</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>Keyword</strong></td>
<td><em><strong><code>interface</code></strong></em> <br/> e.g <code>public interface MyInterface {}</code></td>
<td><strong><code>abstract</code></strong> <br/> e.g <code>public abstract class MyAbstractClass {}</code></td>
<td><em><strong><code>virtual</code></strong></em> <br/> e.g <code>public virtual class MyVirtualClass {}</code></td>
</tr>
<tr>
<td><strong>How to use?</strong></td>
<td>By <em><strong><code>implements</code></strong></em> <br/> e.g <code>public class MyChildClass implements MyInterface {}</code></td>
<td>By <strong><code>extends</code></strong> <br/> e.g <code>public class MyChildClass extends MyAbstractClass {}</code></td>
<td>By <strong><code>extends</code></strong> <br/> e.g <code>public class MyChildClass extends MyVirtualClass {}</code></td>
</tr>
<tr>
<td><strong>Type of Methods</strong></td>
<td>Only method signature <br/> e.g <code>String getFullName(String firstName, String lastName);</code></td>
<td>Can contains <code>abstract</code>, <code>virtual</code> and implements own methods. <br/> e.g <code>abstract String getFullName(String firstName, String lastName);</code> <br/> <code>public virtual String getFullName(String firstName, String lastName);</code></td>
<td>Can contains only <code>virual</code> and implements onw methods <br/> e.g <code>public virtual String getFullName(String firstName, String lastName);</code></td>
</tr>
<tr>
<td><strong>Implement Parent Mehthods</strong></td>
<td>✅ All interface's methods needs to be implemented</td>
<td>✅ Only methods signed as <code>abstract</code></td>
<td>❌ Cannot force child class to implements parent methods</td>
</tr>
<tr>
<td><strong>Override Parent Methods</strong></td>
<td>❌ Interface doesn't contain logic to override</td>
<td>✅ Only methods signed as <code>virtual</code></td>
<td>✅ Only methods signed as <code>virtual</code></td>
</tr>
<tr>
<td><strong>Has basic logic?</strong></td>
<td>❌ Interface contains only method signature</td>
<td>✅ Methods signed as <code>virual</code> and inner methods can contains basic logic</td>
<td>✅ Methods signed as <code>virual</code> and inner methods can contains basic logic</td>
</tr>
<tr>
<td><strong>Can be initialized directly?</strong></td>
<td>❌ <s>new MyInterface();</s></td>
<td>❌ <s>new MyAbstractClass();</s></td>
<td>✅ new MyVirtualClass();</td>
</tr>
<tr>
<td><strong>Pros</strong></td>
<td>✅ New layer of abstraction. <br/> ✅ Interface can be treated as a new data type. <br/> ✅ Logic behind interface can be change without changes in related classes. <br/> ✅ We program to interfaces, not implementations. Code doesn't have reference to specific classes. <br/> ✅ Child class is forced to implement interface's method (Guarantee specific logic). <br/> ✅ Child class can implement many interfaces.</td>
<td>✅ Abstract class can store common logic (avoid redundancy)<br/> ✅ Child class can be forced to implement some (signed as <code>abstract</code>) methods. <br/> ✅ Child class can override some (singed as <code>virtual</code>) methods. <br/> ✅ Basic logic can be provided by abstract class inner methods. (<code>private</code>, <code>protected</code>, <code>public</code>) <br/> ✅ Easy to update common code for all child method. Just update code in abstract class.</td>
<td>✅ virtual class can be treated as a base class with base logic, which shoul be accessed by all child classes. <br/> ✅ Virutal class can be initialized direct <br/> ✅ Child class can override some (signed as <code>virtual</code> methods) <br/> ✅ Easy to update common code for all child method. Just update code in virtual class. <br/> Basic logic can be provided by abstract class inner methods. (<code>private</code>, <code>protected</code>, <code>public</code>)</td>
</tr>
<tr>
<td><strong>Cons</strong></td>
<td>❌ Hard to add or change interface's methods, because all classes that implements interface needs to be change as well. <br/> ❌ Apex class needs to implement all interface methods even if it's not relevant.</td>
<td>❌ Cannot be initialized directly. <br/> ❌ Apex class needs to implement all <code>abstract</code> methods even if it's not relevant. <br/> ❌ Child class can be only extended by one parent class.</td>
<td>❌ Cannot force child class to implement parent method (<code>abstract</code> cannot be used) <br/> ❌ Child class can be only extended by one parent class.</td>
</tr>
<tr>
<td><strong>Goal</strong></td>
<td>To create new layer of abstraction</td>
<td>To provide kind of &quot;partial&quot; class with common logic</td>
<td>To provide kind of &quot;full&quot; class with base logic</td>
</tr>
</tbody>
</table>

-   Both `virtual` and `abtract` classes allow you to extend the class (i.e. create child classes that inherit non-private methods and variables)
-   A `virtual` class can be instantiated directly, whereas an `abstract` class cannot
-   Both `virtual` and `abstract` classes can contain `virtual` methods (`virtual` methods can have a default implementation that is inherited by child classes, whereas `abstract` methods can only be signatures, and *must* be implemented in child classes)
-   Only `abstract` classes may contain `abstract` methods
-   Methods defined inside interfaces do not have access modifiers. They are always global.
-   Interface defines what an object can do whereas Astract class deines what an object is.

# [SOLID Principles](https://www.youtube.com/watch?v=yxf2spbpTSw)
## The Single Responsibility Principle
The Single Responsibility Principle states that a class should do one thing and therefore it should have only a single reason to change.

## Open-Closed Principle
The Open-Closed Principle requires that classes should be open for extension and closed to modification.

Modification means changing the code of an existing class, and extension means adding new functionality.

## Liskov Substitution Principle
The Liskov Substitution Principle states that subclasses should be substitutable for their base classes.

This means that, given that class B is a subclass of class A, we should be able to pass an object of class B to any method that expects an object of class A and the method should not give any weird output in that case.

## Interface Segregation Principle
Segregation means keeping things separated, and the Interface Segregation Principle is about separating the interfaces.

## Dependency Inversion Principle
The Dependency Inversion principle states that our classes should depend upon interfaces or abstract classes instead of concrete classes and functions.

https://www.freecodecamp.org/news/solid-principles-explained-in-plain-english/
Youtube Resource : https://www.youtube.com/watch?v=69sfWNzxTMc

# [Apex Design Patterns](https://salesforcecookcode.wordpress.com/2021/02/26/apex-design-patterns/)
General design pattern catgeory 

1. Creational Patterns:
Creational patterns focus on object creation mechanisms, providing flexibility in creating objects and isolating the process of object instantiation. Examples of creational patterns include:

Singleton Pattern
Factory Pattern
Abstract Factory Pattern
Builder Pattern
Prototype Pattern


2. Structural Patterns:
Structural patterns deal with object composition and class relationships, helping to create larger structures from individual objects. These patterns emphasize the composition of classes and objects to form more complex structures while keeping them flexible and efficient. Examples of structural patterns include:

Adapter Pattern
Decorator Pattern
Composite Pattern
Proxy Pattern
Bridge Pattern
Facade Pattern


3.Behavioral Patterns:
Behavioral patterns focus on communication and interaction between objects, specifying how objects collaborate and distribute responsibilities. These patterns are concerned with the interaction patterns between objects and the delegation of responsibilities. Examples of behavioral patterns include:

Observer Pattern
Strategy Pattern
Command Pattern
Iterator Pattern
Template Method Pattern
State Pattern

## Singleton
Restricts the instantiation of a class to one “single” instance only within a single transaction context.

Suppose you have a Salesforce application that requires global configuration settings, such as API endpoints, authentication credentials, or other application-specific parameters. You want to ensure that these configuration settings are loaded and accessible from anywhere within your application.


public class AppConfig {
    private static AppConfig instance;
    private String apiUrl;
    private String apiKey;

    private AppConfig() {
        // Load configuration settings from a data source, such as Custom Settings or Custom Metadata
        // ...
        // For simplicity, we will directly assign dummy values here
        apiUrl = 'https://api.example.com';
        apiKey = 'your-api-key';
    }

    public static AppConfig getInstance() {
        if (instance == null) {
            instance = new AppConfig();
        }
        return instance;
    }

    public String getApiUrl() {
        return apiUrl;
    }

    public String getApiKey() {
        return apiKey;
    }
}


## Strategy
lets you define a family of algorithms, put each of them into a separate class, and make their objects interchangeable.

![image](https://user-images.githubusercontent.com/34469349/155385118-69b3e245-6c12-4abc-bbcd-1d334074f5f0.png)


## Decorator

The decorator design pattern falls into the structural category, that deals with the actual structure of a class, whether is by inheritance, composition or both. The goal of this design is to modify an objects’ functionality at runtime without altering its structure.

In Salesforce context, you need to obtain or display temporary information on a LWC/Visualforce page that is not needed beyond the context of the interaction.
For example, you may have a specific requirement to show Accounts along with the sum of Amount of all related closed opportunities.
Now just for this specific requirement we will not create a new field on Account object since that would be an overkill. Instead, we will implement decorator pattern and create a new variable called opptyAmountSum which is temporary field (proxy field) in the Response class that will be calculated at run time based on the Account. Since we did not create a field on object, we did not change the structure and we also modified functionality at run time. So we successfully implemented Decorator pattern.

## Facade
hides the complexity of the system and provides simple interface (not be confused with interface class, here we mean literal interface, something to interact with).

Example - 
Suppose you have a requirement of showing Contact details on a LWC. These details include First Name, Last Name, Account Name, Sum of all oppty amounts of parent account. Now for this we will need to create some Wrapper class and we will only get/calculate these details and assign them to wrapper class's members(variables)
In this use case Wrapper is nothing but Facade for our LWC. It hid all the complexity of calculating sum or other non required fields of Contact object and only provided simple interface with required details.

## Composite
lets you compose objects into tree structures and then work with these structures as if they were individual objects.

Example - 
Let's say we need order details. Now Order contains multiple things such as Order id, Customer info, Line Items, Shipment details etc. Futher, Customer contains many things such as Id, Name, Email etc. Line Item contains Product, quantity, total price etc. We can break Product further down into Product Name, Id, price etc. So the complex Order class is COMPOSED of sub parts and again these sub parts are composed of more smaller parts until there are no sub parts.
This is called as Composite Design patter.

## Bulk State Transition
used to perform bulk actions efficiently based on change of state of one or more records.

Example - 
Write bulkified methods/code that can do a generic task and it should be very specific to particular requirement (it shuld be extensible)
Give example from this link - https://salesforcecookcode.wordpress.com/2021/02/28/bulk-state-transition/


# [Apex Enterprise Patterns](https://www.apexhours.com/apex-enterprise-patterns/)
- [Apex Enterprise Patterns — Separation of Concerns](https://andyinthecloud.com/2012/11/16/apex-enterprise-patterns-separation-of-concerns/)
![image](https://user-images.githubusercontent.com/34469349/157428587-a1bb5df9-4d0e-41a2-a642-740da04b5c3b.png)

- [Apex Enterprise Patterns — Selector Layer](https://andyinthecloud.com/2013/09/09/apex-enterprise-patterns-selector-layer/)
- [Apex Enterprise Patterns — Domain Layer](https://andyinthecloud.com/2013/04/24/apex-enterprise-patterns-domain-layer/)
- [Apex Enterprise Patterns — Service Layer](https://andyinthecloud.com/2013/02/11/apex-enterprise-patterns-service-layer/)
- [Apex Enterprise Patterns — Unit Of Work](https://andyinthecloud.com/2013/06/09/managing-your-dml-and-transactions-with-a-unit-of-work/)
- [Apex Enterprise Patterns — Unit Of Work](https://andyinthecloud.com/2014/07/17/doing-more-work-with-the-unit-of-work/)

- 
The Unit of Work pattern is used to manage the state and persistence of multiple records within a transactional boundary. It ensures that all changes to records are treated as a single unit, either all succeed or all fail, maintaining data integrity. This pattern is particularly useful when dealing with complex business processes that involve multiple records and related objects.

Let's consider a valid use-case to understand the Unit of Work pattern in Apex:

Use-case: In a Sales Management application, a sales representative wants to update the details of multiple Opportunity records and related Quote records in a single transaction. The updates should be performed atomically, ensuring that either all the updates succeed, or none of them are saved.

To implement the Unit of Work pattern, you would typically create the following components:

UnitOfWork class: This class acts as a container for managing the records and their changes within a transaction. It provides methods to add records, track changes, and commit the changes.

public class UnitOfWork {
    private List<SObject> records;

    public UnitOfWork() {
        records = new List<SObject>();
    }

    public void addRecord(SObject record) {
        records.add(record);
    }

    public void commitChanges() {
        Database.SaveResult[] results = Database.update(records, false);
        // Handle the save results and perform necessary error handling or logging
    }
}

- [Apex Enterprise Patterns — FinancialForce Apex Common Updates](https://andyinthecloud.com/2014/06/28/financialforce-apex-common-updates/)


### DESIGN PATTERNS IN CONTEXT OF APEX 

Design patterns are reusable solutions to common software design problems that have been proven to work effectively in various situations. By using design patterns, developers can save time and effort by avoiding reinventing the wheel and instead leveraging existing best practices and solutions.

In the context of Apex development, there are several design patterns that can be used to solve different problems. Here are some examples:

- Singleton Pattern: This pattern is used when we need to ensure that only one instance of a class is created and used throughout the application. This can be useful for managing shared resources or configuration data.

- Factory Pattern: This pattern is used when we want to create objects dynamically based on some inputs or conditions. The factory class encapsulates the object creation logic and returns the appropriate object based on the inputs.

- Decorator Pattern: This pattern is used to add new functionality to an existing class without modifying its source code. This is achieved by creating a decorator class that wraps the original class and adds new behavior to it.

- Strategy Pattern: This pattern is used to define a family of algorithms that can be used interchangeably. This allows us to change the algorithm used at runtime without changing the code that uses it.

- Observer Pattern: This pattern is used to define a one-to-many relationship between objects, where one object (the subject) notifies a set of other objects (the observers) when its state changes. This can be useful for implementing event-driven architectures.

### SOLID PRINCIPLES IN CONTEXT WITH APEX 
- Single Responsibility Principle (SRP): A class should have only one reason to change. In other words, a class should have only one responsibility. In the context of Apex, this means that a class should be responsible for a single task or functionality. This makes the class easier to understand and maintain.

-  Open/Closed Principle (OCP): A class should be open for extension but closed for modification. In other words, we should be able to add new functionality to a class without changing its existing code. In the context of Apex, this means that we should use interfaces and abstract classes to define the behavior of a class and then implement those interfaces or extend those abstract classes to add new functionality.

- Liskov Substitution Principle (LSP): Subtypes should be substitutable for their base types. In other words, if a class inherits from a base class, it should be able to be used in place of the base class without any issues. In the context of Apex, this means that we should follow the Salesforce.com's Apex inheritance rules and make sure that the derived class behaves like the base class.

 - Interface Segregation Principle (ISP): A client should not be forced to depend on methods it does not use. In other words, we should avoid creating interfaces that have too many methods that are not used by all implementing classes. In the context of Apex, this means that we should create interfaces that are focused on a specific functionality and are used only by the classes that need them.

- Dependency Inversion Principle (DIP): High-level modules should not depend on low-level modules. Both should depend on abstractions. In other words, we should use abstractions (such as interfaces and abstract classes) to define the behavior of a class and then inject the implementation of those abstractions into the class. In the context of Apex, this means that we should use dependency injection (DI) to decouple the dependencies between classes and make them easier to test.

By following these principles, we can write Apex code that is easy to understand, maintain, and extend over time.


Constructor : 

In Apex, a constructor is a special method that is used to initialize the state of an object when it is created. Constructors are essential for creating and initializing objects with specific values and configurations. They allow you to set initial values for object properties and perform any necessary setup or validation before the object is used.
public class Car {
    public String make { get; private set; }
    public String model { get; private set; }
    public Integer year { get; private set; }

    public Car(String make, String model, Integer year) {
        // Perform validation on input parameters
        if (make != null && model != null && year != null) {
            this.make = make;
            this.model = model;
            this.year = year;
        } else {
            throw new IllegalArgumentException('Invalid car details');
        }
    }
}
Car myCar = new Car('Honda', 'Civic', 2021);


By using the constructor, you guarantee that every Car object is created with valid initial values. It helps in preventing inconsistent or incorrect states of objects and enforces the necessary validation rules at the time of object creation.

Constructors are also useful for performing other setup tasks, such as establishing database connections, initializing collections, or loading initial data, depending on the specific requirements of your application.


