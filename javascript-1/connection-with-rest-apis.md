# Connection with REST APIs

## What Is A REST API

An **API** is an application programming interface. It is a set of rules that allow programs to talk to each other. The developer creates the API on the server and allows the client to talk to it.

**REST** determines how the API looks like. It stands for “Representational State Transfer”. It is a set of rules that developers follow when they create their API. One of these rules states that you should be able to get a piece of data \(called a resource\) when you link to a specific URL.

Each URL is called a **request** while the data sent back to you is called a **response**.

## The Anatomy Of A Request

 A request is made up of four things:

1. The endpoint
2. The method
3. The headers
4. The data \(or body\)

###  **The endpoint**

```text
root-endpoint/?
```

**The endpoint** \(or route\) is the url you request for. It follows this structure:

 The **root-endpoint** is the starting point of the API you’re requesting from.  The **path** determines the resource you’re requesting for.

 You can access paths just like you can link to parts of a website. For example, to get a list of all posts tagged under “JavaScript” on Smashing Magazine, you navigate to `https://www.smashingmagazine.com/tag/javascript/`. `https://www.smashingmagazine.com/` is the root-endpoint and `/tag/javascript` is the path.

To understand what paths are available to you, you need to look through the API documentation,  any colons \(`:`\) on a path denotes a variable, and can also have query parameters. Query parameters give you the option to modify your request with key-value pairs. They always begin with a question mark \(`?`\). Each parameter pair is then separated with an ampersand \(`&`\).

###  **The Method**

The method is the type of request you send to the server. You can choose from these five types below:

* `GET`
* `POST`
* `PUT`
* `PATCH`
* `DELETE`

These methods provide meaning for the request you’re making. They are used to perform four possible actions: `Create`, `Read`, `Update` and `Delete` \(CRUD\).

| Method Name | Request Meaning |
| :--- | :--- |
| \`GET\` | This request is used to get a resource from a server. If you perform a \`GET\` request, the server looks for the data you requested and sends it back to you. In other words, a \`GET\` request performs a \`READ\` operation. This is the default request method. |
| \`POST\` | This request is used to create a new resource on a server. If you perform a \`POST\` request, the server creates a new entry in the database and tells you whether the creation is successful. In other words, a \`POST\` request performs an \`CREATE\` operation. |
| \`PUT\` and \`PATCH\` | These two requests are used to update a resource on a server. If you perform a \`PUT\` or \`PATCH\` request, the server updates an entry in the database and tells you whether the update is successful. In other words, a \`PUT\` or \`PATCH\` request performs an \`UPDATE\` operation. |
| \`DELETE\` | This request is used to delete a resource from a server. If you perform a \`DELETE\` request, the server deletes an entry in the database and tells you whether the deletion is successful. In other words, a \`DELETE\` request performs a \`DELETE\` operation. |

The API documentation lets you know what request method to use each request.

###  **The Headers**

Headers are used to provide information to both the client and server. It can be used for many purposes, such as authentication and providing information about the body content: ****[**L**ist of valid headers](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers).

 HTTP Headers are property-value pairs that are separated by a colon.

###  **The Data \(Or “Body”\)**

The data **** contains information you want to be sent to the server. This option is only used with `POST`, `PUT`, `PATCH` or `DELETE` requests.

{% embed url="https://www.smashingmagazine.com/2018/01/understanding-using-rest-api/" %}



