# Regular Expressions (Regex) Tutorial

Regular expressions, generally referred to as Regex, are incredibly powerful and useful patterning matching strings, or sequence of characters. They are encoded text strings that can match patterns in other strings. These expressions may be relatively simple such as when they are used to match exact strings, or they can be quite complex where the strings that are matched contain a set rules. Regex are supported by nearly all programming languages. They allow for cleaner, more effecient code, and relatively faster validations in code, by replacing many of the if/else statements in code since the validation will only need to be done once with regex. It is important to understand that when using a regular expression, it will only validate the structure of a particular string. For example, there would be no way of using regex to validate whether someone was using a legitimate or actual email address, only whether the provided email was structured properly as an email address. But, even with this particular drawback, regular expressions provide many benefits over other validation methods.

## Summary

This tutorial will be matching an email string as an example of a regular expression. The following will be the example regex email string:<br>

<code>/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/</code>


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

The caret <code>^</code> and the dollar sign <code>$</code> are characters that are called anchors in a regular expression. The caret <code>^</code> indicates the beginning of a string, and the dollar <code>$</code> indicates the end of a string. In the email example listed in the Summary, the beginning of the example email regex is displayed in this snippet <code>^([a-z0-9_\.-]+)</code> - the snippet begins with a <code>^</code> character. The end of the example email regex is displayed in this snippet <code>([a-z\.]{2,6})$</code> - the snippet ends with a <code>$</code> character.

### Quantifiers

Quantifiers in regular expressions are metacharacters that are used to enumerate how many times the previous character or character group should be matched. This allows for pattern matching characters or character groups of varying lengths. Since quantifiers attempt to match as many characters or character groups as possible, they are referred to as being "greedy". They include the following:

    - <code>?</code>: Pattern match zero or one times.
    - <code>*</code>: Pattern match zero or more times.
    - <code>+</code>: Pattern match one or more times.
    - <code>{}</code>: Curly brackets set limits for a match in the following ways:
        - <code>{ n }</code>: Exact pattern match <code>n</code> number of times (where n is a number).
        - <code>{ n, }</code>: Pattern match at least <code>n</code> or more number of times (where n is a number).
        - <code>{ n,m }</code>: Pattern match from a minimum of <code>n</code> number of times to a maximum of <code>m</code> number of times (where n and m are both numbers and n < m).

In the email example listed in the Summary, the quantifiers being used is the <code>+</code> character and the limiter <code>{ n,m }</code>. The <code>+</code> is used twice - here <code>([a-z0-9_\.-]**+**)</code> and here <code>([\da-z\.-]**+**)</code>. Where as the limiter is used here <code>([a-z\.]**{2,6}**)</code>.
    

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

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
