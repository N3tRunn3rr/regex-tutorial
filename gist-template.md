# Regex Tutorial

As a web dev student, I have created a tutorial that explains some specific components of regex so that I can better understand them. I hope they help you understand the search patterns of regex as well.

## Summary

A regex or regular expression is a sequence of characters that define a search pattern. Usually this pattern is used by string searching algorithms for "find" or "find and replace" operations on strings, or for input validation. It is a technique developed in theoretical computer science and formal language theory. 
Most characters stand for themselves, and match the corresponding character in the input string, and the simplest form of regex is actual literal text. For example, the regex "abc" matches the string "abc".
- We will look at the following components of regex:

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
- You can use a caret (^) to negate what is between the brackets. This means that the bracket expression will match any character that is NOT in the list.
    - kind of like an inverse of the brackets.
- You can use a hyphen (-) to specify a range of characters. For example, [a-z] matches any lowercase letter.
- You can use a backslash (\) to escape a hyphen (-) or a closing bracket (]). For example, [a\-z] matches a hyphen (-) or a lowercase letter.
    - remember that these character sets are case sensitive, unless you set the i flag
- Curly braces are used to specify the number of characters to match. For example, [a-z]{3} matches three lowercase letters.
    - you can use these in conjunction with a comma to specify more than one amount of characters to match.
- Parentheses represent remembered groups or matches. For example, ([a-z]{3}) matches three lowercase letters and remembers the match.


### Character Classes

- Character classes are predefined sets of characters that you can use in a bracket expression. For example, \d matches any digit character.
- character classes are also called character sets. They are a shorthand way of specifying a set of characters.
    - you can tell the regex engine to match only one character from a set of characters.
    - just place the characters you want to match inside square brackets.
    - ex. if you want to match an a or an e, use [ae]
    - the order of the characters inside a character class does not matter. the regex engine will match any of the characters in the set.
- You can use a caret (^) to negate a character class. This means that the character class will match any character that is NOT in the list.
- Unlike the dot (.), negated character classes also match line breaks.
- To use a backslash (\) in a character class, you must escape it with another backslash. For example, [\\] matches a backslash.
- If you repeat a character class by using the ?, *, or + quantifiers, the entire character class is repeated.
    - you're not repeating just the character inside the character class.
    - ex. [ae]* matches zero or more a's or e's.

### The OR Operator

- The OR operator (|) matches either the expression before or the expression after the operator.
- The OR operator has a lower precedence than the concatenation operator, so a|b*c matches either a or bc.
- The OR operator has a higher precedence than the quantifier operators, so a*|b matches a* or b.
    - the OR operator acts like a boolean. it will match either the expression before or the expression after the operator. it will not match both. 
    - it will also be tested in order no matter if its in a group or a whole expression.

### Flags

- Regex can have flags to modify the search 
- Flags are optional and can be added to the end of the regex expression
- Flags can be added in any order
    - there are only 6 flags in JavaScript:
        - g: global
            looks for all matches in the string, not just the first one.
        - i: ignore case
            makes the regex case insensitive: [a-z] will match both upper and lower case letters.
        - m: multiline
            makes the ^ and $ match the start and end of each line (not only the whole input string)
        - s: dotAll
            makes the dot (.) match all characters, including line breaks.
        - u: unicode
            enables full unicode support. the flag enables correct processing of surrogate pairs.
        - y: sticky
            searching at the exact position in the text

### Character Escapes

- Character escapes are used to match characters that are otherwise interpreted as special regex characters.
    - escaped characters are treated as normal characters.
    - \C, \G, \X, \z, are not supported 
- The following table lists the character escapes that are supported by the JavaScript regular expression engine. 
    - \\ single backslash
    - \0 null character
    - \A start of string
    - \b word boundary
    - \B non-word boundary
    - \d single digit
    - \D single character that is not a digit
    - \E stop processing escaped characters 
    - \l match a single lowercase letter
    - \L match a single uppercase letter
    - \Q ignore escaped characters until \E is encountered
    - \s single whitespace character
    - \S single character that is not whitespace
    - \u single uppercase letter
    - \U single lowercase letter
    - \w single word character
    - \W single character that is not a word character [^a-zA-Z0-9_]
    - \Z end of string

## Author

Kenji Fleming
Hi I am a student in the UCF full stack coding bootcamp and I hope this tutorial on some of the basics of regex was helpful. I found some great resources online for extra information and I will link them below. I hope you enjoyed this tutorial and I hope you have a great day!
* [GitHub](https://github.com/N3tRunn3rr)

## Resources

* [character escapes](https://www.jmp.com/support/help/zh/15.2/index.shtml#page/jmp/escaped-characters-in-regular-expressions.shtml)
* [flags](https://javascript.info/regexp-introduction)
* [grouping constructs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions/Cheatsheet)
* [character classes](https://www.regular-expressions.info/charclass.html)
* [bracket expressions](https://plainenglish.io/blog/regular-expressions-brackets-f2d6f69ffe13)
* [quantifiers](https://learn.microsoft.com/en-us/dotnet/standard/base-types/quantifiers-in-regular-expressions)





