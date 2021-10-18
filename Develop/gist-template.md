#  Tutorial on the regular expressions (Regex)


## Introduction
When registering an account for on any website, almost every piece of information we give for a sign-up or sign-in form is validated:
* Does our email meet the properly formatting with the @ symbol with for most website with a valid email (in use) 
* Does our phone number match the expecting criteria (10 digits, with (), with - sign or with . or sometimes no space 
* Does our password meet the acceptance criteria (a certain length, with upper case, lower case, digit, special characters)
* For website including payment they will check our payment card is valid (card number, exp date and cvv code)
* For delivery website and app they will check our address exist and our zip code meet the criteria

Those information get to be verified on almost our website and app by using the regular expressions (Regex) someone also call it regexp. Regex is a special sequence of characters that describe a pattern of text that should be found, or matched, in a string or document. By matching text, we can identify how often and where certain pieces of text occur, as well as have the opportunity to replace or update these pieces of text if needed. Regex can be use the the following situation :

* Validation of a user input in HTML forms
* Verification and parsing of a text in files ( a code and app examining a test result)
* Find keywords in emails and web pages, so we can send you targeted add


## Summary
Regex are special sequences of characters that describe a pattern of text that is to be matched.


## Table of Contents
- [Tutorial on the regular expressions (Regex)](#tutorial-on-the-regular-expressions-regex)
  - [Introduction](#introduction)
  - [Summary](#summary)
  - [Table of Contents](#table-of-contents)
  - [Regex Components](#regex-components)
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
  - [Author](#author)


## Regex Components
  - Literals will match the exact characters 
  - | will match the text preceding or following the |
  - [] will match one character from a series of characters
  - . will match any single character 
  - Ranges will specify a range of characters from which we can make a match
  - \w, \d and \s is a range representing word\,digit\ and characters\ and whitespace
  - () will group parts of a regex to limit alternation for part of a regex
  - {} will indicate the exact quantity or a range of quantity of a character we wish to match
  - ? will indicate that a character in the Regex is optional, which mean this specific character could appear either 0 time or 1 time
  - * will quantified the preceding character 0 or more times
  - + will matched the preceding character 1 or more times
  - ^ and $ will be used to match a text at the start and end of a string
  

### Anchors
Anchor in Regex will match a specific expression in order to ensure that we don't match any unintended expression. We use the combination of the ^ at the begging of the expression and $ at the end of the string.
The following example:
^Mongoose: npm package when using MongoDB$ 
will match the following expression:
  - Mongoose: npm package when using MongoDB
but it won't match 
  - MySQL: npm package when using MongoDB
Therefore
  - ^ will ensure to match the begging expression of Mongoose 
  - $ will ensure to match the ending expression by MongoDB 
  Without  the anchor ^ and $ the expression could match anything such as but not limited to:
  - MySQL: npm package when using MongoDB and Mongoose
  - Mongoose: npm package when using SQL


### Quantifiers
- {} will be used as a fixed quantifiers,this will allow us to indicate the exact quantity of a character we want to match, or allow us to provide a quantity range to match. the following example will help to understand the fixed quantifiers work:
      - \w{3} will match exactly a word (in Regex\w will equal to word, \d will be equal to digit and \s will be equal to the whitespace) with exactly 3 characters
      - woo{3}f will match wo followed by 3"o" and then the character f which will match woooof
  
  - \w{4,7} will match at a word with a minimum of 4 characters and a word with a maximum of 7 characters
       - woo{4,7}f will match wo followed by at least 4"o" and maximum 7 "o"then the character f which will match any og the following 
           - woooof
           - wooooof
           - woooooof
           - wooooooof 

Quantifiers are will match the highest quantity of characters which mean the regex wo{2,4} will match the text woooo in the expression, and wont match the expression woo or wooo. 

- ? is a optional quantifiers which will indicate a character in the regex is optional. Therefore, the characters could  appear 0 times or 1 time. For example:
    - behaviou?r will match the expression behavio then characters "u" will occur 0 or 1 time and then then the letter "r". So we could match both of the following:
          - behavior (English USA)
          - behaviour (English UK)
 
- * is a quantifier that will return 0 or more, which mean the regex could match the character 0 time, 1 time or many more times. the following example will help us understand how * quantifier woks:
- the regex meo*w could match the following:
      - me
      - mew
      - meow
      - meooow
      - meoooooooooooow

- + is also a qualifier that will matches the preceding character 1 or more times.\
      - The Regex woo+f will match either
            - woof
            - woooof
            - woooooof
    - but the following expression wont be  a match wof


### OR Operator
- | will allow an alteration, which mean the expression  match the preceding characters OR the following characters. For example  
      - The regex dogs|cats will match either:
          - dogs
          - cats 


### Character Classes
- [] will allow us to match 1 character from a series of characters, will allow the Regex expression to match a word with an incorrect or a different spellings. The following Regex con[sc]en[sc]us will match the following
      - consensus (correct spelling)
      - concensus (incorrect spelling)
      - consencus (incorrect spelling)
      - concencus (incorrect spelling)

- The regex [dog] will match the characters d, o, or t, but it wont match the word dog
- The regex [^dog] wont match the characters d, o, or t, but it could match the characters c, a, or t

So qualifier  give the Regex expression to be ,ore flexible to allow to match correct spelling, incorrect spelling and/or make some alternation


### Flags
N/A


### Grouping and Capturing
- () will group a portion of the Regex, which mean the expression  wil group, capture or subtract what is between the (), which will limit the alteration to a part of the regex. The following
      - The regex I want  some (dogs|cats) will match either:
          - I want some dogs
          - I want some cats 


### Bracket Expressions
- [abc] and [a-c] is exactly the same expression which called a range. It allow us to  specify a range of characters which can match without typing the individual character. So the the regex [abc] or [a-c] would match a, b, or c. The symbol "-" specified that we want to match a range of characters. For the following example:
      - The regex I want [2-9] [b-h]ats will match any of following but not limited to:
          - I want 3 hats 
          - I want 7 cats 
          - I want 9 bats


### Greedy and Lazy Match
- . will allow us to match any single character which could be a (letter, digit, symbol or whitespace) in a given text. we will use it when care to know if the the specific characters exist in the text and do not care about a  specific value. Hence, in the following example:
      - Let’s say we want to match any 9-character piece of text. The regex ......... will match any given word with 9-character. So the word squeezing and the word blackjack will be equally matched 
      - I have . laptops will match both  but not limited to the following:
        - I have 2 laptops
        - I have 9 laptops

In case we want to use the punctuation . we will use \.


### Boundaries
- \b define the boundary which will match a word starting with the specific character. In the following example: 
      - The regex \bcat\b would match to the following:
          - cat in a black cat
    - but it wouldn't match cat to the following but not limited to the expression
          - catatonic
          - tomcat 
          - certificate 
  

### Back-references
- \1 is a back-references which will match the same text as previously matched by a capturing group. for example in a  HTML tags the following Regex:
    - <([A-Z][A-Z0-9]*)\b[^>]*>.*?</\1> will match the following string [A-Z][A-Z0-9]*.  and since it is \1 it will only backlash once but we could write the same expression with \99 and it will match the expression for 99 times  


### Look-ahead and Look-behind
N/A


## Author
- Eleonore Caclard [Github](https://github.com/UofTL)
