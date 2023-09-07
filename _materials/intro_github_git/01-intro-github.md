---
title: "Introduction to GitHub"
permalink: /materials/intro-github-git/01-intro-github
excerpt: "An introduction to GitHub"
toc: true
---

## What is GitHub?

![GitHub Logo](https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png)

GitHub is a web-based platform that allows you to host and version code-related projects, while also working collaboratively. The best analogy is to imagine a blend of a data management and collaborative work platform like Google Drive with a social media platform like Twitter. It uses Git, a version control system, which is confusingly different from GitHub (more about git available in the [next lesson]({{site.baseurl}}/materials/intro-github-git/02-intro-git)), to manage the history of a project. The platform was created in late 2007 and acquired by Microsoft in 2018[^1],and has become the largest global platform for hosting code, with the platform recently announcing that they had over 100 million of users.[^2]

![100 million users](https://github.blog/wp-content/uploads/2023/01/100million-header.png?resize=1200%2C627)

### Considerations and Criticisms

These numbers sound impressive, but should also be concerning. The consolidation of code and data on a single platform raises questions about the centralization of knowledge and the power of a single company to control the future of software development, if not all technology writ large. 

While alternatives to GitHub exist (primarily [GitLab](https://about.gitlab.com/) or [Bitbucket](https://bitbucket.org/product)), it is hard to overstate how much in the last decade GitHub has become the de facto platform for this type of work. Such a centralization is truly a double-edged sword. For example, GitHub has created what amounts to the largest code archive in the world through their GitHub Arctic Code Vault, an initiative to take a snapshot of all code hosted on their platform on February 2, 2020 and store it in the Svalbard Global Seed Vault. Such an initiative is impressive and was done in partnership with some academic institutions (the exact partners were the Long Now Foundation, the Internet Archive, the Software Heritage Foundation, Arctic World Archive, Microsoft Research, the Bodleian Library, and Stanford Libraries). But it also raises a number of ethical, archival, and political questions.

![arctic code vault]({{site.baseurl}}/assets/images/artic_code_vault.png)

For example, this Arctic Code Vault has been criticized for its erasure of the indigenous Sami people who live on Svalbard and its performative approach to archives.[^3] GitHub also has contracts with U.S. Immigrations and Customs Enforcement (ICE) led to protests and boycotts from some sectors of the developer community.[^4] While we plan to use this platform, it's important to do so with these issues in mind.

## Why Use GitHub for Digital Humanities?

While primarily marketed towards software developers, GitHub is also incredibly popular for digital humanities. It is widely used for hosting data sets, text corpora, and other scholarly research assets. It provides a central place to publish, discover, and collaborate on such resources. 

For instance, academic journals like the *Programming Historian* use GitHub for the entire publishing life cycle (you can explore for yourself [https://github.com/programminghistorian/jekyll](https://github.com/programminghistorian/jekyll)). You can get a sense of how popular GitHub is for digital humanities through searching for `digital-humanities` on the platform. 

![dh popularity]({{site.baseurl}}/assets/images/dh_github_popularity.png)

You'll notice that there's a number of categories on the left-hand side. Under `Filter By`, we have code, repositories, issues, pull requests, discussions, users, commits, packages, wikis, topics, marketplace. Then underneath, we have `Languages` which lists a series of programming languages. And finally we have `Advanced` which is a set of advanced filters that lets you search by date, owner, topic, etc...

We won't cover each of these in detail today, but there's a few you should become familiar with.

### Repositories

Repositories are the core of GitHub, and are essentially like folders in Google Drive. They are where all the files, code, and data for a project is stored, along with version histories of them. Repositories can be public or private. Public repositories are visible to anyone, while private repositories are only visible to the owner and collaborators.

You can view the activity on a repository by clicking on the `Insights` tab. This will show you a graph of the activity on the repository, including activity by contributors, under the `Contributors` tab.

[![contributors jekyll]({{site.baseurl}}/assets/images/contributors_jekyll.png)](https://github.com/programminghistorian/jekyll/graphs/contributors)

### Issues

Issues are a way to track bugs, feature requests, or other tasks related to a project. They are a way to track the development of a project and can be used to coordinate work between collaborators. Issues can be assigned to specific users, labeled, and commented on. They can also be closed when the issue is resolved.

![issue](https://docs.github.com/assets/cb-119863/mw-1440/images/help/issues/issue-assignees.webp)

### Discussions

You have all tried out discussions already! Discussions are a way to have threaded conversations about a project. They are similar to issues, but are more open-ended and can be used for general questions or conversations. They are a way to build community around a project.

![discussions](https://github.githubassets.com/images/modules/site/discussions/overview.png)

### Topics

While GitHub's search engine is powerful, one way to make your projects for findable is to add topics, which allows you to tag a repository with keywords.  For example, if you search for `digital-humanities` and then click on the `Topics` tab, you'll see a list of topics that are associated with repositories that have been tagged with `digital-humanities`. You can also see how many repositories have been tagged with each topic.

![dh topics]({{site.baseurl}}/assets/images/dh_topics.png)

### Users

You are all also familiar now with users, since you all have accounts on GitHub. While user profiles are somewhat self-explanatory, there's a number of features for users that are worth highlighting.

#### Profile

User profiles are where you can see all of a user's repositories, issues, and discussions. It's also where you can see their followers and who they are following. You can also see their activity on GitHub, including their contributions to repositories, issues, and discussions.

We can explore some of these features through my profile as an example.

[![leblanc profile]({{site.baseurl}}/assets/images/leblanc_github_profile.png)](https://github.com/ZoeLeBlanc)

#### Followers and Following

You can follow other users on GitHub, which allows you to see their activity on the platform. You can also see who is following you. This is a way to build community and find other users who are working on similar projects.

## In Class Lab Activity

### Creating Your First Repository

Now that we've explored some of the features of GitHub, let's create a repository. Again, remember repository is essentially a term for folder.

The folder or repository we are going to create today is going to be a place where you can store your work for this course. We'll be using this repository throughout the course, so it's important that you create it now.

To do this, click on the `New` button in the top right-hand corner of the screen. This will take you to a page where you can create a new repository.

![new repo](https://docs.github.com/assets/cb-31554/images/help/repository/repo-create.png)

Now you'll be asked to give it a name. Let's do our course name `is578-introduction-to-dh`. You can also add a description, choose whether it's public or private, and add a license (we'll discuss licenses later in the semester). 

![create repo](https://cdn-media-1.freecodecamp.org/images/mxGU5eGEki7FsedthUt8Vyi3uqAhL02FbmXF)

You can also initialize the repository with a README, which is a file that provides information about the project. You can also add a `.gitignore` file, which is a file that tells Git to ignore certain files in the repository. We'll talk more about this in the next lesson.

![first commit](https://material.bits.vib.be/topics/git-introduction/images/02-3-create-readme-repository.PNG)

Once you create your repository it should like the photo above. If you do not select the `Initialize this repository with a README` option, you will see a blank repository that looks like the photo below.

![empty repo](https://www.dataquest.io/wp-content/uploads/2019/01/repo_options.png)


*Any questions or problems?*

----

So far what we have is pretty basic, but we can quickly start editing. Let's click on the little pencil icon to edit the README file. This will take us to a text editor where we can edit the file. Let's add some text to the file. For example, let's add the following text:

```
# Introduction to Digital Humanities

This is my repository for IS 578: Introduction to Digital Humanities.
```

Now let's scroll down to the bottom of the page and click on the `Commit changes` button. This will save our changes to the repository. You'll notice that we have to add a commit message. This is a message that describes the changes we made to the repository. For example, we could write `Added text to README file`.

But what exactly did we just do? We just made our first commit and worked with git, so time for the next lesson!



[^1]: For more about this acquistion see Warren, Tom. “Microsoft Confirms It Will Acquire GitHub for $7.5 Billion.” *The Verge*, June 4, 2018. [https://www.theverge.com/2018/6/4/17422788/microsoft-github-acquisition-official-deal](https://www.theverge.com/2018/6/4/17422788/microsoft-github-acquisition-official-deal).
[^2]: Dohmke, Thomas. “100 Million Developers and Counting.” The GitHub Blog (blog), January 25, 2023. [https://github.blog/2023-01-25-100-million-developers-and-counting/](https://github.blog/2023-01-25-100-million-developers-and-counting/).
[^3]: David., “Seeds Or Code?,” accessed April 5, 2023, [https://blog.dshr.org/2019/11/seeds-or-code.html](https://blog.dshr.org/2019/11/seeds-or-code.html).
[^4]: For more information on this topic, you can read ["The Schism at the Heart of the Open-Source Movement"](https://www.theatlantic.com/technology/archive/2020/01/ice-contract-github-sparks-developer-protests/604339/) and [Dear GitHub](https://github.com/drop-ice/dear-github-2.0/blob/master/README.md).

