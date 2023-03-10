# Regex Tutorial

As a web dev student, I have created a tutorial that explains some specific components of regex so that I can better understand them. I hope they help you understand the search patterns of regex as well.

## Summary

A regex or regular expression is a sequence of characters that define a search pattern. Usually this pattern is used by string searching algorithms for "find" or "find and replace" operations on strings, or for input validation. It is a technique developed in theoretical computer science and formal language theory. 
Most characters stand for themselves, and match the corresponding character in the input string, and the simplest form of regex is actual literal text. For example, the regex "abc" matches the string "abc".
- We will look at the following components of regex:
    - Anchors
    - Quantifiers
    - Grouping Constructs
    - Bracket Expressions
    - Character Classes
    - The OR Operator
    - Flags
    - Character Escapes

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)

## Regex Components

### Anchors
- Anchors do not match any characters. They match the position before, after, or between characters.
    - ^ matches the position before the first character in the string.
    - $ matches the position after the last character in the string.
    - ^ and $ together match the entire string.
- If you want to match a literal ^ or $, you can use the escape character \.
- Example: `^abc$` matches the string "abc" but not "ab" or "abcd".
- If you have a string consisting of multiple lines, you can use the multiline flag `m` to match the beginning and end of each line.
- \A only ever matches the beginning of the string, even if the multiline flag is set.
- \Z only ever matches the end of the string, even if the multiline flag is set.
    - these two tokens never match at line breaks.
- In order to match the position before or after a line break, you can use \b and \B.
    - \b matches the position between a word character and a non-word character.
    - \B matches the position between a word character and a word character, or a non-word character and a non-word character.

### Quantifiers
- Quantifiers specify how many instances of a character, group, or character class must be present in the input for a match to be found.
- Quantifiers are greedy by default, meaning they will match as many characters as possible.
    - To make a quantifier non-greedy, you can add a ? after it. This will make it (lazy)
- Greedy or lazy quantifiers can be applied to any of the following regex components:
    - A single character
    - A group
    - A character class
    - A bracket expression
- The following quantifiers are available:
    - * matches zero or more instances of the preceding token.
    - + matches one or more instances of the preceding token.
    - ? matches zero or one instances of the preceding token.
    - {n} matches exactly n instances of the preceding token.
    - {n,} matches n or more instances of the preceding token.
    - {n,m} matches at least n and at most m instances of the preceding token.
- Nesting quantifiers, such as the regular expression pattern (a*)*, can increase the number of comparisons that the regular expression engine must perform.
    - This can cause a significant performance hit.
    - If you are using a quantifier in a way that is not intuitive, you should consider using a different regex pattern.

### Grouping Constructs
- Grouping constructs delineate the subexpressions of a regular expression and capture the substrings of an input string. You can use grouping constructs to do the following:

    - Match a subexpression that is repeated in the input string.

    - Apply a quantifier to a subexpression that has multiple regular expression language elements. For more information about quantifiers, see Quantifiers.

    - Include a subexpression in the string that is returned by the Regex.Replace and Match.Result methods.

    - Retrieve individual subexpressions from the Match.Groups property and process them separately from the matched text as a whole.

- (ABC) is a capturing group. It matches the string "ABC" and captures the string "ABC" in the Match.Groups collection.
- (?:ABC) is a non-capturing group. It matches the string "ABC" but does not capture the string "ABC" in the Match.Groups collection.
- (?<name>ABC) is a named capturing group. It matches the string "ABC" and captures the string "ABC" in the Match.Groups collection. The name of the group is "name". The name of the group can be any valid identifier.
- \1, \2, \3, and so on, are backreferences. They match the same text as previously matched by the n-th capturing group. For example, if the first capturing group matches "ABC", \1 matches "ABC".


### Bracket Expressions

- Brackets indicate a set of characters to match. You can use a bracket expression to match any single character from a list of characters, and you can use a hyphen to specify a range of characters.
    - ex. : 'elephant'.match(/[abcd]/) will return 'a'
- You can use a caret (^) to negate what is between the brackets. This means that the bracket expression will match any character that is not in the list.
    - kind of like an inverse of the brackets.
- You can use a hyphen (-) to specify a range of characters. For example, [a-z] matches any lowercase letter.
- You can use a backslash (\) to escape a hyphen (-) or a closing bracket (]). For example, [a\-z] matches a hyphen (-) or a lowercase letter.
    - remember that these character sets are case sensitive, unless you set the i flag
- Curly braces are used to specify the number of characters to match. For example, [a-z]{3} matches three lowercase letters.
    - you can use these in conjunction with a comma to specify more than one amount of characters to match.
- Parentheses represent remembered groups or matches. For example, ([a-z]{3}) matches three lowercase letters and remembers the match.


### Character Classes



### The OR Operator

### Flags

### Character Escapes

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
