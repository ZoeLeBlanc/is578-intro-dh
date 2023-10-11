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

From these two charts we can start to see the relative popularity of Voyant Tools for example that is very high in the Index of DH Abstracts and our Class dataset, but not in the dataset from the Blog Post. This finding is surprising since the blog post analyzes data from "the proceedings of the largest and broadest event series in the Digital Humanities, ADHO’s annual DH conferences" which should correspond to the Index of DH Abstracts.

To dig into these differences a bit more, I once again transposed the original data, this time by `data_origin` in OpenRefine to create the following dataset:

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

To create the initial dataset, I used the following code:

```python


### Working with Voyant Tools

### Working with AntConc

### Working with MALLET

## Text Analysis Assignment(s)