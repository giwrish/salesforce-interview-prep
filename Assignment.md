# Contanct Management

## PART 1

When you save a new Account with name, send the account name to the external application that will return the full details of its related contact. Once you get the details, create a new related contact of that account and save them. The details that need to be saved in contact are first name, last name, email, full mailing address (street, city, state, country and postal code) and phone number.
***
    
Optional Tasks - 
- Save the Birthday of the contact
- Save the phone number without any hyphens (-), if you are really feeling up for a challange then instead of just hyphen, make it these special characters proof `!@#$%^&*()-`
- If the age of the contact is more than 60 years, then set the account rating to Cold, if it less than 40 years, then Hot otherwise Warm.
    
## PART 2

When you open an account record, the related contact details should be displayed on the bottom of the page. There could be more than 1 related contacts. If the phone of the account is updated, the phone of all realted contact should also be automatically updated and user do not have to refresh the page to see  the updated details on contact.



## PART 3

Show the contacts on LWC like amazon products after getting them from external application.


## API Details 

* Enpoint - https://randomuser.me/api 

* Query Param - companyName

* Authentication - Api Key (as part of the header) `eebdfcb6-35d4-4be0-a240-11193a523c1e`
