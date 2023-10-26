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

Now if we upload the topic network to Palladio we see the following:

<figure>
    <a href="{{site.baseurl}}/assets/images/palladio_topic_network.png"><img src="{{site.baseurl}}/assets/images/palladio_topic_network.png"></a>
</figure>

This is pretty overwhelming so we might also try faceting by tools, like `Palladio` and `Voyant`, which starts to show us which topics overlap between these tools:

<figure>
    <a href="{{site.baseurl}}/assets/images/palladio_topic_network_facet.png"><img src="{{site.baseurl}}/assets/images/palladio_topic_network_facet.png"></a>
</figure>

Now if we try to do the same with our keywords you may find that the browser crashes because it is so much data (over 3000 rows). One alternative is to try something like Gephi-lite.

Now normal Gephi would let us just upload our spreadsheet but Gephi-lite requires an `gexf` file. I'm generating these in this code notebook, but you could also download Gephi and generate them locally from the spreadsheets that way.

I've also uploaded the `gexf` files to GitHub so now we can use them from GitHub directly in Gephi-Lite:

<figure>
    <a href="{{site.baseurl}}/assets/images/gephi_lite_upload.png"><img src="{{site.baseurl}}/assets/images/gephi_lite_upload.png"></a>
</figure>

This gives us an initial graph:

<figure>
    <a href="{{site.baseurl}}/assets/images/gephi_lite_graph.png"><img src="{{site.baseurl}}/assets/images/gephi_lite_graph.png"></a>
</figure>

That we can then use layout algorithms like force layout to visulize our network:

<figure>
    <a href="{{site.baseurl}}/assets/images/gephi_lite_force.png"><img src="{{site.baseurl}}/assets/images/gephi_lite_force.png"></a>
</figure>

And then we can use statistics to color our network again:

<figure>
    <a href="{{site.baseurl}}/assets/images/gephi_lite_statistics.png"><img src="{{site.baseurl}}/assets/images/gephi_lite_statistics.png"></a>
</figure>

The result is a graph that shows us that certain keywords like `user_studies` connects certain tools:

<figure>
    <a href="{{site.baseurl}}/assets/images/user_studies_graph.png"><img src="{{site.baseurl}}/assets/images/user_studies_graph.png"></a>
</figure>

Compared to `data_exploration`:

<figure>
    <a href="{{site.baseurl}}/assets/images/data_exploration_graph.png"><img src="{{site.baseurl}}/assets/images/data_exploration_graph.png"></a>
</figure>

And we can even search for nodes like `mapping`, which is shared across multiple tools:

<figure>
    <a href="{{site.baseurl}}/assets/images/mapping_graph.png"><img src="{{site.baseurl}}/assets/images/mapping_graph.png"></a>
</figure>

There's more explorations we could do, and we could still even project this graph for example but hopefully you are starting to see the potential for network analysis.

## Mapping in DH

Now that we have discussed some of the mapping projects from this week, as well as the broader question of why and how we map in Digital Humanities, we can start to explore ways to map our own data.

You'll notice that I've included a `location` column in these datasets of some of the networked datasets. Let's try using the `projected_weighted_tools_dates_location_edges.csv`.

We can start by uploading our data to Palladio and seeing what we can do:

<figure>
    <a href="{{site.baseurl}}/assets/images/empty_map.png"><img src="{{site.baseurl}}/assets/images/empty_map.png"></a>
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

There are a number of different geocoding services, but we can easily use one through Google Sheets with their extension functionality. Today I'm using the [Geocoding by Awesome Table](https://workspace.google.com/marketplace/app/geocode_by_awesome_table/904124517349) extension.

![gecoder](https://lh3.googleusercontent.com/sKatWxvPUi8V3Y2QKur7jtwybVwncilRmkynaxhyYJiv-lQGQLJml5gvmJHuBvRWTMyavEBF=w1280-h800)

To try this out, I've uploaded our dataset to Google sheets and have installed this extension. The first thing though that I'll try doing is creating a unique list of place names so that I don't have to geocode the same place multiple times.

<figure>
    <a href="{{site.baseurl}}/assets/images/unique_places.png"><img src="{{site.baseurl}}/assets/images/unique_places.png"></a>
</figure>

Now I can select the `Geocode` option from the `Add-ons` menu:

<figure>
    <a href="{{site.baseurl}}/assets/images/geocode_places.png"><img src="{{site.baseurl}}/assets/images/geocode_places.png"></a>
</figure>

Eyeballing the results, they look fairly accurate but geo-coding as we saw in one of our readings is far from exact science and can often result in empty or incorrect values.

If I'm happy with the results, then I just need to merge the two datasets back together:

<figure>
    <a href="{{site.baseurl}}/assets/images/formula_latitude.png"><img src="{{site.baseurl}}/assets/images/formula_latitude.png"></a>
</figure>

Now I could download my data at this point, but Palladio requires geographic data as coordinates, so next I'll combine those two columns into a new one:

<figure>
    <a href="{{site.baseurl}}/assets/images/coordinates_sheets.png"><img src="{{site.baseurl}}/assets/images/coordinates_sheets.png"></a>
</figure>

Now when working with Palladio, I can create the following map:

<figure>
    <a href="{{site.baseurl}}/assets/images/palladio_map.png"><img src="{{site.baseurl}}/assets/images/palladio_map.png"></a>
</figure>

This looks great (though perhaps counting tools to conferences is a bit complicated) but the one downside with Palladio is that I can't easily create an interactive map.

So, I might try a tool like [Kepler.gl](https://kepler.gl/), which is a free open-source geospatial analysis tool for large-scale data sets. The tool is produced by Uber, so it is designed to work with large datasets.

Similar to Palladio we can just upload our data:

![upload kepler](https://d1a3f4spazzrp4.cloudfront.net/kepler.gl/documentation/image42.png)

And we should get a map that looks like the following:

<figure>
    <a href="{{site.baseurl}}/assets/images/initial_kepler_map.png"><img src="{{site.baseurl}}/assets/images/initial_kepler_map.png"></a>
</figure>

We can start to tweak, but if you go the filter functionality you'll notice that we aren't seeing the option of creating a timeline even though Kepler is telling us we have `date` column:

<figure>
    <a href="{{site.baseurl}}/assets/images/kepler_dates.png"><img src="{{site.baseurl}}/assets/images/kepler_dates.png"></a>
</figure>

The issue is that Kepler expects a `datetime` column, so back in google sheets we can update our dataset to do the following:

<figure>
    <a href="{{site.baseurl}}/assets/images/corrected_date.png"><img src="{{site.baseurl}}/assets/images/corrected_date.png"></a>
</figure>

And now if we re-upload our data to Kepler we should see the following:

<figure>
    <a href="{{site.baseurl}}/assets/images/finalized_kepler_map.png"><img src="{{site.baseurl}}/assets/images/finalized_kepler_map.png"></a>
</figure>

Which we can also embed here:

<figure>

<iframe src="https://kepler.gl/#/demo?mapUrl=https://gist.githubusercontent.com/ZoeLeBlanc/32daed91a4eb0038640891b95e78029c/raw/580a8252b3757387e0fc5ae309e88a3c921f9c06/kepler.gl.json" style="border:0px #ffffff none;" name="myiFrame" scrolling="no" frameborder="1" marginheight="0px" marginwidth="0px" height="900px" width="1200px" allowfullscreen=""></iframe>

</figure>

I'll explain more of how I embedded this map next week when we starting talking about websites, but you can see how with filtering and the timeline we can start to explore our data. The big question though that we have yet to discuss is how accurate my geocoding is and how I might improve it. 

## (In Class/At Home) Mapping Assignment

So far we have been using place names already provided to us, but from our readings we also know that we can also extract place names from text to geocdoe and map them.

We've seen an example this before in Voyant Tools:

<figure>
    <!--	Exported from Voyant Tools (voyant-tools.org).
The iframe src attribute below uses a relative protocol to better function with both
http and https sites, but if you're embedding this into a local web page (file protocol)
you should add an explicit protocol (https if you're using voyant-tools.org, otherwise
it depends on this server.
Feel free to change the height and width values or other styling below: -->
<iframe style='width: 891px; height: 487px;' src='https://voyant-tools.org/tool/DreamScape/?corpus=3380d938601f8ebdf055fc572adc1b61'></iframe>
</figure>

Depending on the time left in class, your assignment is to use any textual data (whether your own or abstracts from the *Index of DH Conferences* or novels), and try to creating a dataset of place names to map. You can use any spreadsheet software and any geocoding service, as well as any mapping tool. But the goal is to have at least 10 locations and a map to share with the class. 

Some things to consider include:
- What would you define as a place name? Is that the same as a geographic location? 
- Could you use something like Google Sheets to automate the process of geocoding? Or even the process of locating place names?
- Are your locations points or larger polygons? How might you represent that in your map?
- Are you interested in story mapping or more aggregate views?

Once completed, you should upload a screenshot of your map and share your dataset in this GitHub discussion forum [https://github.com/ZoeLeBlanc/is578-intro-dh/discussions/8].(https://github.com/ZoeLeBlanc/is578-intro-dh/discussions/8).

## Resources 

- Miriam Posner's Mapping Resources [https://miriamposner.com/classes/dh201w23/tutorials-guides/mapping/mapping-resources/](https://miriamposner.com/classes/dh201w23/tutorials-guides/mapping/mapping-resources/) and recommended mapping tools [https://miriamposner.com/classes/dh101f17/tutorials-guides/mapping/recommended-mapping-tools/](https://miriamposner.com/classes/dh101f17/tutorials-guides/mapping/recommended-mapping-tools/)
- Stephen Robertson's Teaching Digital Mapping with kepler.gl [https://drstephenrobertson.com/blog-post/teaching-digital-mapping-with-kepler-gl/](https://drstephenrobertson.com/blog-post/teaching-digital-mapping-with-kepler-gl/)



