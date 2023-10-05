---
title: "Introduction to Data Visualization"
permalink: /materials/intro-visualizing-data/01-intro-data-visualization
excerpt: "An introduction to data visualization and some more advanced data transformations."
toc: true
---

So far we have focused on cleaning and merging data, but a big question has been for what purpose. In this lesson we will start to explore how we can visualize our data to help us better understand it. We will also start to explore some more advanced data transformations that will help us visualize our data.

## Final Merging of Data
*Toggle to See My Solution*
{% capture toggle_content %}

Where we left from last lesson was having to complete a final merge of our two datasets:

- [DH Tools dataset](https://docs.google.com/spreadsheets/d/1ctHUflQQ4vl19A2y8-PnIFe0PVJe4No0wYNCkpi8wkY/edit?usp=sharing)
- [Index of DH Abstracts](https://drive.google.com/file/d/1dXiuQSBzgQQsHEHZmQ4Nfi6m6Cs5yU-6/view?usp=sharing)

I outlined many of the steps in the assignment description, but let's go through them one-by-one.

1. Importing the data
   
First, we need to add our data to our spreadsheet. I did the normal import spreadsheet, but you could directly import from a different Google Sheets as well.

![import_data_into_sheets]({{site.baseurl}}/assets/images/import_data_into_sheets
.png)

2. Resizing and inspecting the data
   
Next we should see a new sheet at the bottom of our sheets, which we can name `index-of-dh-abstracts` if isn't already named that. We also will see that the size of text in each cell is large and makes it difficult to inspect the data.

![original_large_data]({{site.baseurl}}/assets/images/original_large_data.png)

To get around that way can select all the rows with data, press shift, and then use the cursor on the final row to resize them.

![resized_rows]({{site.baseurl}}/assets/images/resized_rows.png)

3. Find shared columns

Between both our datasets, we can see that we have the `work_id` column in common. This is the column we will use to merge our datasets, even if our datasets are differing sizes.
   
4. Merging the datasets into a new sheet

Finally, we can now start merging! 

- First, we need to create a new sheet in our spreadsheet. We can do this by clicking the `+` button at the bottom of the spreadsheet. We can name this sheet `Final Merged Dataset`.

- Second, we need to import our `Merged Dataset` into this dataset (though you could do the inverse if you choose and import `index-of-dh-abstracts` first).

We can either do this manually or use the `ARRAYFORMULA` function:

```shell
=ARRAYFORMULA('Merged Dataset'!A1:S18)
```

Regardless of how we do import the data, we should now see one of our datasets in the sheet. So the final goal is to merge in the other dataset into this sheet. We can do this once again using a formula, and either work from scratch or ask ChatGPT for help.

Some of our previous examples of forumulas for merging include:

- This code for merging two datasets with a shared column:

 ```shell
    =ARRAYFORMULA(IF(A2:A239="", "", IFERROR(VLOOKUP(A2:A239, {'All DH Tools Revised'!A2:A18, 'All DH Tools Revised'!B2:M18}, COLUMN(B1)+1, FALSE), "")))
```

- This code for merging two datasets with a shared column and autocompleting the rest of the columns:


```shell
=ARRAYFORMULA(
   IF(A2:A239="", "", 
      IFERROR(VLOOKUP(A2:A239, 'All DH Tools Revised'!A2:M18, SEQUENCE(1, 12, 2), FALSE), "")
   )
)
```

So our code might look like the following since we have `A1:S18` in `Final Merged Dataset` and `A1:W17` in `index-of-dh-abstracts`:

```shell
=ARRAYFORMULA(
   IF(A2:A18="", "", 
      IFERROR(VLOOKUP(A2:A18, 'index-of-dh-abstracts'!A2:W17, SEQUENCE(1, 23, 2), FALSE), "")
   )
)
```

This doesn't quite work though since we aren't searching for values in our `A` column in `Final Merged Dataset` since `work_id` in that dataset is in column `S`. 

So we need to change our formula to the following:

```shell
=ARRAYFORMULA(
   IF(S2:S="", "", 
      IFERROR(VLOOKUP(S2:S, 'index-of-dh-abstracts'!A2:W17, SEQUENCE(1, 23), FALSE), "")
   )
)
```

If we input this formula we'll see that we get the correct values for the rows but are missing the columns. 

We can ask ChatGPT for help to fix the issue (toggle for answer):

{% capture toggle_prompt %}

Prompt: 

> I have two Google Sheets that I would like to merge. The first is called `Merged Dataset` and has a range of `A1:S18` and the second is called `index-of-dh-abstracts` and has a range of `A1:W17`. Both datasets contain a column called `work_id`, which is in column `S` in `Merged Dataset` and is in column `A` in  `index-of-dh-abstracts`. I want to merge these two into a new sheet called `Final Merged Dataset` and also both these sheets are already in the same Google Sheet as individual sheets. Help me complete this task

ChatGPT Response:

Merging the two Google Sheets based on a common column can be achieved using the `VLOOKUP` function or the `QUERY` function in Google Sheets. Here's a step-by-step guide to merge the two sheets into a new sheet called `Final Merged Dataset`:

1. **Create the New Sheet**:
   - Open your Google Sheet document.
   - At the bottom, click on the '+' icon to add a new sheet.
   - Rename the new sheet to `Final Merged Dataset`.

2. **Copy the Data from `Merged Dataset`**:
   - Go to the `Merged Dataset` sheet.
   - Select the range `A1:S18` and copy it.
   - Go to `Final Merged Dataset` and paste the data starting from cell `A1`.

3. **Use VLOOKUP to Fetch Data from `index-of-dh-abstracts`**:
   
   In this step, you'll retrieve the additional columns from the `index-of-dh-abstracts` sheet using the `VLOOKUP` function.
   
   - In the `Final Merged Dataset` sheet, go to cell `T1`.
   - This is where you'll start to pull in data from the `index-of-dh-abstracts` sheet, excluding the `work_id` since it's already present.
   - Enter the following formula in `T1`:
     ```
     =IFERROR(VLOOKUP($S1, 'index-of-dh-abstracts'!$A$1:$W$17, COLUMN(B1), FALSE), "")
     ```
   - Drag the formula to the right to cover all columns you want to import from `index-of-dh-abstracts` (up to column `V` since you're excluding the first column `work_id`).
   - Then, drag down the formula to row `18` to populate all rows with data from the second sheet.

4. **Refining the Final Dataset**:

   The steps above will give you the merged data in `Final Merged Dataset`. However, if there are any discrepancies or formatting issues, you'll need to manually adjust them. It's also a good practice to review the data and ensure that everything was merged correctly.

Remember: Always create a backup of your original data before making significant changes or manipulations. This way, if something goes wrong, you can always refer back to the original data.

{% endcapture %}
{% include toggle.html content=toggle_prompt %}

We can get the following formula:

```shell
=IFERROR(VLOOKUP($S1, 'index-of-dh-abstracts'!$A$1:$W$17, COLUMN(B1), FALSE), "")
```

This formula differs from our attempt but shows some similarities, such as the use of the `IFERROR`, `VLOOKUP`, and `COLUMN` functions.

And now we should have the following data in our `Final Merged Dataset`:

![final_merged_dataset]({{site.baseurl}}/assets/images/final_merged_dataset.png)

{% endcapture %}
{% include toggle.html content=toggle_content %}

## Data Visualization

Now that we have our final merged dataset, we can start to explore how we can visualize our data. We will start with some basic visualizations in Google Sheets and then move to a more advanced tool called [RawGraphs](https://rawgraphs.io/).


Now that we have merged both our datasets we can finally compare how popular these tools are across the class compared to this dataset. In our original merge sheet `Merged Dataset` we should have the following:

![counts table]({{site.baseurl}}/assets/images/counts_table.png)





1. Finish finalized merged dataset
2. Start to visualize in Google Sheets
   1. Then do Raw Graphs
3. Then transpose in OpenRefine
4. The import in Google Sheets
5. Sum values
6. Start to visualize in RawGraphs again

Talk about what makes a good data visualization

Give the students the total tool counts and have them create a visualization in Google Sheets and RawGraphs
Reflect on what makes these tools useful or not, difficult or easy to use
