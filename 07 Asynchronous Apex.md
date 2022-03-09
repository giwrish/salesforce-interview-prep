# [Asynchronous Apex](https://developer.salesforce.com/docs/atlas.en-us.apexcode.meta/apexcode/apex_async_overview.htm)

### [Apex Hours](https://www.apexhours.com/asynchronous-apex/)

### Which asynchronous can be called from where
![image](https://user-images.githubusercontent.com/34469349/157425189-abc2fc02-98a7-4ea5-a1ae-c5e7e361b96d.png)

Simply remeber this -
- A Batch cannot be called from Future and vice versa
- Future can't be called from a Future

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
