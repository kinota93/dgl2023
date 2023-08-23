# RegExp Data Generation Language
Using enhanced regular expressions as a Data Generation Language. 
Enhance PCRE by introducing
## data types
- `formatted number` 
- `date`,`time`,`year`, `month`, `day`
- `enum`: gender, weekday-name, month-name, ...
- `set`: colors
  
## random data
  
random data  from data types, following distribution:\
`$type{start:step:end:dist}$`
  
- `$number{1:1}$` outputs `2,3,1,4,...`
- `$number{1:2}$` outputs `3,1,5,7,...`
- `$number{4.00:-0.11:0.00}$` outputs `3.89, 3.57, 4.00, 3.78, ...`
- `$date{'2022-4-1':'7d':'2023-3-31'}$` outputs `'2022-4-15','2022-4-1','2022-4-22',...`
- `$time{'8:00':'1h30m':'21:00'}$` outputs `'9:00','12:00','10:30',  ...` 
  
## sequential data
  
sequential data of some type:\
`type(start:step:end)`

- `$number(1:1)$` outputs `1,2,3,...`
- `$number(1:2)$` outputs `1,3,5,...`
- `$number(4.00:-0.11:0.00)$` outputs `4.00, 3.89, 3.78, 3.57,...`
- `$date('2022-4-1':'7d':'2023-3-31')$` outputs `'2022-4-1', '2022-4-8', '2022-4-15', ...`
- `$time('8:00':'1h30m':'21:00')$` outputs `'9:00','10:30', '12:00', ...`
  
## variables
- `{:a:}`

- *functions*

  - `fn x=>2*x`

## PCRE: Perl Compatible Regular Expressions  

### delimiters `/`
`/pattern/`
  
### meta charactors
  
- meta-chars outside square brackets\
`\ ^ $ . [ ] | ( ) ? * + { }` 

- meta-chars inside square brackets\
`\`  general escape char\
`^`  negste the class (only if the first character)\
`-`  indicate character range
  
### escape sequences

- **unicode character properties** 
- **character classes**
  - posix notations\
    `[:alnum:] [:alpha:] [:ascii:] [:blank:] [:digit:] [:xdigit:]`\
    `[:lower:] [:upper:] [:punct:] [:space:] [:word:] [:print:]`
  - character types\
     `\d \D \s \S \w  \W`
  
### alternation `|`
  
Vertical bar characters are used to separate alternative patterns
  
### dot

Outside a character class, a dot in the pattern matches any one character in the subject, including a non-printing character, but not (by default) newline.
  
### repetition
  
Repetition is specified by quantifiers, which can follow any of the following items: single char, dot, char class, parenthesized subpattern.
  
- quantifier specified by minimum ans maximum\
`{n,m}, {n}, {n,}`
- single-character quantifier\
`*`  equivalent to `{0,}`\
`+`  equivalent to `{1,}`\
`?`  equivalent to `{0,1}`
  
### subpattern
  
Subpatterns are delimited by parentheses (round brackets), which can be nested. Marking part of a pattern as a subpattern does two things:
  
- localizes a set of alternatives
- sets up the subpattern as a capturing subpattern