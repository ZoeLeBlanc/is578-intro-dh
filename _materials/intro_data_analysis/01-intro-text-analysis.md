---
title: "Introduction to Text Analysis"
permalink: /materials/intro-data-analysis/01-intro-text-analysis
excerpt: "An introduction to studying and working with texts."
toc: true
---

So far we have started to consider how our potential questions might shape how we work with our data, but today we will be exploring some of the ways in which digital humanists *analyze* data, especially textual data. Exploring these methods will help us to think about how we might approach our own data and what kinds of questions we might ask of it, as well as the limitations of this kind of analysis.

## Final Data Visualization Solutions

Last week I shared a dataset that contained all the counts of the DH tools mentioned in the abstracts from the Index of the DH conference, along with the counts we already had from class and from the original blog post. While optional, one of our assignments was to create a data visualization that would help us to understand the differences between these datasets.

Below is a few of my attempts.

First, I started with Raw Graphs and made a few line graphs, using the following columns:

<figure>
    <a href="{{site.baseurl}}/assets/images/raw_graphs_updated_columns.png" class="image-popup">
        <img src="{{site.baseurl}}/assets/images/raw_graphs_updated_columns.png">
    </a>
</figure>

This is what the line graph looks like:

<figure>
    <a href="{{site.baseurl}}/assets/images/raw_graphs_area_tools.png" class="image-popup">
        <img src="{{site.baseurl}}/assets/images/raw_graphs_area_tools.png">
    </a>
</figure>

And also used a similar approach to get at the distribution from each of our `data origins`:

<figure>
    <a href="{{site.baseurl}}/assets/images/raw_graphs_data_origin.png" class="image-popup">
        <img src="{{site.baseurl}}/assets/images/raw_graphs_data_origin.png">
    </a>
</figure>

These graphs help demonstrate both the uneveness of our data and the distribution of tools, but there was a few issues with incorrect formatting of dates and difficulty parsing this amount of data. So, I also tried working with Google Sheets.

First, I made a pie chart of all the tools:

<figure>
    <a href="{{site.baseurl}}/assets/images/google_charts_pie.png" class="image-popup">
        <img src="{{site.baseurl}}/assets/images/google_charts_pie.png">
    </a>
</figure>

This was helpful in showing the sheer dominance of TEI, but didn't really help visualize the change over time.

To get at that change though, I had to once again transpose my data since Google Sheets wanted each of the tools as a column to visualize lines. Using OpenRefine, I was able to quickly transform the dataset to look like the following:

<figure>
    <a href="{{site.baseurl}}/assets/images/transpose_tools.png" class="image-popup">
        <img src="{{site.baseurl}}/assets/images/transpose_tools.png">
    </a>
</figure>

Which then allowed me to create a line graph that showed the change over time:

<figure>
    <a href="{{site.baseurl}}/assets/images/google_charts_line.png" class="image-popup">
        <img src="{{site.baseurl}}/assets/images/google_charts_line.png">
    </a>
</figure>

These again were helpful for getting at the change, but Google Sheets did even worst with the dates than Raw Graphs did. So, I decided to try DataWrapper.

The first two graphs chart the popularity of tools over time, and I added some annotations to help explain the changes:

<iframe title="DH Tool Popularity in Index of DH Abstracts" aria-label="Interactive area chart" id="datawrapper-chart-WPmEd" src="https://datawrapper.dwcdn.net/WPmEd/1/" scrolling="no" frameborder="0" style="width: 0; min-width: 100% !important; border: none;" height="400" data-external="1"></iframe><script type="text/javascript">!function(){"use strict";window.addEventListener("message",(function(a){if(void 0!==a.data["datawrapper-height"]){var e=document.querySelectorAll("iframe");for(var t in a.data["datawrapper-height"])for(var r=0;r<e.length;r++)if(e[r].contentWindow===a.source){var i=a.data["datawrapper-height"][t]+"px";e[r].style.height=i}}}))}();
</script>

<iframe title="DH Tool Popularity According to Class and Blog Post" aria-label="Interactive area chart" id="datawrapper-chart-rH0sN" src="https://datawrapper.dwcdn.net/rH0sN/1/" scrolling="no" frameborder="0" style="width: 0; min-width: 100% !important; border: none;" height="563" data-external="1"></iframe><script type="text/javascript">!function(){"use strict";window.addEventListener("message",(function(a){if(void 0!==a.data["datawrapper-height"]){var e=document.querySelectorAll("iframe");for(var t in a.data["datawrapper-height"])for(var r=0;r<e.length;r++)if(e[r].contentWindow===a.source){var i=a.data["datawrapper-height"][t]+"px";e[r].style.height=i}}}))}();
</script>

From these two charts we can start to see the relative popularity of Python for example that is very high across our datasets. Indeed, the only potential outlier we can see is with Voyant/Voyant Tools, which is the one popular tool in our class dataset. To further explore these differences a bit more, I once again transposed the original data, this time by `data_origin` in OpenRefine to create the following dataset:

<figure>
    <a href="{{site.baseurl}}/assets/images/transpose_data_origin.png" class="image-popup">
        <img src="{{site.baseurl}}/assets/images/transpose_data_origin.png">
    </a>
</figure>

Organizing the data in this structure allowed me to create a scatter plot that compares the popularity of tools from the Index of DH Abstracts to the blog post, and also compares the popularity of tools from our class to the Index of DH Abstracts:

<iframe title="Popularity of DH Tools from Index of DH Abstracts Compared to Blog Post" aria-label="Scatter Plot" id="datawrapper-chart-LePm9" src="https://datawrapper.dwcdn.net/LePm9/1/" scrolling="no" frameborder="0" style="width: 0; min-width: 100% !important; border: none;" height="400" data-external="1"></iframe><script type="text/javascript">!function(){"use strict";window.addEventListener("message",(function(a){if(void 0!==a.data["datawrapper-height"]){var e=document.querySelectorAll("iframe");for(var t in a.data["datawrapper-height"])for(var r=0;r<e.length;r++)if(e[r].contentWindow===a.source){var i=a.data["datawrapper-height"][t]+"px";e[r].style.height=i}}}))}();
</script>

<iframe title="Popularity of DH Tools from Index of DH Abstracts Compared to Blog Post" aria-label="Scatter Plot" id="datawrapper-chart-6Dhy9" src="https://datawrapper.dwcdn.net/6Dhy9/1/" scrolling="no" frameborder="0" style="width: 0; min-width: 100% !important; border: none;" height="563" data-external="1"></iframe><script type="text/javascript">!function(){"use strict";window.addEventListener("message",(function(a){if(void 0!==a.data["datawrapper-height"]){var e=document.querySelectorAll("iframe");for(var t in a.data["datawrapper-height"])for(var r=0;r<e.length;r++)if(e[r].contentWindow===a.source){var i=a.data["datawrapper-height"][t]+"px";e[r].style.height=i}}}))}();
</script>

Once again we can see that while many of the tools are consistent popular/unpopular between these datasets, Voyant is an outlier. Such an observation may be worth exploring further, especially since Voyant is a tool that is often used in DH. To dig into why Voyant has such differing results requires starting to consider how we analyze and work with textual data.

## Text Analysis

To create this tool frequency dataset, I used some code in Python since counting words is difficult to do in Excel or Google Sheets. The code is available in the following Google Colab notebook for those interested.

As we have learned in our readings this week, working with text is a common and growing area of DH research. But this practice, much like creating datasets or visualizing them, is far from straightfoward.

- turning unstructured data into structured data when it is text
  - tokenization
- cleaning and normalizing textual data
  - stopwords
- working with text as data
  - word counts
  - word frequencies
  - word clouds
  - topic modeling



One of the main ways we can structure our Humanist listserv data is by undertaking something called *text analysis*. This is a very broad term for a whole set of practices and overlapping disciplines and fields, some of which are shown in this figure below:

![text analysis](https://miro.medium.com/max/1200/0*ewkxRItArykG27dU.png)

But again this figure has its limits. For example, data mining is something that Library & Information Sciences undertakes, and databases are used across these domains.

Rather than trying to define text analysis as a whole, I find a more helpful distinction is talking about Information Extraction vs Information Retrieval. 

**Information Retrieval (IR):**

![information retrieval](https://i.stack.imgur.com/0GsKI.gif)

- Goal of finding relevant documents for user’s needs/queries (eg. Google)
- Often used for text classification of documents
- Can be done without “understanding” syntax and treating documents as “bag of words”

**Information Extraction (IE)**

![information extraction](https://i.stack.imgur.com/0GsKI.gif)

- Goal of extracting specific features from documents
- Focused on linguistic analysis of textual features
- Requires both syntactic and semantic analysis

Today we will be focusing on the first category of these two categories, Information Retrieval, and next week we will dig into Information Extraction.

### What is Information Retrieval?

According to[Wikipedia](https://en.wikipedia.org/wiki/Information_retrieval), Information Retrieval (or IR) was first theorized in the 1940s:

![origins IR]({{site.baseurl}}/assets/images/origins_ir.png)

Information retrieval is strongly tied to the historical development of search engines and the basic goal is to find relevant documents for a user’s query. To do that though requires parsing textual information and finding patterns in the text. 

One way we can do that is with simple counting of words and the frequency they appear across a text. 

In our example, we could start counting words that appear in our email logs. Thinking back to some of our readings, we could try and compare the rate that `humanities computing` appears compared to `digital humanities` that we first explored in the Google Ngram Viewer, demonstrated below.



### Working with Voyant Tools

### Working with AntConc

### Working with MALLET

## Text Analysis Assignment(s)