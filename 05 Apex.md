# Apex 

### [Collections](https://developer.salesforce.com/blogs/2021/10/mastering-apex-collections)
-   A [List](https://developer.salesforce.com/docs/atlas.en-us.apexref.meta/apexref/apex_methods_system_list.htm) holds an ordered collection of non-unique elements
-   A [Set](https://developer.salesforce.com/docs/atlas.en-us.apexref.meta/apexref/apex_methods_system_set.htm) holds an unordered collection of unique elements
-   A [Map](https://developer.salesforce.com/docs/atlas.en-us.apexref.meta/apexref/apex_methods_system_map.htm) holds a dictionary of key values in which keys are unique but values are not


### [`with sharing`, `without sharing`, and `inherited sharing`](https://developer.salesforce.com/docs/atlas.en-us.apexcode.meta/apexcode/apex_classes_keywords_sharing.htm)

When inherited sharing is used, it means that it will inherit the sharing settings of the caller class.

-   If a class with `without sharing` is calling the method of class with `inherited sharing`, then it will run in `without sharing` mode.
-   If a class with `with sharing` is calling the method of class with `inherited sharing`, then it will run in `with sharing` mode.
-   If a class with `omitted sharing` (i.e. no sharing is mentioned) is calling the method of class with `inherited sharing`, then it will run in **`without sharing`** mode as the default sharing mode of the `omitted sharing` is to run in `without sharing` mode (This is because the calling class is established as a `without sharing` context). A class declared as `inherited sharing` runs as `without sharing` only when **explicitly** called from an **already established** `without sharing` context.
-   If a class with `with sharing` is calling a method of class with `omitted sharing` which in turn calls a method of class with `inherited sharing`, then it will run in `with sharing` mode, as the calling class is in `with sharing` mode and omitted class is established as `with sharing` context.
-   If a class with `without sharing` is calling a method of class with `omitted sharing` which in turn calls a method of class with `inherited sharing`, then it will run in `without sharing` mode, as the calling class is in `without sharing` mode and the omitted class is established as `without sharing` context.
-   If the class is used as the entry point to an Apex transaction, an `omitted sharing` declaration runs as `without sharing`.
-   If the class is used as the entry point to an Apex transaction, `inherited sharing` ensures that the default is to run as `with sharing`.

1.  [Apex Best Practices](https://developer.salesforce.com/blogs/developer-relations/2015/01/apex-best-practices-15-apex-commandments.html) - This is a must read. you should atleast know 5 apex best practices.

# [Asynchronous Apex](https://developer.salesforce.com/docs/atlas.en-us.apexcode.meta/apexcode/apex_async_overview.htm)
  #### More Resources
  1. [Apex Hours](https://www.apexhours.com/asynchronous-apex/)

### Questions
1. Batch Apex
   - Can we call another batch class from a batch class? - Yes, it is called batch chaining
   - Can we call future method from a batch? - No we cannot call a future method from a batch
   - Can we make a callout from a batch apex? How?
      implement Database.AllowsCallouts
   - What is the number of maximum batch Apex jobs that can be queued or can be active concurrently?
      5 jobs
   - What is the default batch size?
      200
   - What's the maximum batch size that you can set?
      (2000 in Database.executeBatch() method. If set to more than 2000, the batch size becomes 200 by default.)
   - What are the governor limits for a batch apex?
   - How to use AggregateResult in batch?
   - When to use Interable interface in batch apex?

1.  Future Apex

    - Can we make a callout from a future method? How? @future(callout=true)
    - Can we call future method from another future method? No.
    - Can we call future method from batch apex? No.
    - Can we call future method from queueable apex? Yes, only 1 is allowed.
    - How many future methods are allowed in single transaction? 50.
    - What type of parameters does future method accepts? Premitives only. no sObjects.Why?

1.  Queueable Apex

    - Maximum number of queued apex jobs? 50.

1.  Scheduled Apex

    - What is a cron expression?
    - What is the maximum number of Apex classes scheduled concurrently? 100


### When should we use which asynchronous apex
![image](https://user-images.githubusercontent.com/34469349/152400033-a64f6099-4c49-48bf-92e0-b9b4cf57b732.png)


### Important Interfaces (Frequently Used)

1. Database.Batchable - To impletement batch class
2. Database.Stateful - To maintain the state of variable across multiple batches
3. Database.AllowsCallouts - To make callouts from batch apex
4. Database.RaisesPlatformEvents - To publish platform events from batch
5. Queueable - To implement queueable class
6. Schedulable - To implement schedular class 
7. HttpCalloutMock - To mock http request
8. Callable - Enables developers to use a common interface to build loosely coupled integrations between Apex classes or triggers, even for code in separate packages.
9. Custom Interfaces

- [Unable to lock row - Record currently unavailable errors](https://help.salesforce.com/articleView?id=000338933&type=1&mode=1)

- [Maximum CPU time exceeded](https://help.salesforce.com/articleView?id=000339361&type=1&mode=1)

  - Use Map Based Queries
  - Perform Aynchronous Operations
  - Aggregate SOQL usage
  - Only take necessary data and run a loop

- [You have uncomitted work pending](https://help.salesforce.com/articleView?id=000328873&type=1&mode=1)
- Mixed DML Statement
- [Mixed DML Operations in Test Methods](https://developer.salesforce.com/docs/atlas.en-us.apexcode.meta/apexcode/apex_dml_non_mix_sobjects_test_methods.htm)
- [sObjects That Cannot Be Used Together in DML Operations](https://developer.salesforce.com/docs/atlas.en-us.apexcode.meta/apexcode/apex_dml_non_mix_sobjects.htm)

1. Exception Handling - https://developer.salesforce.com/blogs/2017/09/error-handling-best-practices-lightning-apex

### [Annotations](https://developer.salesforce.com/docs/atlas.en-us.apexcode.meta/apexcode/apex_classes_annotation.htm)

    @AuraEnabled
    @Future
    @InvocableMethod
    @InvocableVariable
    @TestSetup
    @TestVisible
    @IsTest
    @RemoteAction

### Class Reference (Frequently Used)

1.  Schema Class

1.  Database Class

    - What is the use case of savepoints?
    - What is the use case of SaveResults, UpdateResults, DeleteResults etc.

1.  System Class

    - When should you use runAs()? - Know about isTestRunning, isFuture, isBatch, isQueueable?

1.  Limit Class

1.  Test class

    - startTest() - stopTest() - @isTest - seeAllData - Setup Objects
