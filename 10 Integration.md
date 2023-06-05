# Integration

## Types
- Inbound
- Outbound

## Communication Types
- Synchronous
- Asynchronous

### Ways to make OUTBOUND call from Salesforce
   - Workflows, Flows, Process Builders
   - Apex Callout
   - LWC Callout (fetch API)

### Ways to make INBOUND call to Salesforce
   - Salesforce REST APIs
   - Apex REST Web Service
   - Apex SOAP Web Service

## Authentication for Inbound Calls
- Basic Auth (Username-Password Authentication):
    - No Connected App is required for this type of authentication.
    - Basic authentication is a simple authentication scheme used in HTTP protocol. It allows a client to authenticate itself with a server by including a username and password in the HTTP request headers. The server verifies the provided credentials and grants or denies access to the requested resource based on the authentication result.
    - When accessing a protected resource, the client includes the Authorization header in the HTTP request.
    - The value of the Authorization header consists of the word "Basic" followed by a base64-encoded string of the username and password joined by a colon (username:password).
   
- OAuth 2.0 Authentication (Industry Standard):
    - You will need to create a Connected App in Salesforce.
    - High Level Flow Diagram
 
        ![image](https://github.com/shindegirish/salesforce-interview-prep/assets/34469349/69d8f5f2-cd63-4f6d-887b-80c35af6e719)
    
    ### Type of OAuth Flows for Server-to-Server integration
    - [Username-Password](https://help.salesforce.com/s/articleView?id=sf.remoteaccess_oauth_username_password_flow.htm&type=5)
         - Create user in Salesforce
         - Share user credentials with api consumer along with client id and client secret
         - Choose the grant_type=password   
    - [Client Credentials](https://help.salesforce.com/s/articleView?id=sf.remoteaccess_oauth_client_credentials_flow.htm&type=5)
        - Create API User with API Only profile and select Run As this user in Connected App.
        - Only share client id and client sercret.
        - grant_type=client_credentials
    - JWT Bearer Token
        - This is very complicated to implement and hard to manage.
    
    
- [JWT Based Access Token - Beta](https://help.salesforce.com/s/articleView?id=sf.connected_app_enable_jwt.htm&type=5)
- SAML-based Authentication 

    
## HTTP REST
### Verbs (Methods)
| Verb   | Role                 | Body | Send Params In |
| ------ | -------------------- | ----- | ------------ |
| GET    | Retrieve resource(s) | No    | URL          |
| POST   | Add resource(s)      | Yes   | Body         |
| PUT    | Modify resource(s)   | Yes   | Body         |
| DELETE | Delete resource(s)   | Mostly No    | URL          |
   
| PUT                                                                        | PATCH                                                                                  |
| -------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| Used to completely replace a resource                                      | Used to apply partial updates to a resource                                            |
| Replaces the entire representation of a resource                           | Sends only the changes or deltas to be applied                                         |
| Requires sending the complete representation of the resource               | Allows for more granular updates on specific fields or properties                      |
| If the resource doesn't exist, it may create a new resource                | If the resource doesn't exist, it typically won't create a new resource                |
| Idempotent - Multiple identical requests result in the same resource state | Not required to be idempotent - Multiple identical requests may have different effects |
| Typically used with the entire payload of the updated resource             | Typically used with a subset of changes to update specific parts of the resource       |
    
Remember that this table provides a general overview of the differences between PUT and PATCH, but the specific implementation and behavior may vary based on the API design and requirements. It's essential to consider the semantics and intended behavior of your API when choosing between PUT and PATCH.

## Query Params and Id Params 

<img width="1166" alt="image" src="https://github.com/shindegirish/salesforce-interview-prep/assets/34469349/cec71494-eb68-4b95-9261-4d8f70dd6c12">

    
## Named Credentials
Benefit of using Named credentials is we do not have to explicitly specify remote site settings and also they can store the password safely. It takes care of the authentication as well.

state param in oAuth is used to secure the request. If the state param is sent in the request and same state param is responded back. If the param is tampered with, then the request is considered compromised.

### [INTEGRATION API 2023 GUIDE](https://magicfuse.co/blog/ultimate-guide-to-salesforce-apis/)
### [Handling Errors in Platform Events](https://www.apexhours.com/exception-handling-using-platform-events/)
### [Integration Design Patterns](https://developer.salesforce.com/docs/atlas.en-us.integration_patterns_and_practices.meta/integration_patterns_and_practices/integ_pat_intro_overview.htm)


## REST vs SOAP
| REST (Representational State Transfer)                                          | SOAP (Simple Object Access Protocol)                              |
| ------------------------------------------------------------------------------- | ----------------------------------------------------------------- |
| Architectural style                                                             | Communication protocol                                            |
| Uses HTTP methods (GET, POST, PUT, DELETE) to perform operations on resources   | Relies on XML-based messaging format                              |
| Lightweight and scalable                                                        | More complex and feature-rich                                     |
| Supports various data formats (JSON, XML, etc.)                                 | Primarily uses XML for data encoding                              |
| Uses standard HTTP protocols for communication                                  | Can use various protocols (HTTP, SMTP, MQ, etc.)                  |
| Flexible and easily consumed by different clients                               | Typically consumed by more heavyweight clients                    |
| Fewer standards and specifications                                              | Comprehensive set of standards (WSDL, WS-Security)                |
| Suitable for web APIs, browser-to-server communication, and mobile applications | Used in enterprise-level applications requiring advanced features |
| Simple to implement and understand                                              | Can be more complex to implement and require additional tooling   |

JWT

https://medium.com/@tou_sfdx/salesforce-oauth-jwt-bearer-flow-cc70bfc626c2
https://jwt.io/
https://help.salesforce.com/s/articleView?id=000335524&type=1

# [OAuth Flows](https://www.linkedin.com/pulse/salesforce-oauth-which-flow-should-i-use-jannis-bott-/)

![output-onlinepngtools](https://user-images.githubusercontent.com/34469349/157464533-057384b1-1012-4f1a-89e8-67c53a365d6b.png)
INTERVIEW Q : https://www.sfdcamplified.com/in-depth-scenario-based-interview-questions-on-salesforce-integration/

Username Password OAuth - Flow 
https://medium.com/@tou_sfdx/salesforce-rest-api-tutorial-3bcd39e493f6

INTEGRATION PATTERNS : 
https://trailhead.salesforce.com/content/learn/modules/app-integration-patterns?trail_id=explore-integration-patterns-and-practices&trailmix_creator_id=strailhead&trailmix_slug=architect-integration-architecture

Follow the series for more Integration stuff : https://www.youtube.com/watch?v=JreEjNhEd0c
Integration architect series : https://www.youtube.com/playlist?list=PLPPMyrnDS6hs5yTjVevoeJH0UFkNvmjYA

FLow Integration : https://salesforcetime.com/2023/01/05/using-flow-to-make-an-http-callout-without-code/

BULK API WORKING : https://developer.salesforce.com/docs/atlas.en-us.api_asynch.meta/api_asynch/asynch_api_code_curl_walkthrough.htm

  ***************************************** REST API BEST PRACTICES ******************************************************************************
Use Asynchronous Callouts: Perform callouts asynchronously using Apex's built-in future or Queueable interface. This prevents long-running operations from impacting the user experience and allows for better scalability.

Implement Error Handling: Handle any potential errors or exceptions that may occur during the callout process. Make sure to handle HTTP status codes appropriately and provide meaningful error messages to users or log them for troubleshooting purposes.

Implement Retry and Backoff Mechanisms: In case of transient errors, implement retry and backoff logic to ensure the callout is retried with a delay before attempting again. Exponential backoff is commonly used, gradually increasing the wait time between retries.

Leverage Bulk API and Bulk Patterns: If you need to perform bulk data operations, consider using Salesforce Bulk API for higher throughput. Implement bulk patterns such as batching or bulkifying your requests to optimize performance.

Utilize Connection Pooling: Establishing and tearing down connections for each callout can be expensive. Use connection pooling techniques to reuse connections across multiple callouts, reducing overhead and improving performance.

Implement Callout Timeouts: Set appropriate timeout values for your callouts to prevent them from running indefinitely. Use the setTimeout method to set a timeout value in milliseconds, ensuring your callout doesn't exceed the desired time limit.

Secure Sensitive Data: Ensure you handle sensitive data securely when making callouts. Avoid hard-coding credentials or authentication tokens in your code. Instead, use Salesforce's Named Credentials feature or a custom settings object to store and manage authentication details securely.

Consider Bulkification and Throttling: When integrating with external systems, be mindful of API limits and bulkification considerations. Design your solution to work efficiently within those limits and consider implementing throttling mechanisms to prevent hitting API limits.

Implement Proper Testing: Write unit tests to validate your callout code and ensure appropriate coverage. Utilize mock responses to simulate callouts during testing, allowing you to control the data and responses returned.

Monitor and Log Callout Activity: Implement logging mechanisms to capture callout activity, including request and response details, errors, and performance metrics. This information can be invaluable for troubleshooting and optimizing your integration.


*********************************************** WEBSERVICE BEST PRACTICES *************************************************************************
When it comes to writing an Apex web service in Salesforce, there are several best practices you can follow to ensure efficient and maintainable code. Here are some key recommendations:

Use RESTful architecture: Design your web service using the principles of Representational State Transfer (REST). Utilize HTTP methods (GET, POST, PUT, DELETE) to perform operations on resources and follow RESTful URL patterns.

Authentication and Authorization: Implement proper authentication and authorization mechanisms to secure your web service. You can use Salesforce's built-in authentication mechanisms like OAuth, JWT, or session-based authentication.

Input Validation: Validate all incoming data to ensure it adheres to the expected format and meets any necessary constraints. This helps prevent potential security vulnerabilities, data corruption, and errors in your web service.

Use Bulkification: When dealing with large data sets, utilize Apex's bulkification techniques to optimize performance. Avoid writing queries or DML operations within loops as it can lead to governor limit exceptions.

Error Handling: Implement robust error handling mechanisms to provide meaningful error messages and handle exceptions gracefully. Use appropriate HTTP status codes to indicate the outcome of the request (e.g., 200 for success, 400 for bad request, 500 for internal server error).

Governor Limits: Be mindful of Salesforce's governor limits while designing your web service. Ensure that your code remains within the acceptable limits, such as SOQL queries, DML operations, and CPU time. Monitor and log usage to identify and address any potential issues.

Use Proper Logging: Incorporate logging statements in your code to capture relevant information for debugging and monitoring purposes. Utilize Salesforce's logging capabilities, such as Debug Logs or Platform Events, to track and analyze the behavior of your web service.

Unit Testing: Write comprehensive unit tests to validate the functionality of your web service. Aim for high test coverage to ensure that your code behaves as expected and to catch any regressions during future development cycles.

Documentation: Provide clear and concise documentation for your web service, including the API endpoints, request/response structures, authentication requirements, and any additional guidelines for consuming the service. This helps other developers understand and integrate with your web service effectively.

Performance Optimization: Identify potential performance bottlenecks and optimize your code accordingly. Use query and database performance tuning techniques, such as selective filtering and indexing, to enhance the efficiency of your web service.
***************************************************************************************************************<img width="677" alt="Screenshot 2023-06-05 at 10 17 28" src="https://github.com/shindegirish/salesforce-interview-prep/assets/32008754/83501395-1c4b-42aa-b845-072f20be175a">
*************************************
# OUTDATED CONTENT 

1. Workflow outbound messages - outbound
1. Apex callouts (outbound) and Web Services (inbound)
1. Salesforce Connect - both inbound and outbound depending on use case
    Salesforce Connect provides seamless integration of data across system boundaries by letting your users view, search, and modify data that’s stored outside your Salesforce org. For example, perhaps you have data that’s stored on premises in an enterprise resource planning (ERP) system. Instead of copying the data into your org, you can use external objects to access the data in real time via web service callouts.
    Use Salesforce Connect when:
    -   You have a large amount of data that you don’t want to copy into your Salesforce org.
    -   You need small amounts of data at any one time.
    -   You want real-time access to the latest data.
