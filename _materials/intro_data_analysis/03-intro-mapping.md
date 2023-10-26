---
title: "Introduction to Mapping"
permalink: /materials/intro-data-analysis/03-intro-mapping
excerpt: "An introduction to mapping for the humanities."
toc: true
---

## Network Analysis Solutions

So from our assignment last week, there was a number of different datasets and tools to work with. I'm going to focus on showing how we might create networked data from our DH conference + tools data, but happy to answer any questions about the other datasets.

### Networking DH Conference + Tools Data

There's a number of potential networks we might create from our original Index of DH Conferences Data or from our combined tool counts and conference data.

One option is simply take our `updated_all_tool_counts.csv`, which has the following columns:

`tool_name`,`tool_counts`,`data_origin`,`year`

Using the tool `Palladio` we can upload and see if we can generate some initial results:

<figure>
    <a href="{{site.baseurl}}/assets/images/palladio_upload.png"><img src="{{site.baseurl}}/assets/images/palladio_upload.png"></a>
    <figcaption>Drag and dropping our data</figcaption>
</figure>

Once we've uploaded our data, we see the following interface:

<figure>
    <a href="{{site.baseurl}}/assets/images/palladio_interface.png"><img src="{{site.baseurl}}/assets/images/palladio_interface.png"></a>
</figure>

Notice the red dot. That's telling us that Palladio has some concerns about our data, we can click on it and verify for Palladio that the data is correct:

<figure>
    <a href="{{site.baseurl}}/assets/images/palladio_verify.png"><img src="{{site.baseurl}}/assets/images/palladio_verify.png"></a>
    <figcaption>Verifying our data</figcaption>
</figure>

Now we can start generating our network graph. I'm deciding to explore `tool_name` to `data_origin`:

<figure>
    <a href="{{site.baseurl}}/assets/images/palladio_network.png"><img src="{{site.baseurl}}/assets/images/palladio_network.png"></a>
    <figcaption>Network graph of tools and data origins</figcaption>
</figure>

Now we can see that certain tools connect our three datasets, but others are outliers. We can also explore this over time with the timeline facet:

<figure>
    <a href="{{site.baseurl}}/assets/images/palladio_timeline.png"><img src="{{site.baseurl}}/assets/images/palladio_timeline.png"></a>
    <figcaption>Network graph of tools and data origins over time</figcaption>
</figure>

This shows us the subset of data for all three data_origins. We can also start to explore the metrics between these datasets:

<figure>
    <a href="{{site.baseurl}}/assets/images/palladio_metrics.png"><img src="{{site.baseurl}}/assets/images/palladio_metrics.png"></a>
    <figcaption>Network graph of tools and data origins over time with metrics</figcaption>
</figure>

You'll notice we are getting an error about trying to run metrics on a `bipartite network` rather than a `unipartite network`. These types of networks were discussed in last week's readings. In most network analysis tools, they assume you want to work with `unipartite` rather than `bipartite` data. So we need to figure out how to convert our data to `unipartite` data.

In this case we might want to collapse `data_origin` as an edge between `tool_name`. 

So instead of the following data structure:

|tool_name|tool_counts|data_origin|year|
|---|---|---|---|
|Drupal|1.0|class_popularity|2023|
|Drupal|100.0|conference_popularity|2000|


We want to create the following data structure:

|source|target|weight|
|---|---|---|
|Drupal|Drupal|1.0|

Projecting is difficult to do in Google Sheets or Excel, so often this is where people either manually annotate their data or using programming.

For the sake of time, I'm using programming but I'm happy to show how to do this manually. You can find the code in the following [Colab notebook](https://colab.research.google.com/drive/1cMABrwzWv8jkpQIQfy7ny5BBCHkPGBkM?authuser=1#scrollTo=5DiHZaQWCEVt&line=1&uniqifier=1) if you are curious.

Once we've created our new data structure, we can upload it to Palladio and see the following:

<figure>
    <a href="{{site.baseurl}}/assets/images/palladio_projected_graph.png"><img src="{{site.baseurl}}/assets/images/palladio_projected_graph.png"></a>
</figure>

This now accurately shows our data but isn't that meaningful. We might try faceting to one tool like Voyant:

<figure>
    <a href="{{site.baseurl}}/assets/images/palladio_voyant.png"><img src="{{site.baseurl}}/assets/images/palladio_voyant.png"></a>
</figure>

But again this just shows us our connections. So instead, we might try a different tool like Network Navigator.

Now if we upload our data to Network Navigator we need to be careful to change the column names to `source` and `target`:

<figure>
    <a href="{{site.baseurl}}/assets/images/network_navigator_upload.png"><img src="{{site.baseurl}}/assets/images/network_navigator_upload.png"></a>
</figure>

Now we can see a similar force layout graph, but if we select adjacency matrix we can see the following:

<figure>
    <a href="{{site.baseurl}}/assets/images/network_navigator_adjacency.png"><img src="{{site.baseurl}}/assets/images/network_navigator_adjacency.png"></a>
</figure>

This is starting to help us see the overlap between tools in our dataset. We can even rerun our code to filter out `TEI` since it is so overwhelming and regenerate this graph:

<figure>
    <a href="{{site.baseurl}}/assets/images/network_navigator_adjacency_filtered.png"><img src="{{site.baseurl}}/assets/images/network_navigator_adjacency_filtered.png"></a>
</figure>

Now we can for example see that `Twitter` and `Python` are likely to overlap at conferences, whereas `Palladio` is less likely to overlap with those two tools. 


These examples are a bit contrived, but hopefully they give you a sense of how you might start to explore your own data.

A less contrived question might be how do we explore the relationship between tools and conferences, or even keywords and topics to conferences or tools.

Now we can split our keywords and topics using OpenRefine and then merge our datasets together:

<figure>
    <a href="{{site.baseurl}}/assets/images/openrefine_split.png"><img src="{{site.baseurl}}/assets/images/openrefine_split.png"></a>
</figure>

But for time, I'm once again going to use some code to generate our data (you can find it in the same notebook if you are curious). The result is the following datasets:

- `bipartite_weighted_keyword_tool_edges.csv`, which as the following structure:

| Date | Location | Source | Target | Weight | 
| --- | --- | --- | --- | --- | 
| 1996-01-01 | Bergen, Norway | TEI | Japanese classical text | 2 | 
| 1996-01-01 | Bergen, Norway | TEI | archaeology | 1 | 

- `bipartite_weighted_topic_tool_edges.csv`, which as the following structure:

| Date | Location | Source | Target | Weight |
| --- | --- | --- | --- | --- |
| 2013-01-01 | Lincoln, Nebraska, United States | GLAM: galleries, libraries, archives, museums | Drupal | 2 |
| 2013-01-01 | Lincoln, Nebraska, United States | GLAM: galleries, libraries, archives, museums | Google Books | 1 |






## Mapping in DH

Now that we have discussed some of the mapping projects from this week, as well as the broader question of why and how we map in Digital Humanities, we can start to explore ways to map our own data.

You'll notice that I've included a `location` column in these datasets of some of the networked datasets. This is because I wanted to show how we might start to map our data.

We can start by uploading our data to Palladio and seeing what we can do:

<figure>
    <a href="{{site.baseurl}}/assets/images/palladio_location.png"><img src="{{site.baseurl}}/assets/images/palladio_location.png"></a>
</figure>

You'll notice that our map contains no data. That's because our `location` column though containing the locations of columns is not actually geocoded.

### Geocoding Location Data

Often in DH, scholars will want to create a map from some type of data but struggle to understand that places mentioned in texts or even spreadsheets are not actually geographic locations.

To transform that type of data, we need to do something called geocoding. 

Geocoding is the process of converting addresses (like "1600 Amphitheatre Parkway, Mountain View, CA") into geographic coordinates (like latitude 37.423021 and longitude -122.083739), which you can use to place markers on a map, or position the map. 

Here's a step-by-step breakdown of how geocoding typically works:

1. **Input Data**: The process begins with an address or place name, which can come from various sources such as a spreadsheet, database, or text.

2. **Query**: This input data is then sent as a query to a geocoding service.

3. **Processing**: The geocoding service processes this query by searching for a match in its vast database of addresses and geographic coordinates.

4. **Output**: Once a match is found, the service returns the precise latitude and longitude of the address or place name.



---

I hope this helps complete your lesson on geocoding! If you need further information or examples, please let me know.

### Extracting Place Data from Text

We've seen an example of geocoding before in Voyant Tools:

<figure>
    <!--	Exported from Voyant Tools (voyant-tools.org).
The iframe src attribute below uses a relative protocol to better function with both
http and https sites, but if you're embedding this into a local web page (file protocol)
you should add an explicit protocol (https if you're using voyant-tools.org, otherwise
it depends on this server.
Feel free to change the height and width values or other styling below: -->
<iframe style='width: 891px; height: 487px;' src='https://voyant-tools.org/tool/DreamScape/?corpus=3380d938601f8ebdf055fc572adc1b61'></iframe>
</figure>

## Mapping Assignment(s)

1. Curated Mapping: Manually Generating GeoSpatial Data

Using either some of our *Index of DH Conferences* data or your own, 
   
2. Computationally Mapping: Extracting and Mapping Named Entities

3. Mapping DH: Investigating Maps in DH Projects
