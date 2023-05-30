# Integration

REST vs SOAP

<table class="alt">
<tr><th>No.</th><th>SOAP</th><th>REST</th></tr>
<tr><td>1)</td><td>SOAP is a <strong>protocol</strong>.</td><td>REST is an <strong>architectural style</strong>.</td></tr>
<tr><td>2)</td><td>SOAP stands for <strong>Simple Object Access Protocol</strong>.</td><td>REST stands for <strong>REpresentational State Transfer</strong>.</td></tr>
<tr><td>3)</td><td>SOAP <strong>can't use REST</strong> because it is a protocol.</td><td>REST <strong>can use SOAP</strong> web services because it is a concept and can use any protocol like HTTP, SOAP.</td></tr>
<tr><td>4)</td><td>SOAP <strong>uses services interfaces to expose the business logic</strong>.</td><td>REST <strong>uses URI to expose business logic</strong>.</td></tr>
<tr><td>5)</td><td>SOAP <strong>defines standards </strong> to be strictly followed. </td><td>REST does not define too much standards like SOAP.</td></tr>
<tr><td>6)</td><td>SOAP <strong>requires more bandwidth</strong> and resource than REST.</td><td>REST <strong>requires less bandwidth</strong> and resource than SOAP.</td></tr>
<tr><td>7)</td><td>SOAP <strong>defines its own security</strong>.</td><td>RESTful web services <strong>inherits security measures</strong> from the underlying transport.</td></tr>
<tr><td>8)</td><td>SOAP <strong>permits XML</strong> data format only.</td><td>REST <strong>permits different</strong> data format such as Plain text, HTML, XML, JSON etc.</td></tr>
<tr><td>9)</td><td>SOAP is <strong>less preferred</strong> than REST.</td><td>REST <strong>more preferred</strong> than SOAP.</td></tr>
</table>

What are types of Integration?
    - Inbound
    - Outbound
    
Communication types - 
    - Synchronous
    - Asynchronous

What type of Integrations you should know?



1. Workflow outbound messages - outbound
1. Apex callouts (outbound) and Web Services (inbound)
1. Salesforce Connect - both inbound and outbound depending on use case
    Salesforce Connect provides seamless integration of data across system boundaries by letting your users view, search, and modify data that’s stored outside your Salesforce org. For example, perhaps you have data that’s stored on premises in an enterprise resource planning (ERP) system. Instead of copying the data into your org, you can use external objects to access the data in real time via web service callouts.
    Use Salesforce Connect when:
    -   You have a large amount of data that you don’t want to copy into your Salesforce org.
    -   You need small amounts of data at any one time.
    -   You want real-time access to the latest data.

Authentication and Authorization - 
1. OAuth flows
    - Web Server flow
    - JWT Server to Servier integration
    
REST Methods - 
1. PUT vs PATCH
    - Short difference - PUT does an UPSERT with complete payload.
      Meaning if the request payload is -
      Request endpoint - /person/1
      {
      name : "John Doe",
      age : 30
      }

    the PUT operation will check if person with id 1 exists, if yes then it will update the name and age.
    if notm then it will create new person at id 1.

    However,
    PATCH modifies existing data with given payload.
    Meaning, Request endpoint - /person/1
    payload-
    {
    name: "Jane Doe"
    }
    The path will only update the name and not whole object.
    Also, if the resource does not exists, then it will fail.
    
## Named Credentials
Benefit of using Named credentials is we do not have to explicitly specify remote site settings and also they can store the password safely. It takes care of the authentication as well.

state param in oAuth is used to secure the request. If the state param is sent in the request and same state param is responded back. If the param is tampered with, then the request is considered compromised.

### [INTEGRATION API 2023 GUIDE](https://magicfuse.co/blog/ultimate-guide-to-salesforce-apis/)
### [Handling Errors in Platform Events](https://www.apexhours.com/exception-handling-using-platform-events/)
### [Integration Design Patterns](https://developer.salesforce.com/docs/atlas.en-us.integration_patterns_and_practices.meta/integration_patterns_and_practices/integ_pat_intro_overview.htm)


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
