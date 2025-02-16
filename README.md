# Salesforce Developer Interview Preparation Guide

### FA Technical Qs

1. Write a batch class
2. Write a trigger to not allow multiple accounts insertion with the same Name (Answer - We can use adderror() method)
3. Write a trigger on Account to update all the related contacts email with the associated account's email
4. Contact and Account have lookup relationship but when we delete an account all the associated contacts are deleted. Why? (Answer - Contacts are deleted because their lookup relationship with the Account is a "cascade delete" relationship. Cascade deletes don't run triggers as well.)
5. Can we call a batch from another batch and if yes then how? How can we write test classes for such batches?
6. Can we do callouts from a batch? If yes, then what is the prerequisite for that?
7. How to write a test class for a batch? How it is different from other apex test classes? How can we run a batch in test class?
8. What are the options available to run a batch?
9. What is a stateful batch?
10. Apex best practices
11. Order of execution in an apex transaction? What are system validations?
12. Why we should bulkify our code?
13. What is the difference between insert DML statement and Database.insert
14. If we have 2 savepoints and we rollback first savepoint, what happens to the second savepoint?
15. What is custom setting and custom metadata? How they are different? Types of custom settings and the difference between them.
16. What is the difference between REST and SOAP API?
17. What is the difference between the POST and PUT method in REST? Can we perform the update using the POST method and if yes then how it is different from PUT?
18. What are governor limits?
19. How lightning is different from classic? How lightning components are different from VF pages?
20. What are the events in lighting and what's the difference between them?
21. Can we directly convert VF pages to lighting components?
22. What is lighting out? What is @AuraEnabled annotation?
23. Can we use Angular is the lighting? If yes, what is the prerequisite for that?
24. Can we modify the records in the after events?
25. What can be after deleting of a record? Can we modify it?
26. How do we ensure object and field-level security in lighting? (Answer - using lighting data service)
27. Security model of the salesforce.
28. How do you handle NullPointerException in apex?

https://www.sfdc99.com/2014/12/18/common-interview-questions-for-salesforce-developers/
