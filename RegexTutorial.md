# Regular Expressions (Regex) Tutorial

Regular expressions, generally referred to as Regex, are incredibly powerful and useful patterning matching strings, or sequence of characters. They are encoded text strings that can match patterns in other strings. These expressions may be relatively simple such as when they are used to match exact strings, or they can be quite complex where the strings that are matched contain a set rules. Regex are supported by nearly all programming languages. They allow for cleaner, more effecient code, and relatively faster validations in code, by replacing many of the if/else statements in code since the validation will only need to be done once with regex. It is important to understand that when using a regular expression, it will only validate the structure of a particular string. For example, there would be no way of using regex to validate whether someone was using a legitimate or actual email address, only whether the provided email was structured properly as an email address. But, even with this particular drawback, regular expressions provide many benefits over other validation methods.

## Summary

This tutorial will be using an email string sequence as an example of a regular expression. The following will be the example regex email string sequence:<br>

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

The caret <code>^</code> and the dollar sign <code>$</code> are characters that are called anchors in a regular expression. The caret <code>^</code> indicates the beginning of a string sequence, and the dollar <code>$</code> indicates the end of a string sequence. In the email example listed in the Summary, the beginning of the example email regex is displayed in this snippet <code>^([a-z0-9_\.-]+)</code> - the snippet begins with a <code>^</code> character. The end of the example email regex is displayed in this snippet <code>([a-z\.]{2,6})$</code> - the snippet ends with a <code>$</code> character.

### Quantifiers

Quantifiers in regular expressions are metacharacters that are used to enumerate how many times the previous character or character group should be matched. This allows for pattern matching characters or character groups of varying lengths. Usually, quantifiers attempt to match as many characters or character groups as possible. When quatifiers attempt this action they are referred to as being "greedy", and include the following:

- <code>?</code>: Pattern match zero or one times.
- <code>*</code>: Pattern match zero or more times.
- <code>+</code>: Pattern match one or more times.
- <code>{}</code>: Curly brackets set limits for a match in the following ways:
    - <code>{ n }</code>: Exact pattern match <code>n</code> number of times (where n is a number).
    - <code>{ n, }</code>: Pattern match at least <code>n</code> or more number of times (where n is a number).
    - <code>{ n,m }</code>: Pattern match from a minimum of <code>n</code> number of times to a maximum of <code>m</code> number of times (where n and m are both numbers and n < m).

In the email example <code>/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/</code>, the quantifiers being used are the <code>+</code> character and the curly brackets limit setter <code>{ n,m }</code>. The <code>+</code> is used twice - here <code>([a-z0-9_\.-]**+**)</code> and here <code>([\da-z\.-]**+**)</code>. Where as the limit setter is used here <code>([a-z\.]**{2,6}**)</code>.

A discussion of 'lazy' quantifiers may be found in the 'Greedy and Lazy Match' section of this tutorial.
    
### OR Operator

In regular expressions, using the OR operator <code>|</code>, also called a pipe symbol or vertical bar, allows for matching everything either to the left **'OR'** to the right of the pipe symbol. This is used to match a single regex out of many potential regular expressions. If the pattern matching is to be limited to a certain string sequence in a single regex, then parentheses around a string sequence will group together that particular sequence for matching.

For the email example <code>/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/</code>, there was no OR operator <code>|</code> used.

### Character Classes

In regular expressions, a character class, which is also called a character set, provides a way to specify a set of characters for pattern matching each of those characters that apply to a given string. Generally, character classes are enclosed in brackets, and the matching takes place with any character from the set of characters that are specified within brackets. Character classes provide an easy and convenient way to match a specific set of characters, or even exclude any particular character(s) from a pattern match. So, for example, the regex <code>[a-z]</code> matches any lowercase letter, while <code>[^a-z]</code> matches any character that is not a lowercase letter. 

Character classes may also allow be mixed with metacharacters, such as quantifiers and anchors, to produce much more complex patterns for matching. For example, if someone wishes to match multiple characters in a row, instead of only matching one character at a time, you would use a quantifier such as <code>*</code> or <code>+</code>.

Some common character classes are as follows:

- <code>[abc]</code>: this will match one character that is either an 'a', 'b', or 'c'.
- <code>[a-z]</code>: this will match any one lowercase letter from 'a' to 'z'.
- <code>[A-Z]</code>: this will match any one uppercase letter from 'A' to 'Z'.
- <code>[0-9]</code>: this will match any one digit from '0' to '9' (the metacharacter '**\d**', which matches any Arabic digit, can be used instead of [0-9]).
- <code>[\w]</code>: this will match any one-word character, including an underscore, letters, or digits.
- <code>[\s]</code>: this will match any whitespace character, including a space, tab, or newline.

**Note:** placing an <code>^</code> in front of the character set (inside the brackets) such as seen here <code>[^a-z]</code> will match characters not part of that set. In this example from above, it matches any character that is not a lowercase letter.

For the email regex example <code>/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/</code>, the following are character classes, or character sets:

- <code>[a-z0-9_\.-]+</code>: this character set matches any character that is a lowercase letter, a digit, and one of any underscore <code>_</code>, period <code>.</code>, or dash <code>-</code>. There is also a quantifier <code>+</code> after the closing bracket, which will match the character set one or more times. **Note:** the backslash character <code>\\</code> in this example is not being used as an escape character, but means that only that character following it will be matched.

- <code>[\da-z\.-]+</code>: this character set matches any character that is any Arabic digit, lowercase letter, and one of any period <code>.</code> or dash <code>-</code>. There is also a quantifier <code>+</code> after the closing bracket, which will match the character set one or more times. **Note:** the backslash character <code>\\</code> in this example is not being used as an escape character, but means that only that character following it will be matched.

- <code>[a-z\.]{2,6}</code>: this character set matches any character that is any lowercase letter, and one of any period <code>.</code>. There is also a quantifier <code>{2,6}</code> after the closing bracket, which will match the character set between two (2) and six (6) times. **Note:** the backslash character <code>\\</code> in this example is not being used as an escape character, but means that only that character following it will be matched.

### Flags

Regular expression flags are components or parameters that are placed at the end of a regex sequence to modify some of the regex's default behavior; essentially, adding further functionality for the regex. There are many different flags that can be used, depending on the programming language. However, three common flags that are used in nearly every programming language are the following:

- <code>g</code>: this is a Global Flag.
    - When using regular expressions, the default action is to only have the first set of characters in a string that matches be returned. But, by using the global flag <code>g</code> at the end of a regex, all possible set of characters that match the pattern will be returned.

- <code>i</code>: this is a Case-Insensitive Flag.
    - When using regular expressions, the default action is for a regex pattern to be case sensitive. So, if <code>/world/</code> is used in the pattern matching sequence, "World" would not be matched since <code>/world/</code> is all lowercase. But, by using the case-insensitive flag <code>i</code> at the end of a regex <code>/world/i</code>, "world" and "World" would be matched since case would be ignored.

- <code>m</code>: this is a Multiline Flag.
    - When using regular expressions, the default action when using the beginning character called a caret <code>^</code>, is for that character to take into account every character as only one string on a single line. So, if what is to be matched is on several lines, only the first line of a string sequence will be taken into account for pattern matching. But, if what is to be matched is on several lines, then using the multiline flag <code>m</code> at the end of a regex, will allow for pattern matching on all lines of a string sequence.

For the email example <code>/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/</code>, there are no flags being used.

### Grouping and Capturing

In regular expressions, there is a very useful feature for simplifying any complex pattern for matching. This is called **'Grouping'**, where a repeated sequence of characters, such as in the email example <code>/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/</code>, are grouped or captured. Any regex subpattern may be considered a group when enclosed within parentheses <code>()</code>. For example, <code>(abc)</code> is considered a group that matches the string sequence 'abc'. For the email example in this tutorial, the following are groups:

- <code>([a-z0-9_\.-]+)</code>: this matches any character that is a lowercase letter, a digit, and one of any underscore <code>_</code>, period <code>.</code>, or dash <code>-</code> with a quantifier.

- <code>([\da-z\.-]+)</code>: this matches any character that is any Arabic digit, lowercase letter, and one of any period <code>.</code> or dash <code>-</code> with a quantifier.

- <code>([a-z\.]{2,6})</code>: this matches any character that is any lowercase letter, and one of any period <code>.</code> with a quantifier.

A more detailed explanation of each group may be found in the 'Character Classes' section.

### Bracket Expressions

In regular expressions, a bracket expression is a sequence of characters that are encloded by square brackets <code>[]</code>. Bracket expressions may contain any combination of characters that matches any single character within a string sequence. For example, the regex <code>[123]</code> with match any single digit enclosed within the brackets, whereas <code>[^123]</code> will match any single character that is not a 1, 2, or 3 due to the caret character <code>^</code> within the brackets - this was discussed previously in the 'Character Classes' section of this tutorial. There may also be what are termed range expressions enclosed within a bracket expression. The range expression is two characters that are separated by a hyphen '-'. This will match any single character between the two characters separated by the hyphen. For example, <code>[a-d]</code> will match all lowercase letters between 'a' and 'd'.

The bracket expressions in the email example <code>/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/</code> are as follows:

- <code>[a-z0-9_\.-]</code>
- <code>[\da-z\.-]</code>
- <code>[a-z\.]</code>

A more detailed explanation of each bracket expression may be found in the 'Character Classes' section.

### Greedy and Lazy Match

In regular expressions, 'greedy' and 'lazy' generally refer to quantifiers. As discussed previously in this tutorial in the 'Quantifiers' section, as a general rule, quantifiers will attempt to match as many characters or character groups as possible. Due to this, they are referred to as being "greedy". However, there are quantifiers that may be used to match patterns as few times as possible, before attempting to match longer ones by expansion. In general, lazy pattern matching will lead to the shortest possible string being matched. When a lazy pattern match is to be accomplished, append a question mark <code>?</code> to an exitsting quantifier. 

Some common lazy quantiifers include:

- <code>??</code>: Pattern match the preceding character or subexpression zero or one times (zero is preferred).
- <code>*?</code>: Pattern match the preceding character or subexpression zero or more times (as few as possible).
- <code>+?</code>: Pattern match the preceding character or subexpression one or more times (as few as possible).
- <code>{n}?</code>: Exact pattern match <code>n</code> number of times (where n is a number). This is the same as the greedy quantifier.

For the email example <code>/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/</code>, there are no lazy quantifiers being used. A more detailed explanation of greedy quantifiers may be found in the 'Quantifiers' section.

### Boundaries

In regular expressions, boundaries are assertions that indicate the beginning and the end of lines or words. They may also be patterns that indicate a match is possible, such as 'look-ahead' or 'look-behind' assertions (the 'look-ahead' or 'look-behind' assertions will be discussed in the 'Look-ahead and Look-behind' section of this tutorial). For the email example <code>/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/</code>, the following are boundaries:

- <code>^</code>: this indicates the beginning of the string sequence - also called an anchor.
- <code>$</code>: this indicates the end of the string sequence - also called an anchor.

### Back-references

In regular expressions, a back-reference is a regex command that refers back to a previous part of a matched regex pattern. A back-reference is indicated by a backslash and a single digit, such as <code>\3</code>. In a regex pattern, back-references match the same content as a previously matched subexpression, which is the part of a regex that a back-reference refers to, specified by parentheses.

For the email example <code>/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/</code>, there are no back-references being used.

### Look-ahead and Look-behind

In regular expressions, a look-ahead and a look-behind are assertions that together are called a look-around, which may be performed in a positive or negative way. 

The positve look-around is typically used when a check is needed to determine whether a given pattern is proceeded or followed by another pattern. If the string sequence is to be traversed from the beginning, then a look-ahead is used. If the string sequence is to be traversed from the end, then a look-behind is used. A positive look-ahead is indicated by a <code>?=</code>. A positive look-behind is indicated by a <code>?<=</code>.

The negative look-around is typically used when a check is needed to determine whether a given pattern is not proceeded or followed by another pattern. If the string sequence is to be traversed from the beginning, then a look-ahead is used. If the string sequence is to be traversed from the end, then a look-behind is used. A negative look-ahead is indicated by a <code>?!pattern</code>. A negative look-behind is indicated by a <code>?<!pattern</code>.

For the email example <code>/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/</code>, there are no look-arounds being used.

## Author

Stephen Twomey<br><br>
If there are questions or comments about this tutorial,<br>
please visit: https://github.com/sctwomey.
