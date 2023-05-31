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

### [OAuth 2.0 User-Agent Flow for Desktop or Mobile App Integration](https://help.salesforce.com/articleView?id=remoteaccess_oauth_user_agent_flow.htm&type=5&language=en_US)

With the OAuth 2.0 user-agent flow, users authorize a desktop or mobile app to access data using an external or embedded browser. Client apps running in a browser using a scripting language such as JavaScript can also use this flow. This flow uses the OAuth 2.0 implicit grant type.

![image](https://user-images.githubusercontent.com/34469349/157460005-86fd0e9e-6cb8-4030-9ddb-05d8690beaa5.png)

### [OAuth 2.0 Web Server Flow for Web App Integration](https://help.salesforce.com/articleView?id=remoteaccess_oauth_web_server_flow.htm&type=5)

To integrate an external web app with the Salesforce API, use the OAuth 2.0 web server flow, which implements the OAuth 2.0 authorization code grant type. With this flow, the server hosting the web app must be able to protect the connected app’s identity, defined by the client ID and client secret.

![image](https://user-images.githubusercontent.com/34469349/157460323-4c2175aa-e778-4a37-a8ed-85eef1ae6692.png)


### [OAuth 2.0 JWT Bearer Flow for Server-to-Server Integration](https://help.salesforce.com/articleView?id=remoteaccess_oauth_jwt_flow.htm&type=5)

Sometimes you want to authorize servers to access data without interactively logging in each time the servers exchange information. For these cases, you can use the OAuth 2.0 JSON Web Token (JWT) bearer flow. 

![output-onlinepngtools](https://user-images.githubusercontent.com/34469349/157462122-423f14c0-5eb9-4a0c-a4bc-06ca65c4696c.png)

### [OAuth 2.0 Username-Password Flow for Special Scenarios](https://help.salesforce.com/articleView?id=remoteaccess_oauth_username_password_flow.htm&type=5)

You can use the username-password flow to authorize a client—via a connected app—that already has the user’s credentials. However, we recommend avoiding this flow because it passes credentials back and forth. Use it only if there’s a high degree of trust between the resource owner and the client, the client is a first-party app, Salesforce is hosting the data, and other grant types aren’t available. In these cases, set user permissions to minimize access and protect stored credentials from unauthorized access.

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

Best Practices : 
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


# OUTDATED CONTENT 

1. Workflow outbound messages - outbound
1. Apex callouts (outbound) and Web Services (inbound)
1. Salesforce Connect - both inbound and outbound depending on use case
    Salesforce Connect provides seamless integration of data across system boundaries by letting your users view, search, and modify data that’s stored outside your Salesforce org. For example, perhaps you have data that’s stored on premises in an enterprise resource planning (ERP) system. Instead of copying the data into your org, you can use external objects to access the data in real time via web service callouts.
    Use Salesforce Connect when:
    -   You have a large amount of data that you don’t want to copy into your Salesforce org.
    -   You need small amounts of data at any one time.
    -   You want real-time access to the latest data.
