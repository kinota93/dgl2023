# RegExp Data Generation Language
Using enhanced regular expressions as a Data Generation Language. 
Enhance PCRE by introducing
- *data types*
  formatted numbers, 
  date, time,
  domain: weekday-name, month-names, ...
- *random data*
  1. random numbers following some distribution
  1. random data from data types
- *sequential data*
  1. sequential data of some type
  `1,2,3,...`
  `1,3,5,...`
  `4.00, 3.89, 3.78, 3.57,...`
  `'2022-4-1', '2022-4-8', '2022-4-15', ...`
  `'9:00','10:30', '12:00', ...`
- *variables*
- *functions*
   

## PCRE: Perl Compatible Regular Expressions  
- delimiters /
  /pattern/
- meta charactors
  - meta-chars outside square brackets
    \ ^ $ . [ ] | ( ) ? * + { } 
  - meta-chars inside square brackets
    \  general escape char
    ^  negste the class (only if the first character)
    \-  indicate character range
- escape sequences
- unicode character properties 
- character classes
  1. posix notations
    [:alnum:] [:alpha:] [:ascii:] [:blank:] [:digit:] [:xdigit:]
    [:lower:] [:upper:] [:punct:] [:space:] [:word:] [:print:]
  1. character types
    \d \D \s \S \w  \W
- alternation |
  Vertical bar characters are used to separate alternative patterns
- anchors
- dot
  Outside a character class, a dot in the pattern matches any one character in the subject, including a non-printing character, but not (by default) newline.
- repetition
  Repetition is specified by quantifiers, which can follow any of the following items: single char, dot, char class, parenthesized subpatt.
  1. quantifier specified by minimum ans maximum
   `{n,m}, {n}, {n,}`
  1. single-character quantifier
   `*`  equivalent to `{0,}`
   `+`  equivalent to `{1,}`
   `?`  equivalent to `{0,1}`
- subpattern
  Subpatterns are delimited by parentheses (round brackets), which can be nested. Marking part of a pattern as a subpattern does two things:
  1. localizes a set of alternatives
  1. sets up the subpattern as a capturing subpattern