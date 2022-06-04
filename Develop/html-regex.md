# Regular Expression HTML Explained

Welcome! This gist will explain the the regular expression (regex) utilized to match an HTML tag.

## Summary

Thank you for continuing. The regex I will break down today can be seen below:

`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]_)_\/?$/`

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Character Classes](#character-classes)
- [Bracket Expressions](#bracket-expressions)
- [Grouping and Capturing](#grouping-and-capturing)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [OR Operator](#or-operator)
- [Flags](#flags)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)
- [Auther](#author)

## Regex Components in Our HTML regular expression

### Anchors

- An anchor in regex ensures that the expression being matched is anchored to a certain position in the string.

- As shown above, the HTML regex starts with the symbol \^. This symbol is called the start-of-string anchor, and as it is named, it ensures that a match to our expression is positioned to match the start of the string that we are matching. This positioning is need to preserver proper syntax in matches.

        - In the HTML Regex, `^(https?:\/\/)` ensures that we are matching to a website that begins with http. It also indicates that http is the beginning of a string. For example:

            - Placing the start-of-string anchor in front of /^🍎🍎🍊/ would allow for the return of that same pattern if used against input like  🍎🍎🍊🍋🍎, however, the start-of-string anchor would prevent a match when compared against input like 🍎🍋🍋🍎🍎🍊

- The \$ is known as the end-of-string anchor, and it appears in the HTML regex here: `([\/\w \.-]_)_\/?$` This end-of-string anchor indicates the end of a string, and also ensures that our URL's end matches the end of the URL we are testing against. For example:

        - Placing the end-of-string anchor behind /🍎🍎🍊$/ would allow for the return of that same pattern against input like 🍎🍋🍋🍎🍎🍊, but nothing would be matched against and input like 🍎🍋🍋🍎🍎🍊🍋

### Quantifiers

- A regex quantifier specifies the number of consecutive occurences of the expression or character which directly preceeds it. The Quantifiers used in this regex example are \?\,\+\, and \{}\.

  - The ? character appears twice, as seen in the code snippes below:

    - `(https?` as a portion of the beginning of the regex HTML to indicate that the \"s" in https is optional, and that the expression http or https will be recognised.
    - `_\/?` as a portion of the end of the regex HTML as the \/ character is also optionally utizlied in a URL, and using or not using /, will result in recognition.

  - The \+ quantifier is seen in the snippet `([\da-z\.-]+)`. This quantifer states that any input such as characters or numbers placed within in the \[] at least one, but possilby more, occurrences.
  - The \{} quantifier is seen in the snippet `([a-z\.]{2,6})`. Here, the HTML regex will be on the alert for any letter betwee a and z, which will have an occurrence of at least 2 times, but not more than 6 times.

### Character Classes

- Character classes are found enclosed within [Bracket Expressions](#bracket-expressions), they can tell the regex engine to match only one, or several charactes. In this regex HTML the, this use case is seen three times:

  - `([\da-z\.-]+)` - `([a-z\.]{2,6})` - `([\/\w \.-]_)`

  -In the first instance, the characters specified are a range of characters from da-z (as specified by the - between them)
  -In the second instance, the characters are a range of characters from a-z , used in concert with the \{} to specify the number of times these characters may occurr
  -In the third instance, the characters are /, comma, w, ., and the underscore. These also feature backslash which is a character with a special meaning, that is used to escape characters as a literal, and example being a plus sign in an equation like 1+1=2, where the lack of a backslash preceding the plus symbol would yield 111=2.

### Bracket Expressions

- As noted above, bracket expressions are a list of characters and/or classes which are found enclosed in brackets \[]. - Bracket expressions can be used to match single or multiple characters in a list. - In the HTML regex, they are found three times: `([\da-z\.-]+)` - `([a-z\.]{2,6})` - `([\/\w \.-]_)`

### Grouping and Capturing

- Enclosing a group of characters in parantheses is referred to as Group and Capturing. This practice allows the user to apply regex operators, such as quantifiers, to the entire grouped regex. - Groups and captured characters occur four times in this regex HTML:

        - `(https?:\/\/)`
        - `([\da-z\.-]+)`
        - `([a-z\.]{2,6})`
        - `([\/\w \.-]_)`

### Greedy and Lazy Match

- A greedy match is utilized to identify the longest possilbe string that can be matched. In this HTML regex, the use of \+ in `([\da-z\.-]+)` is an example of a greedy match, as it allows for one, but is open to many more

- A lazy match is used to identify the shortest possible string that can be matched. The use of `([a-z\.]{2,6})` in our HTML regex is an example of a lazy match, as this quantifier looks for at least a minimum number of matches, but sets a limit for a maximum number of matches.

### Boundaries

- Boundaries define where a match is taking place in a regex expression. - In JavaScript, particularly, \b is used to signal to the regex engine to check that the position in which it was encountered is a word boundary. - \^ and \$ are boundaries utilized to dilineate definited starting and ending points. They are each used in the HTML regex here `^(https?:\/\/)` and here `([\/\w \.-]_)_\/?$`

## Other Helpful Regex Definitions

### OR Operator

- The "OR" operator \| is used when attempting to choose between mulitple characters. A

  - And example of the use of an "OR" operator is this, A|B|C means A,B, or C.

### Flags

- Flags are optional regex parameters that modify the behavior of searching. A flag will cause the regex to search in a different way. There are 6 flags in JavaScript. They are i, g, s, m, y, and u.

### Back-references

- Back references are utilized to match text which was previously matched by a capturing group. The use of back references is helpful when utilizing previous parts of a pattern, and also can ensure that two pieces of a string match.

### Look-ahead and Look-behind

- Look-ahead and look-behind are used to find matches for a pattern that are followed or proceeded by another pattern. Together these two are called "lookaround."

## Author

Hi! My name is Aaron Stokes. I am newly minted web developer making my way towards a career in the field. I am a graduate of The College of Charleston with a Bachelors degree in Earth Scienes/Geology. I hold and Associates Degree in Applied Sciences: Nursing, and am currently a Registered Nurse. I am always in the process of learning, but am currently deeply immersed in node.js, HTML, CSS, JavaScript, and the MERN stack. Please visit my github [here!](https://github.com/hestokes)
