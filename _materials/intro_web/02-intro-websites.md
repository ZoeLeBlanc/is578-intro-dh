---
title: "Introduction to Websites"
permalink: /materials/intro-web/02-intro-websites/
excerpt: "An introduction to making websites."
toc: true
---

## Interactive Map 2.0

In our assignment last week, we created an HTML version of our Kepler.gl map and explored in our browser. But we did not discuss how I embedded the map into this course website.

First, rather than download an HTML version of the map, I downloaded the JSON file, an option you can see here:

<figure>
  <a href="https://d1a3f4spazzrp4.cloudfront.net/kepler.gl/documentation/k-save-and-export-5.png" class="image-popup">
    <img src="https://d1a3f4spazzrp4.cloudfront.net/kepler.gl/documentation/k-save-and-export-5.png" alt="Exporting Kepler Maps to JSON" />
  </a>
</figure>

Then I uploaded it to something called a GitHub gist. Gists are a way to share individual code snippets and files with others, rather than entire projects. Somewhat confusingly, though GitHub gists are part of GitHub, they are not part of a GitHub repository. You can read more about gists [here](https://docs.github.com/en/github/writing-on-github/creating-gists).

<figure>
  <a href="{{site.baseurl}}/assets/images/kepler_gist.png" class="image-popup">
  <img src="{{site.baseurl}}/assets/images/kepler_gist.png">
  </a>
</figure>

This is what my gist looks like, and you'll notice I created a secret one. That's because this code contains my mapbox token so I don't want to share that publicly or others might use and either use up all my free map loads or worse lead to MapBox charging me for too many loads.

So taking my downloaded json file, I simply pasted into my gist and saved it (again as a secret gist).

Then I simply copied the link to the gist (in this case `https://gist.githubusercontent.com/ZoeLeBlanc/32daed91a4eb0038640891b95e78029c/raw/580a8252b3757387e0fc5ae309e88a3c921f9c06/kepler.gl.json`) and pasted in the following code:

```html
<figure>

  <iframe src="https://kepler.gl/#/demo?mapUrl=https://gist.githubusercontent.com/ZoeLeBlanc/32daed91a4eb0038640891b95e78029c/raw/580a8252b3757387e0fc5ae309e88a3c921f9c06/kepler.gl.json" style="border:0px #ffffff none;" name="myiFrame" scrolling="no" frameborder="1" marginheight="0px" marginwidth="0px" height="900px" width="1200px" allowfullscreen=""></iframe>

</figure>
```

You'll notice in this HTML we are using some new elements (`figure` and `iframe`) and those elements have attributes that we've seen (like `style`) and then a bunch of new ones (`src`, `name`, `scrolling`, `frameborder`, `marginheight`, `marginwidth`, `height`, `width`, `allowfullscreen`).

While this code is more complex, to give a top level overview, this code uses the `figure` element to create a container for our map, and then the `iframe` element to embed the map into our page. The `src` attribute tells the browser where to find the map, and the `style` attribute tells the browser how to display the map. The rest of the attributes are used to set the size of the map.

So to recreate this approach I could simply copy this code and put it in our `first_page.html` file, and see the results when I open that page in the browser.

But even if I can see it and you can see it via my Zoom screen, you cannot currently see it on the internet. To do that, we need to discuss how the web works.


## What is the Web and How does it Work?

We all use the web constantly, but what is it exactly? 

If we go to our handy source of information, Wikipedia, we can find the following definition:

[**From Wikipedia:**](https://en.wikipedia.org/wiki/World_Wide_Web)
"The World Wide Web (WWW), commonly known as the Web, is an information system where documents and other web resources are identified by Uniform Resource Locators (URLs, such as <https://www.example.com/>), which may be interlinked by hypertext, and are accessible over the Internet.[1][2] The resources of the WWW are transferred via the Hypertext Transfer Protocol (HTTP) and may be accessed by users by a software application called a web browser and are published by a software application called a web server."

This is technically a definition but there's a lot to unpack here. 

### What is a Uniform Resource Locators (or URL)?

<figure>
  <a href="https://developer.mozilla.org/en-US/docs/Learn/Common_questions/Web_mechanics/What_is_a_URL/mdn-url-all.png" class="image-popup">
    <img src="https://developer.mozilla.org/en-US/docs/Learn/Common_questions/Web_mechanics/What_is_a_URL/mdn-url-all.png" alt="URL Encoding" />
  </a>
</figure>

This diagram is from the Mozilla web docs that have a great overview of the topic [https://developer.mozilla.org/en-US/docs/Learn/Common_questions/Web_mechanics/What_is_a_URL](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/Web_mechanics/What_is_a_URL). You've already seen a form of URLs when we created an `a` tag in our HTML page. 

```html
<a href="https://www.google.com/">Google</a>
```

This is a type of **Hyperlink** or **Link** that allows us to link to other webpages. In our case, we created something called an **external link** because we linked to a webpage that is not part of our website. But you can also created **internal links** that link to other pages on your website or **anchors** that link to specific parts of a webpage (this is how you can use the sidebar to navigate this page). You can read more about hyperlinks here [https://developer.mozilla.org/en-US/docs/Learn/Common_questions/Web_mechanics/What_are_hyperlinks](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/Web_mechanics/What_are_hyperlinks).

But URLs are more than just links, they are also the way we access webpages.Mozilla describe URLs as similar to postal addresses, which I think is a helpful analogy. If you want to send a letter to someone, you need to know their address. If you want to send a request to a webpage, you need to know the URL. Before we break down this anatomy of URLs, it's helpful to know a bit about domain names and how the web works. 

While we often talk about the **cloud**, the concept of the web was originally based on the idea of a **web** of interconnected computers.

<figure>
  <a href="https://developer.mozilla.org/en-US/docs/Learn/Common_questions/Web_mechanics/How_does_the_Internet_work/internet-schema-2.png" class="image-popup">
  <img src="https://developer.mozilla.org/en-US/docs/Learn/Common_questions/Web_mechanics/How_does_the_Internet_work/internet-schema-2.png">
  </a>
</figure>

While this is very reductive, essentially each computer operates as a **client** and a **server**. A client is a computer that requests data from a server, and a server is a computer that provides data to a client.

<figure>
  <a href="https://2.bp.blogspot.com/_4l9wMe5bbSk/TMpvwVcMT3I/AAAAAAAAAK4/sCEjRQCkF1o/s1600/Client+Server+communication.GIF" class="image-popup">
  <img src="https://2.bp.blogspot.com/_4l9wMe5bbSk/TMpvwVcMT3I/AAAAAAAAAK4/sCEjRQCkF1o/s1600/Client+Server+communication.GIF">
  </a>
</figure>

Though our current internet is vastly more complex, this core idea of a client **requesting** data and server **hosting** and **sending** data is still at the heart of how the web works. If you're interested in this longer history of the internet, I highly recommend checking out this timeline from the Computer History Museum, covering the history from the 1960s to the 1990s [https://www.computerhistory.org/internethistory/](https://www.computerhistory.org/internethistory/).

Now, as we discussed last week a lot of this data sent from server to client are actually HTML documents, but as you know this data can also be images, videos, audio, or really any type of data. 

So, besides understanding that we have clients and servers, the other core concept is understanding how these computers communicate with each other, using something called the **Hypertext Transfer Protocol (HTTP).**

### What is HTTP?

You'll notice that almost every URL starts with `http://` or `https://`. This is the protocol that the client and server use to communicate with each other. This is a standard that was developed in the early days of the web, and allows for the client and server to understand each other.

I particularly like [Julia Evans' Zine on HTTP](https://jvns.ca/blog/2019/09/12/new-zine-on-http/) for explaining this concept:

<figure>
  <a href="https://pbs.twimg.com/media/EAiEGSgXsAELERE?format=jpg&name=large" class="image-popup">
  <img src="https://pbs.twimg.com/media/EAiEGSgXsAELERE?format=jpg&name=large">
  </a>
</figure>

This is a bit technical, but the core thing to understand is that when we type a URL for a webpage (say google.com) into a web browser (say Chrome), we're actually sending an **HTTP request** to a **server** that hosts the actual HTML files and data. If the server decides that our request is ok (200), then it will give us access to the webpage.

There's a number of different types of status codes, that you can see here:

<figure>
  <a href="https://pbs.twimg.com/media/D-bI-xyWkAAY0Qb?format=jpg&name=large" class="image-popup">
  <img src="https://pbs.twimg.com/media/D-bI-xyWkAAY0Qb?format=jpg&name=large">
  </a>
</figure>

But the most important are either `200` which means the request was successful, or `404` which means the request was not successful.

<figure>
  <a href="https://user-images.githubusercontent.com/2938045/56276896-af93b580-6103-11e9-9885-74981a49a5ae.png" class="image-popup">
  <img src="https://user-images.githubusercontent.com/2938045/56276896-af93b580-6103-11e9-9885-74981a49a5ae.png">
  </a>
</figure>

So if you've ever seen an error message when you go to a webpage saying the page doesn't exist, that means that you received a 404 error, which is a type of status code you get back from an HTTP request.

So now we look more closely at the components of URL, through the Mozilla example here [https://developer.mozilla.org/en-US/docs/Learn/Common_questions/Web_mechanics/What_is_a_URL#scheme](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/Web_mechanics/What_is_a_URL#scheme). 

So first we have the scheme or protocol, which tells the browser how to communicate with the server:

<figure>
  <a href="https://developer.mozilla.org/en-US/docs/Learn/Common_questions/Web_mechanics/What_is_a_URL/mdn-url-protocol@x2_update.png" class="image-popup">
  <img src="https://developer.mozilla.org/en-US/docs/Learn/Common_questions/Web_mechanics/What_is_a_URL/mdn-url-protocol@x2_update.png">
  </a>
</figure>

One thing to note is that websites, web browsers, and search engine are all software applications that use the HTTP protocol to communicate with web servers, but are also different:

- a *website* is a collection of web pages and related content that is identified by a common **domain name** and published on at least one web server, like our course website. A website might have internal and external links on it as well.
- a *web browser* is a software application that is used to access websites and view web pages, like Google Chrome or Firefox or Safari. So while you can open any HTML document in a web browser, you can also use a web browser to access websites that are hosted from other servers.
- a *search engine* is a web service like Google or DuckDuckGo that allows users to search for content on the web, usually accessed from a web browser. These search engines often *crawl* websites via URLs to index the content of the web.

So now that we have some terminology, we can look at some of the rest of the URL.

### What is a Domain Name?

Next we have the **authority or domain name**, which is the name of the server that hosts the website:

<figure>
  <a href="https://developer.mozilla.org/en-US/docs/Learn/Common_questions/Web_mechanics/What_is_a_URL/mdn-url-authority.png" class="image-popup">
  <img src="https://developer.mozilla.org/en-US/docs/Learn/Common_questions/Web_mechanics/What_is_a_URL/mdn-url-authority.png">
  </a>
</figure>

Originally, when you used the internet you would access other websites using something called an **IP address**, which is a series of numbers that identifies a particular computer on the internet. You can see an example of an IP address here:

<figure>
  <a href="https://www.ipxo.com/app/uploads/2021/09/IPv4-anatomy.png" class="image-popup">
  <img src="https://www.ipxo.com/app/uploads/2021/09/IPv4-anatomy.png">
  </a>
</figure>

IP Addresses are still used today, but they are not very user friendly (though we will be seeing some in action today), so instead, we use domain names. Domain names are part of the [**Domain Name System (DNS)**](https://en.wikipedia.org/wiki/Domain_Name_System) which is often described as a "phone book" or "address book" that translates IP addresses of servers into easier to understand domains.

Here's an example of a domain name:

<figure>
  <a href="https://developer.mozilla.org/en-US/docs/Learn/Common_questions/Web_mechanics/What_is_a_domain_name/structure.png" class="image-popup">
  <img src="https://developer.mozilla.org/en-US/docs/Learn/Common_questions/Web_mechanics/What_is_a_domain_name/structure.png">
  </a>
</figure>

In this explanation from Mozilla [https://developer.mozilla.org/en-US/docs/Learn/Common_questions/Web_mechanics/What_is_a_domain_name](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/Web_mechanics/What_is_a_domain_name), they outline that there are two general main components to a domain name:

- the **top-level domain (TLD)**, which is the last part or suffix of the domain name, like `.com` or `.org` or `.edu`. These are registered and managed by a central organization called ICANN (Internet Corporation for Assigned Names and Numbers). As you can imagine there's a long history and fraught politics around TLDs, since they are often tied to countries (for example, `.uk` or `.ca`). Noteably, while there is `.us` for the United States, most US websites use `.com` or `.gov` if they are government-related. If you're curious to learn more I would recommend this blog post on dead-tlds [https://astrid.tech/2022/04/05/1/dead-tlds/](https://astrid.tech/2022/04/05/1/dead-tlds/) and checking out the rich literature on Internet Governance with books like Milton Mueller's *Networks and States* or Laura DeNardis' *The Global War for Internet Governance*.
- the other part of a domain name is the **second-level domain (SLD)**, which is the part of the domain name that is to the left of the TLD, like `mozilla` in `mozilla.org`. These are managed by domain name registrars, like GoDaddy, and are registered by individuals or organizations. One key thing to understand is that you can purchase a domain name through registrars but not in perpetuity. This leads to not only needing to renew your domain names, but also to the rise of domain name speculation, where people purchase domain names in the hopes of selling them for a profit. You can read more about this in this article by Ingrid Burrington on visting a Domain-Names Conference [https://www.theatlantic.com/technology/archive/2017/02/domain-names-dot-horse/516438/](https://www.theatlantic.com/technology/archive/2017/02/domain-names-dot-horse/516438/).

So in the case of the mozilla example, we have a subdomain `developer` and a second-level domain `mozilla` and a top-level domain `org`.

Another example is this course website, which is available at the subdomain of my website `zoeleblanc.com`, which finally brings us to our core part of today's lessons: **static sites**.

## Static Sites

So now that we understand the basics of how the web works, we can start to explore how we make websites. As you've started to read about, something called static sites are an incredibly popular approach to making websites (though want to emphasize it is one of many options). 

One of the things we have yet to discuss much is something called **hosting**. That's essentially how servers (aka computers) make their data available to clients. Most websites have a database that stores the data, and then a server that hosts the website.

<figure>
  <a href="{{site.baseurl}}/assets/images/dynamic_vs_static.png" class="image-popup">
  <img src="{{site.baseurl}}/assets/images/dynamic_vs_static.png">
  </a>
</figure>

So hopefully we can see some differences between dynamic and static, but to be honest this distinction is a bit more blurry than it might seem.

<figure>
  <a href="{{site.baseurl}}/assets/images/defining_static_sites.png" class="image-popup">
  <img src="{{site.baseurl}}/assets/images/defining_static_sites.png">
  </a>
</figure>

Part of why they are so popular is that they are safer to host (without a database you can't get hacked for example), are often cheaper to host (since they are just files), and can be easier to load over the web (though that depends on the size of the files). But they also as we have read, often require lots of labor to build and maintain them.

The core thing to know is that static sites are not the only way to host websites, and that there are many other options, including dynamic sites, which are often built with something called a **content management system (CMS)**, using services like Wordpress or Squarespace. The choice of how to build a website should be informed by the principles of minimal computing, but that does not always mean a static site is the right option. 

### Static Site Generators

A google search for static site generators returns millions of medium and quora posts debating which static site is the best, but few of these actually delve into the mechanics. Fundamentally, a **static site generator takes some form of plain text file (like Markdown) and transforms it into html files**. These generator libraries will also let you style your website using a combination of modular HTML files, Style Sheets, and Javascript scripts.

Most static site generators rely on similar patterns for how to manipulate your data, even if the details differ. To get a static site generator on your computer, means the first step is to usually download a code library. These libraries contain the code to transform your data, and they are almost always available to see on Github if you want to delve deeper.

### Creating a Jekyll Site

One of the most popular static site generators is **Jekyll**, which is built in the programming language **Ruby**. You don't need to know Ruby to use Jekyll, but you do need to have it installed on your computer. One of the best resources for doing that is Amanda Visconti, "Building a static website with Jekyll and GitHub Pages," *Programming Historian* 5 (2016), [https://doi.org/10.46430/phen0048](https://doi.org/10.46430/phen0048).

I will be demo-ing how to create a Jekyll site using the command line, but you can also use a GUI (graphical user interface) like Github Desktop or GitKraken.

Once again I can use both the Jekyll documentation [https://jekyllrb.com/docs/](https://jekyllrb.com/docs/) and my handy ChatGPT to help me generate the initial commands for creating a Jekyll site.

<div class="notice--info">⚡️ Before you can use Jekyll, you will need to install Ruby on your computer. The best instructions are through either Jekyll Documentation <a href="https://jekyllrb.com/docs/installation/#requirements">https://jekyllrb.com/docs/installation/#requirements</a> or the Programming Historian Lesson <a href="https://programminghistorian.org/en/lessons/building-static-sites-with-jekyll-github-pages#on-a-mac-">https://programminghistorian.org/en/lessons/building-static-sites-with-jekyll-github-pages#on-a-mac-</a>. Please reach out to the instructor if you get stuck so that you can get assistance.</div>

The following commands should work once you have everything correctly installed:

1. Install Jekyll and Bundler Gems:

Open your terminal and run the following command:

```bash
gem install jekyll bundler
```

2. Create a New Jekyll Site:
  
Navigate to the directory where you want your site to be created and run. In my case, I want to create a site called `new-intro-dh` but you can name this project anything (it doesn't need to be the same as your domain name either):

```bash
jekyll new new-intro-dh
```

3. Change Directory:
   
Move into the directory of your new Jekyll site:
  
```bash
cd new-intro-dh
```

4. Build the Site and Make it Available on a Local Server:

```bash
bundle exec jekyll serve
```

Some of these commands you've seen before, like `cd`, but the rest are new. You don't really need to understand them but to sum it up:

- first, we install the necessary code libraries for our static site (you can see some of these files here [https://github.com/jekyll/jekyll](https://github.com/jekyll/jekyll))
- then, we use those libraries to make a new Jekyll site that is a directory of files and code (essentially the command `jekyll new` is built into the Jekyll library)
- then, we move into that directory
- finally, we use another command **build** the site and make it available on a local server

You might see some angry warning messages but you can ignore them as long as you see the following lines:

```bash
Server address: http://127.0.0.1:4000/
Server running... press ctrl-c to stop.
```

Those lines tell us that our computer is now acting as a server for our site and so if we click on that Server address, we should see our new site in the browser, which should look like the following:

<figure>
  <a href="https://programminghistorian.org/images/building-static-sites-with-jekyll-github-pages/building-static-sites-with-jekyll-github-pages-11.png" class="image-popup">
  <img src="https://programminghistorian.org/images/building-static-sites-with-jekyll-github-pages/building-static-sites-with-jekyll-github-pages-11.png">
  </a>
</figure>

In many ways, this site is the exact same as the HTML files you all created, but there's a few differences. First, if we had looked through our directory before doing the `bundle exec jekyll serve` command, we would have seen that there was no folder called `_site` and that while there were HTML files, there weren't any of our About page or blog posts. That command essentially tells Jekyll to take those Markdown files and create HTML files from them, and then put those HTML files in the `_site` folder. Which is why this type of static site generator is so popular: it saves you the time of having to manually create HTML files.

We don't have time today to full explore all the parts of this site, but I do want to highlight a few things:

1. `_config.yml`

Almost all static site generators have a configuration file that allows you to set some basic parameters for your site. In Jekyll, this is the `_config.yml` file. You can see that this file has a number of parameters, including the title of the site, the description, the url, and the baseurl. Here's an example of the default Jekyll config:

<figure>
  <a href="https://programminghistorian.org/images/building-static-sites-with-jekyll-github-pages/building-static-sites-with-jekyll-github-pages-15.png" class="image-popup">
  <img src="https://programminghistorian.org/images/building-static-sites-with-jekyll-github-pages/building-static-sites-with-jekyll-github-pages-15.png">
  </a>
</figure>

So, we could change the title and domain of our website through this file. Instead of changing the URL though, I want to change the baseurl, because I want to host this from my `zoeleblanc.com` domain as a subdomain.

```yml
title: New Intro to DH
baseurl: /new-intro-dh
```

Now if we regenerate our site, can see that our site is available at `http://127.0.0.1:4001/new-intro-dh/` with out new title.

<figure>
  <a href="{{site.baseurl}}/assets/images/updated_jekyll_site.png" class="image-popup">
  <img src="{{site.baseurl}}/assets/images/updated_jekyll_site.png">
  </a>
</figure>


1. `posts` directory
   
The other main attraction of static sites is that they are excellent for blogging, because almost every static site option has a directory called `posts` (sometimes seen as `_posts`).

If we open up the example in our new site, we'll see the following:

<figure>
  <a href="https://programminghistorian.org/images/building-static-sites-with-jekyll-github-pages/building-static-sites-with-jekyll-github-pages-19.png" class="image-popup">
  <img src="https://programminghistorian.org/images/building-static-sites-with-jekyll-github-pages/building-static-sites-with-jekyll-github-pages-19.png">
  </a>
</figure>

My main goal here is to show you how I can embed my Kepler map into this page, so I'm going to create a new file (using the `touch` command), make sure to name it similarly to this existing file (so date followed by topic), and then fill in the rest of the metadata and add my code. 

```markdown
---
layout: post
title:  "Interactive Map 2.0"
date:   2021-10-04 12:00:00 -0400
categories: jekyll update
---

<figure>

  <iframe src="https://kepler.gl/#/demo?mapUrl=https://gist.githubusercontent.com/ZoeLeBlanc/32daed91a4eb0038640891b95e78029c/raw/580a8252b3757387e0fc5ae309e88a3c921f9c06/kepler.gl.json" style="border:0px #ffffff none;" name="myiFrame" scrolling="no" frameborder="1" marginheight="0px" marginwidth="0px" height="900px" width="1200px" allowfullscreen=""></iframe>

</figure>
```

Once completed and **saved** (always remember to save!), I should be able to **reload** the site and see the interactive map as a part of my new site. 

<figure>
  <a href="{{site.baseurl}}/assets/images/jekyll_map_post.png" class="image-popup">
  <img src="{{site.baseurl}}/assets/images/jekyll_map_post.png">
  </a>
</figure>

Now the final step is to host this site on the internet.

### Hosting a (Jekyll) Site with GitHub Pages

As we've discussed today, there are many options for hosting websites (Wordpress, Squarespace, etc.). That's also true for Static Sites, with many DHers liking [Reclaim Hosting](https://www.reclaimhosting.com/) for hosting their websites and purchasing domain names. 

Today, we're instead going to use GitHub Pages. GitHub Pages is a free service that allows you to host static sites on GitHub. You can read more about GitHub Pages here [https://pages.github.com/](https://pages.github.com/).

To host a Jekyll site on GitHub Pages, we need to do a few things:

1. Create a GitHub Repository (Somewhat Optional)

First, we need a GitHub repository for where we want to store our website files. You could use your existing repository for this course or create a new one.

<figure>
  <a href="{{site.baseurl}}/assets/images/create_jekyll_repo.png" class="image-popup">
  <img src="{{site.baseurl}}/assets/images/create_jekyll_repo.png">
  </a>
</figure>

If you do create a new repository, be sure to make it public and add a README.md file.

2. Update our Jekyll Gemfile

Before, we add our files we need to make a small change so that GitHub correctly renders our website (this is what went wrong with my example in class 😅). 

If you open your `Gemfile`, you should see the following:

<figure>
  <a href="{{site.baseurl}}/assets/images/existing_gemfile.png" class="image-popup">
  <img src="{{site.baseurl}}/assets/images/existing_gemfile.png">
  </a>
</figure>

You'll notice that's there an automated message saying that we should add a line to our `Gemfile` to make sure that GitHub Pages correctly renders our site:

```ruby
# If you want to use GitHub Pages, remove the "gem "jekyll"" above and
# uncomment the line below. To upgrade, run `bundle update github-pages`.
# gem "github-pages", group: :jekyll_plugins
# If you have any plugins, put them here!
```

So to follow those instructions we need to make sure there's a `#` symbol before this line:

```ruby
gem "jekyll", "~> 4.3.2"
```

Then we need to remove the `#` symbol from this line:

```ruby
# gem "github-pages", group: :jekyll_plugins
```

So the final result should look like the following: 

<figure>
  <a href="{{site.baseurl}}/assets/images/updated_gemfile.png" class="image-popup">
  <img src="{{site.baseurl}}/assets/images/updated_gemfile.png">
  </a>
</figure>

Finally, we need to run the following command to update our Jekyll site:

```bash
bundle update github-pages
```

If you get an error with that command, I would recommend trying either `bundle update` or `bundle install` instead.

3. Push/Add our Jekyll Site to GitHub

Once we have our GitHub repository and our updated `Gemfile`, we can now add our Jekyll site to GitHub. You can do this through the `.dev` interface or through using ChatGPT to generate the correct commands.

Regardless, we want our final repository to look like the following:

<figure>
  <a href="{{site.baseurl}}/assets/images/updated_github_repo.png" class="image-popup">
  <img src="{{site.baseurl}}/assets/images/updated_github_repo.png">
  </a>
</figure>

4. Configure GitHub Pages to publish our website

Once we have this all added, the final piece is to go into our settings and configure GitHub Pages to publish our website. You can do this by going to the `Settings` tab and then scrolling down to `Pages`:

<figure>
  <a href="https://www.stefanocottafavi.com/assets/img/gh_actions.png" class="image-popup">
  <img src="https://www.stefanocottafavi.com/assets/img/gh_actions.png">
  </a>
</figure>

To make our site run, we need to select the `GitHub Actions` option under `Build and deployment`:

<figure>
  <a href="{{site.baseurl}}/assets/images/github_pages_jekyll.png" class="image-popup">
  <img src="{{site.baseurl}}/assets/images/github_pages_jekyll.png">
  </a>
</figure>

Selecting this option will open another page that looks a bit intimidating:

<figure>
  <a href="{{site.baseurl}}/assets/images/jekyll_github_action.png" class="image-popup">
  <img src="{{site.baseurl}}/assets/images/jekyll_github_action.png">
  </a>
</figure>

You don't need to change anything on this page, but simply just press the green `Commit changes` button and then GitHub will start building your site. If you give a minute or two, when you go back to the `Settings` tab and scroll down to `Pages` you should see a green box saying your site is published and a link to your site.

<figure>
  <a href="{{site.baseurl}}/assets/images/published_github_pages.png" class="image-popup">
  <img src="{{site.baseurl}}/assets/images/published_github_pages.png">
  </a>
</figure>

If you instead get a message like this in actions:

<figure>
  <a href="{{site.baseurl}}/assets/images/jekyll_build_fail.png" class="image-popup">
  <img src="{{site.baseurl}}/assets/images/jekyll_build_fail.png">
  </a>
</figure>

It means that GitHub failed to build your website. This error message is not super important to understand but to fix it you need to run the following line of code in your Terminal in the directory with your Jekyll site, which I learned from the following StackOverflow post (which is a forum for coding questions) [https://stackoverflow.com/questions/72331753/ruby-and-rails-github-action-exit-code-16](https://stackoverflow.com/questions/72331753/ruby-and-rails-github-action-exit-code-16):

```bash
bundle lock --add-platform x86_64-linux
```

Then you need to commit and push your changes to GitHub. Once you do that, GitHub should start building your site correctly. If you get **any** other error message, please don't hesitate to reach out to the instructor for help, and just remember that these types of issues though frustrating **are not representative of your ability to do this work**. In fact, an HCI professor wrote an excellent post about how this type of configuration errors can deter students (you can read a bit about that here [https://www.kevinbrowne.ca/command-line-bullshittery-and-other-realities-of-computing/](https://www.kevinbrowne.ca/command-line-bullshittery-and-other-realities-of-computing/)).


Now you can see all this code in my repository [https://github.com/ZoeLeBlanc/map-jekyll-intro-dh](https://github.com/ZoeLeBlanc/map-jekyll-intro-dh) and visit the website at [http://zoeleblanc.com/map-jekyll-intro-dh/](http://zoeleblanc.com/map-jekyll-intro-dh/).

Now this entire example only works because I already have a domain name for my website (aka an address) but before you can have a subdomain, you need a domain. So let's talk about how to get a domain name (for free!).

#### Creating a Custom Github.io Website

As a user on GitHub, you can create a custom website that is hosted on GitHub Pages. This is a great option for creating a personal website, or a website for a project. This website is hosted at the `github.io` domain name so you don't have to pay for a domain name. However, to make this domain you need to create a repository with a specific name: your username. So for example, my GitHub username is `ZoeLeBlanc` so I need to create a repository called `ZoeLeBlanc.github.io`.

<figure>
  <a href="{{site.baseurl}}/assets/images/githubio_repo.png" class="image-popup">
  <img src="{{site.baseurl}}/assets/images/githubio_repo.png">
  </a>
</figure>

When you create your repository, you need to make sure it is `Public` and you can add a `README.md` (though that is optional).

<figure>
  <a href="{{site.baseurl}}/assets/images/create_new_file.png" class="image-popup">
  <img src="{{site.baseurl}}/assets/images/create_new_file.png">
  </a>
</figure>

Once you have your repository, the next step is to add some web files. The most basic file you can add is an `index.html` file.

<figure>
  <a href="{{site.baseurl}}/assets/images/create_index_html.png" class="image-popup">
  <img src="{{site.baseurl}}/assets/images/create_index_html.png">
  </a>
</figure>

Once you've created your `index.html` file, you can either leave it blank or add some HTML code. Now the key thing is to remember to **commit** your HTML page. Remember committing is how we save things on GitHub. So you can either commit via the command line or via the GitHub website.

Now, GitHub should start automatically hosting your website at `https://yourusername.github.io`. 

<figure>
  <a href="{{site.baseurl}}/assets/images/github_pages_settings_html.png">
  <img src="{{site.baseurl}}/assets/images/github_pages_settings_html.png">
  </a>
</figure>

You'll notice you don't need to configure any Actions (though you can for HTML), and that's because this is a special type of repository that GitHub does this for, so any HTML files you add will automatically be hosted but that will **not** happen in other repos.

You can still see how GitHub is deploying your site by clicking on the tab called `Actions`:

<figure>
  <a href="{{site.baseurl}}/assets/images/actions_tab.png">
  <img src="{{site.baseurl}}/assets/images/actions_tab.png">
  </a>
</figure>

You should see some green lines and checks, all of which indicates your site is live.

<figure>
  <a href="{{site.baseurl}}/assets/images/live_website.png">
  <img src="{{site.baseurl}}/assets/images/live_website.png">
  </a>
</figure>

You can find see this live here [https://testzoe.github.io/](https://testzoe.github.io/).

So, hopefully following these steps will help you create your initial website. You can do the similar steps above for a `Jekyll` site with your github.io repository, just be sure to update your `Gemfile`, add your files, and then configure GitHub Pages to publish your site with the `Github Actions for Jekyll`. If you get stuck or have questions, don't hesitate to reach out to the instructor for help.

You might also look at the following resources for more information:

- GitHub's documentation on GitHub Pages [https://docs.github.com/en/pages/getting-started-with-github-pages/about-github-pages](https://docs.github.com/en/pages/getting-started-with-github-pages/about-github-pages)
- GitHub's documentation on Jekyll and GitHub Pages [https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll)
- Library Carpentries Lesson on GitHub Pages [https://librarycarpentry.org/lc-git/05-github-pages.html](https://librarycarpentry.org/lc-git/05-github-pages.html)

## At Home/In Class Static Assignment(s)

1. Try to take your HTML page and Host Via GitHub Pages

Rather than having a blank HTML page, try to copy your content from the HTML homework from last week and host it via GitHub Pages. You can do this via the Command Line or `github.dev`. If neither are working, reach out the Instructor for assistance (likely you'll need to download GitHub's Desktop app or give the instructor permissions to collaborate on your repository).

2. Try to take your Jekyll site and Host Via GitHub Pages

Now once you have your HTML page hosted, the next step is considering how you might want a website at this URL rather than just a homework assignment. Either through the command line or this example Jekyll site via Google Drive [available here](https://drive.google.com/drive/folders/13ls8prYus36iEG_QHUMcCNNOK_29iUFO?usp=drive_link), try to customize a website that includes your HTML homework as a post, and then add that to GitHub Pages. Remember to delete your original `index.html`.

Once your link is live, post it to our final GitHub discussion forum [https://github.com/ZoeLeBlanc/is578-intro-dh/discussions/10](https://github.com/ZoeLeBlanc/is578-intro-dh/discussions/10).
  