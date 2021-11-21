# Local storage

### Local Storage

* Key-value storage that stores values as strings
* Does not have expiration date (persistent storage) unless explicitly clear the browser using settings or Javascript
* Up to 10MB data can be stored
* Follow the same-origin policy, which means the Protocol(Http/Https), port and the host are the same. Only scripts of the same origin can access LocalStorge data
* Do not send to server, for client-side usage only

#### Use case:

Can be use to store user-related data

### **Session Storage**

* Key-value storage that stores values as strings
* Data stored does not survive after the table/window is closed
* Up to 10MB data can be stored
* Follow the same-origin policy and is bound to a tab
* Do not send to server, for clien-side usage only

&#x20;**Use case:**\
****Store user-related data for one session only like language selection

### Cookie

* Key-value storage that stores values as string
* Have expiration time, if no expiration time is given then the cookie will get expired at the end of the browser session.
* Up to 4KB data can be stored
* Send to server for every request and follow same-origin policy

**Use case:**

Server can get data from cookie to track session status.

### IndexedDB

* Can store both objects and key-value pairs
* Up to 250MB for IE
* IndexedDB API is asynchronous, unlike loca storage and session storage. IndexedDB operations are event-driven by various events like onsuccess, onerror, oncomplete etc.
* Follow the same-origin policy
* Do not have expiration time (persistent storage) unless explicit deletion

#### **Use case:**

When need to store a large number of objects which is time-consuming and a lag on performance to convert to string for Local Storage every time.

### WebSQL

* Deprecated by W3C
* Can be accessed using SQL statements.
* Follow same-origin policy
* Persistent storage unless explicit deletion

![](<../.gitbook/assets/image (2).png>)
