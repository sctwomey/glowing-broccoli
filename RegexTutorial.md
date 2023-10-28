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

In the email example <code>/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/</code>, the quantifiers being used are the <code>+</code> character and the curly brackets limit setter <code>{ n,m }</code>. The <code>+</code> is used twice - here <code>([a-z0-9_\.-]**+**)</code> and here <code>([\da-z\.-]**+**)</code>. Where as the limit setter is used here <code>([a-z\.]**{2,6}**)</code>.
    
### OR Operator



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

### Bracket Expressions

### Greedy and Lazy Match

### Boundaries

### Back-references

### Look-ahead and Look-behind

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
