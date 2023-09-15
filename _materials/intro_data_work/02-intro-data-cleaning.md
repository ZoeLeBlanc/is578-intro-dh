---
title: "Introduction to Working with Data"
permalink: /materials/intro-spreadsheets/02-intro-data
excerpt: "An introduction to creating and working with data."
toc: true
---

So far we have been talking about file formats and trying our hand at creating data, but what about best practices for this work? And what does it mean to work with data?

## A Tale of Two Datasets

This week we read articles that provided datasets. 

First, we can have the data from Barbot, Laure, Frank Fischer, Yoann Moranville, and Ivan Pozdniakov. “Which DH Tools Are Actually Used in Research?,” December 6, 2019. [https://weltliteratur.net/dh-tools-used-in-research/](Barbot, Laure, Frank Fischer, Yoann Moranville, and Ivan Pozdniakov. “Which DH Tools Are Actually Used in Research?,” December 6, 2019. https://weltliteratur.net/dh-tools-used-in-research/) and then the data from Index of DH Conferences [https://dh-abstracts.library.virginia.edu/downloads](https://dh-abstracts.library.virginia.edu/downloads).

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