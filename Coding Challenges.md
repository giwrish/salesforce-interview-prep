# Apex

1.  Create an Apex controller `AccountHierarchyController` with a method `getAccountHierarchy` that retrieves the account hierarchy data from Salesforce. The Apex controller should return a list of account records, including their parent-child relationships. The data should incude the account name, rating and created data.
       ```json
         [
            {
               "Id":"001xxxxxxxx",
               "Name":"Salesforce.com",
               "Rating":"Hot",
               "CreatedDate":"09-05-2023",
               "ChildAccounts":[
                  {
                     "Id":"001xxxxxxxx",
                     "Name":"Level 1 Child",
                     "Rating":"Warm",
                     "CreatedDate":"09-05-2023",
                     "ChildAccounts":[]
                  }
               ]
            },
            {
               "Id":"001xxxxxxxx",
               "Name":"Apple Inc.",
               "Rating":"Cold",
               "CreatedDate":"09-05-2023",
               "ChildAccounts":[
                  {
                     "Id":"001xxxxxxxx",
                     "Name":"MacBook Pro",
                     "Rating":"Warm",
                     "CreatedDate":"09-05-2023",
                     "ChildAccounts":[
                        {
                           "Id":"001xxxxxxxx",
                           "Name":"MacBook Pro 14 Inch",
                           "Rating":"Warm",
                           "CreatedDate":"09-05-2023",
                           "ChildAccounts":[

                           ]
                        },
                        {
                           "Id":"001xxxxxxxx",
                           "Name":"MacBook Pro 16 Inch",
                           "Rating":"Warm",
                           "CreatedDate":"09-05-2023",
                           "ChildAccounts":[

                           ]
                        }
                     ]
                  }
               ]
            },
            {
               "Id":"001xxxxxxxx",
               "Name":"Slack",
               "Rating":"Hot",
               "CreatedDate":"09-05-2023",
               "ChildAccounts":[

               ]
            }
         ]
      ```
