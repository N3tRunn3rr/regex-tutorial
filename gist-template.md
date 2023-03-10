# Title (replace with your title)

Introductory paragraph (replace this with your text)

## Summary

Briefly summarize the regex you will be describing and what you will explain. Include a code snippet of the regex. Replace this text with your summary.

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

### Character Classes

### The OR Operator

### Flags

### Character Escapes

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
