---
title: "Introduction to Cleaning and Working With Data"
permalink: /materials/intro-spreadsheets/02-intro-data-cleaning
excerpt: "An introduction to cleaning and working with data for DH and LIS."
toc: true
---

<div class="notice--info">⚡️ This lesson has been adapted from Heather Froehlich's A Gentle Introduction To Excel And Spreadsheets For Humanities People <a href="https://hfroehli.ch/2021/06/17/a-gentle-introduction-to-excel-and-spreadsheets-for-humanities-people/">https://hfroehli.ch/2021/06/17/a-gentle-introduction-to-excel-and-spreadsheets-for-humanities-people/</a></div>


So far we have been talking about file formats and trying our hand at creating data, but what about best practices for this work? And what does it mean to work with data in the humanities?

### What is Humanities Data and How Can We Work with It?

As you've read this week, there's no one definition of or way to work with humanities data, especially since the very category of 'humanities' itself is contested and nebulous. One of the key things that you've hopefully learned from our assignment this week is that creating data is a process that requires many interpretative steps and that it can difficult to know how to proceed if you don't have a clear goal in mind.

As Posner writes:

> "It requires some real soul-searching about what we think data actually is and its relationship to reality itself; where is it completely inadequate, and what about the world can be broken into pieces and turned into structured data? I think that’s why digital humanities is so challenging and fun, because you’re always holding in your head this tension between the power of computation and the inadequacy of data to truly represent reality."

While hopefully we have discussed some of the choices everyone made in their dataset creation assignment, I also wanted to share my attempt at creating this dataset.

[![custom dataset]({{site.baseurl}}/assets/images/custom_dataset.png)](https://zoeleblanc.notion.site/All-DH-Tools-Dataset-from-IS578-2e91aff0480e48dfbc3d2adb01795930?pvs=4)
*Click on the image to see my dataset*

As I mentioned in class, when manually cleaning data, I often use Notion (though you can do this work in Google Sheets, Excel, AirTable, etc...). In my example, you can see I've made a few interpretative choices from our original dataset from class:

1. I have renamed all the column names to be lowercase and underscored. This is a common practice in datasets since it is easier for computers to autocomplete and requires less typing, depending on the software you are using.
2. I have changed the description column to contains `True`, `False`, `None` which are values that work better with computers rather than `Yes` or `No`.
3. I have filled in as many of the missing values as I could. But I also created a column called `abstract_original` so that I could keep track of whether a contributor had initially submitted an abstract or if it was one I found. This choice was so that I was not skewing the initial records but still had a way to fill in missing values.
4. I also created a column called `revised_keywords` where I combined our two categorical columns (`Tool Category` and `Area of Use`) and also limited the number of values. This choice is very subjective and I could have made different choices, but I wanted to limit the number of values to make it easier to work with the data. The more options you have, the more complexity you create.
5. Lastly, I used some of the built-in Notion functionality to color some of the values. This makes it easier for me to look at the data, but it is important to note that computers do not understand colors. So if I wanted to use this data in a visualization, I would need to create a new column that would translate the colors into values that computers can understand.

All of these choices are subjective and represent my own interpretation of the data. But they are also choices that I made to make it easier to work with the data down the road. One of the reasons I use Notion is also because this lets me export the data as a Markdown File and CSV, which you can also find in the [GitHub repository](https://github.com/ZoeLeBlanc/is578-intro-dh/tree/gh-pages/public_course_data/dh_tools_data).


### Dataset Foundations

From this experience of creating data, you are starting to learn that creating datasets requires taking `unstructured` data and giving it some type of `structured` format. In other fields, you will often be given data from the outset that is already created but in DH, a lot of the work requires making your own data and thinking about how it should be organized.

A great example of this is the *Shakespeare and Company Project* at Princeton which has digitized lending library cards to build their project:

![annotated card](https://shakespeareandco.princeton.edu/media/images/Card_Annotated.max-964x1051.png)

You can read more about the project here [https://shakespeareandco.princeton.edu](https://shakespeareandco.princeton.edu), but there are some key principles that will help you as you continue to do this work, even if the software you use will differ.


1. Datasets are made up of rows and columns. Each row represents a single record and each column represents a single variable. So for example, a row might be a single book and the columns might be the title, author, and publication date. Or in our case a row might be a single DH tool and the columns might be the name, description, and category.
2. Single values are often called cells. These cells are the intersection of a row and column, and can contain many types of data. Often a rule of thumb is that a cell should contain a single observation or data point, but this is a general rule and not always the case.
3. The first row of a dataset is often called the header row. This row contains the column names and is often used to describe the data in the dataset. Naming columns is an important part of creating a dataset because it helps you and others understand what the data represents.
4. Many spreadsheet software allow you to have multiple sheets (like Google Sheets for example), or you might try to add multiple datasets on one sheet like we did in class last week. Another general rule of thumb is that each sheet should contain a single dataset. This is because it makes it easier to work with the data and to share it with others.
5. Finally, it is important to remember that this is not a text document so it is crucial to work with these softwares in ways the expect. For example, many of these softwares might try to automatically deduce your data from the formatting, so if you have dates you might want to structure it as `YYYY-MM-DD` or if you have numbers you might want to remove any commas or dollar signs. This is because computers do not understand the same things as humans, so we need to make sure that we are structuring our data in a way that computers can understand.

Here's an example from Google Sheets:

![google sheets](https://sheetshelp.com/wp-content/uploads/2021/12/parts-of-a-spreadsheet-1b-1024x516.png)

And you can read more about these foundations here: [https://sheetshelp.com/spreadsheet-parts/](https://sheetshelp.com/spreadsheet-parts/)


### Data Types

Now let's trying working in Google Sheets again with this revised All DH Tools dataset to start understanding some of the foundations of working with data.

[![gsheets dataset]({{site.baseurl}}/assets/images/gsheets_dataset.png)](https://docs.google.com/spreadsheets/d/1gqfnd5GssQ_4g2ELnM_zQ_40Lgg7TwOnehVri0WpeOc/edit?usp=sharing)

Here's an uploaded version of the dataset I created in Notion. You'll notice a few things immediately. First, all the colors are gone as predicted. You'll also see that all the links are automatically rendering as links, and that `experience` is also rendering as `TRUE` and `FALSE` versus `abstract_original` which was a checkbox in Notion that is now rendered as `Yes` or `No` since that was how Notion exported that format.

When working with data it is crucial to understand that there are different types of data.

![data types](https://ucarecdn.com/2bc4eb6c-4c71-4679-8c0b-308b293b8515/)

![additional explantion]({{site.baseurl}}/assets/images/data_types.png)

Using this graph we can see that our data is primarily `categorical` from `tool_name` to `description`, etc... But we also have some `boolean` data in `experience` and `abstract_original`. Boolean is a fancy way of saying `True` or `False`. We also have a `None` value in `abstract_original` which is a way of saying that there is no value in that cell. Explicitly stating that there is no value can be useful so that there's no ambiguity, though most spreadsheet software will automatically assume empty cells contain `None` (which is also called a Null value).

You will also see that my `revised_keywords` column now has commas to separate our keywords. When working with a list of items in a cell, it is good practice to use some type of symbol that can be a `delimiter`. Most software assumes that commas or semi-colons are delimiters, and by having this standard format it will allow you to more easily work with this data.

We can try creating some `derived` `numerical` data from our current dataset through Google Sheets. Derived data is a termed often used to denote any aggregation or transformation of a dataset to create additional data that was not there originally.

One thing we might want to know is how popular these tools are across the class. We can get some help through ChatGPT to find the exact syntax, through using the following prompt:

> I have a Google Sheets dataset with the following columns: tool_name, link_tool, abstract_title, link_dh_abstract, contributor, description, experience, revised_keywords, original_submission, rationale, abstract_original, alternative_link. I want to know how many times each tool was used and save that into a new column called `tool_count`. `tool_name` is in column A and I want `tool_count` to be in column M. There is also 18 rows including the header column. My sheet is also called `All DH Tools Revised`. How can I do this?


And from ChatGPT we learn that:


Given your dataset and the specified columns, here's how you can determine how many times each tool was used and save that into the `tool_count` column:

1. **Column Headers**:
   Assuming you have your headers in row 1, type "tool_count" in cell M1 to label the new column.

2. **Count Formula**:
   In cell M2, right next to the first tool name in column A, you will use the `COUNTIF` function to calculate the number of times that tool appears in the `tool_name` column.

   Enter the following formula in cell M2:
   ```shell
   =COUNTIF(A$2:A$18, A2)
   ```

3. **Drag Down the Formula**:
   After entering the formula in cell M2, you can click on the bottom-right corner of the cell (where there's a little square or "handle") and drag it down to fill cells M2 through M18. This will apply the formula to each row, counting occurrences of the corresponding tool in column A.

4. **Result**:
   Now, column M will contain the count of each tool listed in column A for all rows 2 through 18.

Remember, the absolute reference (`$` in `A$2:A$18`) ensures that as you drag the formula down, it will always count against the entire specified range, whereas the relative reference (`A2`) updates for each row you drag to.

If done correctly, we should get a result that looks like this:

![count column]({{site.baseurl}}/assets/images/count_column.png)

We can also visually examine the popularity of tools by creating a bar chart. Using the graph button in Google Sheets to see the most popular tools:


![graph]({{site.baseurl}}/assets/images/graph_count.png)

### Data Merging and Filtering

Now that we have our own dataset, let's try and work with some other datasets to compare our results. 

First, we can have the data from Barbot, Laure, Frank Fischer, Yoann Moranville, and Ivan Pozdniakov. “Which DH Tools Are Actually Used in Research?,” December 6, 2019. [https://weltliteratur.net/dh-tools-used-in-research/](https://weltliteratur.net/dh-tools-used-in-research/), which should download as `tools-dh-proceedings.csv`. Let's open this up in Google Sheets and try and connect it to our existing dataset to compare the popularity of these tools.

First, we need to import this data into our existing spreadsheet but as a **separate** sheet. Under `File` we can select the import option and then upload our csv file.

![import]({{site.baseurl}}/assets/images/import_csv.png)

Now we should have a sheet called `tools-dh-proceedings` at the bottom of our spreadsheet. Next we can once again ask ChatGPT for help by using the following prompt:

> I have a Google Sheets dataset with two sheets. The first is called `All DH Tools Revised` with the following columns: tool_name, link_tool, abstract_title, link_dh_abstract, contributor, description, experience, revised_keywords, original_submission, rationale, abstract_original, alternative_link, tool_count. The second is called `tools-dh-proceedings` with the following columns: Tool, 2015, 2016, 2017, 2018, 2019. How can I merge these two datasets into a single dataset? The Tool column contains the same information but there are fewer rows in the first dataset than the second. Should I rename the two columns to match?

And we get this answer from ChatGPT:

Yes, renaming the header "Tool" to "tool_name" in the `tools-dh-proceedings` sheet would simplify the merging process a bit, especially when viewing or referencing the data. If you do that, here's a more streamlined approach:

1. **Create a New Sheet**:
   - Add a new sheet by clicking the "+" button at the bottom-left of the Google Sheets interface. Name it something like "Merged Dataset".

2. **Copy the Headers**:
   - Copy the headers from the `All DH Tools Revised` sheet and paste them into the new "Merged Dataset" sheet.
   - After the last column from `All DH Tools Revised`, copy the headers from `2015` to `2019` in the `tools-dh-proceedings` sheet and paste them next to the previously pasted headers in "Merged Dataset".

3. **Transfer the Data from `All DH Tools Revised`**:
   - Copy all the data from the `All DH Tools Revised` sheet (excluding the header row) and paste it into the "Merged Dataset" sheet below the corresponding headers.

4. **Use ARRAYFORMULA with VLOOKUP for the Remaining Columns**:
   - Assuming the data from `All DH Tools Revised` starts in row 2 of the "Merged Dataset" sheet, in the next available column (which corresponds to `2015`), input the following formula in the cell corresponding to row 2:
     ```excel
     =ARRAYFORMULA(IFERROR(VLOOKUP($A2:$A, 'tools-dh-proceedings'!$A:$F, COLUMN(B1), FALSE), ""))
     ```
   - Drag this formula to the right for the years `2016`, `2017`, `2018`, and `2019`. Adjust the `COLUMN(B1)` part to `COLUMN(C1)`, `COLUMN(D1)`, etc., respectively, as you move right.

5. **Explanation**:
   The VLOOKUP function searches for each tool name from the "Merged Dataset" sheet in the `tool_name` column of the `tools-dh-proceedings` sheet. The ARRAYFORMULA allows the VLOOKUP to process multiple rows at once. If a match is found, it fetches the corresponding year's data. If not, it returns an empty string (due to the IFERROR function).

6. **Tidy Up**:
   After merging, verify the data to check for any discrepancies or errors. If you wish, you can replace formulas with static values (by copying the columns and using "Paste Special" > "Paste Values Only") to prevent accidental recalculations or errors if the original data is modified.

Now you should have a more easily managed merged dataset with the data from both sheets based on the "tool_name" headers.

![merged_dataset]({{site.baseurl}}/assets/images/merged_dataset.png)

We can even ask ChatGPT how to alter our formula so that it includes zeros instead of empty cells:

```shell
=ARRAYFORMULA(IF(A2:A18="", "", IFERROR(VLOOKUP($A2:$A18, 'tools-dh-proceedings'!$A:$F, COLUMN(B1), FALSE), 0)))

```

Now there's more we could do with this dataset, like comparing our counts but first let's try also merging this dataset with our Index of DH Abstracts which is available here [https://dh-abstracts.library.virginia.edu/downloads](https://dh-abstracts.library.virginia.edu/downloads).

First, we would need to download the dataset and upload it to our Google Sheet.

*Class Question: How and can we import this data into our existing Google Sheet?*

Now we need to figure out how we can merge these two datasets. What columns are shared between the two?

In our `dh tools` dataset we have two potential candidates: either the `link_dh_abstract` or `abstract_title`. We can try using the `link_dh_abstract` column first, but we will need to clean it up a bit first.

If you notice the `link_dh_abstract` column contains urls that have the following structure `https://dh-abstracts.library.virginia.edu/works/2621` where the number at the end is the unique identifier for each abstract. We can use this to create a new column that only contains the number at the end of the url.

We can once again use ChatGPT to help us with this task. 

*Class Question: How should I write a prompt to create a new column called `work_id` that only contains the number at the end of the url?*

Now this is a bit of a gotcha but because our `dh_conferences_works` is so large we need to filter it down to only the rows that contain the `work_id` we are looking for. We can do this by using the `Filter` functionality in Google Sheets.

![filter_data]({{site.baseurl}}/assets/images/filter_data.png)

Now that we have this filtered data, we can again try and merge it.

*Class Question: How should I write a prompt to merge these two datasets?*

We should end up with something that looks like this:

![merged_data]({{site.baseurl}}/assets/images/merged_data.png)

*Class Question: How could we bring in more columns from DH Abstracts dataset into our DH Tools dataset?*

## Data Cleaning and Merging Assignment

To be posted after class depending on how far we get collectively 😅.



## Additional Resources

- “OpenRefine for Natural History Collection Data.” [https://data-lessons.github.io/OpenRefine-nhcdata-lesson/](https://data-lessons.github.io/OpenRefine-nhcdata-lesson/).
- Miriam Posner's Get Started with OpenRefine [https://github.com/miriamposner/get-started-with-openrefine/blob/master/get-started-with-openrefine.md](https://github.com/miriamposner/get-started-with-openrefine/blob/master/get-started-with-openrefine.md) (also available as a video https://share.descript.com/view/5Hx7a2XNWbW?t=1.470981&autoplay=1)