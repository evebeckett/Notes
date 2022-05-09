# Heading Level 1
## Heading Level 2
### Heading Level 3
#### Heading Level 4
##### Heading Level 5
###### Heading level 6

To create paragraphs, use a blank line to separate one or more lines of text.  Unless the paragraph is in a list, don't indent paragraphs with spaces or tabs.

Line Breaks -- To create a line break or new line, end a line with two or more spaces, and then hit enter.  

## Bold Text

To make text bold, **add TWO stars/asterisks before and after the part that should be bold**.

##Italics

To italicize text,  *add ONE asterisk before and after a word or phrase.*

## Bold AND Italic

To emphasize text with bold and italics at the same time, ***add THREE asterisks before and after the word/phrase.***

## Blockquotes 

To create a blockquote add a > in front of a paragraph, like this:

> This is a paragraph using a blockquote.

Note:  Blockquotes can contain multiple paragraphs.  To do this, add a > on the blank lines between the paragraphs, like this:

>  This is an example of using blockquotes with mutliple paragraphs.
>
>This is the second paragraph.

Note:  Blockquotes can be nested by adding a >> in front of the paragraph you want to nest, like this:

> This is a blockquote.
>> This is a nested blockquote.

Note:  Block quotes can contain other markdown formatted elements, though not all of them will work.  

Ex:

> The quarterly results look great!
>
> - Revenue was off the chart.
> - Profits were higher than ever.
>
> *Everything* is going according to **plan**

Note:  Before and after blockquotes, put blank lines for compatibility purposes.

## Lists

### Ordered List -- To create an ordered list, add line items with numbers followed by periods.  They don't have to be in numerical order, but the list must start with the number 1.  No matter what numbers you use, the list will come out ordered.

Ex 1:  Correctly ordered

1. First Item
2. Second item
3. Third item
4. Fourth item

Ex 2: Ordered list even though the numbers are out of order.  (Must START with 1, though...)

1. First item
8. Second item
7. Third item
4. Fourth item

Note:  To indent an ordered list, simply space/tab over.

1. First item
2. Second item
    1. First indented item
    2. Second indented item.
3. Third item

### Unordered Lists

To add a bullet point to your text, put a dash (-) in front of the item you want to have a bullet point followed by a space, like this:

- This item has a bullet point.

To indent your bullet point, simply space / tab over and start a new bullet point

Ex:

- This item has a bullet point.
    - This item has an indented bullet point.

### Starting Unordered Lists Items With Numbers

If you need to start an unordered list item with a number followed by a period, you can use a backslash ("\") to escape the period.

Ex:

- 1968\. A great year!
- I think 1969 was second best.

### Paragraphs in a List

To add another element in a list while preserving the continuity of the list, indent the element four spaces or one tab.

- This is the first list item.
- Here's the second list item.

    I need to add a paragraph below the second list item.

- And here's the third list item.

With blockquotes:

- This is the first list item.
- This is the second list item.

     > I need to add a blockquote below the second list item.

 - This is the third list item.

 ## Code

To denote a word or hrase as code, enclose it in backticks.

Ex:

At the command prompt, type `nano`.
 
Note on escaping backticks:

If the word/phrase you want to denote as code includes one or more backticks, you can escape it by enclosing the word/phrase in double backticks.

Ex:

``Use `code` in your markdown file.``

### Code blocks

 Code blocks are normally indented four spaces or one tab.  If they're in a list, indent them eight spaces / two tabs.

 Normally:

     <h1>Hello World!<h1>

In a list:

1. Open the file
2. Find the following code block on line 21:

        <html>
            <head>
                <title>Test</title>
            </head>

3. Update the title to match the name of your website.

## Horizontal Rules

To create a horizontal rule (a horizontal line across the page), use three or more asterisks (***), dashes (---), or underscores (___) on a line by themselves.

***

## Links

To create a link, enclose the link text in brackets (e.g. [Duck Duck Go]) and then follow it immediately with the URL in parentheses. (e.g. (https://duckduckgo.com))

Ex:

My favorite search engine is [Duck Duck Go](https://duckduckgo.com).

### Adding Titles to Links

You can add a title for a link.  This will appear as a tool tip when the user hovers over the link.  To add a title, enclose it in quotation marks after the URL.

Ex:

My favorite search engine is [Duck Duck Go](Https://duckduckgo.com "The best search engine for privacy").

### URLs and Email Addresses

To quickly turn a URL or email address into a link, enclose it in angle brackets.

<https://www.markdownguide.org>

<fake@example.com>

### Formatting Links

To emphasize links, add asterisks before and after the brackets and parentheses. 

**Bold**:

I love supporting the **[EFF](https://eff.org)**.

*Italics*:

This is the *[Markdown Guide](https://www.markdownguide.org)*.

To denote links as code, add backticks in the brackets.

## Images

To add an image, add an exclamation mark (!) followed by alt text in brackets, and the path / URL to the image asset in parentheses.  You can optionally add a title in quotation marks after the path / URL.

EX:

![alt text](path/url to image)

![colorful floating umbrellas](https://images.unsplash.com/photo-1532135468830-e51699205b70?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=988&q=80)


## Escaping Characters

To display a literal character that would otherwise be used to format text ina  markdown document, add a backslash ("\") in front of the character.

You can use a backslash to escape the following characters:

\\  Backslash

\`  Backtick

\*  asterisk

\_ underscore

\{curly braces}

\[brackets]

<angleBrackets>

(parentheses)

\# pound sign

\+ plus sign

\- minus sign (hyphen)

\. dot

\! exclamation mark

\| pipe