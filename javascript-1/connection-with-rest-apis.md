# Connection with REST APIs

## What Is A REST API

An **API** is an application programming interface. It is a set of rules that allow programs to talk to each other. The developer creates the API on the server and allows the client to talk to it.

**REST** determines how the API looks like. It stands for “Representational State Transfer”. It is a set of rules that developers follow when they create their API. One of these rules states that you should be able to get a piece of data \(called a resource\) when you link to a specific URL.

Each URL is called a **request** while the data sent back to you is called a **response**.

### The Anatomy Of A Request

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

\*\*\*\*



CONTINUAR...



{% embed url="https://www.smashingmagazine.com/2018/01/understanding-using-rest-api/" %}



