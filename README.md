# Class of August 20, 2023

## Regular Expressions (RegEx)
1. A Regular Expression or RE or Regex is a specifies a set of strings that matches it. 
2. Functions in the module let us check if the specified string matches given RE. 
3. Regex can contain both Special Characters and Ordinary Characters. Most Ordinary Characters like `A` or `a`
or `0` are simplest Regular Expressions.
4. Regular Expressions in Python are powerful tool for complex strings and text 
data. 
5. RegEx are always imported through **re** module. Regular Expressions are even though complex but makes easy to 
format strings rather we use For Loops, Parsing etc. 
6. Syntax of Regular Expressions is as follows:
```commandline
re.findall(pattern, string, flag)
pattern = the defined criteria of what we want to find or search. Pattern can be either Ordinary Characters or 
Special Characters. 
string = the place from where we want to find.
flag = Flag is if there is specific search criteria. Default is "False" which is 0. Flag = 1 is True
```
Regular Expressions are outputted in Lists. 
7. We cannot pass 2 Flags in the same function but in different we can:
```commandline
re.findall(pattern, string, re.Multiline)
re.findall(pattern, string, re.IGNORECASE)
```
8. REs allow us to manipulate strings on the pattern we define making it easy to perform operations.

### Patterns
In Regular Expressions (RegEx), a pattern refers to the sequence of characters that defines a specific search criteria. 
Patterns are the heart of regular expressions; they allow you to describe a set of strings that you want to match or manipulate within a larger text.
Patterns can include a combination of *ordinary characters*, *special characters*, and *metacharacters* that have 
special meanings within the context of RegEx.
1. **Combination of Characters**: Patterns are built by combining different characters and metacharacters. For 
   example, abc is a simple pattern that matches the sequence **"abc"** in a string.
2. **Special Characters**: Special characters have predefined meanings in RegEx. For example, `.` matches any character 
**except a newline**, `*` matches zero or more occurrences, and `+` matches one or more occurrences.
3. **Characters Classes**: Character classes allow you to define a set of characters that can match at a certain position. 
For instance, `[aeiou]` matches any vowel.
4. **Quantifiers**: Quantifiers determine how many times an element should occur. For example, {2,5} means the preceding element should occur between 2 to 5 times.
5. **Anchors**: Anchors define positions within the text. ^ and $ anchor to the start and end of a line (or string with re.MULTILINE).
6. **Alternation**: The pipe symbol | allows you to create alternatives within a pattern. For example, cat|dog matches either "cat" or "dog".
7. **Groups and Captures**: Parentheses () define groups and capture portions of the matched text. These can be used for extracting specific parts of the match.
8. **Escape Characters**: Some characters have special meanings in RegEx. To match them literally, you need to escape them with a backslash `\`.
9. **Modifiers(Flags)**: Flags modify how a pattern is applied, like making it case-insensitive or enabling multiline matching.

Here's a simple example of a pattern: Suppose you want to find all email addresses in a text. The pattern for a basic 
email address might look like `\w+@\w+\.\w+`, where 
* \w matches any word character and 
* "+" indicates one or more occurrences.

### Flags 

In the context of Regular Expressions (RegEx), a flag is an optional modifier that you can apply to a regular expression pattern. Flags control how the pattern is matched against the input string. They provide additional instructions to the RegEx engine. Some common flags include:
1. `**re.IGNORECASE**`: Makes the pattern case-insensitive, so it matches both uppercase and lowercase characters.
2. `**re.MULTILINE**`: Changes the behavior of ^ and $ anchors to match the beginning and end of lines within a 
   multiline string.
3. `**re.DOTALL**`: Makes the dot (.) match any character, including newline characters.
4. `**re.VERBOSE**`: Allows you to write more readable and organized patterns using whitespace and comments.

## Special Characters 

In Regular Expressions, special characters are symbols that have special meanings and are used to define patterns for 
searching and manipulating text. These characters are used to represent certain classes of characters or to specify how 
many times a certain element should repeat

1. dot (.) matches any character except backslash n or \n.
2. Caret (^) matches the start of the String. In **MULTILINE** mode also matches immediately after new line.
3. Plus (+) causes resulting REs to match **1** or more repetitions of preceding REs. `ab+` will match "a" followed 
   by non-zero numbers of "b's"; it will not just match "a". REs should Appear at least once. 
4. Dollar ($) matches end of the string or just before the new line at end of string and in **MULTILINE** also 
   matches before new line.
5. Asterisk (*) causes resultant REs to match `0` or more repetitions of preceding REs, as many repititions are 
   possible. `ab*` will match 'a', 'ab' or 'a' followed by any number of "b's". REs can appear 0 or as many unlike + 
   that has to be at least 1. If empty text, * will return empty []. 
6. Question Mark (?) will match 0 or 1 of preceding REs. `ab` will match either `a` or `b`. In short, it means optional.
**Rule** to convert any special character in to normal character, use `\` followed by a special character.
Example:
```commandline
pattern = "." # any character without \n
pattern = "\." # Ordinary dot character. 
pattern = "\+" ordinary plus character
```
7. [] is used to indicate set of characters. In a Set:
* Characters can be listed Individually eg [aml] will match `a`, `m` or `l`.
* Ranges of characters can be indicated by giving two  characters and separate them by `-`, like `[a-z]` will 
  match any lowercase ASCII letter. 
* Special characters lose their speciality inside Brackets []. Meaning that any special character will be treated as 
  a normal character inside []. 
8. Curly Braces {m,n} causes Resulting REs to match from "m" to "n" attempting to match as many as possible.
9. `\d` Matches unicode decimal digit [0-9]
10. `\w` matches [A-z]

## Miscellaneous

### Word Boundary Concept
The word boundary concept in Regular Expressions allows you to match patterns that are at the edges of words or surrounded 
by non-word characters. A word boundary \b is a zero-width assertion that doesn't consume any characters but asserts a 
specific position in the string. It's often used to match whole words.
* \b: Matches a position where a word starts or ends. It's often used as `\bword\b` to match the entire word "word."

1. Word Boundary is denoted by `\b`. This concept checks the character boundary as defined. 
2. Matches the empty string, but only at the beginning or end of a **word**.
3. A word is defined as a sequence of word characters.
4. To apply Boundary concept, use `r` before pattern
`pattern = r'STRING'`
5. Use the `r'\bword\b'` pattern to match the whole word

A string has the following positions that qualify as word boundaries:

* Before the first character in the string if the first character is a word character (\w).
* Between two characters in the string if the first character is a word character (\w) and the other is not (\W – 
  inverse character set of the word character \w).
* After the last character in a string if the last character is the word character (\w)

In the example `Python 3!` has *four* words: 
1. Before the letter P (criteria #1)
2. After the letter N (criteria #2)
3. Before the digit 3 (criteria #2)
4. After the digit 3 (criteria #2)

Word boundaries are important for ensuring precise matching of words within a larger text. They help avoid partial 
matches and ensure that you're matching complete words rather than substrings within words.
