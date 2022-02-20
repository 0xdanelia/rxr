## Regular Expression Replacer
A command line tool to *find + replace* using regular expressions in linux.
This tool uses Python's `re` module as its regex engine.

```
rxr [OPTION...] EXPRESSION REPLACEMENT
```

Pass input in via stdin. Set your regex and replacement text via command 
line arguments. Any input text matching your regex will be replaced by 
your specified replacement text. Any unmatching text will remain unchanged. 
Then the results are printed to stdout.


### Installation

rxr is a single Python file. Simply download the file, then copy it to a location in your `$PATH` to use it.
```
git clone https://github.com/0xdanelia/rxr
cd rxr
cp rxr.py /usr/local/bin/rxr
```

### Examples

```
[0xdanelia]$ echo "hello_FooBar_world" | rxr --ignore-case '_[a-z]*_' '@'
hello@world
```
```
[0xdanelia]$ tree
.
├── README.md
└── rxr.py

[0xdanelia]$ tree | rxr '([a-z]+)\.py' 'Python file: \1'
.
├── README.md
└── Python file: rxr
```
```
[0xdanelia]$ seq 1 5
1
2
3
4
5

[0xdanelia]$ seq 1 5 | rxr '\n' ', '
1, 2, 3, 4, 5, 

[0xdanelia]$ seq 1 5 | rxr '\n' ', ' | rxr '^' '{' | rxr ', $' '}'
{1, 2, 3, 4, 5}
```

### Options
These flags must be set prior to declaring the expression and replacement text
```
rxr [OPTION...] EXPRESSION REPLACEMENT

  -i, --ignore-case     treat uppercase and lowercase letters as the same
  -a, --ascii-only      perform ascii-only matching instead of unicode
  -d, --dot-all         the dot will match on everything, including newlines
  -p, --print           print the number of replacements made
      --count=NUM       if NUM > 0, limit the number of replacements to NUM
      --help            display this help text and exit
```
