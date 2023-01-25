# Matching an Email Address in Regex

## Summary

This tutorial will explain the use of regex using the expression below:<br>
~~~
/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/
~~~
This expression is useful for finding a strings containing email addresses with differing username and domain names.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Boundaries](#boundaries)

## Regex Components

***

### **Anchors**
**Anchors** are a regex token that asserts that a regex matches at a specific location within a string. 
`^` and `$` are examples of anchors. `^` sets a regex match to the beginning of a string, while `$` sets regex match to the end of a string. 
<br>

~~~
hat
hate
chat
chatter
~~~

Given the strings above, the regex `^hat` would match the **first** two strings because `hat` appears at the beginning of each of those strings.
<br> 

The regex `hat$` would match the **third** string because `hat` appears at the end of that string. 
Finally, the regex `^hat$` would only match the **first** string because `hat` appears at the beginning and end of that string.
<br>

In our expression, the whole string is wrapped in `^` and `?`, so the string must match all specifications exactly.

***

### **Quantifiers**
A **quantifier** defines how many instances of the string, or section of the string, that exist to match the regex. They may include the numeric range of characters for which your regex is searching.  
<br>

`*`, `+`, and `?` are quantifiers which match repeated sequences. 

~~~
*   Matches the pattern zero or more times
+   Matches the pattern one or more times 
?   Matches the pattern zero or one time

{2     Matches the pattern exactly twice
{2, }  Matches the pattern two or more times
{2, 4} Matches the pattern two, three, or four times
~~~

***

### **Greedy and Lazy Match**
**Quantifiers** can be categorized as **greedy** or **lazy**. By default, they are greedy, which means they match the longest occurrence of a pattern. A lazy match, on the other hand, matches the fewest number of characters in a string. 
<br>

In our expression, we have two `+` quantifiers. 

`([a-z0-9_\.-]+)` and `([\da-z\.-]+)` indicates that any character within the brackets is expected to appear at least once in the string. Because quantifiers are greedy by default, it will match the pattern many times as possible.
<br>

The final capturing group, `([a-z\.]{2,6})` in our expression contains a quantifier that looks for the pattern between two and six times. 

***

### **OR Operator**
The **OR** operator ( `|` ) allows you to the option to search for one character **OR** another. An expression using an OR operator may be written as `(1|2|3)`. In this example, we are looking for 1 *or* 2 *or* 3. 

**<span style="color:red">There are no OR operators used in our email expression.</span>**

***

### **Character Classes**
A **character class** defines a set of characters and acts as a "shortcut" to different classes of characters. 

~~~
\s  whitespace          

\w  any alphanumeric character       
    same as [A-Za-z0-9_]    

\d  any numeral digit                
    same as [0-9]

.   any character except newline 
~~~

Our expression contains `@([\da-z\.-]+)`, which includes `\d`, indicating we are looking for any numeral digit after the @ symbol. 

***

### **Flags**
A **flag** is placed at the end of a regex, after the second slash. The purpose of a flag is to define additional functions. 

An `i` flag after the second slash (e.g. `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/i`), would indicate that the regex is case-insensitive.


**<span style="color:red">There are no flags used in our email expression.</span>**

***

### **Grouping and Capturing**
A **grouping construct** allows you to check multiple "parts," or **subexpressions** of a string for certain parameters. Because an email address has a username and domain name, our expression requires multiple grouping constructs for each part of the email address.
<br>
Our expression is grouped into three subexpression: 
<br>

**Username**<br>
`([a-z0-9_\.-]+)`<br>
Matches one or more (+) characters in these sets: a-z, 0-9, underscore (`_`), escaped (`\.`), hyphen (`-`)
<br>

**Domain name** (e.g. hotmail, gmail, yahoo)<br>
`([\da-z\.-]+)`<br>
Matches one or more (+) characters in these sets: a-z, 0-9, escaped (`\.`), hyphen (`-`)
<br>

**Domain name** (e.g. com, net, org)<br>
`([a-z\.]{2,6})`<br>
Matches two to six ({2,6}) characters in these sets: a-z, escaped (`\.`)

***

### **Bracket Expressions**
A **bracket expression** is a pattern that is defined within a set of square brackets (`[]`). Bracket expressions allow us to define the characters we want to include and match. <br>
Our expression contains three bracket expressions:

`[a-z0-9_\.-]`<br>
a-z, 0-9, underscore (`_`), escaped (`\.`), hyphen (`-`)
<br>

`[\da-z\.-]`<br>
a-z, 0-9, escaped (`\.`), hyphen (`-`)
<br>

`[a-z\.]`<br>
a-z, escaped (`\.`)
<br>

***

### **Boundaries**
A regex **boundary** (`\b`) allows you to search for whole words. 

~~~
\bRegex\b       Matches the word "Regex" exactly
~~~

**<span style="color:red">There are no boundaries used in our email expression.</span>**

***

## **Author**

Zachary Berkley<br>
[GitHub](https://github.com/ZBerkley88)
