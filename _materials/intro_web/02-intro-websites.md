---
title: "Introduction to Websites"
permalink: /materials/intro-web/02-intro-websites/
excerpt: "An introduction to making websites."
toc: true
---

## HTML Pages and the Web

In our assignment last week, the goal was to create 
<figure>
  <a href="https://d1a3f4spazzrp4.cloudfront.net/kepler.gl/documentation/k-save-and-export-5.png" class="image-popup">
    <img src="https://d1a3f4spazzrp4.cloudfront.net/kepler.gl/documentation/k-save-and-export-5.png" alt="Exporting Kepler Maps to JSON" />
  </a>
</figure>
Some of these steps require working with Kepler's guidelines for embedding maps.

## What is the Web?

[**From Wikipedia:**](https://en.wikipedia.org/wiki/World_Wide_Web)
"The World Wide Web (WWW), commonly known as the Web, is an information system where documents and other web resources are identified by Uniform Resource Locators (URLs, such as <https://www.example.com/>), which may be interlinked by hypertext, and are accessible over the Internet.[1][2] The resources of the WWW are transferred via the Hypertext Transfer Protocol (HTTP) and may be accessed by users by a software application called a web browser and are published by a software application called a web server."

![http](https://2.bp.blogspot.com/_4l9wMe5bbSk/TMpvwVcMT3I/AAAAAAAAAK4/sCEjRQCkF1o/s1600/Client+Server+communication.GIF)

*What does this mean exactly?*

When we type a url for a webpage (say google.com), we're actually sending an **HTTP request** to a **server** that hosts the actual HTML files and data. If the server decides that our request is ok (200), then it will give us access to the webpage.

![404 page](https://user-images.githubusercontent.com/2938045/56276896-af93b580-6103-11e9-9885-74981a49a5ae.png)

If you've ever seen an error message when you go to a webpage saying the page doesn't exist, that means that you received a 404 error, which is a type of status code you get back from an HTTP request.

## What is HTTP?

**Courtesy of [Julia Evans' Zine](https://jvns.ca/blog/2019/09/12/new-zine-on-http/)**

![What is HTTP?](https://pbs.twimg.com/media/EAiEGSgXsAELERE?format=jpg&name=large)

This comic explains a bit more in depth what is comprised of an HTTP request. We also want to have a sense of what types of status codes we can get back from a request.

![HTTP Status Codes](https://pbs.twimg.com/media/D-bI-xyWkAAY0Qb?format=jpg&name=large)

Finally, in our example we used the `GET` method when calling a webpage (using `request.get()`), but there's multiple methods that we can use to send data across the web.

![HTTP Request Methods](https://pbs.twimg.com/media/EB8dt0CWsAAET4b?format=jpg&name=large)

![How to learn more](https://pbs.twimg.com/media/ECvlQX1W4AE9EgP?format=jpg&name=large)

[More information about HTTP from Mozilla Docs](https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview)

If you're interested in the longer history of the internet checkout this timeline from the Computer History Museum, covering the history from the 1960s to the 1990s [https://www.computerhistory.org/internethistory/](https://www.computerhistory.org/internethistory/).

## Static Sites

