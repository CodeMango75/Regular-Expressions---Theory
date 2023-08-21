# Regular Expressions 

## Regular Expressions (RegEx)
1. A Regular Expression or RE or Regex is a sequence of characters that matches the character sequence with search pattern. 
2. Functions in the module let us check if the specified string matches given RE. 
3. Regex can contain both Special Characters and Ordinary Characters. Most Ordinary Characters like `A` or `a` or `0` are simplest Regular Expressions.
4. Regular Expressions in Python are powerful tool for complex strings and text 
data. 
5. RegEx are always imported through **re** module. Regular Expressions are even though complex but makes easy to search characters in strings rather using long codes of FOR, PARSE etc 
6. Syntax of Regular Expressions is as follows:
```commandline
re.findall(pattern, string, flag)
pattern = the defined criteria of what we want to find or search. Pattern can be either Ordinary Characters or 
Special Characters. 
string = the place from where we want to find.
flag = Flag is if there is specific search criteria. Default is "False" which is 0. Flag = 1 is True
# Please note that at this stage, we only covered findall() function. 
```
7. Regular Expressions are outputted in Lists. 
8. We cannot pass 2 Flags in the same function but in different we can:
```commandline
re.findall(pattern, string, re.Multiline)
re.findall(pattern, string, re.IGNORECASE)
```
9. REs allow us to manipulate strings on the pattern we define making it easy to perform operations.

### Patterns
In Regular Expressions (RegEx), a pattern refers to the sequence of characters that defines a specific search criteria. 
Patterns are the heart of regular expressions; they allow you to describe a set of strings that you want to match or manipulate within a larger text.
Patterns can include a combination of *ordinary characters*, *special characters*, and *metacharacters* that have 
special meanings within the context of RegEx.
1. **Combination of Characters**: Patterns are built by combining different characters and metacharacters. For 
example, abc is a simple pattern that matches the sequence **"abc"** in a string.
2. **Special Characters**: Special characters have predefined meanings in RegEx. For example, `.` matches any character **except a newline**, `*` matches zero or more occurrences, and `+` matches one or more occurrences.
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

### The **Dot (.)** Character

**Dot (.)** matches any character except backslash n or \n.
```
# Dot . Character 
import re
string = "Talaal Yousoof is currently Studiyng Data Sciences"
pattern = '.'
dotmatch = re.findall(pattern, string)
print(dotmatch) # since there is only one dot it matches only one character except \n had there been multiple dots, it would have matched the correspondent characters as per dots defined. 

```
```
# Dot with preceding character
pattern2 = '.a'
dotmatch2 = re.findall(pattern2, string)
print(dotmatch2) # . will match each character preceding a
['Ta', 'la', 'Da', 'ta'] 
```
```
# Dot with Proceding Character
pattern3 = 'a..'
dotmatch3 = re.findall(pattern3, string)
print(dotmatch3)
# Output : ['ala', 'al ', 'ata']
```
### **Caret (^)**
Matches the start of the String. In **MULTILINE** mode also matches immediately after new line.

If you use the caret (^) at the beginning of your RegEx pattern, it will look for matches that occur at the very beginning of a line or a piece of text.
For example, if you have the RegEx pattern ^Hello, it will only match instances of "Hello" that appear at the very beginning of a line or string, and not if "Hello" appears later in the text.

```
# Caret Character
string2 = "Hello I am Talaal \n Hello I am Omer \n Hello World"
pattern_caret = "^Hello"
caretmatch = re.findall(pattern_caret, string2)
print(caretmatch) # Output ['Hello']
```
This is single output because its not **MULTILINE**. Since in the example, Hello is appearing thrice, we can use **MULTILINE** Flag:
```# Caret Character
string2 = "Hello I am Talaal \nHello I am Omer \n Hello World"
pattern_caret = "^Hello"
caretmatch = re.findall(pattern_caret, string2, re.MULTILINE)
print(caretmatch)
# Output => ['Hello' , 'Hello'] 
```
Why wasn't the third "Hello" matched? Notice the space after new line (\n), thats a character.
```
CaretString = """Python was invented by Goidum Van Rossum
He is from Netherlands"""
caretpattern = "^P..+"
matchCaret = re.findall(caretpattern, CaretString)
print(matchCaret)
# Output => ['Python was invented by Goidum Van Rossum']
```
### **Plus (+)**
Plus + causes resulting REs to match **1** or more repetitions of preceding REs. `ab+` will match "a" followed 
by non-zero numbers of "b's"; it will not just match "a". Character should appear at least once. 
```
text = """Pakistan Zindabad! Pakistan is in Asia
Pakistan was Founded by Quaid-e-Azam"""
pluspattern = ".+"
plusmatch = re.findall(pluspattern, text)
print(plusmatch) #It printed whole sentence until line break. + matches the character that should appear at least once. In this case, dot matches every character individually since there is a single dot, and plus concatenates them. 
```
**Note**: *Had thre been no element before plus OR element after plus, it would have resulted in an error because it matches preceding character occuring at least once and there is either nothing to repeat at position 0.*

### **Dollar ($)**
Matches *end of the string* or just before the new line at end of string and in **MULTILINE** also matches before new line. In simpler terms, if you use the dollar sign ($) at the end of your RegEx pattern, it will look for matches that occur right at the very end of a line or a piece of text. It's like a marker that tells the RegEx engine to focus on finding patterns only at the end of the input.

For example, if you have the RegEx pattern Hello$, it will only match instances of "Hello" that appear right at the very end of a lin or string, and not if "Hello" appears earlier in the text.
```
import re
text = "Hello, this is a sample text. Hello"
# Using $ to match "Hello" at the end of lines
pattern = 'Hello$'
matches = re.findall(pattern, text, re.MULTILINE)
print(matches)
# Output => ['Hello']
```
In this example, the text contains two instances of "Hello." However, only the last "Hello" at the end of the text is matched by the pattern with the dollar sign ($) at the end. 
### **Asterisk (*)** 
Causes resultant REs to match `0` or more repetitions of preceding REs, as many repititions are possible. `ab*` will match 'a', 'ab' or 'a' followed by any number of "b's". REs can appear 0 or as many unlike `+` that has to be at least 1. If empty text, `*` will return empty []. 

### **Question Mark (?)** 
Will match 0 or 1 of preceding REs. `ab` will match either `a` or `b`. In short, it means optional.
1. It indicates that the preceding element in the pattern is optional.
2. This means that the preceding element can occur either zero times or exactly once.
3. In simpler terms, if you use the question mark (?) after a character or group of characters in your RegEx pattern, it means that the RegEx engine will consider that character or group as optional. It can be there, or it might not be there at all, and the pattern will still be considered a match.
4. For example, if you have the RegEx pattern `colou?r`, it will match both "color" and "colour." The question mark makes the "u" in "colour" optional, so the pattern will match regardless of whether the "u" is present or not.
```
import re
text = "The color of the sky is blue. The colour of the ocean is also blue."
# Using ? to make "u" optional in the pattern
pattern = r'colou?r'
matches = re.findall(pattern, text)
print(matches)
# In this example, the pattern colou?r matches both "color" and "colour" in the text. The question mark allows the "u" to be there or not, making the pattern flexible enough to match both variations.
```
### Other Characters 

1. [] is used to indicate set of characters. In a Set:
* Characters can be listed Individually eg [aml] will match `a`, `m` or `l`.
* Ranges of characters can be indicated by giving two  characters and separate them by `-`, like `[a-z]` will 
  match any lowercase ASCII letter. 
* Special characters lose their speciality inside Brackets []. Meaning that any special character will be treated as 
  a normal character inside []. 
2. Curly Braces {m,n} causes Resulting REs to match from "m" to "n" attempting to match as many as possible.
3. `\d` Matches unicode decimal digit [0-9]
4. `\w` matches [A-z]
**Rule** to convert any special character in to normal character, use `\` followed by a special character.
Example:
```commandline
pattern = "." # any character without \n
pattern = "\." # Ordinary dot character. 
pattern = "\+" ordinary plus character
```
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

## Example 1 - Match Dates 
```
datestring = """I was Born in 19/10/1195
Sister 1 in 19*08*1996
Sister 2 in 9.3.2000
"""
patterndate = "\d{1,2}[*/,.]\d{1,2}[*/,.]\d{2,4}"
matching = re.findall(patterndate, datestring)
print(matching) 
```
I know that \d is used for decimal digits 0-9 and {1,2} in first 2 instances means digit can be either 1 or 2 similarly 2 or 4 (in last curly braces). [[*/,.]] means that the pattern can have any of the character in the string
