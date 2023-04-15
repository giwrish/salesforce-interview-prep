# Apex Triggers
1. [Context Variables](https://developer.salesforce.com/docs/atlas.en-us.apexcode.meta/apexcode/apex_triggers_context_variables.htm)
1. [Context Variable Considerations](https://developer.salesforce.com/docs/atlas.en-us.apexcode.meta/apexcode/apex_triggers_context_variables_considerations.htm)

![image](https://user-images.githubusercontent.com/34469349/153751105-a5789a44-1619-4232-baeb-d9189f764f91.png)



### When should you use before and after triggers?

The rule of thumb is we should use before triggers if we need to add any custom validations on the record or update the field of the same record.
Use the after trigger for all other scenarios.

Why should we use after trigger for all other scenarios? For example, creating a contact after an account is created. You might ask.
The simple reason is there could be some calculations/updates happening on the same record by after trigger/flows/processes etc. And we do not want to impact the result of those actions because of our code in before trigger.

### [Triggers and Order of Execution](https://developer.salesforce.com/docs/atlas.en-us.apexcode.meta/apexcode/apex_triggers_order_of_execution.htm)

  1. Loads existing record in trigger.old or initilizes for upsert
  2. Loads trigger.new with new values
  3. System validations
  4. Flows configured to run before record is saved
  5. Before triggers
  6. System Validations & Custom Validations
  7. Duplicate Rules
  8. Saves the record in database
  9. After triggers
  10. Assignment rule (Case & Leads only)
  11. Auto response rules (Case & Leads only)
  12. Workflow rules
  13. If worlfow updates the field then goes thru the save process only one time
  14. Escalation Rules (Case only)
  15. Flow automations but not in specific order - Processes, Flows launched by processes and flows launched by workflow rules
  16. Flows configured to run after record is saved
  17. Entitlement rules (Case only)
  18. Parent roll up summary calculation
  19. Grand parent roll up summary calculation
  20. Criteria based sharing rule
  21. Commits all dml operations
  22. Post commit logic - send email, enqueue async apex (queueable and future)
  
![image](https://user-images.githubusercontent.com/34469349/153751113-921ed046-43f6-4782-99ac-268a7e2eb3c9.png)

# Platform Events and Triggers

### Custom Platform Events
### Data Capture Change Events
### Trigger Best Prac : https://developer.salesforce.com/forums/?id=906F0000000DBl8IAG
