Regex- Tutorial

What is regex? Regex stands for regular expression. It is a sequence of charecters that specifies a search pattern in text. It can search for a specific string, integer, match etc. It can be used to locate and manage text. 

## Summary

^(?=.*[A-Z].*[A-Z])(?=.*[!@#$&*])(?=.*[0-9].*[0-9])(?=.*[a-z].*[a-z].*[a-z]).{8}$

This is a regex expression to check a password meets a certain criteria. This code can be broken down to the following:

(?=.*[A-Z].*[A-Z]) --- This part of the sequence is ensuring the password has atleast 2 uppercase letters.

(?=.*[!@#$&*]) --- This section of regex requires the password to contain atleast 1 special charecter.

(?=.*[0-9].*[0-9]) --- This section of the code is requiring the password to have atleast 2 digits.

(?=.*[a-z].*[a-z].*[a-z]) --- This is requiring the password to contain atleast 3 lowercase letters.

.{8} --- This is indicating the password must be atleast 8 charecters in length

$ --- This is our end anchor. 

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

All regex coding utilizes all of the same componants. There most contain a starter and ender sytmbols called anchors and boundries. 

Then depending on how we plan to use our regex code, we will add in an assortment of additional componants in order to sort, confirm or find what we are looking to accomplish. Below are the key componants of what makes up a regex code block and a description of what each charecter type is used for and how it responds. 



## Anchors

Anchors are starting and ending points of our code. Typically a '^' is used to inidicate the beginning of a string and a '$' is used to end our string. 

^ =	Start of string or line	
Example Expression: ^abc
Example Results: abc (appearing at start of string or line)
$ =	End of string, or end of line
Example Expression:	xyz$	
Example Results: xyz (appearing at end of string or line)



## Quantifiers

Quantifiers allow you to declare a certain quantity of a particular charecter. 

* = zero or more of the preceding charecter. 
Example Expression: ha*t 
Example Results: hat,ht, or haaaaat

charecter\{m\} = exactly 'm' occurances of a charecter. 
Example expression: A\{5\} 
Example Results: AAAAA

charecter\{m,n\} = No fewer than 'm' and nore more than 'n'
Example Expression: A\{3,6\}
Example Results: AAA,AAAA,AAAAA,AAAAAA

charecter\{m,\} = Atleast 'm' amount of occurances
Example Expression: A\{3,\}
Example Results: AAA,AAAAAAAAA,AAAAAAAAAAAA but not AA or A.



## OR Operator

The OR operator is a way to match charecters on the right to the left. 

(|) = A logical match between left and right side of '|' 
Example Expression: (t|T)
Example Results: Will match either 't' or 'T' from the input string. 



## Character Classes

Charecter classes is a way to search for text utilizing thier classification. It uses fundamental word charecters such as numbers and letters AND non-word charecters such as spaces and puctuation. 

. = Matches any single character except the newline character.	
Example expression: ab.def	
Example results: abcdef, ab9def, ab=def

\s = Matches a whitespace character (such as a space, a tab, a form feed, etc.)	Example expression: abcd\se	
Example results: abcd e, abcd(tab)e

\S = NOT whitespace	
Example Expression: \S\S\s\S
Example Results: AB D, 99(tab)9

\w	A word character. A word character is a letter, a number, or an underscore. This set of characters may also be represented by the regex character set [a-zA-Z0-9_]	Example Expresion: \w\{1,\}-\w\{1,}
Example Results: well-wishes, far-fetched

\W	NOT a word character
Example Expression:	\w\W\{1,\}\w
Example Results: a,!-(?&;b, 9-5



## Flags

A flag is an optional parameter to a regex that modifies its behavior. 

i =	Ignore Casing	Makes the expression search case-insensitively.

g =	Global	Makes the expression search for all occurrences.

s =	Dot All	Makes the wild character . match newlines as well.

m =	Multiline	Makes the boundary characters ^ and $ match the beginning and ending of every single line instead of the beginning and ending of the whole string.

y =	Sticky	Makes the expression start its searching from the index indicated in its lastIndex property.

u =	Unicode	Makes the expression assume individual characters as code points, not code units, and thus match 32-bit characters as well.



## Grouping and Capturing

Capturing and grouping is a way to treat multiple charecters as a single unit. They are created by placing the characters to be grouped inside a set of parentheses.

For example, the regular expression (dog) creates a single group containing the letters "d" "o" and "g". The portion of the input string that matches the capturing group will be saved in memory for later recall via backreferences



## Bracket Expressions

Bracket expressions aka ranges are a way to sort or search for any series of charecters or a certain number of integers. 

[characters] =	The characters listed inside the brackets are part of a matching-character set
Example Expression: [abcd]
Example Results: a, b, c, d, abcd

[^...] = Characters inside the brackets are a NON-matching set. Any character not inside the brackets is a matching character.	
Example Expression: [^abcd]	
Example Results: Any occurrence of any character EXCEPT a, b, c, d. For instance, when, zephyr, e, xyz

[character-character] = Any character in the range between two characters, including the characters, is part of the set	
Example Expression: [a-z]
Example Reuslts: Any lowercase letter

[^character] = Any character that is NOT the listed character
Example Expression:	[^A]
Example Results: Any character EXCEPT capital A

Ranges can also be combined by concatenating. For instance:	[f-hAC-E3-5]	Matches any occurrence of an f, g, h, A, C, D, E, 3, 4, 5

Ranges can also be modified with a quantifier. For instance:	[a-c0-2]*	Matches zero or more consecutive occurrences of a, b, c, 0, 1, 2. For example, ac1cb would match



## Greedy and Lazy Match

'Greedy' means match longest possible string.

'Lazy' means match shortest possible string.

For example, the greedy h.+l matches 'hell' in 'hello' but the lazy h.+?l matches 'hel'.

Lazy will stop as soon as the condition l is satisfied, but greedy means it will stop only once the condition l is not satisfied any more



## Boundaries

Boundries are expressions that specifically searches a certain series of letters or string. It is limited to the begining or end of a word. 

\b = word boundry. Specifically matching the END of a word. 
Expression Example: ing\b 
Example Results: Act-ing, fish-ing etc. 

\B = NOT word boundry. Meaning if using the same example above, it would include all findings where -ing is anywhere in a word.
Example Expresion: \Bing\B
Example Results: St-ing-er or S-ing-er 

\< = The start of a word. 
Example Expresion: \< what
Example Resutls:  It would locate any word starting with 'what' i.e what-ever.

\> = The end of a word. 
Example Expresion: \>hold
Example Results: It would find be-hold. 



## Back-references

A backreference is specified in the regular expression as a backslash (\) followed by a digit indicating the number of the group to be recalled. For example, the expression (\d\d) defines one capturing group matching two digits in a row, which can be recalled later in the expression via the backreference \1.

To match any 2 digits, followed by the exact same two digits, you would use (\d\d)\1 as the regular expression:

Enter your regex: (\d\d)\1
Enter input string to search: 1212
I found the text "1212" starting at index 0 and ending at index 4.
If you change the last two digits the match will fail:
 
Enter your regex: (\d\d)\1
Enter input string to search: 1234
No match found.



## Look-ahead and Look-behind

Lookahead and lookbehind, collectively called “lookaround”, are zero-length assertions just like the start and end of line, and start and end of word. The difference is that lookaround actually matches characters, but then gives up the match, returning only the result: match or no match. That is why they are called “assertions”. They do not consume characters in the string, but only assert whether a match is possible or not. Lookaround allows you to create regular expressions that are impossible to create without them, or that would get very longwinded without them.

## Author

My name is Mike Jones and I am currently a territory manager for an Orthopedic sales distributorship. I have been selling medical implants in surgery for the last 12 years. I have always had a love/hate relationship with it and it has allowed my family to grow and prosper however, its come at a cost. Long unpredictable hours. Missing valuable family time missing my kids grow and I am looking for a change. 

I am married with 2 kids. A 4 year old boy and a 2 year old girl. My family is everything to me and is why I continued in a career i have lost the love for long ago. All I want is to be with them and take them on adventures. We are a very outdoorsy family. We love hiking, camping rafting and fishing. We try to get out as much as we can. 

With all of that, I have always had a passion for computers and coding has always intrigued me. I am ready for a change. I am hoping to pursue something that can challenge me in ways I have not been challenged before and allow me to use parts of my brain I have not, in a long time. I am hoping that I can find a role that will also utilize my previous employment in sales, service and hospitality along with the creative side of coding. 

I am very excited to start a new career. Thank you for reading my tutorial and please feel free to check out my github and linked in. Thanks again and have a great day!!

Mike Jones

github repo:
https://github.com/mwjones2186

Linked in:
www.linkedin.com/in/michael-jones-0617b681
