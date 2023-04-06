# Regex Tutorial

<br>
Regular expressions ('Regex' for short) can be intimidating because they may seem like complete giberish on first glance. However, that string of giberish is actually a search pattern that can enable users to do things like search for a specific string of characters, or match an email or URL. With a little study one can become familiar with the properties of Regex and learn how to incorporate it into their coding.

## Summary

<br>
In this tutorial, we will be learning about using Regex to match an email value. While it may look confusing now, by the end of this tutorial you will fully understand how to use an expression like the one we will break down below.

`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

## Table of Contents

<br>
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

<br>
The first thing to know about regexes is that they are literal, so the begining and ending of the espression will have a backslash ('/') character. This defines the start and end of the regex.

Looking back at our expression, we can identify that our string of gibberish does indeed start and end with the backslashes.

`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

### Anchors

<br>
Anchors are signified with either a ^ or $ symbols. A ^ anchor signifies that the following characters belong to the string that the expression is searching for.
<br>
For example, ^hello, would match any string of charcters that begins with "hello". However, because regex is case sensitive, "Hello" or 'hellO" would not match.

A `$` anchor signifies the preceding characters belong to the string the expression is looking for.
<br>
In our example, we see a ^ anchor following the first backslash and a `$` anchor preceding the final backslash.

`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

### Quantifiers

<br>
When trying to match a string of characters, quantifiers are used to set limits of the string your regex matches. In this case a $ anchor is used to signify the quantifier of `([a-z\.]{2,6})` in our regex.
<br>
What exactly do the characters within the quantifier mean though?
<br>
`{}` curly brackets are used in a quatifier to provides limits for a match. In our example, the `{2,6}` signifies that the regex is looking to match with a string of characters between 2 and 6 characters long.

<br>
If we wanted to match with a specific character length, we could just use a single number. For example `{2}` would only return strings two characters long. 
<br>
If we wanted to match with a character length 2 or more, we could add a comma after the two, `{2,}`.

### OR Operator

<br>
The OR operator can be used to use the logic in a bracket expression outside of the expression. For example in our regex the `a-z` portion could be rewritten `(a|b|c|d|e|f|g...etc)`.

### Character Classes

<br>
Character classes can be used to define a set of characters. For example, the `\d` matches any arabic numeral digit, while `\w` matches any alphanumberic character. The corresponding bracket expression would be `[0-9]` and `[A-Za-z0-9_]` respectively.

### Flags

<br>
While typically regexes start and end with a `/`, there is one expection and that has to do with flags. Flags are placed at the end of a regex and can define additonal functionality. For example, adding a `g` means the regex should be tested against all possible matches, while a `i` signifies that the regex should ignore case sensitivity.

### Grouping and Capturing

<br>
Grouping is signified by the parentheses `()` and is used to seperate parts of the regex, so various parameters are only met by the code inside of them, which is called the subexpression.
<br>
In our example you can clearly identify two subexpressions on either side of the `@` symbol. The first subexpression `([a-z0-9_\.-]+)` contains our bracket expression which defines our first matching string, the `+` outside of the brackets, but inside the parentheses signifies that the patter inside can match more or one time.

### Bracket Expressions

Bracket expressions, also known as positive character groups, wrap around characters or ranges of characters we want to match. Because we have three sets of characters, letters, numbers and special characters, we can use ranges to define what exactly we are looking to match. <br>

For example, the first bracket expression in our code is as follows: `[a-z0-9_\.-]`
<br>
The letter match parameters are determined by `a-z` part of the expression. We are asking the expression to match a string with any letters from a through z.
<br>
Likewise, the expression is looking to any numbers between 0-9. If we wanted to search for only numbers between zero and five, we would use this: `0-5`.
<br>
Lastly, to define the matching special characters, we have to just place them in the bracket expression. In this case, the expression will try to match the characters `_ \ . or -`
<br>
When combined in our example, we are asking the expression to match with any string that includes lowercase letters from a though z, numbers 0 through 9 and the special characters `_ \ . or -`

### Greedy and Lazy Match

Quantifiers, which we learned about above, are inherently "greedy". This means they match as many occurances of a particular pattern as possible. However it is possible to make them "lazy", which you might deduce that the regex will try to match as few occurances as possible (zero or one time).

Because quantifiers are inherently greedy, the way to make them lazy is simply to add a ? after it.

For example to make our qualifier lazy we would write it in the following way: `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})?$/`

### Boundaries

Word bounderies are similar to anchors They allow you to match the whole word using a regular expression. For example, `/bHello/b` would match the string "Hello".

### Back-references

Back references attempt to match the text as previously matched by a grouping. They can be used to reduce the amout of characters or repeating subexpressions in your code.

### Look-ahead and Look-behind

Look ahead and look behind are zero-length assertions that matches characters, but then returns on the result of match or no match. For example in a negative lookahead like such `q(?=u)` matches a `q` that is not followed by a `u`.

## Author

George currently taking a full stack developer bootcamp to increase his knowlegede of coding. Please visit his Github for examples of his work located here:
https://github.com/gharrison307
