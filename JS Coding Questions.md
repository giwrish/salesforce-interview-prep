# Javascript Coding Questions

## Array 
1. Merge 2 arrays `[23,535,23,1] and [9,7,6,5,8,3,2]`
2. Find intersection (common) of 2 arrays `[1,3,4,5] and [1,2,5,6,7]`
3. Find delta of 2 arrays (different elements) `[1,3,4,5] and [1,2,5,6,7]`
4. Get all elements from array A that are not in array B `[1,3,4,5] and [1,2,5,6,7]`
5. Get all the users with age less than 50 - https://github.com/shindegirish/salesforce-interview-prep/blob/main/userdata.json
6. Get a usser with email marie.christensen@example.com
7. Return true if all users are less than 80 years old.
8. Get index of a user whoe email is enrique.stanley@example.com
9. Create a new array with all sub-array elements concatenated into it `const arr1 = [0, 1, 2, [3, 4]]`
10. In given array `['ant', 'bison', 'camel', 'duck', 'elephant']`, replace `camel` with `dog`.
11. In users database, check if at least one user is from Denmark.
12. From given array `['ant', 'bison', 'camel', 'duck', 'elephant']`, get a new array with elements from 2nd index to 4th.

## Objects
const account = { name : "N26", address : "Berlin", type : "Bank", isInternational : true };
1. output => ['name', 'address', 'type', 'isInternational']
2. output => "N26 Berlin Bank true"

For input - https://github.com/shindegirish/salesforce-interview-prep/blob/main/userdata.json

3. output => get only id, gender and email of users

4. output => for all records, get only id with location in form of street number, street name, city, state, country adn post code. For example, {  "id": "16b10cac-f376-4a8c-9367-a67d376441ec", location : "5305, Circuito San Luis Potosí, Plan de Ayala (Santa Rosa), Ciudad de Mexico, Mexico, 79818"}

5. check the depth of following object ( output should be 3 since there are 3 nested children)
```
const test = [{
  id: "1234",
  name: "test 1",
  child: {
      id: "6434",
      name: "test 2",
      child: {
          id: "987",
          name: "test 3",
          child: {
              id: "435",
              name: "test 4",
              child: null
          }
      }
  }
},
{
  id: "1234",
  name: "rest 1",
  child: {
      id: "6434",
      name: "rest 2",
      child: null
  }
},
{
  id: "1234",
  name: "zara 1",
  child: {
      id: "6434",
      name: "zara 2",
      child: {
          id: "6434",
          name: "zara 3",
          child: null
      }
  }
}
]
```
6. output => "test 1 test 2 test 3 test 4 rest 1 rest 2 zara 1 zara 2 zara 3"
