# Process Automation

### Workflows

- Workflow Actions
- Difference between everytime created and edited and subsequently meet the criteria
- Time-based workflows and considerations
- Limitations - Cannot be executed before record is modified.

#### created - Invoked only when record is created
Evaluate the rule criteria each time a record is created. If the rule criteria is met, run the rule. Ignore all updates to existing records.
With this option, the rule never runs more than once per record.

#### created, and every time it’s edited - Invoked everytime record is created and updated
Evaluate the rule criteria each time a record is created or updated. If the rule criteria is met, run the rule.
With this option, the rule repeatedly runs every time a record is edited, as long as the record meets the rule criteria.
Note: We cannot add time-dependent actions to the rule if you select this option.

#### created, and any time it’s edited to subsequently meet criteria - Invoked when ISCHANGED(fieldName) or prior value != current value
Evaluate the rule criteria each time a record is created or updated.
For a new record, run the rule if the rule criteria is met.
For an updated record, run the rule only if the record is changed from not meeting the rule criteria to meeting the rule criteria.
With this option, the rule can run multiple times per record, but it won’t run when the record edits are unrelated to the rule criteria.

### Process Builders

- Process Builder Actions
- Limitations

### Flows
**Flow vs Trigger**
- https://www.theblueflamelabs.com/record-triggered-flow-vs-apex-trigger/
- https://www.linkedin.com/pulse/record-trigger-flow-vs-apex-yusuf-aydemir/
### Approval Process
**Flow Vs Worflow vs Process Builder**
- https://www.sfdcpoint.com/salesforce/difference-between-workflow-process-builder-and-flow/#:~:text=Flow%20is%20more%20powerful%20than,delete%20records%20for%20multiple%20objects.


### When to choose Apex over Flows

- Flows are difficult to debug compared to apex. The in-built debug feature is not very user friendly.
- Cannot add custom error message in case of validations like triggers for record trigged flows.
- Flows do not support Maps so doing operations on large data set is not very efficient.
- Doing complex and mathematical logic calculation in flows is comparatively difficult and hard to maintain.
