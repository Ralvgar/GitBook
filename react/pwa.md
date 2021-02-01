---
description: progressive web app
---

# PWA

Put it simply, Progressive Web Apps are web applications that load in a web browser just like web pages or websites. It gives you a rich mobile experience via native-like functionalities such as the ability to work offline, push notifications, and device hardware accessibility.

It feels like a native app and offers the same experience as a native one. There is no need to download it from an app store. It loads, runs, and functions in a web browser.

### Service Worker

A service worker is a script written in javascript that allows intercepting and control of network requests and asset caching from the web browser. With service workers, web developers can create reliably fast web pages and offline experiences. It’s a browser feature but it doesn't have access to the DOM, its role is different than a normal JS script.

As service Workers have access to manage network requests, they can be very powerful, especially if used maliciously by an attacker, allowing things like script injection or replacing the whole site. This is why HTTPS is so important here, in order to prevent third parties from injecting them into your website.



{% embed url="https://create-react-app.dev/docs/making-a-progressive-web-app/" %}



