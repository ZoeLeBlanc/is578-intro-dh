---
title: "Introduction to File Formats"
permalink: /materials/intro-spreadsheets/01-intro-file-formats/
excerpt: "An introduction to file formats and how they are used in DH."
toc: true
---

## What is a file and why are there so many formats?

This is a huge topic in LIS and CS but to put it simply a file is a collection of data stored in a single unit, identified by a filename. It can be a document, an image, a video, a sound, or any other collection of data. The file extension is the part of the file name after the period. For example, in the file name `DH-Tool.md`, the file extension is `.md`. The file extension tells the computer what type of file it is and what program to use to open it.

![file formats](https://www.filecenter.com/blog/wp-content/uploads/2022/04/The-Giant-List-of-Document-File-Types-and-Extensions.jpg)

There are many different file formats and each one has its own purpose. For example, a `.docx` file is a Microsoft Word document, a `.jpg` file is an image, and a `.mp3` file is an audio file. Some file formats are proprietary, meaning they are owned by a company and can only be opened by certain programs. For example, `.docx` files can only be opened by Microsoft Word. So if you try to open up a word document in a PDF Viewer you might see what looks like a bunch of gibberish.

![corrupted word doc](https://www.fonelab.com/images/data-retriever/fonelab-data-retriever-how-to-corrupt-a-word-file-doc-text-only.jpg)

This gibberish is actually the code that makes up the file, but since the PDF Viewer doesn't know how to read the code it just shows you the code itself rather than the data stored in the files.

Other file formats are open source, meaning they are not owned by a company and can be opened by many different programs. For example, `.txt` files are plain text files that can be opened by any text editor. 

### What is plain text and Markdown?

Plain text is a file format that only contains text and no formatting. It is the simplest file format and can be opened by any text editor. Markdown is a plain text file format that uses symbols to add formatting to the text. For example, if you want to make a word bold you would put two asterisks on either side of the word.

```
**bold**
```

If you want to make a word italic you would put one asterisk on either side of the word.

```
*italic*
```

If you want to make a list you would put a dash in front of each item.

```
- item 1
- item 2
- item 3
```

If you want to make a heading you would put a hashtag in front of the heading.

```
# heading 1
## heading 2
### heading 3
```

These types of file formats are incredibly popular in DH for a few reasons. First, they are free to use and are more sustainable long term since they do not require specialized software to open. Second, this interoperability makes them easier to share and collaborate on, as well as use in a variety of DH Tools. Finally, the use of such file formats also preserves this data for future use. For example, if you have a `.docx` file and Microsoft Word goes out of business, you will no longer be able to open that file. However, if you have a `.txt` file you will always be able to open it in any text editor. 

The key thing to understand is that every file format has a history and is the product of multiple decisions and communities. In the case of Markdown, it was created by John Gruber with help from Aaron Swartz in 2004. The goal was to create a file format that was easy to read and write, and could be converted into HTML. They also wanted to create a file format that was easy to use and could be used by anyone. You can read more about the history of Markdown, in Bednarski, Dawid. “The History of Markdown: A Prelude to the No-Code Movement.” Taskade Blog, March 25, 2022. [https://www.taskade.com/blog/markdown-history/](https://www.taskade.com/blog/markdown-history/).

It's important to understand that Markdown has this history because many flavors of Markdown exist, and standardization of Markdown has been an ongoing project. For example, GitHub Flavored Markdown (GFM) is a flavor of Markdown that was created by GitHub in 2009. It is a superset of Markdown, meaning it adds additional features to Markdown. For example, GFM allows you to create tables in Markdown, which is not possible in regular Markdown. You can read more about GFM in “GitHub Flavored Markdown Spec.” GitHub, 2022. [https://github.github.com/gfm/](https://github.github.com/gfm/).

![markdown flavors](https://d11a6trkgmumsb.cloudfront.net/original/3X/c/b/cb7374a606a66c5b8e489afed76d93ed49dc7836.png)

This figure shows some examples of how Markdown is written depending on the Platform and standards. You can also see some of the discussions that go on to help shape these standards through the various repositories on GitHub that host the standards. For example, CommonMark is another popular Markdown style and improvements to it are discussed in this repository [https://github.com/commonmark/commonmark-spec/issues](https://github.com/commonmark/commonmark-spec/issues).

## Popular File Formats in DH

Understanding some of the tradeoffs and histories of file formats helps us consider increasingly popular file formats in DH. We have already discussed Markdown, but we will also be looking at two others: `JSON` and `CSV`.

### JSON

![json example](https://www.softwaretestinghelp.com/wp-content/qa/uploads/2017/12/Including-Car-in-Employee-JSON.jpg)

JSON stands for JavaScript Object Notation and is a file format that stores data in a key-value pair. For example, if you wanted to store our data from assignments this week you might write it like this:

```
{
  "DH Tool": "GitHub",
  "Found by": "Zoe LeBlanc"
}
```

This file format is popular in DH because it is easy to read and write, and can be used in a variety of programming languages. It is also a popular file format for sharing data across the web. You can read more about JSON in “JSON: JavaScript Object Notation.” MDN Web Docs, 2022. [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON).

We won't be using this file format much in this course, but it's important to know it exists since many datasets are available as JSON files. These files will have the file ending of `.json` and will always have the curly brackets, and values separated by colons and listed with commas.

### CSV

![csv example](https://static.tildacdn.com/tild3262-3665-4232-b835-303031616463/Screenshot_2022-04-2.png)

The other incredibly popular file format that you likely have already used before and that we will use a lot in this course is CSV. CSV stands for Comma Separated Values and is a file format that stores data in a table. For example, if you wanted to store our data from assignments this week you might write it like this:

```
DH Tool, Found by
GitHub, Zoe LeBlanc
```
CSVs are a usually read by spreadsheet software, like Excel or Google Sheets and have the file ending of `.csv`. Unlike `.xlsx` files, which are proprietary to Microsoft Excel, CSVs are open source and can be opened by any spreadsheet software. 

![excel vs csv](https://miro.medium.com/v2/resize:fit:1400/1*eGVQ8M6mgERo8WFMUjYjZA.jpeg)

CSVs have a long history as well and the file format was first created in the 1970s. But as we we will discuss more next week, the act of putting data into tables has an even longer history.

![punch card](https://imgur.com/V5mfB2w.jpg)

## In Class (Breakout Room) Assignment

So far we have a list of DH Tools in everyone's respective repositories. How could we create a CSV file from this data? What would the columns be? What would the rows be? 

Working together in groups, you'll need to do the following.

1. First create a folder in this [Google Drive Folder](https://drive.google.com/drive/folders/1ZFIPZtkJrmAOWITohsk6n7sNGluIwQEg?usp=sharing) with your group name.
2. Then create a Google Sheets file in this folder and name it `DH Tools`.
3. Discuss how you want to organize your data and what columns you want to include.
4. Enter the data from your repository into this Google Sheets file.

Once completed, we will discuss collectively as a class.

## Additional Resources

- Gregory, Ben. “Data Formats 101.” Astronomer, n.d. [https://www.astronomer.io/blog/data-formats-101](https://www.astronomer.io/blog/data-formats-101).






