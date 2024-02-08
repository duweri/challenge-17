# Title (replace with your title)

Regular Expression Tutorial by Danielle Uweri

## Summary

RegEx or Regular Expressions is a sequence of characters that forms a search pattern and can be used to check if a string contains the specified search pattern. In this Regex Tutorial, you will learn how to validate the featured email address using regualr expression: /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/. 
The tutorial breaks down and explains each component of the regex, making the validation process easier to grasp. After finishing this tutorial, you will have a better understanding of how the regex works to validate and confirm the input of a legitimate email address.

## Table of Contents
- [Regex Components](#regex-components)
- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Character Classes](#character-classes)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Author](#author)

## Regex Components

Regular Expressions are literal which consists of a pattern enclosed between slashes as follows: /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/. If we examime the "Matching an email address" regex, you will see that this is true.

### Anchors

Regular expressions are effective tools for identifying patterns in text. Anchors are special characters in regular expressions that define the pattern's position within the input string. In email validation, such as the regex included in this tutorial: /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/, it is critical to guarantee that the full input string matches the provided pattern, rather than just a part of it.

The characters ^ and $ are both considered to be anchors.

Two types of anchors:
Start Anchor ^: This asserts that the pattern must match the start of the string.
End Anchor $: This asserts that the pattern must match the end of the string.

Example One: The regex ^hello$ matches only the string "hello" and nothing else. It won't match "hello world" or "say hello" because the pattern is not at the start or end of the string, respectively.
Example Two: The regex ^hello matches any string where "hello" is at the start of the string. It will match "hello" in "hello world", but it will not match "hello" in "world hello" because the string does not start with "hello".
Example Three: The regular expression hello$ matches any string where "hello" is at the end of the string. It will match "hello" in "world hello" but it will not match "hello" in "hello world" because the string does not end with "hello".

Anchors are useful for email vaildation because it makes sure that the entire email address complies to the specified pattern which is essential for accurate validation and prevents partial matches or unwanted results. 

### Quantifiers

Quantifiers define the boundaries of the string that your regex matches (or a specific piece of it). They often contain the minimum and maximum amount of characters that your regex searches for.

The + quantifier means "one or more," and is used after the pattern `[a-z0-9_\.-]` in the first capturing group `([a-z0-9_\.-]+)`. This means that the pattern `[a-z0-9_\.-]` should appear at least once, but it can also occur numerous times consecutively. Thus, the group will include one or more lowercase letters, numerals, underscores, dots, or hyphens.

Similarly, the + quantifier is used after the pattern `[\da-z\.-]` in the second capturing group `([\da-z\.-]+)`. This group matches one or more digits, lowercase letters, dots, or hyphens.

The `{2,6}` quantifier is used after the character class `[a-z\.]` in the third capturing group `([a-z\.]{2,6})`. This group matches a sequence of 2 to 6 lowercase letters or dots. This means that the email address must end with a two to six letter top-level domain, such as .com, .edu, or .co.uk.

Example: Quantifiers in regex describe the number of times a pattern should match. They are inserted after a character, character class, or group to establish the minimum and maximum repetitions of the previous pattern.

Given the regex `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`:

Quantifier `+` : Matches "one or more" occurrences.

`([a-z0-9_\.-]+)`: Matches one or more lowercase letters, digits, underscores, dots, or hyphens.
`([\da-z\.-]+)`: Matches one or more digits, lowercase letters, dots, or hyphens.
Quantifier `{2,6}` : Matches between 2 and 6 occurrences.

`([a-z\.]{2,6})`: Matches a sequence of 2 to 6 lowercase letters or dots.
The regex above matches valid email addresses with the following pattern:

One or more lowercase letters, digits, underscores, dots, or hyphens
Followed by the @ symbol
Followed by one or more digits, lowercase letters, dots, or hyphens
Followed by a period
Ending with a two to six letter top-level domain (e.g., .com, .edu, .co.uk)

### Character Classes

Character classes, also known as character sets, are shorter and more succinct regular expressions (regex) that represent particular groups of characters. Using character classes, you may simplify and shorten regex patterns, making them more legible and understandable.

The highlighted email regex employs the principal character class: \d and.. Square brackets specify character sets, such as `[a-z]`, `[0-9]`, and `[.-]`. These sets represent numerous characters, with a single character matching from the provided range.

Consider the following: `/[a-zA-Z0-9]/`.


This regex pattern matches a single alphanumeric character, which can be capital, lowercase, or digits. The character class \d represents a digit, whereas `[a-z]` and `[A-Z]` are character sets that represent lowercase and capital letters, respectively. Combining these character sets within square brackets results in a pattern that matches any single alphanumeric character.

### Grouping and Capturing

Grouping structures in regular expressions (regex) are used to combine one or more letters or sub-expressions and consider them as a single unit within the expression. They are contained within the brackets () and fulfil the following functions:

* Applying quantifiers to a set of letters.
* Capturing a specific segment of the match for later use.
* Creating a backreference for the previously matched group.
* Using alternation on a collection of characters

Our Email regex example : `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/` contains 3 grouping/capturing constructs which capture 3 different parts of the email address such as the local part, domain and the top-level domain.

#### The Local Part

`([a-z0-9_\.-]+)` matches the username of the email address which helps to ensure that the username follows a valid format and matches one or more characters that can be:

* Lowercase letters: a-z
* Numbers: 0-9
* Underscores: _
* Dots: .
* Hyphens: -
Example: The email address: danielle_uweri.123@example.com

The Local-Part of the email address is danielle_uweri.123. It matches the regex ([a-z0-9_\.-]+) for the following reasons:

It contains lowercase letters: d, a, n, i, e, l, u, w, and r
It contains numbers: 1, 2, and 3
It contains an underscore: _
It contains a dot: .
This Local-Part follows a valid format and is in compliance with the regex pattern provided. The regex pattern ([a-z0-9_\.-]+) effectively captures the username portion of the email address as seen above, by allowing a combination of lowercase letters, numbers, underscores, dots, and hyphens.

#### Domain 

Secondly, `([\da-z\.-]+)` matches the Domain name. The group represents the domain of the email address (the part between the @ symbol and the final period .). This helps to ensure that the domain name follows a valid format and matches one or more characters that can be:

* Numbers: \d
* Lowercase letters: a-z
* Dots: .
* Hyphens: -
Example: The email address: danielle.uweri@sub-domain123.example.com

It matches the regex ([\da-z\.-]+) for the following reasons:

It contains lowercase letters: s, u, b, d, o, m, a, i, n, e, x, a, m, p, l, and e
It contains numbers: 1, 2, and 3
It contains a dot: .
It contains a hyphen: -
This Domain follows a valid format and is in compliance with the regex pattern provided above. The regex pattern ([\da-z\.-]+) effectively captures the domain name portion of the email.

#### Top-level domain 

Thirdly,`([a-z\.]{2,6})` matches the Top-Level Domain. The group represents the Top-Level Domain of the email address (the part after the final period .). This helps to ensure that only the valid top-level domains are accepted and matches between 2 to 6 characters that can be:

* Lowercase letters: a-z
* Dots: .
Example: The email address: danielle_uweri.123@example.com

The Top-Level Domain of the email address is com. It matches the regex ([a-z\.]{2,6}) for the following reasons:

* It contains lowercase letters: c, o, and m
* It has a length of 3 characters, which falls within the valid range of 2 to 6 characters.

 The regex pattern `([a-z\.]{2,6})` effectively captures the top-level domain portion of the email address by allowing a combination of lowercase letters and dots, with a length between 2 to 6 characters.
### Bracket Expressions

Anthying within the Square brackets ([...]) represents a range of characters that we want to match and will become a part of the allowed set. Not only are they known as bracket expressions, but also positive character group because they outline the characters we want to match. 
In our regex featured in this tutorial: /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/ there are (3) main bracket expressions:

### 1st Bracket Expression:

Here's the breakdown of this expression:

* a-z: Matches lowercase letter from a to z.
* 0-9: Matches digit from 0 to 9.
* _: Matches underscore character.
* \.: Matches literal period (dot) character. The backslash is used to escape the dot since it has a special meaning in regex.
* -: Matces the hyphen character.
Example: Consider the following email address: danielle_1402-@stu-dent2024.com

The local part, of the username, is danielle_1402-.

Now let's break it down according to the bracket expression [a-z0-9_\.-]:

* danielle contains lowercase letters d, a, n, i, e, l, l and e, matching the a-z part of the expression.
* _ is an underscore character, matching the _ part of the expression.
* 1402 contains digits 1, 4, 0, and 2, matching the 0-9 part of the expression.
* - is a hyphen character, matching the - part of the expression.
* . is a literal period (dot) character, matching the \. part of the expression.
In the example, the bracket expression [a-z0-9_\.-] successfully matches the local part thomas_1234- of the email address.

### 2nd Bracket Expression:

The bracket expression [\da-z\.-] matches any single character in the range 0-9, a-z, or one of the characters ., or -. Thus the expression is used to match the Grouping Constructs: domain part of the email address.

Here's the breakdown of this expression:

* \d: Matches digit from 0 to 9. This is a shorthand for [0-9].
* a-z: Matches lowercase letter from a to z.
* \.: Matches the literal period (dot) character.
* -: Matches hyphen character.
Example: Consider the following email address: danielle_1402-@stu-dent2024.com

The domain part of the email address is student2024.com.

Now let's break it down according to the bracket expression [\da-z\.-]

* stu contains lowercase letters s, t, and u, matching the a-z part of the expression.
* - is a hyphen character, matching the - part of the expression.-
* dent contains lowercase letters d, e, n, and t, matching the a-z part of the expression.
* 2024 contains digits 2, 0, 2, and 4, matching the \d part of the expression.
* \. is a literal period (dot) character, matching the \. part of the expression.
* com contains lowercase letters c, o, and m, matching the a-z part of the expression.
In this example, the bracket expression [\da-z\.-] successfully matches the domain part stu-dent2024.com of the email address.

### 3rd Bracket Expression:

The bracket expression [a-z\.]{2,6} matches any single character in the range a-z or the literal period (dot) character. The expression is then followed by a quantifier {2,6}, which specifies that the matched characters must occur between 2 and 6 times, inclusive. Thus used to match the Grouping Constructs: top-level domain of the email address.

Here's the breakdown of this expression:

* a-z: Matches lowercase letter from a to z.
* \.: Matches literal period (dot) character.
* {2,6}: Matches quantifier that specifies the number of times the preceding expression (i.e., [a-z\.]) must be matched, which is between 2 and 6 times, inclusive.
Example: Consider the following email address: danielle_1402-@bstu-dent2024.examp.le

The top-level domain part of the email address is examp.le.

Now let's break it down according to the bracket expression [a-z\.]{2,6}:

* examp.le contains lowercase letters a-z (specifically, e, x, a, m, and p), matching the a-z part of the expression.
* \. is a literal period (dot) character, matching the \. part of the expression.
* examp.le the entire top-level domain part examp.le matches the {2,6} quantifier, as it consists of 6 characters in total (5 letters and 1 dot).
In the example, the bracket expression [a-z\.]{2,6} successfully matches the top-level domain part examp.le of the email address.


## Author

Github: 
Deployed GitHub-Gist Link: 
GitHub Repository: 

