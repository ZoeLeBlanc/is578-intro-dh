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

All of these choices are subjective and represent my own interpretation of the data. But they are also choices that I made to make it easier to work with the data down the road. One of the reasons I use Notion is also because this let's me export the data as a Markdown File and CSV, which you can also find in the [GitHub repository](


### Dataset Foundations

From this experience of creating data, you are starting to learn that datasets are highly structured ways to work with and manipulate data.

While the particular software you use will influence you experience, there are some key things to know about datasets:

1. Datasets are made up of rows and columns. Each row represents a single record and each column represents a single variable. So for example, a row might be a single book and the columns might be the title, author, and publication date. Or in our case a row might be a single DH tool and the columns might be the name, description, and category.
2. Single values are often called cells. These cells are the intersection of a row and column, and can contain many types of data. Often a rule of thumb is that a cell should contain a single observation or data point, but this is a general rule and not always the case.
3. The first row of a dataset is often called the header row. This row contains the column names and is often used to describe the data in the dataset. Naming columns is an important part of creating a dataset because it helps you and others understand what the data represents.
4. Many spreadsheet software allow you to have multiple sheets (like Google Sheets for example), or you might try to add multiple datasets on one sheet like we did in class last week. Another general rule of thumb is that each sheet should contain a single dataset. This is because it makes it easier to work with the data and to share it with others.
5. Finally, it is important to remember that this is not a text document so it is crucial to work with these softwares in ways the expect. For example, many of these softwares might try to automatically deduce your data from the formatting, so if you have dates you might want to structure it as `YYYY-MM-DD` or if you have numbers you might want to remove any commas or dollar signs. This is because computers do not understand the same things as humans, so we need to make sure that we are structuring our data in ways that computers can understand.

Here's an example from Google Sheets:

![google sheets](https://sheetshelp.com/wp-content/uploads/2021/12/parts-of-a-spreadsheet-1b-1024x516.png)

And you can read more about these foundations here: [https://sheetshelp.com/spreadsheet-parts/](https://sheetshelp.com/spreadsheet-parts/)


### Data Types

Now let's trying working in Google Sheets again with this revised All DH Tools dataset to start understanding some of the foundations of working with data.

[![gsheets dataset]({{site.baseurl}}/assets/images/gsheets_dataset.png)](https://docs.google.com/spreadsheets/d/1gqfnd5GssQ_4g2ELnM_zQ_40Lgg7TwOnehVri0WpeOc/edit?usp=sharing)

Here's an uploaded version of the dataset I created in Notion. You'll notice a few things immediately. First, all the colors are gone as predicted. You'll also see that all the links are automatically rendering as links, and that `experience` is also rendering as `TRUE` and `FALSE` versus `abstract_original` which was a checkbox in Notion that is now rendered as `Yes` or `No` since that was how Notion exported that format.

When working with data it is crucial to understand that there are different types of data.

![data types](https://ucarecdn.com/2bc4eb6c-4c71-4679-8c0b-308b293b8515/)

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

First, we can have the data from Barbot, Laure, Frank Fischer, Yoann Moranville, and Ivan Pozdniakov. “Which DH Tools Are Actually Used in Research?,” December 6, 2019. [https://weltliteratur.net/dh-tools-used-in-research/](https://weltliteratur.net/dh-tools-used-in-research/), which should download as 


## A Tale of Two Datasets

This week we read articles that provided datasets. 

F and then the data from Index of DH Conferences [https://dh-abstracts.library.virginia.edu/downloads](https://dh-abstracts.library.virginia.edu/downloads).

Let's explore these datasets together and discuss some of their features.

### Dataset Structure

As you've started to see structuring datasets requires a number of choices and that there is not one way to create a dataset. 

Let's dig into some of the features of these datasets:

1. How have they each documented and structured their datasets? How are they similar and different?
2. Do we notice any unique values? Why do unique values matter even?
3. How have these datasets created their column names? What are some of the differences between the column names?
4. How have they organized their time values? 

Based on these examples, what might we want to change about our current dataset structure?

## Transforming Data

Let's start working with our custom and the provided DH Tools dataset more in-depth.

First, how could we transform our current custom DH Tool dataset that adopts some of these practices? Could we add in a structure to allow for duplicate entries for tools?

Second, how could we combine our custom dataset with the DH Tools dataset from the article? What are some of the challenges we might face?

To do all of this we need to start doing something often called data cleaning.

## Data Cleaning

We will be discussing this more next week but data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect, incomplete, irrelevant, duplicated, or improperly formatted. It is an important part of working with data because it ensures that your data is accurate and consistent. It also helps you avoid errors in your analysis and makes it easier to share your data with others.

Let's upload the existing DH Tools dataset into Google Sheets and see if we can start transforming it to work with our custom dataset.

Let's try and complete the following tasks:

1. We want to join our dataset together. How could we do this?
2. We want to compare the popularity of tools over time. How could we do this?

### Data Manipulation with Google Sheets (Proceed with Caution)

I am assuming that most of you have used Google Sheets before, but if not that's ok too.

First, we need to determine what are shared values between our two datasets. Is there a column we could join on? Maybe one that contains DH tool names?

Now we could manually add in the data from the DH Tools dataset into our custom dataset, but that would take a long time. Instead, we can use a function called `VLOOKUP` to do this for us.

1. First, we need to create a new column in our custom dataset called `Tool`
2. Now let's use ChatGPT to help us solve this problem 😅!

Here's an example of a solution it provided:

```
To merge two Google Sheets that share a primary key but have different columns and numbers of rows, you can use the `VLOOKUP` function in Google Sheets. Here's how you can do it:

1. **Open Google Sheets**: Open both Google Sheets that you want to merge.

2. **Identify Primary Key**: Identify the column that contains the primary key in both sheets. This will be the column that you use to merge the data.

3. **Use `VLOOKUP`**: In one of the sheets, use the `VLOOKUP` function to pull the data from the other sheet based on the primary key. 

The `VLOOKUP` function in Google Sheets searches a range of cells in one column, and returns the corresponding value from another column in the same row. The syntax for the `VLOOKUP` function is:

```
VLOOKUP(search_key, range, index, [is_sorted])
```

- `search_key`: The value that the function needs to find in the first column of the range of cells you specified.
- `range`: The range of cells to search. This range needs to include at least two columns.
- `index`: The column index of the value to be returned. The first column in the range is numbered 1.
- `[is_sorted]`: A logical value that indicates whether the first column in the range is sorted. If `TRUE`, `VLOOKUP` will return the nearest match. If `FALSE`, `VLOOKUP` will only return an exact match. Usually, you will set this to `FALSE`.

For example, if you have two sheets, "Sheet1" and "Sheet2", and you want to merge them based on a primary key in column A, and you want to pull the data from column B in "Sheet2" into "Sheet1", you would enter the following formula in "Sheet1":

```
=VLOOKUP(A2, 'Sheet2'!A:B, 2, FALSE)
```

This formula will search for the value in `A2` in the first column of the range `A:B` in "Sheet2", and return the corresponding value from the second column of the range.

4. **Drag the Formula**: Drag the formula down to apply it to all rows in the sheet.

5. **Repeat for Other Columns**: Repeat steps 3 and 4 for all other columns that you want to merge.

6. **Check for Errors**: After you have merged all columns, carefully check for errors. The `VLOOKUP` function will return `#N/A` if it can't find the search_key, so make sure to check for this error.

7. **Finalize the Data**: If everything looks correct, you can copy the merged data and paste it as values to remove the formulas. This is an optional step, but it can help to reduce the file size and make the sheet load faster.
```

Let's try and work through this solution together, this may or may not work!

### Data Manipulation with Open Refine

While Google Sheets is great, it has a number of limitations. However, there are many tools for working with data, and one of the most popular is Open Refine.

Open Refine is a free and open source tool that allows you to clean and transform data. It is a powerful tool that can help you with a number of tasks, but it is not a magic bullet. It is important to understand that data cleaning is a process and that it is not always possible to clean data perfectly. Also how you want your data structured often depends on your goals.

Let's follow this tutorial by Miriam Posner [https://github.com/miriamposner/get-started-with-openrefine/](https://github.com/miriamposner/get-started-with-openrefine/)

1. First, we would need to download OpenRefine and open it up.

![open refine home](https://github.com/miriamposner/get-started-with-openrefine/raw/master/images/get-started-with-openrefine/open-openrefine.png)

YOu'll notice that there's a weird set of numbers or something called localhost. This is the address of your computer. You can think of it as a phone number for your computer. It is how OpenRefine knows where to find your data.

2. Now let's import the existing DH Tool dataset into OpenRefine.

![open project](https://github.com/miriamposner/get-started-with-openrefine/raw/master/images/get-started-with-openrefine/open-your-data-file.png)

To do this we need to create a new project and then select the file we want to import.

3. Now we can start cleaning our data.

A few things to try. Let's try and make it so that we can not have our years be columns but instead be rows. How could we do this?

![transposing](https://tavareshugo.github.io/r-intro-tidyverse-gapminder/fig/07-data_shapes.png)

In OpenRefine, we can do a complex data transformation called transposing. This is a way to turn columns into rows and rows into columns. It is a powerful tool that can help you with a number of tasks, but it is not a magic bullet. It is important to understand that data cleaning is a process and that it is not always possible to clean data perfectly. Also how you want your data structured often depends on your goals. Let's use the OpenRefine documentation to help us with this task [https://openrefine.org/docs/manual/transposing](https://openrefine.org/docs/manual/transposing).


### Dataset Documentation

Increasingly, datasets you find will have some sort of documentation, sometimes that is a README file or maybe datasheet. This documentation is important because it tells you how the data was created, what it contains, and how to use it.

What are some of the differences between the documentation of these datasets? What does a required field mean?

Let's create documentation for our dataset in this Google Drive. Then let's upload all of this to GitHub.


## Data Cleaning and Discovery Assignment

Depending on how far we got today, your homework for this week is to complete the following:

1. Finish cleaning and documenting your custom DH Tools dataset.
2. Upload that dataset to GitHub and link in the relevant discussion (link forthcoming).
3. Find a DH dataset, download it, and upload a sample to GitHUb, sharing in the relevant discussion (link forthcoming).

### Advanced Assignment (May do together next week TBD)

So far we have been using the Index of DH Conferences data as an example of how to organize datasets, but now let's start trying it out on your own.

1. Download OpenRefine [https://openrefine.org/](https://openrefine.org/) and download the `Simple CSV` from the Index of DH Conferences [https://dh-abstracts.library.virginia.edu/downloads](https://dh-abstracts.library.virginia.edu/downloads).
2. Open OpenRefine and create a new project with downloaded CSV file.
3. Try and turn the `conference_year` column into a date format. 
4. Try and create a timeline facet of the `conference_year` column. 
5. Try creating a text facet to search for one of the DH Tools we listed in the `full_text` column.
6. Now we have a subset of our data and are almost ready to export. But the final piece is that we want to have unique values in each cell, so let's use the split cells function.
7. Finally let's export our subset of data and upload to GitHub.


## Additional Resources

- “Open Refine for Natural History Collection Data.” [https://data-lessons.github.io/OpenRefine-nhcdata-lesson/](https://data-lessons.github.io/OpenRefine-nhcdata-lesson/).
- Miriam Posner's Get Started with Open Refine [https://github.com/miriamposner/get-started-with-openrefine/blob/master/get-started-with-openrefine.md](https://github.com/miriamposner/get-started-with-openrefine/blob/master/get-started-with-openrefine.md) (also available as a video https://share.descript.com/view/5Hx7a2XNWbW?t=1.470981&autoplay=1)