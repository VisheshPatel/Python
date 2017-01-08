
# Identifiers:

- `\d` = any number
- `\D` = anything but a number
- `\s` = space
- `\S` = anything but a space
- `\w` = any letter
- `\W` = anything but a letter
- `.`  = any character, except for a new line
- `\b` = space around whole words
- `\.` = period. must use backslash, because . normally means any character.

# Modifiers:

- `{1,3}` = for digits, u expect 1-3 counts of digits, or "places"
- `+` = match 1 or more
- `?`  = match 0 or 1 repetitions.
- `*` = match 0 or MORE repetitions
- `$` = matches at the end of string
- `^` = matches start of a string
- `|` = matches either/or. Example x|y = will match either x or y
- `[]` = range, or "variance"
- `{x}` = expect to see this amount of the preceding code.
- `{x,y}` = expect to see this x-y amounts of the precedng code

# White Space Characters:

- `\n` = new line
- `\s` = space
- `\t` = tab
- `\e` = escape
- `\f` = form feed
- `\r` = carriage return

# Characters to REMEMBER TO ESCAPE IF USED!

```
. + * ? [ ] $ ^ ( ) { } | \
```

# Brackets:

- `[]` = quant[ia]tative = will find either quantitative, or quantatative.
- `[a-z]` = return any lowercase letter a-z
- `[1-5a-qA-Z]` = return all numbers 1-5, lowercase letters a-q and uppercase A-Z

# Sample Code

```

import re

# r'expression' denotes raw string which include newline(\n), tab(\t), etc
print re.split(r'\s*', 'here are some words')
print re.split(r's*', 'here are some words')
print re.split(r'(\s*)', 'here are some words')
print re.split(r'[a-fA-F]', 'adsfjkl;asdfjk;lASDDFG', re.I | re.M)

print re.findall(r'\d{1,9}\s\w+\s\w+\.', 'street no 1023 india INDIA.com')

# Python offers two different primitive operations based on regular
# expressions: match checks for a match only at the beginning of the
# string, while search checks for a match anywhere in the string (this is
# what Perl does by default).

searchObj = re.search(
    r'(.*) are (.*?) .*', "Cats are smarter than dogs", re.M | re.I)

print searchObj.group()
print searchObj.group(1)
print searchObj.group(2)

# replace comment with blank
print re.sub(r'#.*$', "", "2004-959-559 # This is Phone Number")
```

# Output

```
['here', 'are', 'some', 'words']
['here are ', 'ome word', '']
['here', ' ', 'are', ' ', 'some', ' ', 'words']
['', '', 's', 'jkl;', 's', '', 'jk;l', 'S', '', '', 'G']
['1023 india INDIA.']
Cats are smarter than dogs
Cats
smarter
2004-959-559 
```
