# Matching an Email Using a Regular Expression

Searching for specific text within a document, whether it be on a website, in a block of code, or anything else, introduces unique problems.  Most text editors give you the ability to quickly and easily search a document for exact matches to text - but the ability to search for general phrases can be extremely useful.  For example, instead of searching the literal characters that spell out an email, we can use what's called a regular expression to search for any email, as long as it is formatted like a regular email tends to be formatted.

## Summary

This tutorial will detail a regular expression for matching an email address.  A regular expression is a series of characters that can be used to search text using very specific and customizable patterns.

The regular expression used in this tutorial for matching an email is shown below:

`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

This tutorial will explain in detail how this regular expression (abbreviated "regex") searches for an email by specificying parameters that are found in most emails.  The tutorial will describe how every character in the expression contributes to the search pattern.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components

### Anchors

Anchors in regular expressions allow for a user to search within a certain position within a series of characters.  Specifically, anchors allow users to search for characters at the beginning, end, or anywhere else within a string of characters.

In the regex code for matching an email there are two anchors: `^` and `$`.

The `^` symbol matches the beginning of a string.  In the email matching regex, this anchor comes at the start of a block of parentheses containing all the letters, numbers, underscore, period, and dash symbols (the `+` symbol will be discussed in the next section):

`^([a-z0-9_\.-]+)`

Therefore, this will match for any alphanumeric characters at the start of the string.

The `$` symbol matches the end of a string.  In the email matching regex, this anchor comes at the end of a block of parentheses containing all of the letters and a period, as well as two numbers in curly brackets, which will be discussed in the next section:

`([a-z\.]{2,6})$`

The `$` symbole here indicates that the string ends in a-z or a period. 

### Quantifiers

Quantifiers in regular expressions define the number of characters or groups of characters that have to be found in order to establish a match.

In the regex code for matching an email there are two quantifiers: `+` and `{ n , m }`.

The `+` symbol indicates that the expression will match whatever precedes it if it occurs one or more times.

The `+` symbol here occurs after the square brackets at the start of the expression but within the parentheses.  Therefore, it applies to everything in the square brackets:

`[a-z0-9_\.-]+`

Therefore, this expression will match any alphanumeric character, number, underscore, period, or dash if it occurs at the start one *or more* times.

Specifically, this pertains to the first part of an email address; that occuring before the "@" symbol.

The `{n , m}` quantifier will match in a range from `n` to `m`.

In the case of the email validation expression, this occurs in the form of `{2 , 6}` at the end of the final square brackets containing alphanumeric characters and a period:

`[a-z\.]{2,6}`

Therefore, this expression will match any alphanumeric character or period if it occurs between 2 and 6 times.

Specifically, this 



### OR Operator



### Character Classes



### Flags



### Grouping and Capturing



### Bracket Expressions



### Greedy and Lazy Match



### Boundaries



### Back-references



### Look-ahead and Look-behind



## Author

This tutorial was created by Skipper Thurman:
- **[email](slthurman01@gmail.com)**
- **[github](https://github.com/skip-thurm)**
