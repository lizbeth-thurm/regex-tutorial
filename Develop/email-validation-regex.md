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
- [Character Classes](#character-classes)
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

Specifically, this pertains to the end part an email address, such as ".com" or ".edu".

### Character Classes

Character classes in regex establish characters to be matched or ranges of characters.  The following character classes are used in the email validation regex:

- `[a-z]`
    - Matches any letter, a through z.
- `[0-9]`
    - Matches any numeral, 0 through 9.
- `\d`
    - Also matches any numeral, 0 through 9.  The "d" stands for "decimal."
- `.`
    - The arrangement `\.` indicates an escape character for the period.  This is necessary because ordinarily the period has an actual fucntion within a character class and so the slash sets it off as a character to be searched, rather than using it for its other purpose (which for `.` is the wildcard character and will match *any* character in a string).

### Grouping and Capturing

Grouping in a regular expression is accomplished using parentheses `()`.  The symbols inside the parentheses are "captured" allowing operators to be applied to the entire group.

In the expression above, grouping occurs three times; in the beginning, after the "@" symbol, and at the end:

- start:
    - `^([a-z0-9_\.-]+)`
    - This indicates that everything inside the parentheses is grouped and the `^` operator is applied to the whole thing.
- after "@":
    - `([\da-z\.-]+)\.`
    - This simply groups everything inside the parentheses to occur before the "." before the extension at the end of the email address.
- end:
    - `([a-z\.]{2,6})$`
    - This indicates that everything inside the parentheses is grouped and then the `$` operator is applied.

### Bracket Expressions

Bracket expressions in regex are set off by square brackets: `[]`.  The expression will match any of the characters inside the brackets.

In the email validation regex, the bracket expression occurs three times; once at the start, once after the "@" symbol, and once at the end:

- start:
    - `[a-z0-9_\.-]`
        - This indicates that the expression will match any alphanumeric character OR underscore, period, or dash.
        - This pertains to the first part of an email address before the "@" symbol.
- after @:
    - `[\da-z\.-]`
        - This indicates that the expression will match any decimal number (indicated by `\d`) OR letter, period, or dash.
        - This pertains to the part of an email address after the "@" symbol but before the extension at the end following the period.
- end:
    - `[a-z\.]`
        - This indicates that the expression will match any letter OR periods.
        - this pertains to the extension at the end of an email address following a period (such as ".com").

### Greedy and Lazy Match

Regex operators can be greedy or lazy.  Operators are greedy by default meaning that they will match as many instances of what they are operating on as possible.  For example, the `+` operator (which matches one or more of what comes before it) is greedy by default.  Therefore, in the email validation expression, `+` applied to `[a-z0-9_\.-]` will match as many of the characters occuring in a string as it can.

Operators are made lazy by adding a `?` to it.  A lazy operator will match the minimum bnumber of instances that it is searching for.  There is no lazy matching in the email validation expression.

### Boundaries



### Back-references



### Look-ahead and Look-behind



## Author

This tutorial was created by Skipper Thurman:
- **[email](slthurman01@gmail.com)**
- **[github](https://github.com/skip-thurm)**
