# Platform

1. [Platform Events](https://developer.salesforce.com/blogs/developer-relations/2017/05/first-impressions-platform-events-salesforce-enterprise-messaging-platform.html)
1. [Platform Events](https://www.apexhours.com/integrating-with-salesforce-using-platform-events/)
1. [Platform Events](https://developer.salesforce.com/blogs/2018/12/platform-events-eventbus-a-new-chapter-in-the-never-ending-saga-of-bulkification.html)
2. [Change Data Capture](https://developer.salesforce.com/blogs/2018/08/what-is-change-data-capture)
3. [Which Streaming API should I use?](https://developer.salesforce.com/blogs/2018/07/which-streaming-event-do-i-use)
4. [Streaming API Features](https://developer.salesforce.com/docs/atlas.en-us.api_streaming.meta/api_streaming/event_comparison.htm)
5. [Platform Cache](https://developer.salesforce.com/blogs/2020/06/caching-in-the-salesforce-platform.html)


Platform Event vs Change Data Capture

1. Change Data Capture is fired automatically when any record in the system is created, updated, deleted and undeleted where as PE is manually fired by user

change data capture vs pushtopic

push topic is an object in salesforce vs cdc is not
push is bound to a query vs cdc is fired when changes occur in record
push topic is subscribed using emp api for ui and commetd protocol for backed vs cdc can be subscrived using triggers in apex, empi in ui and grpc for backend

ReplayId for re-subscritpion
ReplayId is the unique Id given to an event in the event bus 
Example : 
Set<Integer> set = [89,67,4,3,88,90,100,1];
We have 8 events here, lets say these are sent accross if 4 of them fail , failing from 3, replayId will help us identify which have failed coz we
will get replayId until 3 - we can now ask the system to send other events after replayId of 3.

